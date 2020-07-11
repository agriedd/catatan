#### Tips Composer

##### install vs update

```cli

$ composer install

```

❤ digunakan hanya ketika menginstall package yang terdapat pada __composer.json__


```cli

$ composer update

```

❤ mengupdate versi yang ada pada __composer.lock.json__

⚠ akibat versi menjadi tidak stabil, karena terdapat perbedaan versi ketika bekerja sebagai tim

[Referensi](https://id-laravel.com/post/composer-install-vs-update/) @ 4/13/2020 1:06:02 PM


##### Composer Why? 🤨

fungsi perintah why ini untuk menunjukan kenapa terdapat package yang bersangkutan di dalam composer.json
jika package ini penting karena dibutuhkan package lain atau tidak.

```cli

$ composer why tymon/php-jwt

```

[referensi](https://stackoverflow.com/questions/50331822/composer-is-not-removing-entry-from-composer-lock)

