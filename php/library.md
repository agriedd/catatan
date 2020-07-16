### Daftar Librari PHP


### API

#### JWT

##### 1. Firebase - PHP JWT

[Firebase - PHP JWT](https://github.com/firebase/php-jwt)

###### install

```cli

$ composer require firebase/php-jwt

```

###### cara pakai

```php

use \Firebase\JWT\JWT;

$key = "example_key";
$payload = array(
    "iss" => "http://example.org"
);

JWT::$leeway = 60; //optional - seconds

$jwt = JWT::encode($payload, $key);
$decoded = JWT::decode($jwt, $key, array('HS256')); //object

```

###### Error Handling

```php

	catch(\Firebase\JWT\ExpiredException $e){
		//expired
	} catch(\Exception $e){
		//commons
	}

```