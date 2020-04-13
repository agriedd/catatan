# catatan git

# menginisalisasi git

dengan mengetikan baris perintah seperti dibawah:

```cmd

git init

```

# konfigurasi

## mengatur name dan email

sebelum melakukan git init pastikan name dan email sudah diset secara global, dengan mengetikan:

```cmd

git config --global user.name "Nama User"
git config --global user.email "username@mail.com"

```

## Mengatur origin pada directory

menggunakan __git pull__ atau __git push__ dengan mengetikan __git pull directory.git__ branch seperti:

```cmd

git pull https://github.com/agriedd/catatan.git master

```

setiap kali melakukan pull maka harus mengetikan url atau directory .git tersebut
untuk menghindari masalah ini dengan mengatur variabel origin sebagai berikut:

```cmd

git remote add origin https://github.com/agriedd/catatan.git

```

sehingga ketika mengetikan perintah git yang berhubungan dengan url dari git yang sama dapat diganti dengan
variabel origin

```cmd

git pull origin master

```

## Menyimpan data login github

setiap kali melakukan __git push__ selalu meminta username dan email dari github

```cmd

git config credential.helper store

```

maka git akan menyimpan data store pertama kali.