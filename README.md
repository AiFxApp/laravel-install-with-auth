## laravel-install-with-auth (from scratch)
* These are notes for installing a new Laravel build, then with Auth, then more notes to follow...

`laravel new {project_name}`

`cd {project_name}`

`composer require laravel/ui`

`php artisan ui [vue / boostrap / react...] --auth`

`npm i` 

* Attend to any dependency errors first...
* Review the alternatives if needed

`npm audit fix` <- normally does the trick

`npm run dev`

## That sorts out the basic set up for Laravel with Auth
<hr>

`php artisan migrate`

`php artisan serve`

Register View: `example.com/register`
Login View: `example.com/login`

## At some point you might want to disable the register URL 
* web.php <br>
`Auth::routes(['register' => false]);`

## Route Restriction
* web.php <br>
Route::get('dashboard', 'App\Http\Controllers\UserController@dashboard')->middleware('auth');

or 
* controller
```<?php

class UserController extends Controller
{
	public function __construct()
	{
	    $this->middleware('auth');
	}

	public function dashboard(){
		//
	}

	...

}
```

