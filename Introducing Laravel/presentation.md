theme:Plain Jane, 7
build-lists: true
slidenumbers: true

# [fit] **Introducing** _**Laravel**_

---

# _**Why a framework?**_

Long ago, in the before time, developers were responsible not only for business logic, but also components common across sites

* User authentication
* Input validation
* Database access
* Templating

---

# _**Why a framework?**_

Today, we have dozens of frameworks and thousands of packages and components at our fingertips.

Frameworks like Laravel prepackage these components together and glue them together with things like config files, service providers, and so on.

In general, when using a framework, somebody else has made decisions not only about _which_ components to use, but also how they're pieced together.

^ With packages, someone else is responsible for developing and maintaining isolated pieces of code. They have a well-defined job and in theory, the package's author has a deeper understanding of the single component than you do (or need to).

---

# _**But I can do this myself!**_

* No framework, where do you start?
* Routing HTTP requests
* Then you need a router
* Now to configure the routes
* Syntax? Where do I put it? Controllers?

^ - Probably routing HTTP requests
- Then you're evaluating routers
- What's the syntax of the routes file? Where are you going to put it?
- Before you know it, you've built this intricate web of components, but what happens when another developer looks at it? You documented everything as you went along, right?
- What happens when you do this on two projects? Four? Each one is likely to be at least subtly different.

---

# _**Consistency and flexibility**_

* Frameworks aim to solve many of the problems of hand-rolling
* Ensures the chosen components work well together
* Provide conventions that reduce the amount of code a new developer has to understand
* If you understanding routing in one Laravel project, it's the same in all of them
* The best frameworks not only provide a solid foundation, but are flexible enough to let you customise

^ Feel free to build a framework as a learning experience, but seriously consider whether you put that into a workplace production environment.

---

# _**History**_

* Ruby on Rails
* Influx of PHP frameworks
* CodeIgniter
* Laravel 1, 2, and 3
* Laravel 4
* Laravel 5

^ Understanding 'why Laravel?' is understanding its history and what came before it. There were a number of other frameworks and movements both in PHP and other web development spaces.
- RoR in 2004. Hard to find a framework that hasn't been influenced by it in some part since. Popularised MVC, RESTful APIs, convention over configuration, ActiveRecord and loads more.
- Clear to many that Rails and similar frameworks were a vision of the future. CakePHP was the first PHP flavour in 2005, followed soon after by Symfony, CodeIgniter, Zend, and Kohana. Yii in 2008, Aura and Slim in 2010. Some were more Rails-y and targeted rapid development, others like Symfony and Zend focussed more on enterprise and ecommerce.
- CI was arguably the most popular of the independent PHP frameworks. Simple and easy to use, great docs and community. Its use of modern tech and patterns advanced slowly. As more frameworks appeared and PHP's tooling advanced, CI started falling behind. Whilst this was happening, Laravel's creator became dissatisfied with CI and set off to write his own framework.
- First Laravel 1 beta June 2011 and written completely from scratch. Featured a custom ORM, closure-based routing inspired by Ruby's Sinatra, a module system for extension, helpers for forms, validation, authentication, and more.
- Early dev moved quickly, Laravel 2 and 3 were released three months apart between Nov 2011 and Feb 12.
- Composer was now ubiquitous and showing signs of becoming industry-standard. Laravel 4 was rewritten from scratch as a collection of components bundled together and distributed via Composer.
- Slated as 4.3, the development of this version of Laravel made it clear the significance of changes warranted a major release.

---

# _**Why Laravel?**_

* Increase developer speed and happiness
* Equipping and enabling developers
* Quick to learn, start, and develop
* Write code that's simple, clear, and long-lasting
* Happy developers make the best code

^ Developer happiness is a primary concern of the framework and has a huge impact on Laravel's style and decision-making process
- Shallow learning curve, minimising steps between starting and publishing a new app
- All of the common, boilerplate tasks are made simple by out of the box components
- Not just the framework, entire ecosystem from development to deploy. Homestead and Valet for local development. Forge for server management, Envoyer for advanced deployment strategies.
- Host of first-party packages for payments and subscriptions, web sockets, search, API authentication, social login.
- Removes the repetitive work of your job as developers so you can focus on what makes your app unique

---

# _**The Laravel community**_

> From the very beginning of Laravel, I've had this idea that all people want to feel like they are part of something. It's a natural human instinct to want to belong and be accepted into a group of other like-minded people. So, by injecting personality into a web framework and being really active with the community, that type of feeling can grow in the community.
-- Taylor Otwell

^ One of the distinguishing elements of Laravel that has contributed to its grown and success, is the welcoming, teaching community that surrounds it. From Jeffrey Way's Laracasts video tutorials, to Laravel News, to Slack and IRC, to countless people on Twitter and blogs sharing their experiences, and the Laracon conferences. Laravel has a rich and vibrant community of folks who've been around since day one and many more who are on their first day.

---

# _**Hello, World!**_

```php
// Closure-based route
Route::get('/', function () {
    return 'Hello, World!';
});

// Controller-based route
Route::get('/', 'WelcomeController@index');
```

---

# _**Hello, World!**_

```php
// app/Http/Controllers/WelcomeController.php
<?php

namespace App\Http\Controllers;

class WelcomeController extends Controller
{
    public function index()
    {
        return 'Hello, World!';
    }
}
```

---

# _**Why Laravel?**_

> Because Laravel helps you bring your ideas to reality with no wasted code, using modern coding standards, supported by a vibrant community, with an empowering ecosystem of tools.
> And because you, dear developer, deserve to be happy
-- Matt Stauffer, Laravel Up and Runnig

---

# _**Developing in Laravel**_

* Modern PHP framework requiring PHP >= 5.6.4 (Laravel 5.4)
* Laravel 5.5 will require PHP >= 7.0
* Use what you know - MAMP, WAMP, XAMP
* Laravel Valet (Mac)
* Laravel Homestead (Vagrant VM)

^ Valet - lightweight, local environment. Makes it easy to serve folders in a given base directory on a local domain
^ Homestead - makes it much easier to replicate your production environment in dev, particularly if you use Laravel Forge for server management

---

# _**Creating a new project**_

## Using the Laravel installer

```bash
composer global require "laravel/installer=~1.1"
laravel new projectName
```

## Using Composer

```bash
composer create-project laravel/laravel projectName --prefer-dist
```

---

# _**Configuration**_

* The core settings of your Laravel application live in files in the `config` folder.
* These files simpley return an array

```php
// config/app.php
return [
    'name' => env('APP_NAME', 'My Laravel App'),
];
```

^ Each value in the array will be accessible by a config key comprised of the file's name and all descendant keys separated by dots

---

# _**Testing**_

* Laravel includes PHPUnit out of the box
* Simplifies testing by providing terse method names for making assertions against your code
* Dusk provides an easy-to-use browser automation and testing API

---

# _**Routing and Controllers**_

* Core to any web framework is taking requests from a user and delivering responses
* Usually starts with defining applicaiton routes
* Without routes, you have no way to interact with your users

---
[.build-lists: false]

# _**Route definitions**_

* Laravel separates web (`routes/web.php`) and API (`routes/api.php`) routes
* Web routes are those visited by your end users
* API routes are those consumed by mobile apps, AJAX requests, and more

```php
Route::get('/', function () {
    return 'Hello, World!';
});
```

^ Does anybody know why we return instead of print? There's a few answers, but the simplest is that there are a lot of wrappers around Laravel's request and response cycle, including middleware.
- When the route closure (or controller method) is finished executing, the response is returned so that it continues to flow through the response stack and any other middleware before it is returned to the end user.
- Allows us to do things like validating form input and redirecting the user if there was an error
- We use the get verb, but we can also use post, put, patch, and delete depending on what your route is doing

---

# _**Route parameters**_

```php
Route::get('/{name}', function ($name) {
    return "Hello, {$name}!";
});
```

^ * Common to use the same name for route parameter and method variable
* Not required unless you're using route/model binding
* Parameters are passed to their receiving method in order from left to right

---

# _**Route parameters**_

```php
Route::get('/{name}', function ($visitorName) {
    return "Hello, {$visitorName}!";
});
```

---

# _**Views**_

* Views are files that describe what some particular output should look like
* You can use plain PHP - `welcome.php` or,
* You can use Laravel's Blade templating language - `welcome.blade.php`
* Separates your business logic from your presentation logic

---

# _**Views**_

```php
Route::get('/{name}', function ($name) {
    return view('welcome')->with('name', $name);
});

// resources/views/welcome.blade.php
<html>
<head>
    <title>Welcome</title>
</head>
<body>
    <h1>Hello, {$name}!</h1>
</body>
</html>
```

^ As you can imagine, defining all of your presentation logic in the routes file will get unwieldly fast.

---
[.build-lists: false]

# _**Controllers**_

* Controllers are another part of the MVC pattern
* Organise the logic of one or more routes together in one place
* Tend to group similar routes together, particularly if your application is structured as a traditional CRUD-application
* Controller will typically handle Create, Read, Update, and Delete operations for a resource

```bash
php artisan make:controller WelcomeController
```

---

# _**Controllers**_

```php
// app/Http/Controllers/WelcomeController.php
<?php

namespace App\Http\Controllers;

use Illuminate\Http\Request;

class WelcomeController extends Controller
{
    //
}
```

---

# _**Controllers**_

```php
class WelcomeController extends Controller
{
    // The $name variable is received from the route parameter,
    // in the same way as the earlier route closure example.
    public function index($name)
    {
        return view('welcome')->with('name', $name);
    }
}
```

---

# _**Getting user input**_

```php
// routes/web.php
Route::get('/contact', 'ContactController@create'); // Display the contact form
Route::post('/contact', 'ContactController@store'); // Save the contact details

// app/Http/Controllers/ContactController.php
public function store()
{
    $contact = new Contact;
    $contact->name = Input::get('name');
    $contact->email = Input::get('email');
    $contact->message = Input::get('message');
    $contact->save();

    return redirect('thank-you');
}
```

---

# _**Route model binding**_

A common routing pattern is to use the first line(s) of a controller to find the resource for the given ID.

```php, [.highlight: 2]
Route::get('users/{id}', function ($id) {
    $user = User::findOrFail($id);
});
```

^ Laravel provides a feature that simplifies this pattern called route model binding
* Allows you to define a particular parameter name should be resolved to an Eloquent record
* Passes the resolved record in as the parameter, not the raw value
* The simplest way to use route model binding is to name your parameter something unique to the model, then typehint the parameter in your method, using the same variable name.

---

# _**Implicit route model binding**_

```php, [.highlight: 1]
Route::get('users/{user}', function (User $user) {
    return view('users.show')->with('user', $user);
});
```

^ Because the route parameter (`{user}`) is the same as the method parameter (`$user`), and the method parameter is typehinted with a `User` model (`User $user`), Laravel sees this as a route model binding.
* You can also do custom, or explicit, route model binding but since implicit binding was introduced, i've rarely found a need for it

---

# _**Form method spoofing**_

* Sometimes, yo need to manually define HTTP verbs
* Javascript
* HTML forms only support `GET` and `POST`
* If you need to use others (`PATCH`, `PUT`, `DELETE`, etc.) you need to specify them yourself
* Laravel makes this really easy by spoofing the unsupported methods

---
[.build-lists: false]

# _**Form method spoofing**_

```html, [.highlight: 2]
<form action="/users/42" method="POST">
    <input type="hidden" name="_method" value="DELETE">
</form>
```

* The hidden `_method` input tells Laravel that the form you're submitting should be treated as something other than a regular `POST`
* Laravel will match and route the submission as if it were actually a request with that verb

---

# _**CSRF Protection**_

* Cross-site request forgery
* If you've ever tried submitting a form already, you have come across a `TokenMismatchException`
* Protects all non-'read-only' routes (`GET`, `HEAD`, or `OPTIONS`) by default by requiring a token be passed along with each request
* Token generated at the start of every seassion
* Every non-read-only route compares the submitted token with the session token

---

# _**CSRF Protection**_

Laravel provides a convenient way of working around this

```html, [.highlight: 2-4]
<form action="/users/42" method="POST">
    <input type="hidden" name="_token" value="<?= csrf_token() ?>">"
    <!-- or simply -->
    <?= csrf_field() ?>
    <input type="hidden" name="_method" value="DELETE">
</form>
```

---

# _**CSRF Projection**_

Laravel is configured to support CSRF tokens with it's suggested JavaScript HTTP client, Axios:

```html
<head>
    <meta name="csrf-token" content="{{ csrf_token() }}">
</head>
```

```javascript
// resources/assets/js/bootstrap.js
let token = document.head.querySelector('meta[name="csrf-token"]');

window.axios.defaults.headers.common['X-CSRF-TOKEN'] = token.content;
```

^ Laravel will automatically check the X-CSRF token on every request. Valid tokens passed there will mark the CSRF protection as satisfied.

---

# _**Templating**_

* Compared to most backend languages, PHP functions relatively well as a templating language
* Most modern frameworks include a templating language
* Laravel offers a custom engine called Blade, inspired by .NET's Razoer engine
* Concise syntax, shallow learning curve, powerful and intuitive inheritance, and easy extensibility

^ * PHP has its shortcomings as a templating language, and using `<?php` inline all over the place is ugly

---

# _**Templating**_

```html
<h1>Users</h1>

@forelse ($users as $user)
    &gt; {{ $user->first_name }} {{ $user->last_name }}<br>
@empty
    There are no users at this time
@endforelse
```

^ Blade introduces a convention through its custom tags, called directives, are prefixed with an @
* Directives used for all control structures, inheritance, and any custom functionality you add
* The syntax is clean and concise, and aims to be more pleasant and tidy to work with than some of the alternatives
* Data is escaped automatically when you use the mustache-notation for echoing data
* Just like the best Laravel components, it takes complex requirements and makes them easy and accessible

---
[.build-lists: false]

# _**Control structures - conditionals**_

`@if`

* Blade's `@if ($condition)` compiles to `<?php if ($condition): ?>`. `@else`, `elseif`, and `@endif` also compile to the exact same PHP syntax
* Just like native PHP conditionals, you can mix and match these as necessary

---
[.build-lists: false]

# _**Control structures - conditionals**_

`@unless` and `@endunless`

* Unlike `@if`, `@unless` is new syntax that doesn't have a direct equivalent in PHP
* It's the direct inverse of `@if`
* `@unless ($condition)` == `@if (! $condition)`

---

# _**Control structures - loops**_

`@for`, `@foreach`, `@while`

Work the same way in Blade as they do in PHP

```html
@for ($i = 0; $i < 42; $i++
    The number is {{ $i }}<br>
@endfor

@foreach ($users as $user)
    {{ $user->name }} ({{ $user->email }})<br>
@endforeach

@while (@item = array_pop($items))
    {{ $item->description() }}<br>
@endwhile
```

---

# _**Control structures - loops**_

`@forelse`

`@forelse` is a `@foreach` loop that also lets you program in a fallback if the object you're iterating over is empty.

```html
@forelse ($tasks as $task)
    &gt; {{ $task->title }}<br>
@empty
    There are no tasks to complete
@endforelse
```

---

# _**Template inheritance - sections**_

```html
<!-- resources/views/layouts/master.blade.php -->
<!DOCTYPE html>
<html>
<head>
    <title>My Site | @yield('title', 'Home Page')</title>
</head>
<body>
    <div class="container">
        @yield('content')
    </div>
    @section('footerScripts')
        <script src="app.js"></script>
    @show
</body>
</html>
```

^ Looks mostly like plain HTML, but you can see we've yielded in two places (title and content), and we've defined a section in a third (footerScripts)
* Three directives that each look a little different - @yield('title') with a defined default, @yield('content') alone, and @section ... @show with content in it
* All three function essentially the same. All three define that there's a section with a given name (first parameter). All three are defining that the section can be extended later. All three define what to do if the section isn't extended, either by providing a string fallback, no fallback (which shows nothing), or an entire block fallback.
* What's different? @yield('content') has no default content. The default content in @yield('title') will only be shown if it's never extended. If it's extended, the child sections will not have programmatic access to the default value. @section ... @show is both defining a default and doing so in a way that the default contents will be available to its children, through the @parent directive

---

# _**Template inheritance - sections**_

```html
<!-- resources/views/dashboard.blade.php -->
@extends('layouts.master')

@section('title', 'Dashboard')

@section('content')
    Welcome to the application dashboard!
@endsection

@section('footerScripts')
    @parent

    <script src="dashboard.js"></script>
@endsection
```

^ @extends indicates the template should not be rendered alone, but instead extends another view. This template's role is to define the content of various sections, but not to stand alone.

---
[.build-lists: false]

# _**Template inheritance - sections**_

`@include`

* What if you're in a view and you want to display some alert message?
* You're surely not going to copy and paste the alert HTML everywhere it's needed

```html
<div class="alert alert-success">
    The operation was successfully completed
</div>
```

---

# _**Template inheritance - sections**_

```html, [.highlight: 1, 3-6, 9-12]
<!-- resources/views/home.blade.php -->
<div class="container">
    @include('partials.alert', [
        'type' => 'success',
        'message' => 'The operation was successfully completed',
    ])
</div>

<!-- resources/views/partials/alert.blade.php -->
<div class="alert alert-{{ $type }}">
    {{ $message }}
</div>
```

^ @include pulls in the partial and, optionally, passes data into it
* You can explicitly pass data to the included partial, or you can reference variables in the included file from the including view

---

# _**Frontend components**_

* Laravel is primarily a PHP framework, but also has a series of components focussed on generating frontend code
* Components like pagination and message bags are PHP helpers that target the frontend
* Laravel also provides a webpack-based build system called Mix

---

# _**Mix**_

* Configuration layer on top of Webpack
* Provides a fluent API for defining Webpack build steps for your Laravel application using several common CSS and JavaScript pre-processors
* Simple method chaining allows you to fluently define your asset pipeline

```javascript
mix.js('resources/assets/js/app.js', 'public/js')
   .sass('resources/assets/sass/app.scss', 'public/css');
```

^ Allows you to compile CSS pre-processors like LESS and SASS into plain CSS
* Provides several features such as compiling ECMAScript 2015 JS syntax to conventional JS
* Handles module bundling, minification and concatenation of JS files
* Makes it easy to extract vendor libraries to their own JS file
* Handles copying files and directories
* Makes it easy to version your assets, allowing you to set long expire headers to leverage browser caching, without having people stuck with old assets

---

# _**Handling user data**_

* Websites that benefit most from a framework often don't just serve static content
* Many deal withi complex and mixed data sources
* The most commen (and most complex) is user input
* Laravel provides tools for gathering, validationg, normalising, and filtering user-provided datra

^ User input can come from URL paths, query parameters, POST data, and file uploads

---

# _**Handling user data - request object**_

* Most common tool for accessing data
* Provides easy access to all of the ways users can provide input
* You can also use the global `request()` helper or the `Request` facade
* Each exposes the same methods, use what you feel most comfortable with

---

# _**Handling user data - injecting a request object**_method

```php, [.highlight: 1]
Route::post('form', function (Illuminate\Http\Request $request) {
    //
});
```

---
[.build-lists: false]

# _**Handling user data - request object**_

`$request->all()`

* As the name suggests, gives you an array containing all of the user-provided input

---
[.build-lists: false]

# _**Handling user data - request object**_

`$request->except()` and `$request->only()`

* Provide the same input as `$request->all()`, but you can choose one or more fields to include or exclude

```php
$request->except('_token');
[
    'first_name' => 'Michael',
    'last_name' => 'Dyrynda',
    'email' => 'michael@example.com',
]

$request->only(['first_name', 'email']);
['first_name' => 'Michael', 'email' => 'michael@example.com']
```

---
[.build-lists: false]

# _**Handling user data - request object**_

`$request->has()` and `$request->exists()`

* Detect whether a particular piece of user input is available to you
* `$request->has()` returns `false` if the key exists and is empty
* `$request->exists()` returns true if the key exists, even if it is empty

---
[.build-lists: false]

# _**Handling user data - request object**_

`$request->input()`

* Allows you to get the value of a single field
* The second parameter allows you to specify a default value, if one was not passed

```php
$request->input('first_name', 'Anonymous');
```

---

# _**Validation**_

* Laravel provides a number of ways to validate data
* The simplest method is using the `validate()` method in your controller

```php, [.highlight: 5-10]
class PostController extends Controller
{
    public function store(Request $request)
    {
        $this->validate($request, [
            'title' => 'required',
            'body' => 'required',
        ]);

        // Post is valid; persist to database
    }
}
```

^ If the validation fails, Laravel will redirect the user back and provide any errors and user input back to the view

---

# _**Database and Eloquent**_

* Laravel provides a suite of tools for interacting with your application's databases
* The most notable tool is Eloquent, Laravel's ActiveRecord ORM implementation
* Eloquent is one of Laravel's most popular and influential features
* Simple; one class per table, which is responsible for retrieving,r epresenting, and persisting data to that table

---

# _**Migrations**_

* Modern frameworks make it easy to define your database structure with code-driven migrations
* Every new table, column, index, and key can be defined in code
* Easy to version, easy share, easy to bring a database up from nothing to default schema in seconds
* Migrations define two things: the modifications desired when running the migration *up* and when running the migration *down*

---

# _**Migrations**_

```php
// Laravel's default user table migration
<?php

use Illuminate\Support\Facades\Schema;
use Illuminate\Database\Schema\Blueprint;
use Illuminate\Database\Migrations\Migration;

class CreateUsersTable extends Migration
{
    public function up()
    {
        Schema::create('users', function (Blueprint $table) {
            $table->increments('id');
            $table->string('name');
            $table->string('email')->unique();
            $table->string('password');
            $table->rememberToken();
            $table->timestamps();
        });
    }

    public function down()
    {
        Schema::dropIfExists('users');
    }
}
```

---

# _**Seeding**_

* Seeding in Laravel is simple
* Allows you to set your databases up with default data
* Useful for specifying default application user groups, roles, and so on
* Used to get your application configured in its default state

^ Has gained widespread adoption as part of normal development workflows in a way it hasn't in previous PHP frameworks

---

# _**Seeding - create a seeder**_

```bash
php artisan make:seeder ContactsTableSeeder
```

```php
// database/seeds/DatabaseSeeder.php
public function run()
{
    $this->call(ContactsTableSeeder::class);
}

// database/seeds/ContactsTableSeeder.php
public function run()
{
    DB::table('contacts')->insert([
        'name' => 'Michael Dyrynda',
        'email' => 'michael@example.com',
    ]);
}
```

^ This will create a single record in the contacts table

---
[.build-lists: false]

# _**Model factories**_

* Model factories define one (or more) patterns for creating fake entries for your database tables
* Particularly useful in application testing

```php
$factory->define(User::class, function (Faker\Generator $faker) {
    return [
        'name' => $faker->name,
        'email' => $faker->email,
    ];
});

// Can now be used as
factory(User::class)->create();
```

---
[.build-lists: false]

# _**Query Builder**_

* The query builder lies at the center of every piece of Laravel's database functionality
* Fluent interface for interacting with your database

```php
// Non-fluent
$users = DB::select(['table' => 'users', 'where' => ['type' => 'donor']]);

// Fluent
$users = DB::table('users')->where('type', 'donor')->get();
```

^ Fluent interface is one that primarily uses method chaining to provide a simpler API to the end user.

---

# _**Eloquent**_

* An ActiveRecord ORM (Object-relational mapping)
* Abstraction layer that provides a single interface to interact with multiple database types
* An Eloquent class is responsible for interacting with both the table as a whole, and presenting individual records
* Primarily focussed on simplicity
* Like the rest of the framework, relies on convention over configuration

---

# _**Eloquent - a simple model**_

```php
<?php

namespace App;

use Illuminate\Database\Eloquent\Model;

class User extends Model
{
    //
}
```

---

# _**Eloquent - interacting with the database**_

```php
// Interacting with the table as a whole
$users = User::all();

// Interacting with a single record
$user = new User;
$user->name = 'Jordan';
$user->save();
```
