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

mysql> DEFINE

```
