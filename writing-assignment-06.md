> 🦖 **Impact Byte x Skilvul batch Joyful Jasper** 🐲
# Writing-Assignment-Week-05-Mirza Bakti Sukaryana 😆 🚀

| Table Of ‘Contents’ |
| ---------------------- |
| <ol> |
|  <li>Node JS</li> |
|  <li>Web Servers & RESTFul API</li> |
|  <li>Express Routing & Middleware</li> |
|  <li>MySQL</li> |
|  <li>Design Database</li> |
| </ol> |

***

## 1. Node JS

Apa perbedaan Node.js dengan JavaScript?

JavaScript adalah bahasa pemrograman yang digunakan bersamaan dengan HTML dan CSS yang berguna untuk membuat halaman website lebih interaktif.

Sedangkan Node.js adalah sebuah software yang digunakan untuk pengembangan aplikasi berbasis web dan ditulis dalam sintaks bahasa pemrograman JavaScript yang bersifat open-source dan cross platform. Mempunyai library sendiri sehingga bisa berjalan tanpa menggunakan program web server seperti Apache atau Nginx.  Bertugas mengeksekusi kode JavaScript sebelum halaman website ditampilkan pada browser.

### Arsitektur Node.js

![image](https://user-images.githubusercontent.com/66278794/182500109-2005716f-a5c0-40a4-bfcb-981ee9647c4c.png)

```js
Request, request masuk yang berasal dari user.

Node.js Server, server yang bertugas untuk menghandle request yang masuk dan memberikan response ke user.

Event Queue, menyimpan request sesuai urutan masuk untuk kemudian diproses oleh Event Loop satu per satu.

Event Loop / Main Thread, semua request yang masuk akan diproses oleh event loop untuk dieksekusi.

Blocking Operastion (Program Berjalan/Sedang dijalankan).

Worker Pool / Thread Pool, berisi thread untuk membantu kerja dari event loop.

Worker Threads(menjalankan perintah).

Execute Callback (mengebalikan Perintah).
```

Single Thread : Javascript menggunakan konsep single thread, yang berarti hanya memiliki satu tumpukan panggilan yang digunakan untuk menjalankan program. Ketika terdapat perintah baru maka akan ditambahkan (push) dan akan di keluarkan ketika perintahnya sudah selasai (pop).

Even Loop : memfasilitasi kondisi event queue (sebagai penampung ketika terdapat perintah baru yang akan dieksekusi), event loop akan memeriksa terus menerus, ketika antrian kosong di call stack maka akan menambah antrian baru dari event queue sampai semua perintah selesai di eksekusi.

Server side scripting : Sejatinya javascript merupakan bahasa pemrograman yang digunakan di front end side. Tetapi dengan menggunakan NodeJS kita dapat menjalankan javascript di server side menggunakan terminal command line menggunakan perintah “node”.

### Instalasi Node.js

Untuk mengetes apakah berhasil terinstall, dapat menjalankan “node -v” untuk mengecek versi NodeJS yang terinstal.

NodeJS ini juga dilengkapi dengan NPM (node package manager) dan dapat mengeceknya juga menggunakan “npm -v”.

Kita dapat menggunakan node di terminal kita dengan mengetik “node” kemudian bisa membuat code javascript dan langsung dieksekusi.

### Module Node JS

#### Jenis Module

```js
Build in : package bawaan dari node js itu sendiri.

External : package yg bukan bawaan node js itu sendiri (mengambil dari luar).

Custom :  package module yang kita buat sesuai kebutuhan.
```

#### Contoh

```js
Bulit-in Module : http, url, path, util, ft.

External Module : express, nodemoon dan lodash.

Custome Module :
    exports.myDateTime = function () {
    return Date();
    };
```

1. Console : merupakan module bawaan dari javascript yang ada di node JS untuk digunakan sebagai debug atau menampilkan code secara interface Console Node JS

2. Process : adalah modules yang digunakan untuk menampilkan dan mengontrol prosess Node JS yang sedang dijalankan.

3. OS : merupakan module yang digunakan untuk menyediakan informasi terkait sistem operasi komputer yang digunakan user.

4. Util : merupakan alat bantu / utilities untuk mendukung kebutuhan internal API di Node JS

5. Events : adalah kejadian yang terjadi di halaman web. Kejadian yang dimaksud di sini seperti aktivitas yang dikerjakan pada halaman web.

6. Error : merupakan modules yang dapat digunakan untuk mendefinisikan error di Node JS sehingga lebih informatif. Kita juga dapat menghandle error menggunakan "try catch"

7. Buffers: modules yang digunakan untuk mengakses, mengelola dan mengubah tipe data raw atau tipe data bytes

8. FS : Fs atau “file system” merupakan module yang dapat membantu berinteraksi dengan file yang ada diluar code. FS paling sering digunakan untuk membaca file dengan ekstensi .txt, .csv, dan .json 9. Timers merupakan modules yang digunakan untuk melakukan scheduling atau mengatur waktu pemanggilan fungsi yang dapat diatur di waktu tertentu

#### Node JS Web Server

```js
Node.js memiliki built-in modul yang disebut HTTP, built-in modul ini memungkinkan Node JS mentransfer data
melalui Hyper Text Transfer Protocol (HTTP).

Untuk menggunakan modul HTTP, gunakan require().

Method createServer() untuk membuat server HTTP.

Callback function yang digunakan pada method http.createServer(), akan dijalankan ketika seseorang mencoba
mengakses komputer pada port 8080.
```

![image](https://user-images.githubusercontent.com/66278794/182504716-3ea1113a-1dfb-498d-b91a-2db790dff221.png)

***

## 2. Web Servers & RESTFul API

Fungsi utama Server atau Web server adalah untuk melakukan atau akan mentransfer berkas permintaan pengguna melalui protokol komunikasi yang telah ditentukan sedemikian rupa. halaman web yang diminta terdiri dari berkas teks, video, gambar, file dan banyak lagi.

![image](https://user-images.githubusercontent.com/66278794/182504956-c9cd00f0-230d-4f09-b016-f545fb685865.png)

#### Perbedaan antara static web server dan dynamic web server

1. Interaksi antara pengunjung dan pemilik web
Dalam web statis tidak dimungkinkan terjadinya interaksi antara pengunjung dengan pemilik web. Sementara dalam web dinamis terdapat interaksi antara pengunjung dengan pemilik web seperti memberikan komentar, transaksi online, forum, dll.
2. Bahasa Script yang digunakan
Web statis hanya menggunakan HTML, CSS, JS dan frameworknya saja. Sedangkan web dinamis menggunakan bahasa pemrograman web yang lebih kompleks.
3. Penggunaan Database
Web statis tidak menggunakan database karena tidak ada data yang perlu disimpan dan diproses. Sedangkan web dinamis menggunakan database seperti MySQL, Oracle, dll untuk menyimpan dan memroses data.
4. Konten
Konten dalam web statis hanya diberikan oleh pemilik web dan jarang di-update, sementara konten dalam web dinamis bisa berasal dari pengunjung dan lebih sering di-update. Konten dalam web dinamis bisa diambil dari database sehingga isinya pun bisa berbeda-beda walaupun kita membuka web yang sama.

#### Arsitektur static site dan dynamic site

```js
Static Site,
client side meminta http request kemudian diterima oleh web server dimana terdapat file seperti html css javascript,
dan responese yang ditampilkan hanya berupa file file tadi.
tidak ada processing data di webserver.

Dynamic site,
Client side meminta GET request dan akan masuk ke web server dan selanjutnya masuk ke dalam web application.
kemudian didalam web application dilakukan processing data dari database dan akan dibawa ke web server
dan dilakukan response sehingga tampilah di dalam browser.
```

#### Yang dapat kita buat pada sisi server

```js
Simpan informasi sesi/status.
Pengalaman pengguna yang disesuaikan.
Penyimpanan dan pengiriman informasi yang efisien.
Akses terkontrol ke konten.
Pemberitahuan dan komunikasi.
Analisis data. 
```

RESTful : Sebuah jenis layanan web API yang menggunakan REST, atau Representational State Transfer. REST adalah gaya arsitektur untuk sistem hypermedia yang digunakan untuk World Wide Web.

#### Komponen REST API

URL Design RESTful API diakses menggunakan protokol HTTP. Penamaan dan struktur URL yang konsisten akan menghasilkan API yang baik dan mudah untuk dimengerti developer. URL API biasa disebut endpoint dalam pemanggilannya.

Jenis HTTP verbs

```js
GET, menyediakan hanya akses baca pada resource
PUT, digunakan untuk menciptakan resource baru
DELETE, digunakan untuk menghapus resource
POST, digunakan untuk memperbarui resource yang ada atau membuat resource baru
OPTIONS, digunakan untuk mendapatkan operasi yang disupport pada resource
```

Response Codes, Kode respons standar yang diberikan oleh server website di internet.
Kode ini membantu mengidentifikasi penyebab masalah saat laman website atau sumber daya lain tidak dimuat dengan benar.

![image](https://user-images.githubusercontent.com/66278794/182505814-87eb541a-0b2d-402f-84b4-bf7472cf7c7b.png)

Format Response Setiap request yang dilakukan client akan menerima data response dari server, response tersebut biasanya berupa data XML ataupun JSON.

***

## 3. Express Routing & Middleware

Express.js adalah framework web app untuk Node.js yang ditulis dengan bahasa pemrograman JavaScript. Framework open source ini dibuat oleh TJ Holowaychuk pada tahun 2010 lalu.

Express.js adalah framework back end. Artinya, ia bertanggung jawab untuk mengatur fungsionalitas website, seperti pengelolaan routing dan session, permintaan HTTP, penanganan error, serta pertukaran data di server. 

Nah, framework yang satu ini punya arsitektur MVC (Model View Controller). Dengan begitu, setiap data diolah pada Model, dihubungkan melalui Controller, lalu ditampilkan menjadi informasi melalui View.

![image](https://user-images.githubusercontent.com/66278794/182506792-f38abb79-3312-41b7-88b6-007552b31656.png)

#### Penggunaan Express API

Buka Terminal 

ketik format ```npm init -y``` untuk membuat inisial pada projek yang akan menampilkan Package-JSON

instal express dengan format ```npm i express```

instal nodemon dengan format ```npm i -D nodemon``` agar dapat restart application otomatis selama proses development

tambahkan sebuah Script pada PackJSON
  ```json
      "start": "node app.js",
      "dev": "nodemon app.js",
  ```
  
jalankan code ```npm run App.js```

### Basic Syntax expressJS

#### Routes

End point yang diapat kita akses menggunakan URL di website. Didalam routes kita perlu menentukan method API, alamat dan response apa saja yang akan dikeluarkan

![image](https://user-images.githubusercontent.com/66278794/182595670-742bee81-b44f-4fca-8769-1d8e4f1128cb.png)

#### Response

Di dalam route kita dapat mengirim response menggunakan parameter dari route express.js yaitu **“res.Send()”** untuk mengirim plain text ketika kita mengakses route tersebut.
Documentation : http://expressjs.com/en/api.html#res

#### Status Code

Dalam pengaplikasian back end application, kita sangat perlu memberikan status code sebagai informasi apakah route yang kita akses berjalan sebagaimana mestinya dan tidak terjadi error.

![image](https://user-images.githubusercontent.com/66278794/182595699-cfeea9b0-ef09-4408-a6a0-619a97668258.png)

#### Query

Query merupakan parameter yang digunakan untuk membantu menentukan tindakan yang lebih spesifik daripada hanya sekedar router biasa. Biasanya query ditaruh di akhir route dengan memberikan informasi diawali dengan “?” kemudian tedapat key dan data yang dapat ditindak lanjuti. Ex : **“?q=hello&age=23”**

#### Nested route

digunakan ketika terdapat banyak route yang memiliki nama yang sama atau ingin membuat route yang lebih mendalam

![image](https://user-images.githubusercontent.com/66278794/182595740-c48a7d77-f883-4291-a3a8-4caf875a434e.png)

### Express Middleware

- Middleware function adalah sebuah fungsi yang memiliki akses ke object **request (req)**, object **response (res)**, dan sebuah fungsi **next** didalam request-response cycle.
- Fungsi next biasanya di berikan nama variable next.

![image](https://user-images.githubusercontent.com/66278794/182595769-4c445127-9be0-4276-ab46-7ae4e23051ac.png)

```js
const express = require("express");

const port = 3000;

const app = express();

app.use(express.json());

const hewan = [
  { id: 1, nama: "Snowy", spesies: "kucing" },
  { id: 2, nama: "Blacki", spesies: "anjing" },
  { id: 3, nama: "Molly", spesies: "kucing" },
  { id: 4, nama: "Milo", spesies: "kelinci" },
  { id: 5, nama: "Rere", spesies: "kucing" },
];

//logger middleware
const logger = (req, res, next) => {
  console.log("this is logger");
  next();
};

//middleware for invalid species
const notValidSpecies = (req, res) => {
  res.status(404).send({
    error: "Species not valid",
  });
};

app.get("/", (req, res) => {
  res.send("Home");
});

//get all hewan
app.get("/hewan", logger, (req, res, next) => {
  try {
    res.send({
      message: "success get data pet",
      hewan: hewan,
    });
    next();
  } catch (error) {
    res.status(500).send(error);
  }
});

//get hewan by id
app.get(
  "/hewan/:id",
  logger,
  (req, res, next) => {
    try {
      const filteredData = hewan.find((u) => u.id === Number(req.params.id));

      if (filteredData) {
        res.status(200).send({
          message: "success get data pet by id",
          hewanFilter: [filteredData],
        });
      } else {
        next();
      }
    } catch (error) {
      res.status(500).send(error);
    }
  },
  (req, res, next) => {
    res.status(404).send({
      message: "data not found",
    });
  }
);

//post hewan
app.post(
  "/hewan",
  logger,
  (req, res, next) => {
    try {
      const body = req.body;

      const newData = {
        id: hewan.length + 1,
        nama: body["nama"],
        spesies: body["spesies"],
      };

      if (newData.spesies === "kucing" || newData.spesies === "anjing" || newData.spesies === "kelinci") {
        hewan.push(newData);
        res.status(201).send({
          message: "success adding data pet",
          hewan: hewan,
        });
      } else next();
    } catch (error) {
      res.status(500).send(error);
    }
  },
  notValidSpecies
);

//put or update hewan by id
app.put(
  "/hewan/:id",
  logger,
  (req, res, next) => {
    try {
      const body = req.body;
      const index = hewan.findIndex((u) => u.id === +req.params.id);
      const updatedData = { id: +req.params.id, ...body };

      if (updatedData.spesies === "kucing" || updatedData.spesies === "anjing" || updatedData.spesies === "kucing") {
        hewan[index] = updatedData;
        res.status(201).send({
          message: "success updated",
          hewan: hewan,
        });
      } else next();
    } catch (error) {
      res.status(500).send(error);
    }
  },
  notValidSpecies
);

//delete hewan by id
app.delete("/hewan/:id", logger, (req, res) => {
  try {
    const index = hewan.findIndex((u) => u.id === +req.params.id);
    const deletedData = hewan.splice(index, 1);

    res.status(200).send({
      message: "success delete",
      deletedHewan: deletedData,
    });
  } catch (error) {
    res.status(500).send(error);
  }
});

app.listen(port, () => {
  console.log(`listening at http://localhost:${port}`);
});
```

***

## 4. MySQL

Database adalah kumpulan informasi yang disimpan didalam komputer secara sistematik dan saling berelasi.

Database sekumpulan tabel yang berisikan informasi untuk diolah yang kemudian data tersebut bisa digunakan di dalam sebuah sistem.

Database Management System (DBMS), software yang dapat digunakan oleh user untuk berkomunikasi dengan data yang ada dalam media penyimpanan.

Tipe utama pada Database management System antara lain, Hierarchical, Network, Relational, Non Relational, and Object Oriented.

```js
Istilah pada Database

Table : kumpulan value yang dibangun oleh baris dan kolom, yang didalamnya berisikan atribut dari sebuah data.

Field : kolom dari sebuah tabel dimana masing-masing field memiliki tipe data masing-masing.

Record : merupakan kumpulan nilai yang saling terkait. Record merupakan isi dari sebuah tabel.
```

SQL atau Structured Query Language merupakan suatu bahasa (Language) yang digunakan untuk mengakses database.

SQL adalah Bahasa Query yang digunakan untuk melakukan interaksi di RDMS (Relational Database Management System).

MySQL adalah Open source RDBMS berbasis SQL. Digunakan untuk mengoptimalkan aplikasi web dan dapat di jalankan dari berbagai platform. MySQL dapat berjalan stabil pada berbagai sistem operasi seperti Windows, Linux, MacOS dll.

Instalasi MySQL
link : https://dev.mysql.com/downloads/installer

### SQL Command

```
SHOW DATABASES
```

menunjukkan seluruh list database di mysql kita

```
CREATE DATABASE nama_db;
```

membuat database baru

```
USE nama_db;
```

menggunakan database yang sudah ada

```
DROP DATABASES nama_db;
```

menghapus / menghilangkan database yang dipilih dari MySQL

```
SHOW TABLES;
```

melihat semua ini table di database

### Membuat Table Pada Databases

- Membuat table baru di database tersebut dengan nama “books”. Sintaks yang dibuat menggunakan **CREATE TABLE [name]** memberikan definisi tiap kolom di table tersebut.



```
DROP TABLES nama_db;
```

menghapus table yang diinginkan jika ingin dihapus.

## DDL (Data Definition Language)

kumpulan perintah SQL yang digunakan untuk membuat, mengubah dan menghapus struktur dan definisi metadata dari objek-objek Database.

### ALTER

- Ketika ingin menambah atau menghilangkap kolom di table yang dipilih, kita bisa menggunakan **ALTER** dan menggunakan **ADD** untuk menambah kolom atau **DROP COLUMN** untuk menghapus kolom seperti contoh diatas.



### INSERT INTO

perintah yang di gunakan untuk input data ke tabel



### INSERT INTO (multiple)



### SELECT

Digunakan untuk melakukan query melihat isi data di table yang dipilih



### SELECT ALIAS (AS)

**AS** untuk menggunakan mengubah nama kolom agar output kolomnya sesuai dengan yang kita inginkan



### WHERE

**WHERE** digunakan untuk mencari data dengan kondisi tertentu dengan command WHERE [column_name] = condition.



### AND, OR, NOT

**AND** untuk mencari query dengan kondisi lebih dari satu
**OR** untuk mencari query dengan kondisi salah satu.
**NOT** untuk mencari query yang tidak ada dalam kondisi yang di definisikan.
Contoh mencari row dengan kondisi id = 1 atau author1 = ‘eddy’. Maka kita akan muncul 2 row dengan salah satu kondisi yang di declare.



### ORDER BY

Untuk melakukan ordering menggunakan **ORDER BY** dengan menggunakan 2 kondisi yaitu ASC dan DESC. Struktur commandnya adalah ORDER BY [column_name] ASC / DESC.

### LIMIT

untuk membatasi berapa query yang akan dimunculkan dengan urutan dari atas.

### UPDATE

UPDATE digunakan untuk melakukan perbaruan data di table.



### DELETE

Digunakan untuk melakukan penghapusan data
**WARNING !!** ketika ingin melakukan delete jangan lupa menggunakan WHERE agar semua data tidak terhapus



## Relasi di SQL

### 1. One to Many

- Paling Sering Digunakan
- Satu baris dalam tabel dapat memiliki beberapa baris di table relasinya



### 2. Many to Many

- Digunakan ketika kedua tabel yang berelasi dapat memiliki beberapa baris di tabel relasinya.



### 3. One to One

- Sangat jarang digunakan
- Diimplementasikan dengan cara yang sama seperti One to Many tetapi dengan kondisi tambahan (foreign key merupakan primary key)



## Database Normalization

Teknik analisis data yang mengorganisasikan atribut-atribut data dengan cara mengelompokkan sehingga terbentuk entitas yang non-redundant, stabil, dan fleksible.

### Tujuan Database Normalization

- Menghilangkan redundan data pada database.
- Memudahkan juka ada perubahan struktur table database.
- Memperkecil pengaruh jika ada perubahan dari struktur table database.

## Bentuk Database Normalization

### 1. First Normal Form (1NF)

1. Menghilangkan multiple value pada sebuah kolom table database
2. Sebuah table memenuhi kaidah 1NF jika :
   -- Setiap kolom bernilai tunggal (single value)
   -- Setiap kolom memiliki nama yang unik
3. Urutan penyimpanan data tidak menjadi masalah



### 2. Second Normal Form (2NF)

1. Harus sudah dalam bentuk 1NF untuk mendapatkan 2NF
2. Menghapus beberapa subset data yang ada pada tabel dan menempatkan mereka pada tabel terpisah.



### 3. Third Normal Form (3NF)

Menghilangkan seluruh atribut atau field yang tidak berhubungan dengan primary key. Dengan demikian tidak ada ketergantungan transitif pada setiap kandidat key.

## Key di SQL

### 1. Super Key

- Kumpulan dari satu atau lebih dari satu key yang dapat digunakan untuk mengidentifikasi record secara unik dalam sebuah tabel.
- Super Key adalah superset dari Candidate Key.

### 2. Candidate Key

- Kumpulan satu atau lebih fields/columns yang dapat mengidentifikasi record secara unik dalam tabel.
- Bisa jadi ada beberapa Candidate Keys di dalam satu tabel
- Setiap Candidate Key bisa digunakan sebagai Primary Key.
  Candidate Key adalah super key yang tidak mempunyai value yang berulang

### 3. Primary Key

- Kumpulan satu atau lebih fields/columns dari sebuah tabel yang secara unik mengidentifikasi sebuah record dalam tabel database.
- Valuenya tidak boleh berupa null ataupun duplicate value.
  Hanya boleh salah satu Candidate Key yang bisa menjadi Primary Key.

### 4. Alternate Key

- Key yang bisa digunakan menjadi primary key.
- Pada dasarnya, Key ini merupakan candidate key yang tidak dijadikan primary key.

### 5. Unique Key

- Kumpulan dari satu atau lebih fields/columns di sebuah table database yang secara unik mengidentifikasi sebuah record dalam table database tersebut.
- Hampir sama dengan Primary key, namun value dari Unique Key bisa berupa satu buah null value di dalam sebuah table database, dan Unique Key tidak bisa memiliki duplicate values

### 6. Foreign Key

Field di sebuah table database yang menjadi Primary Key di table database lain.
Value dari Foreign key bisa menerima multiple null dan duplicate values.

## Join Multiple Table

### 1. Inner Join

- Semua baris akan diambil dari kedua table yang akan di JOIN, selama columns cocok dengan kondisi yang sudah di tentukan.
- Memungkinkan baris dari salah satu tabel muncul di hasil jika dan hanya jika kedua tabel memenuhi kondisi yang ditentukan dalam klausa ON.

### 2. Left Join

- Semua records dari table di sisi kiri JOIN statement akan di pilih.
- Jika record yang di pilih dari table kiri tidak memiliki record yang cocok pada table JOIN yang kanan, maka record tersebut masih dipilih, dan kolom pada table yang kanan akan bernilai NULL.

### 3. Right Join

semua records dari table di sisi kiri JOIN statement akan di pilih, bahkan jika table di sebelah kiri tidak memiliki record yang cocok.

## Aggregate Functions

Mengambil satu nilai setelah melakukan perhitungan pada sekumpulan nilai

### Tipe Aggregate Funtions

**1. MAX** : fungsi mengembalikan nilai terbesar dari kolom yang dipilih.
**2. MIN** : fungsi mengembalikan nilai terkecil dari kolom yang dipilih.
**3. SUM** : fungsi mengembalikan jumlah total kolom numerik.
**4. COUNT** : fungsi mengembalikan jumlah baris yang cocok dengan kriteria yang ditentukan.
**5. AVG** : fungsi mengembalikan nilai rata-rata kolom numerik

## UNION

- Digunakan untuk menggabungkan kumpulan hasil dari dua atau lebih pernyataan SELECT.
- Setiap pernyataan SELECT dalam UNION harus memiliki jumlah kolom yang sama
- Kolom juga harus memiliki tipe data yang serupa
- Kolom dalam setiap pernyataan SELECT juga harus dalam urutan yang sama

## GROP BY

- Mengelompokkan baris yang memiliki nilai yang sama ke dalam baris ringkasan
- Sering digunakan dengan fungsi agregat untuk mengelompokkan kumpulan hasil dengan satu atau lebih kolom.

## HAVING

HAVING ditambahkan ke SQL karena kata kunci WHERE tidak dapat digunakan dengan aggregate functions.

```sql
SHOW DATABASES;

CREATE DATABASE bookstore;

USE bookstore;

SHOW TABLES;

CREATE TABLE `books`(
    `id` INT NOT NULL AUTO_INCREMENT PRIMARY KEY,
    `author1` VARCHAR(100) NOT NULL,
    `author2` VARCHAR(100),
    `author3` VARCHAR(100),
    `title` VARCHAR(100),
    `description` TEXT,
    `place_sell` CHAR(3),
    `stock` INT default 0,
    `creation_date` DATETIME DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP
);

ALTER TABLE books
    ADD `price` INT DEFAULT 0,
    ADD `status` ENUM('available', 'out of stock', 'limited'),
    DROP `place_sell`;

INSERT INTO books VALUES
    (NULL,'Mirza', 'Bakti', 'Sukaryana', 'Belajar Algoritma', 'Belajar algoritma dasar disertai contoh nyata',200, default, 199000, 'available'),
    (NULL,'Eichiiro', 'Oda', 'Sensei', 'One Piece', 'Kisah bajak laut mencari harta karun berharga',99, default, 249000, 'limited'),
    (NULL,'Duta', 'Sheila', 'On Seven', 'Kisah Klasik', 'Kumpulan syair-syair hits',4, default, 229000, 'out of stock');

SELECT * FROM books;

SELECT id AS ID, author1 AS A1, author2 AS A2, author3 AS A3 from books;

SELECT * FROM books WHERE id = 3;

SELECT * FROM books WHERE id = 1 AND price >= 100000;

SELECT * FROM books WHERE stock > 100 OR price <= 200000;

SELECT * FROM books WHERE NOT status = 'out of stock';

SELECT * FROM books ORDER BY id;

SELECT * FROM books LIMIT 2;

UPDATE books SET author1 = 'JK Rowling', price = '125000' WHERE id = 1;

DELETE FROM books where id = 2;
```

```sql
CREATE DATABASE skilvulbookstore;

USE skilvulbookstore;

CREATE TABLE penerbit(
    id INT(10) NOT NULL AUTO_INCREMENT PRIMARY KEY,
    nama VARCHAR(50) NULL,
    kota VARCHAR(50) NULL
);

CREATE TABLE penulis(
    id INT(10) NOT NULL AUTO_INCREMENT PRIMARY KEY,
    nama VARCHAR(50) NULL,
    kota VARCHAR(50) NULL
);

CREATE TABLE buku(
    id INT(10) NOT NULL AUTO_INCREMENT PRIMARY KEY,
    ISBN VARCHAR(50) NULL,
    judul VARCHAR(50) NULL,
    penulis INT(10) NULL,
    penerbit INT(10) NULL,
    harga INT(10) NULL,
    stock INT(10) NULL,
    CONSTRAINT fk_penulis FOREIGN KEY (penulis) REFERENCES penulis(id) ON UPDATE CASCADE ON DELETE CASCADE,
    CONSTRAINT fk_penerbit FOREIGN KEY (penerbit) REFERENCES penerbit(id) ON UPDATE CASCADE ON DELETE CASCADE
);

INSERT INTO penerbit VALUES
    (NULL, 'Elex Media', 'Jakarta'),
    (NULL, 'Bintang Media', 'Jakarta'),
    (NULL, 'Mizan', 'Yogyakarta'),
    (NULL, 'Erlangga', 'Jakarta'),
    (NULL, 'Gramedia', 'Bandung'),
    (NULL, 'Bintang Pustaka', 'Bandung');

INSERT INTO penulis VALUES
    (NULL, 'Tere Liye', 'Jakarta'),
    (NULL, 'Dewi Lestari', 'Bandung'),
    (NULL, 'Haidar Musyafa', 'Jakarta'),
    (NULL, 'Andrea Hirata', 'Bali'),
    (NULL, 'Eka Kurniawan', 'Yogyakarta');

INSERT INTO buku VALUES
    (NULL, '978-7-827-2', 'Laskar Pelangi', 1 , 2 , 75000, 200),
    (NULL, '978-2-860-3', 'Negeri Para Berdebah', 1 , 1 , 60000, 100),
    (NULL, '978-2-852-4', 'Sang guru', 4 , 3 , 150000, 8),
    (NULL, '978-3-802-9', 'Anatomi Rasa', 3 , 5 , 360000, 90),
    (NULL, '978-5-792-6', 'Drunken Marmut', 1 , 4 , 90000, 160);

SELECT *
FROM buku
INNER JOIN penerbit
ON buku.penerbit = penerbit.id;

SELECT *
FROM buku
LEFT JOIN penerbit
ON buku.penerbit = penerbit.id;

SELECT *
FROM buku
RIGHT JOIN penerbit
ON buku.penerbit = penerbit.id;

SELECT id, ISBN, judul, penulis, penerbit, MAX(harga)
AS harga, stock
FROM buku
WHERE stock < 10;

SELECT id, ISBN, judul, penulis, penerbit, MIN(harga)
AS harga, stock
FROM buku;

SELECT COUNT(*)
AS Harga_Dibawah_100
FROM buku
WHERE harga < 100000;
```

***

## 5. Design Database

![image](https://user-images.githubusercontent.com/66278794/182508349-1e34d77d-7339-479a-ad29-005f95ce5102.png)

```sql
CREATE DATABASE skilvul_music_streaming;

USE skilvul_music_streaming;

CREATE TABLE user(
    user_id INT NOT NULL AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(50) NULL,
    email VARCHAR(50) NULL,
    password VARCHAR(50) NULL
    );

CREATE TABLE singer(
    singer_id INT NOT NULL AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(50) NULL
    );

CREATE TABLE album(
    album_id INT NOT NULL AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(50) NULL,
    singer_id INT NOT NULL,
    CONSTRAINT fk_singer_id FOREIGN KEY (singer_id) REFERENCES singer(singer_id) ON UPDATE CASCADE ON DELETE CASCADE
    );

CREATE TABLE playlist(
    playlist_id INT NOT NULL AUTO_INCREMENT PRIMARY KEY,
    user_id INT NOT NULL,
    tracks VARCHAR(50) NULL,
    CONSTRAINT fk_user_id FOREIGN KEY (user_id) REFERENCES user(user_id) ON UPDATE CASCADE ON DELETE CASCADE
    );

CREATE TABLE tracks(
    track_id INT NOT NULL AUTO_INCREMENT PRIMARY KEY,
    title VARCHAR(50) NULL,
    singer_id INT NOT NULL,
    album_id INT NOT NULL,
    CONSTRAINT fk_singer_id_tracks FOREIGN KEY (singer_id) REFERENCES singer(singer_id) ON UPDATE CASCADE ON DELETE CASCADE,
    CONSTRAINT fk_album_id_tracks FOREIGN KEY (album_id) REFERENCES album(album_id) ON UPDATE CASCADE ON DELETE CASCADE
    );

CREATE TABLE track_playlist(
    track_id INT NOT NULL,
    playlist_id INT NOT NULL,
    CONSTRAINT fk_track_id_con FOREIGN KEY (track_id) REFERENCES tracks(track_id) ON UPDATE CASCADE ON DELETE CASCADE,
    CONSTRAINT fk_playlist_id_con FOREIGN KEY (playlist_id) REFERENCES playlist(playlist_id) ON UPDATE CASCADE ON DELETE CASCADE
    );
```

***

> **Sharing is Learning** ❤️‍🔥
