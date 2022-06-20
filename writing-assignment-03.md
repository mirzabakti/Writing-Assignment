> 🦖 **Impact Byte x Skilvul batch Joyful Jasper** 🐲
# Writing-Assignment-Week-03-Mirza Bakti Sukaryana 😆 🚀

| Table Of ‘Contents’ |
| ---------------------- |
| <ol> |
|  <li>Module</li> |
|  <li>Rekursif</li> |
|  <li>Web Storage</li> |
|  <li>Asyncronous</li> |
|  <li>Responsive Web Design</li> |
|  <li>Bootstrap</li> |
| </ol> |

***

### 1. Module

Module adalah sebuah cara untuk menghubungkan berkas JavaScript yang terpisah agar dapat saling digunakan juga dapat digunakan berulang.

Fungsi module;
<ol>
  <li>Maintainability</li>
  <li>Penggunaan Nama Variabel</li>
  <li>Reusable Code</li>
</ol>

Penggunaan

```js
  <script type="module" src="index.js"></script>
```

> :warning: **Warning:** Untuk menjalankan module pada lokal direktori, kamu harus menggunakan static-sever seperti Live Server pada Visual Studio Code.

Export

Contoh dasar melakukan export

```js
export let name = "Mirza";

export let orang = {
  nama: "Bakti",
  umur: 25,
  alamat: "Jl. Narogong",
};

export function sayHello(user) {
  console.log(`Hello, ${user}!`);
}
```

Mengexport sekaligus

```js
  export { name, orang, sayHello };
```

Import

Import digunakan untuk menggunakan variabel yang sudah di-export dari module lainnya.

Penggunaan

```js
import { name, orang, sayHello } from "./user.js";

// Menggunakan hasil import
console.log(name);
console.log(orang);
sayHello(orang.nama);
```

Export As

```js
  export namaVariabelLama as namaVariabelBaru;
  export { warna as color, orang as person, katakanHalo as sayHello };
```

> :memo: **Note:** Kita sudah tidak bisa menggunakan nama variabel yang lama ketika meng-import. Ini dikarenakan variabel yang lama sudah diberikan alias ke nama yang baru ketika di-export.

> :memo: **Note:** Penggunaan export as hanya bisa dilakukan dengan export secara sekaligus di akhir kode.

Import As

```js
  import { namaVariabelLama as namaVariabelBaru } from "./namaModul.js";
  
import {
  warnaKesukaan as favoriteColor,
  orangBaru as newPerson,
  katakanHalo as sayHello,
} from "./user.js";
```

Export Default

```js
  export default data;
  
// greeting.js
function sayHello(user) {
  console.log(`Hello, ${user}!`);
}

export default sayHello;


  import data from "./namaModul.js";
  
  
import sayHello from "./greeting.js";

sayhello("Mirza");

import sayHello, { FONTS } from "./greeting.js"
```

***

### 2. Rekursif

Rekursif adalah fungsi yang memanggil fungsi tersebut atau dirinya sendiri, seolah-olah terjadi suatu perulangan.

```js
function rekursif() {
  // kode lainnya
  rekursif();
}
```

Jika recursive function tersebut memanggil dirinya sendiri, akan terjadi infinity recursion.

Algoritma rekursif;
<ol>
  <li>Base Case</li>
  Base case akan dikunjungi jika rekursi berakhir (kondisi untuk berhenti terpenuhi), serta mengembalikan nilai tanpa melakukan rekursi kembali.
  <li>Recursion Call</li>
  Permasalahan dapat diperkecil dengan mengurangi atau memecahkan data input pada setiap pemanggilannya hingga mencapai base case.
</ol>

```js
function namaFuncRekursif() {
  if (condition) {
    // Base case
  } else {
    // Recursion call
    namaFuncRekursif();
  }
}


function faktorial(n) {
  if (n == 1) {
    return 1;
  } else {
    return n * faktorial(n - 1);
  }
}

console.log(faktorial(4))
```

***

### 3. Web Storage

Web storage adalah salah satu Web API yang dapat menyimpan data secara lokal pada sisi client.

Web storage dapat menampung sebesar 10MB untuk satu domain.

Pada sessionStorage atau localStorage data yang disimpan adalah nilai primitif seperti number, boolean, atau string. Namun kita juga dapat menyimpan data berbentuk objek dengan mengubahnya dalam bentuk string, begitu pula sebaliknya ketika kita ingin menggunakan datanya kembali.

Untuk menyimpan dan mengakses data pada storage, metode yang digunakan adalah key-value. Di sini key menjadi sebuah kunci untuk mengakses data pada storage.

Data yang disimpan pada Web Storage dapat kita lihat menggunakan DevTools pada tab Application (Google Chrome) atau tab Storage (Mozilla Firefox).

Session Storage digunakan untuk menyimpan data sementara pada browser. Data akan hilang ketika browser atau tab browser ditutup.

Untuk menggunakan Session Storage kita gunakan object sessionStorage, kemudian untuk menyimpan datanya gunakan method setItem(), method ini membutuhkan dua argumen yakni key dan nilai yang akan dimasukkan. Kemudian untuk mengakses data yang sudah dimasukkan kita gunakan method getItem() dan gunakan key sebagai argumen methodnya.

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <title>Session Storage</title>
</head>
<body>
  <p>Anda sudah menekan tombol sebanyak <span id="count"></span> kali</p>
  <button id="button">Click Disini!</button>
  
  <script>
    const cacheKey = 'NUMBER';
    if (typeof (Storage) !== 'undefined') {
      // pengecekkan apakah data sessionStorage dengan key NUMBER tersedia atau belum
      if (sessionStorage.getItem(cacheKey) === 'undefined') {
        // Jika belum maka akan atur dengan nilai awal yakni 0
        sessionStorage.setItem(cacheKey, 0);
      }
      
      const button = document.querySelector('#button');
      const count = document.querySelector('#count');
      button.addEventListener('click', function (event) {
        let number = sessionStorage.getItem(cacheKey);
        number++;
        sessionStorage.setItem(cacheKey, number);
        count.innerText = sessionStorage.getItem(cacheKey);
      });
    } else {
      alert('Browser tidak mendukung Web Storage');
    }
  </script>
</body>
</html>
```

Local Storage yang serupa dengan session storage, namun data yang disimpan tidak akan hilang bila browser atau tabs browser ditutup. Kita bisa menghapus data pada local storage dengan method removeItem().

Untuk penggunaan localStorage identik dengan sessionStorage, perbedaannya storage ini diakses melalui object localStorage.

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <title>Local Storage</title>
</head>
<body>
  <p>Anda sudah menekan tombol sebanyak <span id="count"></span> kali</p>
  <button id="button">Click Disini!</button>
  <button id="clear">Hapus Storage</button>
  
  <script>
    const cacheKey = 'NUMBER';
    if (typeof (Storage) !== 'undefined') {
      // pengecekkan apakah data localStorage dengan key NUMBER tersedia atau belum
      if (localStorage.getItem(cacheKey) === 'undefined') {
        // Jika belum maka akan atur dengan nilai awal yakni 0
        localStorage.setItem(cacheKey, 0);
      }
      
      const button = document.querySelector('#button');
      const clearButton = document.querySelector('#clear');
      const count = document.querySelector('#count');
      button.addEventListener('click', function (event) {
        let number = localStorage.getItem(cacheKey);
        number++;
        localStorage.setItem(cacheKey, number);
        count.innerText = localStorage.getItem(cacheKey);
      });
      
      clearButton.addEventListener('click', function (event) {
        localStorage.removeItem(cacheKey);
      });
    } else {
      alert('Browser tidak mendukung Web Storage');
    }
  </script>
</body>
</html>
```

***

### 4. Asyncronous

Javascript adalah bahasa pemrograman single-thread yang artinya hanya dapat mengeksekusi satu task pada satu waktu atau biasa disebut synchronous.

Asynchronous mengizinkan komputer memproses task yang lain sambil menunggu proses yang masih berlangsung.

Kita bisa membuat asynchronous secara simulasi artinya tidak murni asynchronous dengan beberapa cara:

Callback,
Promises,
Async/Await.

Callback function adalah function yang kita letakan di dalam argumen/parameter pada function, dan function tersebut akan dieksekusi setelah function pertama menyelesaikan tugasnya.

setTimeout digunakan untuk simulasi asynchronous. Karena sebenarnya kita tidak bisa membuat proses asynchronous murni.

Promise adalah salah satu fitur baru di ES6, biasa digunakan untuk melakukan http request/fetch data dari API.

Dalam pengambilan data, promise memiliki 3 kemungkinan state.
Pending(sedang dalam proses)
Fulfilled (berhasil)
Rejected (gagal)

Async - await adalah salah satu fitur baru dari javascript yang digunakan untuk menangani hasil dari sebuah Promise. Sedangkan await berfungsi untuk menunda sebuah kode dijalankan sampai proses asynchronous berhasil.

Fetch adalah native web API untuk melakukan HTTP calls dari external network.

```js
// async callback

const mainFunc = (number1, number2, callback) => {
  console.log(number1 * number2);
  callback();
  console.log(number1 + number2);
};

const callbackFunc = () => {
  console.log("callback");
};

mainFunc(10, 20, callbackFunc);

// setTimeOut

const p1 = () => {
  console.log("proses 1");
};

const p2 = () => {
  setTimeout(() => {
    console.log("proses 2");
  }, 5000);
};

const p3 = () => {
  p1();
  p2();
  console.log("proses 3");
};

p3();

let photoProfile = document.getElementById("photoProfile");
let username = document.getElementById("username");
let followers = document.getElementById("followers");

// promise fetch
// get data API
// const getDataGithubPromise = () => {
const url = "https://api.github.com/users/bilasta89";

// melakukan fetch data
fetch(url)
  .then((response) => response.json()) // membuka paket
  .then((result) => {
    console.log(result);
    photoProfile.src = result.avatar_url;
    username.innerText = result.login;
    followers.innerText = result.followers;
  })
  .catch((error) => console.log(error));
// };

// getDataGithubPromise()
// console.log(data);

// async fetch
const getDataGithubAsync = async () => {
  const url = "https://api.github.com/users/bilasta89";

  // melakukan fetch data
  let response = await fetch(url);
  // membuka paket
  let result = await response.json();
  console.log(result);

  photoProfile.src = result.avatar_url;
  username.innerText = result.login;
  followers.innerText = result.followers;

  // function async jika di dalamnya dikasih return
  // maka function ini akan bernilai sebuah promise
  // return result
};

getDataGithubAsync();
```

***

### 5. Responsive Web Design

RWD singkatan dari Responsive Web Design. Responsif artinya webnya dapat merespon atau menyesuaikan diri dengan perangkat yang digunakan.

ViewPort adalah area web yang terlihat dari perangkat (visible area).

```html
  <meta name="viewport" content="width=device-width, initial-scale=1">
```

Media Query digunakan untuk membuat beberapa styles terhantung jenis device

```css
@media only screen and (max-width: 600px) {
  body {
    background-color: lightblue;
  }
}
```

Breakpoint adalah titik di mana terjadi perubahan aturan.

***

### 6. Bootstrap

Bootstrap adalah framework CSS yang bersifat Free dan Open Source. Bootstrap menyediakan class-class CSS dan beberapa fungsi Javascript untuk mempermudah pembuatan web.

Bootstrap awalnya bernama Twitter Blueprint. Karena waktu itu pertama kali dikembangkan oleh Mark Otto dan Jacob Thornton di Twitter.

Kemudian Twitter Blueprint diubah namanya menjadi Bootstrap dan dirilis sebagai proyek Open Source pada 19 Agustus 2011.

Bootstrap 5 resmi dirilis versi Alpha pada tanggal 16 Juni 2020. Berikutnya versi Beta dirilis pada 7 Desember 2020.

Karena akan banyak menggunakan class Bootstrap, dan jika kamu belum paham tentang CSS.. bisa jadi akan kesulitan memahaminya.

Tools;
<ol>
  <li>Code Editor</li>
  <li>Web Browser</li>
  <li>Bootstrapt</li>
   Kita bisa gunakan yang dari CDN atau Download dengan package manger seperti NPM atau download secara manual juga bisa.
</ol>

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>My First Bootstrapt</title>
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.2.0-beta1/dist/css/bootstrap.min.css" rel="stylesheet" integrity="sha384-0evHe/X+R7YkIZDRvuzKMRqM+OrBnVFBL6DOitfPri4tjfHxaWutUpFmBp4vmVor" crossorigin="anonymous">
</head>
<body>
    
    <section>
        <nav class="navbar navbar-expand-lg shadow-sm" style="background-color: #F47C7C;" >
            <div class="container">
                <a class="navbar-brand" href="#">
                    <img src="assets/Saly-44.png" alt="" width="64px" class="d-inline-block align-text-top">
                </a>
              <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarNav" aria-controls="navbarNav" aria-expanded="false" aria-label="Toggle navigation">
                <span class="navbar-toggler-icon"></span>
              </button>
              <div class="collapse navbar-collapse" id="navbarNav">
                <ul class="navbar-nav">
                  <li class="nav-item">
                    <a class="nav-link active mx-5 text-white" aria-current="page" href="#">Home</a>
                  </li>
                  <li class="nav-item">
                    <a class="nav-link mx-5 text-white" href="#">About Us</a>
                  </li>
                  <li class="nav-item">
                    <a class="nav-link mx-5 text-white" href="#">Pricing</a>
                  </li>
                </ul>
              </div>
            </div>
          </nav>
    </section>

    <section id="hero">
        <div class="container">
            <div class="container-fluid">
                <div class="row align-items-center">
                    <div class="col-md-6 col-sm-12 my-5">
                        <h1>Web Design Agency<br/> In Indonesia </h1>
                        <br/>
                        <h5>Perusahaan digital agency dan web design di Jakarta, Indonesia. Kami telah mendesign ratusan website dan membantu meningkatkan performa online mereka melalui SEO, SEM dan Social Media Marketing sejak 2005 –
                            tahun di mana YouTube lahir.
                        </h5>
                    </div>
                    <div class="col-md-6 col-sm-12">
                        <img src="assets/Saly-12.png" alt="" class="img-fluid">
                    </div>
                </div>
            </div>
        </div>
    </section>

    <section id="media">
        <div class="col-12 text-center my-5 fw-bolder fst-italic text-lowercase">
            <h4>Trusted by 99.999+ Customer</h4>
        </div>

        <div class="container">
            <div class="container-fluid">
                <div class="row">
                    <div class="col-2">
                        <img src="assets/Instagram-1.png" alt="customer" class="img-fluid">
                    </div>
                    <div class="col-2">
                        <img src="assets/Discord-1.png" alt="customer" class="img-fluid">
                    </div>
                    <div class="col-2">
                        <img src="assets/Dribbble.png" alt="customer" class="img-fluid">
                    </div>
                    <div class="col-2">
                        <img src="assets/Dropbox2OctDenoiserBeauty_002 2.png" alt="customer" class="img-fluid">
                    </div>
                    <div class="col-2">
                        <img src="assets/PT2OctDenoiserBeauty_002 copy 2.png" alt="customer" class="img-fluid">
                    </div>
                    <div class="col-2">
                        <img src="assets/Reddit2OctDenoiserBeauty_002.png" alt="customer" class="img-fluid">
                    </div>
                </div>
            </div>
        </div>
    </section>

    <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.2.0-beta1/dist/js/bootstrap.bundle.min.js" integrity="sha384-pprn3073KE6tl6bjs2QrFaJGz5/SUsLqktiwsUTF55Jfv3qYSDhgCecCxMW52nD2" crossorigin="anonymous"></script>
</body>
</html>
```

![screencapture](https://user-images.githubusercontent.com/66278794/174532635-ad1cd165-2304-4c81-b0a6-d217ae92dbf6.png)


***

> **Sharing is Learning** ❤️‍🔥
