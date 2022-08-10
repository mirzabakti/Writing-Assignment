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



***

## 3. MongoDB

***

## 4. Mongoose

***

## 5. Docker

***

> **Sharing is Learning** ❤️‍🔥
