## Laravel cheatsheet

### insert lalu ambil data

hanya berlaku buat tabel dengan kolom id sebagai primary key dan dengan memiliki attribute auto_increment

```php

	use \App\User;

	User::insertGetId($request->all()); //return data / null if fail

```

### scope query

ini adalah fitur yang dapat memutasi / menambah / men-custom query builder sendiri

```php

class User extends Model {

	//...

	public function scopePria($query){
		$query->where("jenis_kelamin", "=", "pria");
	}
}

User::pria()->get(); // semua user dengan jenis kelamin pria

```

## Relasi Polymorph

relasi polymorph terjadi pada bagian objek instance bukan pada database sehingga untuk menggunakan relasi ini dengan menggunakan 2 buah kolom tambahana yang pertama parameter relasi dan terakhir parameter type / namespace objeck reference

dengan menambahkan ke dalam migration

```php

	$table->morphs("user");

	// atau

	$table->nullableMorphs("user");
	//untuk nilai default null

```

## Handling Error 💀

laravel menyediakan file untuk mengubah dan menghandle tampilan error jika terjadi error maka custom error yang akan tampil

pada file 📁 ./app/Exeptions/Handler.php

```php
use Symfony\Component\HttpKernel\Exception\HttpException;

	//...

	function render($request, Throwable $exception){

		if($exception instanceof HttpException && !$request->wantsJSON() && $exception->getStatusCode() === 404)
			return view('error.404');

		return parent::render($request, $exception);
	}

```

## Custom Validasi

kita dapat melakukan custom validasi sendiri dengan:

```php

use Validator;

//...

$validator = Validator::make($request->all(), [
	"required",
	function($attribute, $value, $fail){
		if($value === "Fail")
			$fail("the {$attribute}'s' value is fail");
	}
], [ "required" => ":attribute is required" ]);

if($validator->fails())
	return response()->json($validator->getData(), 400);

```

## Insert Get Id

menggunakan insert pada eloquent laravel hanya mendapat nilai kembali 1 / false | null

mengambil data setelah di insert dapat menggunakan $model->insertGetId( ...Array );

```php

	$user = User::insertGetId([ "username" => "edd2008", "password" => "qwertyui" ]);

```

[Reference](https://laravel.com/docs/7.x/queries#inserts)


## Mengirim variabel ke relasi pada orm laravel

dengan menngunakan callback pada eager loader

```php

	$variabel_yang_ingin_dikirim = "hei";

	Admin::with([
		"informasi" => function($query) use($variabel_yang_ingin_dikirim){
			return $query->where("nama", "like", "%{$variabel_yang_ingin_dikirim}%");
		}
	])->first();

```

[Reference](https://stackoverflow.com/questions/36411826/laravel-eloquent-pass-variable-to-with-relationship-function/36411884)


## Optimize Laravel

### Classmap Optimization

Sebagai sebuah framework yang men-cover berbagai macam kebutuhan, maka Laravel menggunakan sistem yang cukup kompleks dimana habits-nya adalah ketika terjadi sebuah request maka Laravel akan menyertakan semua file yang terkait agar request tersebut dapat diproses. Artisan command yang satu ini akan memecahkan masalah tersebut dengan menggabungkan seluruh komponen yang dibutuhkan ke dalam single file, sehingga waktu yang dibutuhkan menjadi lebih sedikit, adapun command-nya adalah:

```cli

$ php artisan optimize --force

```

[Referensi](https://daengweb.id/tips-optimasi-meningkatkan-performance-laravel)