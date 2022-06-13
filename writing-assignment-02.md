> 🦖 **Impact Byte x Skilvul batch Joyful Jasper** 🐲
# Writing-Assignment-Week-02-Mirza Bakti Sukaryana 😆 🚀

| Table Of ‘Contents’ |
| ---------------------- |
| <ol> |
|  <li>Function</li> |
|  <li>Scope</li> |
|  <li>Conditional</li> |
|  <li>Loop</li> |
|  <li>Array</li> |
|  <li>Object</li> |
|  <li>DOM (Writing-Assignment-Week-03)</li> |
|  <li>Git (Writing-Assignment-Week-01)</li> |
| </ol> |

***

### 1. Function

Function merupakan blok kode yang tidak akan dieksekusi sebelum dipanggil dan dapat digunakan berulang.

Terdapat dua tipe fungsi pada JavaScript, yakni native function dan custom function. Contoh native function; console.log(), alert(), dan ada ratusan lainnya.

```javascript
function greeting() {
    return `Good morning, have a great day!`
}

console.log(greeting());
```

```javascript
function greeting(time) {
    return `Good ${time}, have a great day!`
}

console.log(greeting("morning"));
```

```javascript
greeting = (name, language) => {
    if(language === "English") {
        console.log("Good Morning " + name + "!");
    } else if (language === "French") {
        console.log("Bonjour " + name + "!");
    } else {
        console.log("Selamat Pagi " + name + "!");
    }
}

greeting("Harry", "French");
/* output Bonjour Harry! */
```

> :memo: **Note:** Nilai kembalian tidak hanya string, bisa saja berupa number, boolean, objek ataupun array.

***

### 2. Scope

Variabel yang dapat di akses dari seluruh script disebut dengan “globally scoped” atau lingkup global sementara variabel yang hanya dapat diakses hanya pada function tertentu disebut dengan “locally scoped” atau lingkup lokal. Jika variabel didefinisikan di luar fungsi, maka variabel akan bersifat global. Jika variabel didefinisikan di dalam fungsi, maka variabel bersifat lokal dan cakupannya hanya pada fungsi tersebut atau turunannya.

```javascript
// global variable, dapat diakses pada parent() dan child()
const a = 'a'; 
 
function parent() {
    // local variable, dapat diakses pada parent() dan child(),
    // tetapi tidak dapat diakses diluar dari fungsi tersebut.
    const b = 'b'; 
    
    function child() {
        // local variable, dapat diakses hanya pada fungsi child().
        const c = 'c';
    }
}
```

```javascript
function multiply(num) {
    total = num * num;
    return total;
}

let total = 9;
let number  = multiply(20);

console.log(total);
```

> :warning: **Warning:** Perlu kita perhatikan bahwa, ketika kita lupa menuliskan keyword let, const atau var pada script ketika membuat sebuah variabel, maka variabel tersebut akan menjadi global.

***

### 3. Conditional

Conditional artinya persyaratan.

If/else statement dapat digambarkan seolah-olah kita memberikan pertanyaan benar atau salah pada JavaScript, lalu memberikan perintah sesuai jawaban dari pertanyaan tersebut.

```javascript
let x = 60;

if(x > 70) {
    console.log(`Nilai adalah ${x}`);
} else if (x = 70) {
    console.log("Nilai sama dengan 70");
} else {
    console.log("Nilai kurang dari 70");
}
// output Nilai kurang dari 70
```

Jika logical statement tersebut menghasilkan true, maka JavaScript akan mengeksekusi kode yang berada di dalam block if. Jika logical statement menghasilkan nilai false, maka JavaScript akan memeriksa blok else if, jika bernilai false juga, maka kode yang pada block else lah yang akan dieksekusi.

```javascript
let language = "French";
let greeting = null;
switch (language) {
    case "English":
        greeting = "Good Morning!";
        break;
    case "French":
        greeting = "Bonjour!";
        break;
    case "Japanese":
        greeting = "Ohayou Gozaimasu!";
        break;
    default:
        greeting = "Selamat Pagi!";
}
console.log(greeting);
/* output Bonjour! */
```

Switch statement digunakan untuk melakukan pengecekan banyak kondisi dengan lebih mudah dan ringkas. Switch berisi variabel atau expression yang akan dievaluasi. Case diikuti dengan nilai yang valid. Break digunakan untuk keluar dari proses switch. Default memiliki fungsi yang sama dengan keyword else pada control flow if-else.

> :warning: Switch case tidak dapat digunakan untuk membandingkan suatu nilai

***

### 4. Loop

Looping adalah perulangan, di mana kita perlu melakukan hal yang sama berkali-kali tanpa berulang kali menuliskan kode yang sama.

```js
console.log(1);
console.log(2);
console.log(3);
console.log(4);
console.log(5);
```

#### for loop

```js
// start, requirment (true/false), do
// inisialisasi variabel; test kondisi; perubahan nilai variabel

for(let i = 0; i < 5; i++) {
    console.log(i);
}

/* output
0
1
2
3
4 */
```

#### for of loop

```js
let myArray = ['Mirza', 'Bakti', 'Sukaryana', 'Joyful Jasper'];

for (const arrayItem of myArray) {
  console.log(arrayItem);
}

/* Output:
Mirza
BaktiS
ukaryana
Joyful Jasper
*/
```

#### while

```js
let i = 1;

while (i <= 100) {
  console.log(i);
  i++;
}
```

> :bulb: **Tip:** while lebih cocok digunakan pada kasus di mana kita tidak tahu pasti berapa banyak perulangan yang diperlukan.

#### do while

```js
let i = 1;

do {
  console.log(i);
  i++;
} while (i <= 100);
```

Kondisi pada while akan dievaluasi sebelum blok kode di dalamnya dijalankan, sedangkan do-while akan mengevaluasi boolean expression setelah blok kodenya berjalan. Ini artinya kode di dalam do-while akan dijalankan setidaknya satu kali.

#### infinite loop

Infinite loop atau endless loop adalah kondisi di mana program kita stucked di dalam perulangan. Ia akan berjalan terus hingga menyebabkan crash pada aplikasi dan komputer kecuali ada intervensi secara eksternal, seperti mematikan aplikasi.

```js

let i = 1;

while (i <= 5) {
  console.log(i);
}
```

***

### 5. Array

Array merupakan tipe data yang dapat mengelompokkan lebih dari satu nilai dan menempatkannya dalam satu variabel.

> :memo: **Note:** Perbedaan array dengan object adalah data pada array disusun secara berurutan dan diakses menggunakan index.

```js
let myArray = ['Cokelat', 42.5, 22, true, 'Programming'];
console.log(myArray);

/* Output:
["Cokelat", 42.5, 22, true, "Programming"]
*/

// cara akses
console.log(myArray[1]);
/* Output:
42.5
*/

// menambah data array
myArray.push('JavaScript');
console.log(myArray);

/* Output:
['Coklat', 42.5, 22, true, 'Programming', 'JavaScript']
 */
 
// mengeluarkan elemen terakhir
myArray.pop();
console.log(myArray);

/* Output:
['Coklat', 42.5, 22, true, 'Programming']
*/

// Metode shift() digunakan untuk mengeluarkan elemen pertama dari array,
// sementara unshift() digunakan untuk menambahkan elemen di awal array.
myArray.shift();
myArray.unshift('Apple');

console.log(myArray);

/* Output:
['Apple', 42.5, 22, true, 'Programming']
*/

// menghapus data array
// keyword delete hanya menghapus data pada index yang ditentukan lalu membiarkan posisi tersebut kosong.
delete myArray[1];
console.log(myArray);

/* output
['Apple', <1 empty item>, 22, true, 'Programming']
*/

// Untuk menghapus elemen, gunakan metode splice()
myArray.splice(2, 1);   // Menhapus dari index 2 sebanyak 1 elemen
console.log(myArray);

/* output:
['Apple', <1 empty item>, 42.5, true, 'Programming']
*/
```

***

### 6. Object

Objek serupa dengan array yang dapat menampung banyak nilai dengan tipe data yang beragam. Untuk mengelola data menggunakan objek, bedanya objek diakses tidak melalui indexing,  melainkan menggunakan pendekatan key-value. Untuk mengakses nilainya kita gunakan key. Key juga biasa disebut dengan properti.

```js
const user = {
  firstName: 'Mirza',
  lastName: 'Bakti',
  age: 99,
  isJedi: true,
  'home world': 'Bogor',
};

console.log('Halo, nama saya ' + user.firstName + ' ' + user.lastName);
console.log('Umur saya ' + user.age + ' tahun');
console.log('Saya berasal dari ' + user['home world']);

/* Output:
Halo, nama saya Mirza Bakti
Umur saya 99 tahun
Saya berasal dari Bogor
*/
```

#### memodifikasi object

```js
const spaceship = {
  name: 'Millenium Falcon',
  manufacturer: 'Corellian Engineering Corporation',
  maxSpeed: 1200,
  color: 'Light gray',
};

spaceship.color = 'Glossy red';
spaceship['maxSpeed'] = 1300;
spaceship.class = 'Light freighter';
console.log(spaceship);

/* Output:
{
  name: 'Millenium Falcon',
  manufacturer: 'Corellian Engineering Corporation',
  maxSpeed: 1300,
  color: 'Glossy red'
  class: 'Light freighter'
}
 */
 
spaceship = { name: 'New Millenium Falcon' };
// Error

delete spaceship.manufacturer;

console.log(spaceship);
/* Output:
{
  name: 'Millenium Falcon',
  maxSpeed: 1300,
  color: 'Glossy red'
  class: 'Light freighter'
}
 */
```

Object spaceship dideklarasikan sebagai const, tetapi kenapa kita bisa mengubah nilainya?

Yang perlu diperhatikan adalah mengubah nilai berbeda dengan menginisialisasi ulang nilai. Ketika membuat sebuah object, kita tidak terikat dengan properti di dalamnya sehingga kita masih bisa memodifikasi nilainya. Berbeda jika kita menginisialisasi ulang variabel dari object.

Ketika kita mengubah object menggunakan assignment operator dan property/key-nya sudah ada, maka nilai di dalamnya akan tergantikan dengan nilai yang baru. Sedangkan, jika property dengan nama key yang ditentukan tidak ditemukan, maka properti baru akan ditambahkan ke object.

***

> **Sharing is Learning** ❤️‍🔥
