# Mulai

## Konfigurasi .env File
## Docs:

[Goto Docs](./docs/index.md)

### Konfigurasi File

lumen tidak mendudukung konfigurasi manual sehingga untuk membuat konfigurasi manual, copy file yang ada pada directory 📁

```cli

copy ./vendor/laravel/lumen-framework/config/*.php ./config/*.php

```

lalu pada bagian "Create The Application" pada file app.php 📁[./bootstrap/app.php]

```php
	//...
	$app->configure("database"); // jika yang dicopy sebelumnya hanya 📁 config/database.php
	//...
```

### Middleware

#### apa itu middleware ?

```
	
	middleware adalah jembatan penghubung program dengan request, sebelum menyentuh inti program request dari user harus melalui middleware yang sudah ditetapkan.

	biasanya middleware berguna untuk mengecek auterntikasi dari user, sebelum menambah, mengubah, atau menghapus data yang ada pada aplikasi.

```

#### middleware pada lumen

sama seperti middleware pada laravel, middleware pada lumen juga sama seperti pada laravel.

##### Membuat Middleware

dengam menggunakan command artisan

```cli

$ php artisan make:middleware [namaMiddleware]

```

middleware akan dibuat pada 📁 __app/Http/Middleware/...__

##### Mendaftar Middleware

setelah membuat middleware, didaftarkan agar dapat digunakan pada router maupun controller

⚠ sebelumnya menggunakan middleware pastikan pada file 📁 __bootstrap/app.php__ beberapa perintah sudah di uncomment

```php
	//...
			
	$app->routeMiddleware([
	    'auth' => App\Http\Middleware\Authenticate::class,
	]);

	//...

	$app->register(App\Providers\AppServiceProvider::class);
	$app->register(App\Providers\AuthServiceProvider::class);

```

lalu

```php

	//mendaftarkan router router

	$app->routeMiddleware([
	    'auth' => App\Http\Middleware\Authenticate::class,

	    //mendaftar middleware
	    'active' => App\Http\Middleware\ActiveUserMiddleware::class,
	    'super' => App\Http\Middleware\SuperAdminMiddleware::class,
	]);

	//mendaftarkan middleware

	$app->middleware([
	    App\Http\Middleware\ExampleMiddleware::class
	]);


```

[referensi](https://lumen.laravel.com/docs/7.x/middleware)

##### Middleware Auth API & UserGuard

ketika melakukan request sebagai api dapat diterima dengan mendaftar callback yang akan dipanggil untuk middleware 'api'

atau menjadi default jika membuat config/auth.php

tambahkan pada file __AuthServiceProvider.php__

```php
	public function boot(){
        $this->app['auth']->viaRequest('api', function ($request) {
        	//do what the stuff
        	return User::first();
        }
	}

```

hasil return dari api ini akan menjadi hasil dari


```php

	\Auth::user();

```

ketika menggunakan facades pastikan sudah menguncomment $app->withFacades() pada file __bootstrap/app.php__

```php
//...	

$app->withFacades();

//...
```

[Reference](https://laracasts.com/discuss/channels/lumen/lumen-54-auth-guard-driver-api-is-not-defined?page=1)
[Create a REST API for ToDo App with Authentication Using Lumen](https://www.cloudways.com/blog/lumen-rest-api-authentication/)

## Cache

dengan menggunakan Facades
ketika cache sudah digunakan maka kedua kali cache tidak akan memanggil yang ada dalam callback

```php

	Cache::rememberForever('userpertama', function(){
		return User::first();
	});
	//atau dengan menggunakan waktu kadaluarsa
	Cache::remember('userpertama', 60, function(){
		return User::first();
	});
```

untuk menghapus cache

```php

	Cache::pull("userpertama");

```

jika menggunakan database daripada file

pada .env

```
...

CACHE_DRIVER=database

```

maka harus membuat kolom __cache__ pada database

```cli

$ php artisan cache:table

```

lalu mirasi untuk tabel cache dibuat dan siap di-migrate

```cli

$ php artisan migrate

```

[referensi](https://stillat.com/blog/2016/12/07/laravel-artisan-cache-command-the-cachetable-command)