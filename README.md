<p align="center"><a href="https://laravel.com" target="_blank"><img src="https://raw.githubusercontent.com/laravel/art/master/logo-lockup/5%20SVG/2%20CMYK/1%20Full%20Color/laravel-logolockup-cmyk-red.svg" width="400" alt="Laravel Logo"></a></p>

# About Smart CMS

A tutorial system for creating CRUD operations and basic administration interface and working in your own editorial
system.

## Installation


1. Clone project
2. Install Docker (optionally run in PHP ready server)
   1. Install dependencies by docker & sail, you can use `--ignore-platform-reqs`
       ```bash
       docker run --rm \
           -u "$(id -u):$(id -g)" \
           -v "$(pwd):/var/www/html" \
           -w /var/www/html \
           laravelsail/php83-composer:latest \
           composer install
       ```
3. Copy `.env.example > .env` file and setup environments
    - Generate key `sail artisan key:generate` (after `sail up` - if you're using docker)
4. Start app by `sail up` or `sail up -d` (if you're using docker)
5. Install NPM by `sail npm install` (if you're using docker use `sail` or just `npm`)
6. Install NPM by `sail npm run build` (if you're using docker use `sail` or just `npm`)

## Generators

> **Generators** are separately libraries installed as **DEV dependencies**.
>
> This project not using InfyOm Generator, because not working for Laravel 11+ and also doesn't have DEV dependencies
> only.

**Factory generator** - [laravel-factory-generator](https://github.com/TheDoctor0/laravel-factory-generator)

**CRUD generator** - [laravel-crud-generator](https://github.com/awais-vteams/laravel-crud-generator?tab=readme-ov-file)

[laravel-crud-generator - Tutorial](https://medium.com/@awais.sds/generate-laravel-11-api-crud-in-2-min-2124540990f9)

### Steps to generate

**Create CRUD**

1. Run command `sail artisan make:crud {table_name}` and select Tailwind CSS or run
   command `sail artisan make:crud {table_name} tailwind`
2. Add route `Route::resource('users', UserController::class);` to [web.php](routes/web.php)
3. Add CRUD to menu (menu links to routes) to [navigation.blade.php](resources/views/layouts/navigation.blade.php)
    ```bladehtml
        // add to <!-- Navigation Links -->
        <x-nav-link :href="route('users.index')" :active="request()->routeIs('users.index')">
            {{ __('Users') }}
        </x-nav-link>
        
        // add to <!-- Responsive Navigation Menu -->
        <x-responsive-nav-link :href="route('users.index')" :active="request()->routeIs('users.index')">
            {{ __('Users') }}
        </x-responsive-nav-link>
    ```
**Build JS/CSS**

- Run command (local server if you need) `npm run dev` (or use `sail npm ...` if you're using docker)
- Run command (build files) `npm run build` (or use `sail npm ...` if you're using docker)

**Factory Generator**

- Run command `sail artisan generate:factory User`
