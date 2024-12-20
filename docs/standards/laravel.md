---
tags: [laravel, coding-standards, style-guide, php, eloquent, blade-templates]
---

# 📚 Laravel Code Standards and Style Guide

This guide provides the coding standards and style guidelines for developing applications using Laravel. Adhering to these standards ensures code consistency, readability, and maintainability across projects.


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

### Use Blade Directives Over PHP Tags

✅

```blade
@if (count($users) > 0)
    <ul>
        @foreach ($users as $user)
            <li>{{ $user->name }}</li>
        @endforeach
    </ul>
@else
    <p>No users found.</p>
@endif
```

❌

```php
<?php if (count($users) > 0): ?>
    <ul>
        <?php foreach ($users as $user): ?>
            <li><?= $user->name ?></li>
        <?php endforeach; ?>
    </ul>
<?php else: ?>
    <p>No users found.</p>
<?php endif; ?>
```

### Let Laravel Guess Table Names

✅

```php
class User extends Model
{
    // Laravel will automatically guess the table name as 'users'
}
```

❌

```php
class User extends Model
{
    protected $table = 'my_users';
}
```

Setting the table name explicitly can lead to inconsistencies in naming conventions across the application.

### Use Eloquent Relationships Over Queries

✅

```php
class Post extends Model
{
    public function comments()
    {
        return $this->hasMany(Comment::class);
    }
}
```

```php
$comments = $post->comments;
```

❌

```php
class Post extends Model
{
    public function comments()
    {
        return DB::table('comments')->where('post_id', $this->id)->get();
    }
}
```

Using Eloquent relationships simplifies the code, makes it more readable, and takes advantage of Laravel's ORM features.

### Migration Files

- Use meaningful names for migration files.
- Use the `up` and `down` methods for schema changes.
- Avoid using raw SQL queries in migrations.
- Use artisan commands to generate migrations `php artisan make:migration --table=users create_users_table`.
- Name format for migration files: `YYYY_MM_DD_HHMMSS_operation_name_table`

- ✅ `2022_01_01_000000_create_users_table.php`
- ✅ `2022_01_01_000000_update_users_table.php`
- ❌ `2022_01_01_000000_users.php`
- ❌ `RAHHHHHHHHHHHH.php`

✅

```php

return new class extends Migration
{
    /**
     * Run the migrations.
     */
    public function up(): void
    {
        Schema::create('payments', function (Blueprint $table) {
            $table->id();
            $table->foreignIdFor(\App\Models\Guest::class)->nullable()->constrained()->nullOnDelete();
            $table->json('payment_details');
            $table->string('payment_method');
            $table->string('status');
            $table->decimal('total_amount', 16, 2);
            $table->timestamps();
        });
    }

    /**
     * Reverse the migrations.
     */
    public function down(): void
    {
        Schema::dropIfExists('payments');
    }
};

```

❌

```php
return new class extends Migration
{
    /**
     * Run the migrations.
     */
    public function up(): void
    {
        Schema::create('payments', function (Blueprint $table) {
            $table->id();
            $table->integer('guest_id')->unsigned()->nullable();
            $table->foreign('guest_id')->references('id')->on('guests')->onDelete('set null');
            $table->text('payment_details');
            $table->string('payment_method');
            $table->string('status');
            $table->decimal('total_amount', 16, 2);
            $table->timestamps();
        });

    }

    /**
     * Reverse the migrations.
     */
    public function down(): void
    {
        DB::statement('DROP TABLE payments');
    }
};
```

### Validation in Form Request Over Controllers

✅

```php
class StorePostRequest extends FormRequest
{
    public function rules()
    {
        return [
            'title' => 'required|unique:posts|max:255',
            'body' => 'required',
        ];
    }
}
```

❌

```php
public function store(Request $request)
{
    $validatedData = $request->validate([
        'title' => 'required|unique:posts|max:255',
        'body' => 'required',
    ]);

    // Store the post...
}
```

Defining validation rules in a form request class keeps controllers clean and focuses them on their primary responsibility of handling HTTP requests.

### Use Config and Language Files Over Hard-Coded Text

✅

```php
return redirect()->back()->with('message', __('Post has been successfully saved!'));
```

```php
<div class="alert alert-success">
    {{ __('messages.post_saved') }}
</div>
```

❌

```php
return redirect()->back()->with('message', 'Post has been successfully saved!');
```

```php
<div class="alert alert-success">
    Post has been successfully saved!
</div>
```

### Use Route Names Over URIs

✅

```php
Route::get('/posts', [PostController::class, 'index'])->name('posts.index');
```

```blade
<a href="{{ route('posts.index') }}">View All Posts</a>
```

❌

```php
Route::get('/posts', [PostController::class, 'index']);
```

```blade
<a href="/posts">View All Posts</a>
```

Using route names makes it easier to update URIs in the future without changing the links in multiple places.

### Avoid Complex Logic in Blade Templates

✅

```php
// Controller
public function show(Post $post)
{
    $comments = $post->comments()->active()->get();
    foreach ($comments as $comment) {
        $comment->formattedDate = $comment->created_at->format('Y-m-d');
    }
    return view('posts.show', compact('post', 'comments'));
}

// Blade Template
@foreach ($comments as $comment)
    <p>{{ $comment->body }}</p>
    <small>{{ $comment->formattedDate }}</small>
@endforeach

```

❌

```blade
@foreach ($post->comments()->active()->get() as $comment)
    <p>{{ $comment->body }}</p>
    <small>{{ $comment->created_at->format('Y-m-d') }}</small>
@endforeach
```

Complex logic in Blade templates makes them harder to maintain, test and finding it. Keep logic in controllers.

### Prefer Enums or Constants Over Magic Strings

✅

```php
class Post extends Model
{
    public const STATUS_PUBLISHED = 'published';
    public const STATUS_DRAFT = 'draft';
}
```

```php
enum PostStatus: string {
    case PUBLISHED = 'published';
    case DRAFT = 'draft';
}

...

$post->status = PostStatus::PUBLISHED;

```

❌

```php
$post->status = 'published';
```

Using enums or constants makes the code more readable and prevents typos and inconsistencies in string values.

### Avoid Enums in Migration Files

✅

```php
class CreatePostsTable extends Migration
{
    public function up()
    {
        Schema::create('posts', function (Blueprint $table) {
            $table->id();
            $table->string('title');
            $table->text('body')->nullable();
            $table->text('status'); // Use string instead of enum
            $table->timestamps();
        });
    }
}
```

❌

```php
class CreatePostsTable extends Migration
{
    public function up()
    {
        Schema::create('posts', function (Blueprint $table) {
            $table->id();
            $table->string('title');
            $table->text('body')->nullable();
            $table->enum('status', ['published', 'draft']); // Avoid using enum in migrations
            $table->timestamps();
        });
    }
}
```

It's awful to use enums in migrations because it makes it harder to change the enum values in the future.

### Prefer Nullable Columns If Possible

✅

```php
$table->string('blood_type')->nullable();
```

❌

```php
$table->string('blood_type');
```

Due to ever changing requirements, it's better to use nullable columns
and enforce the constraints in the application layer.

## Conclusion

By following these guidelines, you can maintain a high standard of code quality and consistency in your Laravel applications.
