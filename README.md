# Task Management System

A small project and task management web application written in PHP on Laravel 5.1, with a jQuery and Vue.js 1.x front end. Users sign up, add clients, create projects for those clients, and track weighted, prioritised tasks per project. The front end talks to a JSON API exposed by the same app.

Built on the [Laravel](https://laravel.com) 5.1 application skeleton (MIT). The app-specific code lives in `app/`, `database/`, `resources/views/` and `public/assets/js/`.

The code was added to this repository in a single commit in 2022. Several migrations are dated 2014 to 2016, so parts of it are older than the repository.

## Features

- User registration, login, logout and profile update
- Clients: create, update and delete, optionally listed with their total open task weight
- Projects: belong to a client and store production, staging, dev and GitHub URLs
- Project sharing: invite members by email and remove them
- Tasks: name, description, weight, priority and state. A project's total weight is the sum of its open tasks
- Per-project credentials list (name, username, password)
- Search page and a simple admin page
- JSON API under `/api/` for users, clients, projects, tasks and credentials (`app/Http/routes.php`)

## Stack

- PHP >= 5.5.9, Laravel 5.1, `laravelcollective/html`
- MySQL
- jQuery 2 and Vue.js 1.0 (loaded from a CDN), Sass

## Getting started

```bash
composer install
cp .env.example .env        # then set your DB and mail settings
php artisan key:generate
php artisan migrate
php artisan db:seed         # optional sample clients, projects and tasks
php artisan serve
```

## Project structure

```
app/Http/routes.php           web, API and admin routes
app/Http/Controllers/         Users, Clients, Projects, Tasks, Credentials, Files, Admin
app/{Client,Project,Task,Credential,Upload,User}.php   Eloquent models
database/migrations/          schema, from 2014 to 2016
resources/views/ins/          views for logged-in users (hud, projects, clients, settings)
public/assets/js/controllers/ front-end controllers for clients, projects, users and the hud
```

## Status

This is an older codebase and has not been brought up to date. The routes for project files and uploads are commented out. The `/api/` routes are not inside the authenticated route group.
