> 🦖 **Impact Byte x Skilvul batch Joyful Jasper** 🐲
# Writing-Assignment-Week-07-Mirza Bakti Sukaryana 😆 🚀

| Table Of ‘Contents’ |
| ---------------------- |
| <ol> |
|  <li>Authentication & Authorization</li> |
|  <li>Sequelize</li> |
|  <li>MongoDB</li> |
|  <li>Mongoose</li> |
|  <li>Docker</li> |
| </ol> |

***

## 1. Authentication & Authorization

### Authentication

Proses dimana seorang user (melalui berbagai macam akses fisik berupa komputer dll) mendapatkan hak akses kepada suatu entity.

Seorang user melakukan login kedalam suatu infrastruktur jaringan dan sistem mengenali user ID dan menerimanya untuk kemudian diberikan akses, sesuai dengan authorisasi yang dia terima.

Responses to authentication prompts can be categorized into:

Knowledge-Based: “Something You Know”

Possession-Based: “Something You Have”

Inherence-Based: “Something You Are”

![image](https://user-images.githubusercontent.com/66278794/183959910-a77d8121-733d-45b9-af07-03a5053320d9.png)

#### Jenis-Jenis Autentikasi

1. Single Factor Authentication

Jenis autentikasi yang meminta pengguna untuk memasukkan ID pengguna. Kemudian proses autentikasi pun akan berjalan dengan meminta pengguna untuk memasukkan password yang tepat dan sesuai dengan ID pengguna.

![image](https://user-images.githubusercontent.com/66278794/183957660-bd5fb687-0e3b-473c-bad9-8ae646e444e0.png)

2. Multi Factor Authentication

jenis autentikasi yang mewajibkan pengguna untuk memverifikasi tiga jenis identitas, misalnya ID pengguna, sidik jari/wajah, dan beberapa pertanyaan yang berhubungan dengan pengguna.

![image](https://user-images.githubusercontent.com/66278794/183957795-344272f7-d846-41c8-bb28-b3e487bf03e7.png)

### Authorization

Proses penentuan apakah user tersebut diizinkan / ditolak untuk melakukan satu atau beberapa action akses terhadap resources tertentu dalam sistem.

User login terhadap sistem dengan menggunakan user-ID dan password, kemudian sistem mengenalinya dan user mendapatkan akses atau ditolak terhadap suatu resource sistem tertentu.

![image](https://user-images.githubusercontent.com/66278794/183943966-539183d4-9260-48bf-9f82-85f9b1395f11.png)

### Encryption

Proses teknis yang mengonversikan informasi menjadi kode rahasia, sehingga mengaburkan data yang Anda kirim, terima, atau simpan.

##### Jenis-jenis Enkripsi

1. Symmetric encryption Enkripsi yang terkait atau identik digunakan baik untuk proses enkripsi maupun dekripsi. Dalam beberapa kalangan, kunci yang dibagikan disebut sebagai "rahasia bersama", karena pengirim/sistem yang memantau enkripsi harus membagikan Kunci ini kepada siapa pun yang berwenang mendekripsi pesan.

2. Asymmetric encryption Disebut juga sebagai enkripsi kunci publik, berbagai kunci digunakan untuk proses enkripsi dan dekripsi. Satu kunci dibagikan secara publik dan dapat digunakan oleh siapa pun (maka disebut "enkripsi kunci publik"), sementara yang satu lagi adalah kunci pribadi. Hal ini membuat sistem kunci asimetris menjadi lebih aman daripada algoritme kunci simetris, karena peretas atau penjahat cyber tidak dapat menyalin kunci saat dikirimkan.

![image](https://user-images.githubusercontent.com/66278794/183958128-a571c791-eed8-480e-b854-5bcb91993ab4.png)

### JSON Web Token 

Sebuah JSON Object yang didefinisikan dalam RFC 7519 sebagai cara aman untuk mewakili sekumpulan informasi antara dua pihak.

Token terdiri dari Header, Content, dan Signature.

![image](https://user-images.githubusercontent.com/66278794/183947913-ab92d8b3-40cb-4561-88a0-5bb7b03b3c28.png)

![image](https://user-images.githubusercontent.com/66278794/183949804-794e8f78-6478-463d-a6cf-01fa835fceab.png)

### Session VS Cookie VS LocalStorage

![image](https://user-images.githubusercontent.com/66278794/183951907-7718142e-bb0d-4c6f-848d-12180a349fd3.png)\

### Session Based Authentication

```npm init -y```

```npm install express cookie-parser express-session```

```npm install --save-dev nodemon```

```html
// views/index.html

<html>

<head>
  <link rel="stylesheet" href="views/app.css">
</head>

<body>
  <form action="/user" method="post">
    <h2>Login</h2>
    <div class="input-field">
      <input type="text" name="username" id="username" placeholder="Enter Username">
    </div>
    <div class="input-field">
      <input type="password" name="password" id="password" placeholder="Enter Password">
    </div>
    <input type="submit" value="LogIn">
  </form>
</body>

</html>
```

```css
// views/app.css

body {
  display: flex;
  justify-content: center;
}

form {
  display: flex;
  flex-direction: column;
}

.input-field {
  position: relative;
  margin-top: 2rem;
}

.input-field input {
  padding: 0.8rem;
}

form .input-field:first-child {
  margin-bottom: 1.5rem;
}

form input[type="submit"] {
  background: linear-gradient(to left, #4776E6, #8e54e9);
  color: white;
  border-radius: 4px;
  margin-top: 2rem;
  padding: 0.4rem;
}
```

```js
// app.js

const express = require("express");
const cookieParser = require("cookie-parser");
const sessions = require("express-session");

const app = express();
const PORT = 3000;

app.use(
  sessions({
    secret: "thisismysecrctekeyfhrgfgrfrty84fwir767",
    saveUninitialized: true,
    resave: false,
    cookie: {
      maxAge: 60 * 1000,
    },
  })
);
app.use(express.json());
app.use(express.urlencoded({ extended: true }));
app.use(express.static(__dirname));
app.use(cookieParser());

const myusername = "user1";
const mypassword = "mypassword";

var session;
app.get("/", (req, res) => {
  session = req.session;
  if (session.userid) {
    res.send("Welcome User <a href='/logout'>click to logout</a>");
  } else res.sendFile("views/index.html", { root: __dirname });
});

app.post("/user", (req, res) => {
  if (req.body.username == myusername && req.body.password == mypassword) {
    session = req.session;
    session.userid = req.body.username;
    console.log(req.session);
    res.send(`Hey there, welcome <a href=\'/logout'>click to logout</a>`);
  } else {
    res.send("Invalid username or password");
  }
});

app.get("/logout", (req, res) => {
  req.session.destroy();
  res.redirect("/");
});

app.listen(PORT, () => console.log(`Server Running at port ${PORT}`));
```

![image](https://user-images.githubusercontent.com/66278794/183933867-cf7f500d-7b4a-4d2b-b52e-5d262e55ad14.png)

![image](https://user-images.githubusercontent.com/66278794/183934060-7a418981-e5a7-454f-86f9-b7fcb276786a.png)

![image](https://user-images.githubusercontent.com/66278794/183934243-d436f5bc-017b-4726-8e39-7846823d7f7e.png)

### Token Based Authentication

```npm init -y```

```npm install express body-parser jsonwebtoken```

```npm install --save-dev nodemon```

```js
// auth.js

const express = require("express");
const app = express();
const jwt = require("jsonwebtoken");
const bodyParser = require("body-parser");

const port = 3000;

app.use(bodyParser.json());

const authenticateJWT = (req, res, next) => {
  const authHeader = req.headers.authorization;

  if (authHeader) {
    const token = authHeader.split(" ")[1];

    jwt.verify(token, accessTokenSecret, (err, user) => {
      if (err) {
        return res.sendStatus(403);
      }

      req.user = user;
      next();
    });
  } else {
    res.sendStatus(401);
  }
};

const users = [
  {
    username: "terra",
    password: "password123admin",
    role: "admin",
  },
  {
    username: "dave",
    password: "password123member",
    role: "member",
  },
];

app.use(bodyParser.json());
const accessTokenSecret = "youraccesstokensecret";

app.post("/login", (req, res) => {
  const { username, password } = req.body;
  const user = users.find((user) => {
    return user.username === username && user.password === password;
  });

  if (user) {
    const token = jwt.sign(
      { username: user.username, role: user.role },
      accessTokenSecret
    );
    res.json({
      accessToken: token,
    });
  } else {
    res.send("Username or password incorrect");
  }
});

app.get("/ping", (req, res) => {
  res.send("server jalan");
});

app.listen(port, () => {
  console.log(`Running in port ${port}`);
});
```

```js
const express = require("express");
const bodyParser = require("body-parser");
const jwt = require("jsonwebtoken");

const app = express();

const accessTokenSecret = "youraccesstokensecret";

app.use(bodyParser.json());

const authenticateJWT = (req, res, next) => {
  const authHeader = req.headers.authorization;

  if (authHeader) {
    const token = authHeader.split(" ")[1];

    jwt.verify(token, accessTokenSecret, (err, user) => {
      if (err) {
        return res.sendStatus(403);
      }

      req.user = user;
      next();
    });
  } else {
    res.sendStatus(401);
  }
};

const books = [
  {
    author: "Robert Martin",
    country: "USA",
    language: "English",
    pages: 209,
    title: "Clean Code",
    year: 2008,
  },
  {
    author: "Dave Thomas & Andy Hunt",
    country: "USA",
    language: "English",
    pages: 784,
    title: "The Pragmatic Programmer",
    year: 1999,
  },
  {
    author: "Kathy Sierra, Bert Bates",
    country: "USA",
    language: "English",
    pages: 928,
    title: "Head First Java",
    year: 2003,
  },
];

app.get("/books", authenticateJWT, (req, res) => {
  res.json(books);
});

app.post("/books", authenticateJWT, (req, res) => {
  if (req.user.role === "admin") {
    const newBook = {
      author: req.body.author,
      country: req.body.country,
      language: req.body.language,
      pages: req.body.pages,
      title: req.body.title,
      year: req.body.year,
    };

    books.push(newBook);
    res.send("Book added successfully");
  } else {
    res.send("You are not an admin");
  }
});

app.listen(4000, () => {
  console.log("Books service started on port 4000");
});
```

***

## 2. Sequelize

Sequelize adalah ORM (Object Relational Mapping) Node JS yang berbasis promise.

Sequelize mendukung sebagian besar relational Database seperti MySQL, PostgresQL, MariaDB, SQLite dan Miscrosoft SQL Server.

Dengan fitur fitur di Sequelize, kita bisa mengelola dan mengatur data di database kita dengan cepat, dan efisien.

ORM adalah suatu metode/teknik pemrograman yang digunakan untuk mengkonversi data dari lingkungan bahasa pemrograman berorientasi objek (OOP) dengan lingkungan database relational.  

![image](https://user-images.githubusercontent.com/66278794/183961343-8cfe10fd-ae15-403b-9545-6d7b6c0f9144.png)

### Penggunaan Sequelize

#### Instalasi Sequelize

```
npm init -y // utk create project pertama
```

```
npm install express mysql2 sequelize dotenv cors
```

Dan terakhir kita instal nodemon utk auto-reload servernya

```
npm install --save-dave nodemon
```

### Seting di Sequelize

**1. Setting Package.json**

```json
{
  "name": "32-sequelize",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1",
    "dev": "nodemon index.js" // setting nodemon
  },
  "keywords": [],
  "author": "",
  "license": "ISC",
  "dependencies": {
    "cors": "^2.8.5",
    "dotenv": "^16.0.1",
    "express": "^4.18.1",
    "mysql2": "^2.3.3",
    "sequelize": "^6.21.3"
  },
  "devDependencies": {
    "nodemon": "^2.0.19"
  }
}
```

Hasil dari package.json yang di-create

**2. Setting Database**

- Database yang di pakai adalah MySQL - pastikan user dan password login ke MySQL benar.

- buat folder bernama **Config** dan save file dengan **dbConnection.js**

```js
require("dotenv").config();
const { Sequelize } = require("sequelize");

const host = process.env.HOST || "localhost";

const sequelize = new Sequelize({
  database: process.env.DATABASE_NAME || "sekolah",
  username: process.env.DATABASE_USERNAME || "admin123",
  password: process.env.DATABASE_PASSWORD || "admin123",
  dialect: "mysql",
  host,
});

module.exports = sequelize;

```

- create folder models yg berisi file UserModel.js untuk sinkronisasi database pada user

```js
const { Sequelize, DataTypes } = require("sequelize");
const sequelize = require("../config/dbConnection");

const UserModel = sequelize.define(
  "user",
  {
    name: {
      type: DataTypes.STRING,
    },
    email: DataTypes.STRING,
    birth_date: DataTypes.DATE,

  },
  {
    timestamps: true,
    createdAt: false,
    updatedAt: false,
  }
);

module.exports = UserModel;

```

**3. Eksekusi Program**
buat file index.js untuk mengeksekusi konesi databasenya

```js
const express = require("express");
const app = express();

const sequelize = require("./config/dbConnection");
const UserModel = require("./models/UserModel");
const router = require("./routes");

const PORT = process.env.PORT || 8000;

app.use(express.json());

async function testConnection() {
  try {
    await sequelize.authenticate();
    console.log("sukses");

    await UserModel.sync({ alter: true });
  } catch (error) {
    console.log("error", error);
  }
}

testConnection();

app.use(router);

app.listen(PORT, () => {
  console.log("tes koneksi port", PORT);
});

```

**4. Buat Controler**
buat folder controller lalu buat file UserController.js untuk membedakan antara user dan modelnya.

```js
const UserModel = require("../models/UserModel");

module.exports = {
  getAllUser: async (req, res) => {
    const users = await UserModel.findAll();

    res.json({
      message: "sukses ambil data",
      data: users,
    });
  },
};
```

**5. Buat Rute**
Buat folder Route yang isinya index.js, untuk menampung rute-rute aplikasi yang ingin di buat

```js
const express = require("express");
const router = express.Router();

router.get("/", (req, res) => {
  res.json({
    message: "sekolah app",
  });
});

// route untuk user
router.use("/user", userRouter);

module.exports = router;
```

***

## 3. MongoDB

MongoDB adalah salah satu database open source NoSQL yang cukup populer digunakan.

MongoDB sering dipakai untuk aplikasi berbasis Cloud, Big Data maupun Grid COmputing.

Jika SQL menyimpan data menggunakan relasi tabel, MongoDB menggunakan dokumen dengan format JSON.

NoSQL adalah Not Only SQL. Artinya kita bisa mengolah database dengan fleksibel dan tidak membutuhkan Query. Akhirnya kita memiliki skalabilitas yang tinggi sesuai dengan perkembangan data kita.

### Kelebihan dan Kekurangan MongoDB sebagai salah satu NoSQL

#### Kelebihan

Sistem tidak membutuhkan Tabel

Tidak perlu menggunakan Tabel yang terstruktur

By Default sudah menggunakan JSON(JavaScript Object Notation), sehingga memudahkan integrasi dengan JavaScript

Performa lebih cepat dengan kemampuan menampung banyak data yang bervariasi

#### Kekurangan

Tidak mendukung transaksi

Masalah konsistensi data

Menggunakan banyak memory

Hanya bisa menampung maksimal 16MB disetiap document

### Instalasi MongoDB

https://docs.mongodb.com/manual/administration/install-community/

### MongoDB GUI Tools

untuk menggunakan MongoDB, kita bisa menggunakan MongoDB Compass UI untuk mengexplore DB yang ingin kita buat.

https://www.mongodb.com/products/compass

### MongoDB Atlas

Selain menggunakan Mongo compass, kita juga bisa menggunakan management tool / admin UI versi cloudnya. kita bisa menggunakan MongoDB atlas.

https://www.mongodb.com/cloud/atlas

***

## 4. Mongoose

Mongoose adalah library yang bisa dibilang sebagai Object Modelling MongoDB untuk NodeJS.

Mongoose bisa digunakan untuk mengelola hubungan antara data, menyediakan validasi.

Dan juga digunakan untuk menerjemahkan antara objek dalam kode dan representasi Objek tersebut di MongoDB.

https://mongoosejs.com/docs/index.html

### Connect NodeJS and MongoDB

- Install dotenv untuk menampung variabel environment database. Dan juga install MongoDB

```
npm install dotenv
```

```
npm install mongodb
```

- Buat satu file .env untuk menyimpan variabel database

```sql
DATABASE_MONGODBATLAS = mongodb+srv://skilvul:skilvul123@cluster0.t7ybq.mongodb.net/?retryWrites=true&w=majority
```

- Membuat file untuk membuat koneksi, dan interaksi dengan database langsung.

```js
require("dotenv").config();

const mongoose = require("mongoose");

const url = process.env.DATABASE_MONGODBATLAS || "localhost";

const dbConnection = mongoose.connect(url);

module.exports = dbConnection;
```

### Penggunaan Mongoose

**1 Instalasi**
Pastikan NodeJS dan MongoDB juga sudah terinstall.

```
npm install mongoose
```

**2 Buat Koneksi**

- Buat file koneksinya dengan folder **config** yang berisi file **dbConnection.js**

```js
require("dotenv").config();

const mongoose = require("mongoose");

const url = process.env.DATABASE_MONGODBATLAS || "localhost";

const dbConnection = mongoose.connect(url);

module.exports = dbConnection;
```

- Membuat koneksi dengan menggunakan MongoDB database, yang diletakkan di .env

```sql
DATABASE_MONGODBATLAS = mongodb+srv://skilvul:skilvul123@cluster0.t7ybq.mongodb.net/?retryWrites=true&w=majority

```

**3 Definisikan Schema DB**
dari code dibawah ini kita dapat mendefinisikan Skema dan tipe data untuk setiap field yang akan digunakan.

```js
const mongoose = require("mongoose");

// buat schema models

const UserSchema = new mongoose.Schema({
  name: {
    type: String,
    require: true,
  },
  email: {
    type: String,
  },
  telephoneNumber: {
    type: String,
  },
});

const UserModel = mongoose.model("user", UserSchema);

module.exports = UserModel;
```

### Heroku

Heroku adalah Platform cloud berbasis wadah sebagai Layanan (PaaS). Pengembang menggunakan Heroku untuk menyebarkan, mengelola, dan menskalakan aplikasi modern. Platform kami elegan, fleksibel, dan mudah digunakan , menawarkan pengembang jalur paling sederhana untuk membawa aplikasi mereka ke pasar.

#### Cara deploy repo github menggunakan heroku

1. Pastikan kamu sudah memiliki repository Github beserta script-nya.

3. Login terlebih dahulu ke akun Heroku dan Github, Jika belum membuat akun, silahkan buat akunnya terlebih dahulu.

4. Jika sudah login, buat aplikasi baru dengan memilih tombol New dibagian sudut kanan atas.
![image](https://user-images.githubusercontent.com/66278794/183976624-358f3acc-3b2b-4c49-9c62-5485a31ece9e.png)

5. Masukan nama aplikasinya sesuai keinginan kamu, lalu klik Create App.
![image](https://user-images.githubusercontent.com/66278794/183976690-bab88acf-370d-400b-a838-b32d13c3ce23.png)

7. Jika sudah, Pastikan kamu sudah login dengan Github dan pastikan juga kamu sudah mempunyai repository yang ingin dihubungkan dengan Github.
![image](https://user-images.githubusercontent.com/66278794/183976749-05912907-00c9-40d2-b3f0-cfd451e4a47b.png)

8. Cari Github pada Connect to Github, lalu klik.
![image](https://user-images.githubusercontent.com/66278794/183976823-4dc0fcab-9fe5-4eea-8c4c-8e1b307d2b89.png)

9. Klik Authorize Heroku.

![image](https://user-images.githubusercontent.com/66278794/183976870-5b12961a-5d27-4cc7-b899-9b8caea91094.png)

10. Lalu masukan nama repository Github kamu, klik search.
![image](https://user-images.githubusercontent.com/66278794/183976918-e5725cba-bebe-4106-a215-971bb4a9ae3d.png)

11. Jika ada, klik Connect.
![image](https://user-images.githubusercontent.com/66278794/183976962-dcaae48e-0caf-4487-8f14-4198d1e165a7.png)

12. Jika sudah terhubung, ceklis pada bagian Wait for CI to pass before deploy dan klik tombol Enable Automatic Deploy, lanjutkan dengan klik Deploy Branch.
![image](https://user-images.githubusercontent.com/66278794/183976994-2ebd5da7-109e-40b7-a0b0-efad38f63403.png)

13. Tunggu prosesnya, jika selesai, klik view untuk memastikan telah terhubung.
![image](https://user-images.githubusercontent.com/66278794/183977039-6adbaff2-d96e-4d9f-9f84-46681f4bfa42.png)

15. Selesai.

17. Tambahan. Jika saat dilihat, tampilannya seperti gambar di bawah ini, maka pada script yang terdapat pada repository kamu terdapat kesalahan koding, artinya kamu harus memperbaikinya.
![image](https://user-images.githubusercontent.com/66278794/183977123-dcc55152-1036-4066-8c73-8986a26e6e37.png)

***

## 5. Docker

Docker adalah software yang menjalankan suatu aplikasi menggunakan container.

![image](https://user-images.githubusercontent.com/66278794/183978779-70ec5b2e-8f26-4dc8-a2f3-98a1353aac87.png)

![image](https://user-images.githubusercontent.com/66278794/183978874-ea7fdd24-eaf1-430d-a13f-cdbff61fb55c.png)

![image](https://user-images.githubusercontent.com/66278794/183978935-5df435b8-9fa2-4edf-a10f-a321c31ef535.png)

Docker men-sharing kernel dari host OS, serta meng-container-kan suatu aplikasi agar dapat dijalankan dimana saja dan kapan saja.

Aplikasi yg berjalan di dalam container docker tidak terpengaruh oleh faktor luar karena terisolasi.

![image](https://user-images.githubusercontent.com/66278794/183979344-e72156ca-e308-4029-917d-acb6c88a5db3.png)

Docker berfungsi sebagai penyedia layanan virtual bagi aplikasi yg diinstall pada sebuah host. 

Docker akan menyediakan hal-hal yang diperlukan untuk aplikasi mulai dari akses file, koneksi internet, hingga port agar aplikasi dapat berjalan dengan mulus

### Container vs VM

![image](https://user-images.githubusercontent.com/66278794/183979467-6391aa6d-7638-40a2-822c-aa822088f489.png)

VM memakan banyak resource dan waktu utk booting karena melakukan virtualisasi pada host hardware-nya. 

Sedangkan container kebalikannya dari vm, container melakukan virtualisasi pada host OS-nya

### Fundamental Docker

![image](https://user-images.githubusercontent.com/66278794/183979728-ee21a3d5-0152-41ac-936a-970c5855f0f8.png)

Docker File, Blueprint untuk membuat image.

Image, Template untuk menjalankan container.

Container, Perwujudan dari image.

Docker Registry, Tempat untuk upload/download image

### Instalasi Docker

https://www.docs.docker.com/get-docker

### Perintah dasar Docker

1. Melihat Images.

```$ docker images```

2. Download Images.

```$ docker pull debian (latest)```

```$ docker pull debian:9.8 (certain version)```

3. Melihat Docker Container yang sedang running.

```$ docker cotainer ls```

4. Melihat semua list Docker Container.

```$ docker container ls -a```

5. Membuat Docker Container.

```$ docker container create --name mongodb1 mongo:4.0```

6. Start Container.

```$ docker container start mongodb1```

7. Mencari Images.

```$ docker search mysql```

8. Stop Container.

```$ docker container stop mongodb1```

9. Menghapus Container.

```$ docker container rm mongodb1```

10. Membuat Container yang dapat diakses dari host. Dengan kata lain, membuka port pada Container sehingga service yang dijalankan dapat diakses dari luar.

```$ docker container create --name mongodb2 -p 1234:27017 mongo```

11. Menjalankan Images secara langsung. Sehingga, container akan otomatis terbentuk dari Image tersebut.

```$ docker run -itd mongo```

12. Menjalankan Image secara langsung dan otomatis membuat container. Dan juga membuka port untuk container tersebut. Contohnya pada Image mysql/mysql-server.

```$ docker run -d --name mysqlserver1 -p 1234:3306 mysql/mysql-server```

13. Masuk ke dalam Container.

```$ docker exec -it mongodb2 bash```

Nanti mungkin anda akan menemui beberapa sedikit masalah, seperti Image yang tidak bisa di start dengan perintah:

```$ docker container start namacontainer```

walaupun Container tersebut sudah dibuat sebelumnya. Tetapi Image tersebut akan jalan ketika langsung dijalankan dari Image-nya, contohnya seperti mysql atau mysql/mysql-server.

Jadi ada langkah tertentu untuk menjalankan Image tertentu. Seperti mysql/mysql-server, anda bisa melihat dokumentasi resminya. Container mysql dapat di jalankan dengan perintah:

```$ docker run -itd --name mysqlserver1 -p 1234:3306 mysql/mysql-server```

Ketika dilihat pada running Container, maka Container tersebut langsung berjalan.

Jadi perintah tersebut akan membuat container otomatis dari image mysql/mysql-server. Jika image mysql/mysql-server tidak ada di repository local, maka dia akan download image dari registry.

```$ docker ps```

atau 

```$ docker container ls```

14. Membuat Volume

```$ docker volume create data1```

```$ docker volume create data2```

Untuk melihat volume yang sudah dibuat pada docker, ketikkan perintah:

```$ docker volume ls```

Untuk membuat container dengan mencantumkan volume yang ada dapat menggunakan opsi -v.

```$ docker run -itd --name mysqlserver1 -v data1:/var/lib/mysql -p 1234:3306 mysql```

Perintah tersebut akan me-mount volume data1 ke direktori /var/lib/mysql/ pada container mysqlserver1.

15. Melakukan Commit Container

```$ docker commit container1 image1```

Perintah tersebut akan membuat image dengan nama image1 dari container yang sedang running yaitu container1. Jadi kondisi container1 yang sekarang akan disimpan dalam image1.

Jika terjadi perubahan pada container1, maka ketika nanti membuat container baru dari image1 maka perubahan tersebut akan tetap ada.

***

> **Sharing is Learning** ❤️‍🔥
