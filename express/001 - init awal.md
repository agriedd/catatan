# Express

Versi ketika membuat catatan:

	tanggal: 2020-11-03T11:08:11+08:00
	versi: 4.17.1

## Tahapan awal menginstall express

```cli
	npm install express --save
```

## Membuat hello world dengan express

```js

const express = require('express')
const app = express()


app.get('/', (req, res)=>{
    res.status(200).header({ 'Content-Type': 'text/html' }).send("Hello world")
})

app.listen(3000, () => console.log('silahkan mengunjungi http://127.0.0.1:3000') )

```

## menggunakan view engine di express

### Contoh menggunakan template pug js

installasi dependency pug js

```cli
	npm i pug
```

```js

const express = require('express')
const app = express()

app.set('view engine', 'pug')
app.set('views', './res/views') // lokasi target folder view, default ./

app.get('/', (req, res)=>{
    res.render("index") // index.pug
})

app.listen(3000, () => console.log('silahkan mengunjungi http://127.0.0.1:3000') )

```
Untuk keterangan lebih lanjut mengenai pug bisa dilihat di dokumentasi berikut
[Dokumentasi Pug](https://pugjs.org/api/getting-started.html)

## Express Generator

Jadi dengan menggunakan express generator ini kita langsung bisa membuat aplikasi menggunakan boilerplate yang disediakan oleh express generator ini

```cli
npm install -g express-generator
```
lalu membuat generator dengan mengetikan
```cli
$ express --view=pug myapp
```

__myapp__ nama project kita --view=[nama_template_engine]