> 🦖 **Impact Byte x Skilvul batch Joyful Jasper** 🐲
# Writing-Assignment-Week-04-Mirza Bakti Sukaryana 😆 🚀

| Table Of ‘Contents’ |
| ---------------------- |
| <ol> |
|  <li>Introduction to React JS</li> |
|  <li>Back to ES6</li> |
|  <li>React Component</li> |
|  <li>React State</li> |
|  <li>React useEffect</li> |
|  <li>React Hooks</li> |
|  <li>React Router</li> |
| </ol> |

***

## 1. Introduction to React JS

React adalah sebuah library JavaScript yang dikembangkan dan dikelola oleh Facebook & Instagram untuk menampilkan data & membuat komponen-komponen User Interface.
Menurut layanan analitik Libscore, saat ini React digunakan oleh Netflix, Imgur, Bleacher Report, Feedly, Airbnb, SeatGeek, HelloSign, Walmart, dan lain-lain (Wikipedia).

**Konsep _“Atomic Design Methodology”_**

> We're not designing pages, we're designing systems of components. —Stephen Hay

Dalam konsep ADM, komponen dapat diumpakan sebagai atom. Kita menggabunkan atom-atom menjadi molekul, molekul menjadi organisme, organisme menjadi template, template menjadi halaman-halaman.
React sangat cocok diaplikasikan ke dalam konsep pengembangan ADM karena dalam React kita memulai dari mengembangkan komponen-komponen yang kita gabungkan untuk membentuk sebuah halaman.

Keterangan lebih lanjut mengenai ADM dapat dibaca di [tautan ini](http://bradfrost.com/blog/post/atomic-web-design/).

Mengapa menggunakan react? Deklaratif. Berbasis Komponen. Belajar Sekali, Tulis di Mana saja.

Playground online react; CodePen, CodeSandbox, Glitch, atau Stackblitz.

Langkah membuat react.js
<ol> 
 <li>Install [Node](https://nodejs.org/en/) </li> 
 <li>Buka terminal</li> 
 <li>Masukkan command;</li> 
 <li>npx create-react-app my-app</li> 
 <li>npm init react-app my-app</li> 
 <li>yarn create react-app my-app</li> 
 <li>Cek versi; create-react-app –version</li>
 <li>Jalankan react js dengan command npm start</li>
</ol>

### Pengenalan NPM

_Package manager_ adalah software yang digunakan untuk menginstalasi dan mengelola paket-paket software. Hampir setiap bahasa pemrograman dan sistem operasi memiliki _package manager_-nya masing-masing. Beberapa contoh package manager yang terkenal misalnya brew, apt-get, composer, dan bower.

NPM (Node Package Manager) adalah sebuah package manager yang dibuat menggunakan teknologi [Node](https://nodejs.org/en/). Untuk menggunakannya kita harus menginstal Node terlebih dahulu di sistem.

__Catatan__: Selain untuk NPM, kita juga akan membutuhkan Node untuk membuat sebuah aplikasi _backend_ berbasis Node di latihan React _server-side_

* Instalasi Node
	
	Buka laman [Node](https://nodejs.org/en/). untuk membaca cara instalasi Node di sistem operasi yang digunakan.
  
* package.json
	
	Berkas _package.json_ adalah berkas konfigurasi yang digunakan oleh Node. Berkas ini digunakan terutama untuk konfigurasi berkas-berkas yang harus diinstalasi menggunakan NPM.
	
	Cara penggunaannya mudah, kita tinggal membuka direktori yang berisi berkasi _package.json_ melalui terminal lalu memulai instalasi library yang dibutuhkan dengan perintah `npm isntall`.

* Skrip NPM
	Selain mencatat library yang digunakan, _package.json_ juga dapat digunakan untuk menuliskan skrip perintah yang dapat kita jalankan di sebuah lingkungan Node.
	
	Kita juga akan menggunakan skrip `npm start` untuk menjalankan perintah-perintah seperti transpilasi menggunakan webpack atau menjalankan server Node.
	
	Di bagian TDD, kita juga dapat mengatur skrip `npm test` untuk menjalankan _test runner_ seperti Mocha untuk menjalankan tes pada berkas-berkas JavaScript aplikasi kita.
  
***

## 2. Back to ES6
  
### Apa Itu ES6 / ES2015

> ES6 is a significant update to the language, and the first update to the language since ES5 was standardized in 2009.
> Implementation of these features in major JavaScript engines is underway now.
> (https://github.com/lukehoban/es6features)

ECMAScript adalah spesifikasi yang dibuat sebagai proses standardisasi bahasa skrip yang awalnya dikembangkan oleh Brendan Eich untuk Netscape.
Versi JavaScript yang resmi didukung oleh semua peramban modern saat ini adalah ECMAScript 5 yang disahkan pada tahun 2011.

Pada tahun 2015 JavaScript mengalami perubahan besar-besaran dengan disahkannya ECMAScript 2015 atau lebih sering dikenal dengan sebutan ES6.
ES6 dapat dikatakan memiliki banyak fitur yang selama ini diidam-idamkan para programer JavaScript.

Dalam latihan ini kita akan menggunakan banyak fitur terbaru JavaScript yang tercantum di spesifikasi ES6. Oleh sebab itu akan sangat membantu bila fitur-fitur berikut telah dikuasai atau difahami.

### Beberapa contoh fitur terbaru JavaScript di ES6

Selain fitur yang meningkatkan fitur sebelumnya (seperti _for of_) dan fitur standar yang ada di bahasa-bahasa pemrograman lain (seperti _class_), berikut ini adalah beberapa fitur baru di ES6 yang sebaiknya dikuasai untuk membuat aplikasi React menggunakan ES6.

### _let_, _const_
Konstruktor _let_ dan _const_ lebih disarankan daripada penggunaan _var_ karena hanya dipengaruhi oleh blok tempat mereka dinyatakan. Sehingga mengurangi kebingungan bila kita menggunakan banyak blok dalam kode. Konstruktor _const_ digunakan untuk nilai konstan yang tidak akan berubah selama kode dijalankan.

### _Template Literal_
Perhatikan contoh berikut:

__ES5__
```javascript
var greet = 'Namaku ' + firstname + ' ' + lastname ', tinggal di ' + address + '.'
var url = 'http://localhost:3000/api/messages/' + id
```
__ES6__
```javascript
let greet = `Namaku ${firstname} ${lastname}, tinggal di ${address}.`
const url = `http://localhost:3000/api/messages/${id}`
```

Tik `` juga dapat digunakan untuk membuat string yang lebih dari satu baris.

## _Arrow function_ / "_Fat arrow_"
_Arrow function_ membuat penulisan kode menjadi lebih singkat dan jelas. Perhatikan contoh berikut:

__ES5__
```javascript
ajax.response(function(data) {
	//dosomething
})

var testMe = function(name, age) {
	//dosomething
}

var testIt = function() {
	//dosomething
}

something.onClick(function() {
	//dosomething
})

let messages = ids.map(function(value) {
	return "ID is " + value //return eksplisit
});
```
__ES6__
```javascript

ajax.response(data => {
	//dosomething
})

let testMe = (name, age) => {
	//dosomething
}

const testIt = () => {
	//dosomething
}

something.onClick(() => {
	//dosomething
})

let messages = ids.map(value => `ID is ${value}`) //return implisit
```

### Module dan Import

Perhatikan contoh berikut:

```javascript
//module.js
export const port = 3000
export function getAccounts(url) {
	//dosomething
}

# # #

//file lain yang menggunakan module dari module.js
import {port, getAccounts} from './module'
console.log(port) // 3000
```

### _Destructuring Assignment_

Kita dapat mengambil isi sebuah obyek secara langsung menggunakan key-nya. Perhatikan contoh berikut:

Alih-alih menuliskan:
```javascript
import utils from './utils'

function(object) {
	utils.doSomething()
	console.log(object.name)
	console.log(object.address)
	console.log(object.occupation)
}
```

Kita dapat menuliskan:
```javascript
import {doSomething} from './utils'

function({name, address, occupation}) {
	doSomething()
	console.log(name)
	console.log(address)
	console.log(occupation)
}
```

### _Object Literal_

Alih-alih menuliskan:
```javascript
function getCar(make, model, value) {
	return {
		make: make,
		model: model,
		value: value
	}
}
```
Kita dapat menuliskan:
```javascript
function getCar(make, model, value) {
	return {make, model, value}
}
```

Atau kalau gabung dengan penggunaan _arrow function_:
```javascript
const getCar = (make, model, value) => ({make, model, value})
```

### Operator _Rest/Spread_

Dengan sintaks _rest/spread_ "..." kita dapat membuat fungsi yang lebih fleksibel dalam menerima parameter. 
Sintaks ini juga dapat digunakan untuk "menyebarkan" isi setiap anggota array ke dalam array baru.

Perhatikan contoh berikut:

```javascript
function sum(…numbers) {
	var result = 0;
	numbers.forEach(number => {
		result += number;
	});
	return result;
}
console.log(sum(1)); // 1
console.log(sum(1, 2, 3, 4, 5)); // 15

let source = [1,2,3]
let newArr_A = source //<-berpotensi memutasi array sumber
let newArr_B = [...source] //<-operasi pada newArr_B tidak akan memutasi array sumber
```

### Parameter default

Perhatikan contoh berikut:

```javascript
const link = (height = 50, color = 'merah') => {
	console.log(`Tinggi ${height}cm berwarna ${color}`)
}

link() //<- menghasilkan "Tinggi 50cm berwarna merah"
```

### Struktur data Map dan Set

Perhatikan contoh berikut:

```javascript
let set = new Set();
set.add('red')
set.add('green')

set.size //<- menghasilkan 2
set.has('red') //<- menghasilkan true
set.delete('red') //<- menghasilkan true
set.has('red') //<- menghasilkan false

set.clear();
set.size  //<- menghasilkan 0

let map = new Map();
map.set('foo', 123);
map.set('bar', 'hi');

map.get('foo') //<- menghasilkan 123
map.get('bar') //<- menghasilkan 'hi'

map.size //<- menghasilkan 2
map.has('foo') //<- menghasilkan true
map.delete('foo') //<- menghasilkan true
map.has('foo') //<- menghasilkan false

map.clear()
map.size //<- menghasilkan 0
```

---

Beberapa fitur penting lain yang dapat kita gunakan di ES6 adalah `fetch()` dan `Promise()`.
  
***

## 3. React Component

***

## 4. React State

***

## 5. React useEffect

***

## 6. React Hooks

***

## 7. React Router

***

> **Sharing is Learning** ❤️‍🔥
