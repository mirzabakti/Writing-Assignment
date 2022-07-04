> 🦖 **Impact Byte x Skilvul batch Joyful Jasper** 🐲
# Writing-Assignment-Week-04-Mirza Bakti Sukaryana 😆 🚀

| Table Of ‘Contents’ |
| ---------------------- |
| <ol> |
|  <li>Introduction to React JS</li> |
|  <li>Back to ES6</li> |
|  <li>React Component</li> |
|  <li>React State</li> |
|  <li>React useEffect/ Hooks</li> |
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

Secara konsep, komponen mirip dengan fungsi pada Javascript. Komponen menerima beberapa masukan (biasa disebut “props”) dan mengembalikan element React yang mendeskripsikan apa yang seharusnya tampil pada layar. Komponen mempermudah untuk memecah antarmuka pengguna menjadi bagian tersendiri, bagian yang bisa digunakan kembali.

```js
function Welcome(props) {
  return <h1>Halo, {props.name}</h1>;
}

class Welcome extends React.Component {
  render() {
    return <h1>Halo, {this.props.name}</h1>;
  }
}
```

> :memo: **Note:** Selalu awali nama komponen dengan sebuah huruf kapital. React memperlakukan awalan komponen dengan huruf kecil sebagai tag dari DOM. Sebagai contoh, ```<div />```, merepresentasikan sebuah HTML div tag, tetapi <Welcome /> merepresentasikan sebuah komponen dan membutuhkan Welcome to be in scope.

```js
// import file css
import './App.css';
// Penggunaan Export dam Import
import ExportHalaman from './components/ExportHalaman';
// Import local img
import Landscape from "./img/landscape.jpg"
function App() {
  // tempat membuat Variabel sebelum return
  let pulang = "ke kampung halaman";
  const perkalian = 9 * 9;
  // event internal
  const handleClick = () => {
    console.log("burung hantu")
  };
  // conditional
  const isLogin = true
  // Map
  const data = [
    {
      orang: "Arrie",
    },
    {
      orang: "Baharudin",
    },
    {
      orang: "Mirza"
    }];

  return (
    // JSX
    // react membutuhkan pembunggkus untuk parentnya
    <div className="App">
      <header className="App-header">
        {/* import halaman */}
        <ExportHalaman />

        {/* url image */}
        <img width={200} src="https://images.pexels.com/photos/12656616/pexels-photo-12656616.jpeg?cs=srgb&dl=pexels-till-daling-12656616.jpg&fm=jpg" alt='landscape' />

        {/* local image */}
        <br />
        <img width={200} src={Landscape} alt='landscape' />


        {/* Penggunaan class pada React yaitu menggunakan ClassName */}
        <h3 className='nama'>Mirza</h3>

        {/* Curly Braces in JSX */}
        <h2> {7 + 7} </h2>

        {/* Variabel harus dipanggil Terlebih dahulu */}
        <h4> {pulang} </h4>
        <h3> {perkalian} </h3>
        <p> {"surabaya".toUpperCase()} </p>

        {/* Event */}
        {/* Pembuatan Button secara inlane */}
        <button onClick={() => console.log("inlane Button")}>Inlane Button</button>
        <br />
        <button onClick={() => console.log("ayam goreng")}>tekan</button>

        {/* pembuattan button secara internal */}
        <br />
        <button onClick={handleClick}>Tes</button>

        {/* checkbox */}
        <br />
        <input type={"checkbox"} onChange={() => console.log("ayam")} />

        {/* input form */}
        <br />
        <input type={"text"} onChange={(event) => console.log(event.target.value)} />


        <br />
        {/* conditional */}
        {/* satu - satunya codisional yang bisa dipakai pada React Js Ternary operator */}
        {isLogin ? <p>sudah login</p> : <p>belum login</p>}


        {/* maping menampilkan Array of object */}
        {data.map((item, index) => (
          <h1 key={index}>{item.orang}</h1>
        ))}
      </header>
    </div>
  );
}

export default App;
```


***

## 4. React State

State adalah data yang dimiliki oleh sebuah komponen (statefull component). Dan ada kemungkinan datanya dapat berubah.

Membuat state di react membutuhkan useState().

useState, adalah fitur dari react untuk membuat state di dalam functional component.

**cara sederhana useState Hooks**
1. import useState dari react 
   ```js
   import {useState} from "react";
   ```
2. menuliskan userState hooks
   ```js
    const [nama, setNama] = useState("Baharudin");
   ```
3. memanggil data useState
   ```js
   <h3>{nama}<h3>
   ```


***

## 5. React useEffect

Hooks merupakan fitur baru di React 16.8. baru dikenalkan pada tahun 2018 Fitur ini memungkinkan Anda menggunakan state dan fitur React lainnya tanpa menuliskan sebuah kelas.

Hooks yang seriang diggunakan, adalah useState dan useEffect. untuk materi hooks ini akan lebih fokus pada useEffect

**Perbedaan class dan functional**
class menggunakan state sedangkan functional menggunakan state hooks sekilas hasil yang dikeluarkannya sama tidak ada perbedaaan

**kelebihan penggunaan hooks**
- lebih rapi penggunaannya
- lebih pendek 
- mudah dimengerti

**useEffect hooks**
useEffect merupakan hooks yang bisa digunakan untuk menggunakan ***lifecycle*** pada functional component dengan mudah

**Apa itu lifecycle**
LifeCycle yaitu sebuah proses yang dilakukan component yang sedang berjalan 

LifeCycle yang ada didalam hooks hanya mennggunakan useEffect yang menggabugkan 
- Mounting
- Updating
- Unmouting

**Cara Penggunaan useEffect usntuk menampilkan data Github**

1. instal axios dengan format: **npm i axios**
2. import axios dan useEffect
3. siapkan data github
4. berikut ini penggunaan useEffect pada react
```js
import { useEffect, useState } from "react";
import axios from "axios";

function App() {
  const [dataGithub,setDataGithub] = useState({});

  // useeffect call api
  let url = "https://github.com/baharudin-solusite";

  useEffect(() => {
    async function getAPI() {
      const result = await axios.get(url);
      console.log(result);
      setDataGithub(result.data);
    }

    getAPI();
  }, []);

  console.log(dataGithub);

  return (
    <div className="App">
      <h1>Use Effect</h1>

      {/* useEffect data github  */}
      <h1>Nama github: {dataGithub.name}</h1>
      <h1>Username: {dataGithub.login}</h1>
      <h1>id: {dataGithub.id}</h1>
  );
}

export default App;
```

***


## 6. React Router

React Router adalah library perutean klien dan sisi server berfitur lengkap untuk React, library JavaScript untuk membangun antarmuka pengguna. React Router berjalan di mana saja. React berjalan; di web, di server dengan node.js, dan di React Native.

```js
import ReactDOM from "react-dom/client";
import {
  BrowserRouter,
  Routes,
  Route,
} from "react-router-dom";
import App from "./App";
import Expenses from "./routes/expenses";
import Invoices from "./routes/invoices";

const root = ReactDOM.createRoot(
  document.getElementById("root")
);
root.render(
  <BrowserRouter>
    <Routes>
      <Route path="/" element={<App />}>
        <Route path="expenses" element={<Expenses />} />
        <Route path="invoices" element={<Invoices />} />
      </Route>
    </Routes>
  </BrowserRouter>
);
```

```js
import { Outlet, Link } from "react-router-dom";

export default function App() {
  return (
    <div>
      <h1>Bookkeeper</h1>
      <nav
        style={{
          borderBottom: "solid 1px",
          paddingBottom: "1rem",
        }}
      >
        <Link to="/invoices">Invoices</Link> |{" "}
        <Link to="/expenses">Expenses</Link>
      </nav>
      <Outlet />
    </div>
  );
}
```

***

> **Sharing is Learning** ❤️‍🔥
