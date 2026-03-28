# Project Guide

This guide tracks the setup work done for this repository and records the commands used so the same steps can be repeated later.

## Initialize The Laravel Project

The repository already contained a `docs/` folder, so Laravel could not be initialized directly into `.` with `composer create-project laravel/laravel .`.


## Generate The Laravel App Key

After the project files were in place, the application key was generated:

```powershell
cd d:\Coding\budget-manager-laravel
php artisan key:generate --ansi
```

Result:
- `APP_KEY` was written to `.env`


## Install Frontend Dependencies

Laravel ships with frontend build tooling in the project skeleton, including `package.json` and Vite config. That means Node dependencies still need to be installed even though the backend is PHP.

The command used was:

```powershell
cd d:\Coding\budget-manager-laravel
npm install
```

Result:
- `node_modules/` was created
- `package-lock.json` was generated
- the project is ready to use Vite-based asset commands like `npm run dev`

## Configure PostgreSQL For Local Development

The project is configured to use PostgreSQL in Docker Compose while Laravel runs directly on the host machine.

The Laravel database settings are:

```env
DB_CONNECTION=pgsql
DB_HOST=127.0.0.1
DB_PORT=5432
DB_DATABASE=budget_manager
DB_USERNAME=postgres
DB_PASSWORD=change_me
```

These values were written to:
- `.env`
- `.env.example`

Replace `DB_PASSWORD` with your own local password before starting the database container.

## Add Docker Compose For PostgreSQL

A Docker Compose file was added at the project root:

```powershell
cd d:\Coding\budget-manager-laravel
docker compose up -d
```

Service details:
- service name: `postgres`
- container name: `budget-manager-postgres`
- image: `postgres:16-alpine`
- host port: `5432`
- database: uses `DB_DATABASE` from `.env`
- username: uses `DB_USERNAME` from `.env`
- password: uses `DB_PASSWORD` from `.env`

Persistent storage is handled with the named volume `postgres_data`.


## Current Project Status

The Laravel application is now initialized and both PHP and Node dependencies are installed.

Current state:
- Laravel version: `10.45.1`
- project root: `d:\Coding\budget-manager-laravel`
- docs folder preserved at `docs/`
- Composer dependencies installed in `vendor/`
- Node dependencies installed in `node_modules/`
- Laravel environment configured for PostgreSQL
- Docker Compose file added for PostgreSQL

## Current Environment Notes

The active CLI PHP config file is:

```text
C:\Program Files\php-8.3.3-Win32-vs16-x64\php.ini
```

For PostgreSQL, these PHP extensions must be enabled:
- `fileinfo`
- `pdo_pgsql`
- `pgsql`

This matters because:
- Laravel and Composer expect `fileinfo`
- PostgreSQL connections need `pdo_pgsql` and `pgsql`

The required lines in `php.ini` are:

C:\Program Files\php-8.3.3-Win32-vs16-x64\php.ini

```ini
extension=fileinfo
extension=pdo_pgsql
extension=pgsql
```

Terminal: (check dependencies)
php -m  

## Recommended Next Steps

Suggested order from here:

- update `php.ini` with administrator permissions
- start PostgreSQL with Docker Compose
- run migrations
- install authentication
- install Livewire
- install Filament
