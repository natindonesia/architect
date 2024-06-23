---
tags: [laravel, coding-standards, style-guide, php, eloquent, blade-templates]
---
# 📚 Laravel Code Standards and Style Guide

This guide provides the coding standards and style guidelines for developing applications using Laravel. Adhering to these standards ensures code consistency, readability, and maintainability across projects.

## Table of Contents

1. [General Guidelines](#general-guidelines)
2. [Naming Conventions](#naming-conventions)
3. [Code Formatting](#code-formatting)
4. [PHP Specific Standards](#php-specific-standards)
5. [Eloquent ORM](#eloquent-orm)
6. [Blade Templates](#blade-templates)
7. [Example of Do's and Don'ts](#example-of-dos-and-donts)

## General Guidelines

- Use PSR-12 coding standards as a base.
- Follow the principles of clean code.
- Ensure all code is properly documented.
- Use Git for version control with meaningful commit messages.
- Write unit and feature tests for your code.

## Naming Conventions

- **Classes and Interfaces**: Use PascalCase.
- **Methods and Variables**: Use camelCase.
- **Constants**: Use UPPER_SNAKE_CASE.
- **Controllers**: Use descriptive names ending with `Controller`.
- **Routes**: Use kebab-case for route names and URIs.

## Code Formatting

- Indentation should be 4 spaces.
- Use Unix LF line endings.
- Keep lines to a maximum of 120 characters.
- Place `namespace` and `use` declarations at the top of the file.
- Separate each class method with one blank line.

## PHP Specific Standards

### Classes and Methods

- Declare visibility for all properties and methods.
- Use type hints and return type declarations where possible.

### Example:

```php
<?php


namespace App\Http\Controllers;

use Illuminate\Http\Request;

class UserController extends Controller
{
    private UserRepository $userRepository;

    public function __construct(UserRepository $userRepository)
    {
        $this->userRepository = $userRepository;
    }

    public function index(): Response
    {
        $users = $this->userRepository->getAllUsers();

        return response()->json($users);
    }
}
```

## Eloquent ORM

- Use meaningful method names in models.
- Avoid using queries directly in controllers; use repositories or services.
- Prefer relationships and scopes over raw queries.

### Example:

```php
class User extends Model
{
    public function posts()
    {
        return $this->hasMany(Post::class);
    }

    public function scopeActive($query)
    {
        return $query->where('active', 1);
    }
}
```

## Blade Templates

- Use Blade syntax over plain PHP.
- Avoid using complex logic inside Blade templates; keep logic in controllers or view composers.
- Use components and slots for reusable pieces of UI.

### Example:

```blade
<!-- resources/views/components/alert.blade.php -->
<div class="alert alert-{{ $type }}">
    {{ $slot }}
</div>

<!-- Usage -->
<x-alert type="danger">
    This is an error message.
</x-alert>
```

## Example of Do's and Don'ts


By following these guidelines, you can maintain a high standard of code quality and consistency in your Laravel applications.
