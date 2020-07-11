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

### mengubah url origin

```cli

$ git remote set-url origin [url.git]

```

[referensi](https://stackoverflow.com/questions/2432764/how-to-change-the-uri-url-for-a-remote-git-repository) 4/13/2020 1:37:30 PM




## Menyimpan data login github

setiap kali melakukan __git push__ selalu meminta username dan email dari github

```cmd

git config credential.helper store

```

maka git akan menyimpan data store pertama kali.

### mengatur waktu kadaluarsa caching store

```cmd

git config --global credential.helper "cache --timeout 72000"

```

--timeout dalam second/ detik

[referensi](https://stackoverflow.com/questions/11403407/git-asks-for-username-every-time-i-push)

# Tag pada git

tag ini berfungsi untuk membuat versi rilis
cukup dengan mengetikan perintah

```cmd

$ git tag -a [tag_name] -m ["message_description"] # atau
$ git tag [tag_name] # lightweight / tanpa deskripsi

$ git tag

v1.0.0
v1.1.0

$ git show v1.2
tag v1.2
Tagger: Scott Chacon <schacon@gee-mail.com>
Date:   Mon Feb 9 15:32:16 2009 -0800

version 1.2
commit 9fceb02d0ae598e95dc970b74767f19372d61af8
Author: Magnus Chacon <mchacon@gee-mail.com>
Date:   Sun Apr 27 20:43:35 2008 -0700

    Update rakefile

```

[Referensi](https://git-scm.com/book/en/v2/Git-Basics-Tagging) @ 4/13/2020 1:25:59 PM


# Branch

## Menimpa branch

```cli

$ git branch -f master dev_branch

```

master sebagai target
dev_branch sebagai sumber

### menimpa branch pada remote

```cli

$ git push remote +dev_branch:master

```

### menyalin file stashed ke folder tertentu
```cli

$ cp --parents $(git status -s | egrep "M|A|AM|??" | rev | cut -d" " -f1 | rev) ../modified-files

```



