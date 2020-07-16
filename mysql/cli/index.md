# Mysql CLI

## Login

```cli

mysql -u [username] -p [password]

```

## Memilih Database

```cli

mysql> use [database_name]

```

## User

menambah user yang memiliki semua privileges

```cli

$ GRANT ALL PRIVILEGES ON *.* TO 'db_user'@'localhost' IDENTIFIED BY 'P@s$w0rd123!';

```

dimana:
| string 		| description 	|
|---------------|---------------|
| db_user 		| username		|
| P@s$w0rd123! 	| password user yang akan dibuat	|

### Mengubah password user

```cli
$ sudo mysql -u root # I had to use "sudo" since is new installation

mysql> USE mysql;
mysql> UPDATE user SET plugin='mysql_native_password' WHERE User='root';
mysql> FLUSH PRIVILEGES;
mysql> exit;

$ service mysql restart
```
[reference](https://stackoverflow.com/questions/39281594/error-1698-28000-access-denied-for-user-rootlocalhost)


## Mengambil Kolom Sebuah Tabel

```cli

$ mysql> DESCRIBE [table]

```

## Cek Versi Mysql

```cli

$mysql> SHOW VARIABLES LIKE "%version%";

```

[reference](https://www.liquidweb.com/kb/how-to-check-the-mysql-version/)


## Configurasi Mysql Mode

pada saat menggunakan group mysql bermasalah dengan menampilkan pesan ⚠ __only_full_group_by__

### Laravel / Lumen

mengatur mode mysql pada 📁 __config/database.php__

```php

	"mysql" => [
		//...
		'modes' => [
	        'STRICT_ALL_TABLES',
	        'ERROR_FOR_DIVISION_BY_ZERO',
	        'NO_ZERO_DATE',
	        'NO_ZERO_IN_DATE',
	        'NO_AUTO_CREATE_USER',
	    ],
	]

```

atau

```php

	"mysql" => [
		//...
		'strict' => false,
	]

```

[referensi](https://stackoverflow.com/questions/37215265/lumen-create-database-connection-at-runtime)
[Stackoverflow - How can I solve incompatible with sql_mode=only_full_group_by in laravel eloquent?](https://stackoverflow.com/questions/43776758/how-can-i-solve-incompatible-with-sql-mode-only-full-group-by-in-laravel-eloquen) 4/18/2020 5:46:48 AM

### konfigurasi cli

```cli

$ sudo nano /etc/mysql/my.cnf

```

tambahkan:

```textplain

#...

[mysqld]  
sql_mode = "STRICT_TRANS_TABLES,NO_ZERO_IN_DATE,NO_ZERO_DATE,ERROR_FOR_DIVISION_BY_ZERO,NO_AUTO_CREATE_USER,NO_ENGINE_SUBSTITUTION"

```

[referesi](https://stackoverflow.com/questions/23921117/disable-only-full-group-by) 4/18/2020 5:51:55 AM

## Masalah <span style="color: red">"Starting MySQL database server mysqld No directory, logging in with HOME=/"</span>

stop mysql service

```cli

$ sudo usermod -d /var/lib/mysql/ mysql

```

lalu start kembali service

[referensi](https://gist.github.com/elialejandro/9a98d7dec1da4a526d63043f7087ba61) 4/18/2020 5:49:45 AM

## Import data Mysql .sql

```cli

$ mysql -u USERNAME -p -h HOST NAMA_DATABASE < '../file_import.sql'

```

dengan **USERNAME** adalah username dari akun mysql yang terdaftar, **HOST** dengan nama domain atau ip address dari mesin database server, **NAMA_DATABASE** sebagai nama database target dan terakhir lokasi file yang akan diimport

## Export data Mysql .sql

```cli

$ sudo mysql -u USERNAME -p -h HOST NAMA_DATABASE < '../file_target.sql'

``` 