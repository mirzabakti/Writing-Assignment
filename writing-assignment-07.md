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


***

## 2. Sequelize

***

## 3. MongoDB

***

## 4. Mongoose

***

## 5. Docker

***

> **Sharing is Learning** ❤️‍🔥
