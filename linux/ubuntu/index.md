# Webserver dengan ubuntu

lihat dasar dasar perintah [disini](./basic)

### Menginstall webserver apache

dengan mengetikan perintah

```cmd

sudo apt-get install apache2

```

💥 boom! apache2 berhasil di install

jalankan service apache2.

___cara menjalankan service: [basic](./basic#menjalankan-service)___


### Menginstall PHP

menginstall php cukup dengan

```cli

sudo apt-get install php

```

#### Ekstensi PHP

tapi beberapa aplikasi mungkin membutuhkan beberapa ekstensi dari php seperti:

1. openssl
2. php-common
3. php-curl
4. php-json
5. php-mbstring
6. php-mysql
7. php-xml
8. php-zip
9. libapache2-mod-php
10. php-mcrypt (___deprecated@php7.2___)


contoh menginstall ekstensi php-zip untuk versi php secara spesifik
```cli

sudo apt-get install php7.2-zip

```

---------------
##### server requirement lumen v6.x:
1. PHP >= 7.2
2. OpenSSL PHP Extension
3. PDO PHP Extension
4. Mbstring PHP Extension

[referensi](https://lumen.laravel.com/docs/6.x#installation)


##### server requirement laravel v6.x:
1. PHP >= 7.2
2. BCMath PHP Extension
3. Ctype PHP Extension
4. Fileinfo PHP extension
5. JSON PHP Extension
6. Mbstring PHP Extension
7. OpenSSL PHP Extension
8. PDO PHP Extension
9. Tokenizer PHP Extension
10. XML PHP Extension

[referensi]("https://laravel.com/docs/6.x/installation#server-requirements")


### Menginstall Mysql

dengan menginstall package mysql-server

```cli

sudo apt-get install mysql-server

```

#### menggunakan mysql cli

dengan menjalankan service __mysql__ dan mengetikan perintah

```cli

mysql -u [root] -p [password]

```

sejauh ini berjalan dengan baik, hoooooooooooooooooooooooooooooooooooold up bagaimana caranya menghapus package ini secara ___clean___?

stop service mysql jika sedang berjalan

```cli

sudo apt-get remove mysql-server

```