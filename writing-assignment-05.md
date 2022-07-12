> 🦖 **Impact Byte x Skilvul batch Joyful Jasper** 🐲
# Writing-Assignment-Week-05-Mirza Bakti Sukaryana 😆 🚀

| Table Of ‘Contents’ |
| ---------------------- |
| <ol> |
|  <li>React Redux</li> |
|  <li>React Redux Thunk</li> |
|  <li>React Context</li> |
|  <li>React Testing</li> |
|  <li>React Bootstrap</li> |
|  <li>Material UI</li> |
| </ol> |

***

## 1. React Redux

Redux adalah salah satu state management. Meskipun pada umumnya Redux digunakan bersama dengan React, tapi pada dasarnya Redux juga bisa digunakan untuk framework JavaScript yang lain.

#### Mengapa Redux?

Mengatur hubungan antara state dengan component pada React dapat dilakukan dengan hanya menggunakan state dan props. Tetapi pada aplikasi React yang memilliki banyak sekali component, mengelola state bisa menjadi sedikit rumit.

Sebuah state bisa digunakan oleh banyak component, seringkali state harus dipindah ke parent component (lifting up) agar state tersebut dapat digunakan oleh component lain, karena state sendiri bersifat internal atau private.

Dengan Redux kita tidak perlu lagi memindahkan state dari satu component ke component lain, karena Redux mengubah state menjadi global state dan menempatkannya pada suatu tempat bernama store.

Jadi setiap component dapat menggunakan state yang ada di store secara langsung.

Modifikasi state juga dilakukan melalui Redux, store pada Redux menjadi satu-satunya tempat untuk mengelola state (single source of truth).

Aplikasi menjadi lebih konsisten dan mudah untuk ditest.

#### Haruskah menggunakan redux?

Jawabannya tidak harus, meskipun pengelolaan state sudah dilakukan di satu tempat bukan berarti pekerjaan mengelola state menjadi lebih mudah.

Redux sendiri menggunakan pattern yang kompleks dan butuh waktu untuk memahami dan menguasainya.

Selain itu, mengubah state menggunakan Redux harus melewati beberapa proses, hal ini bisa menyebabkan tingkat kerumitan dari aplikasi menjadi bertambah.

#### Lalu kapan harus menggunakan redux?

Sesuai rekomendasi dari Redux, gunakan Redux jika:


<li>Banyak data yang berubah dari waktu ke waktu.</li>
<li>Pengelolaan state harus dilakukan di satu tempat (Single source of truth).</li>
<li>Mengelola state di top-level component sudah tidak lagi relevan.</li>

> :memo: **Note:** Intinya jika tanpa Redux tidak ada masalah, maka tidak perlu gunakan Redux.

#### Konsep Dasar

Actions

Sebuah JavaScript Object yang mewakili apa yang terjadi di dalam aplikasi.

```js
const addNameAction = {
 type: 'name',
 payload: 'brachio'
}
```

Reducers

Function yang menerima object state dan object action, bertugas menentukan bagaimana suatu state diubah. Output reducer adalah state baru.

```js
(state, action) => newState
```

Store

Tempat dimana global state disimpan.

Dispatch

Satu-satunya cara untuk mengubah state di dalam store adalah dengan memanggil method bernama dispatch yang berisi action, kemudian Redux akan mengeksekusi reducer yang sesuai.

Selector

Function yang digunakan untuk mendapatkan data dari state yang ada di dalam store.

#### 3 Konsep dasar

Single Source of Truth

Redux menggunakan store sebagai single source of truth, dimana semua global state disimpan dalam bentuk object di dalam store.

State is Read Only

Untuk menghindari data diubah tanpa sengaja atau terhapus, state hanya bisa diubah dengan cara dispatch suatu action.

Changes are Made with Pure Reducer Function

State diubah menggunakan pure function (Reducer), yaitu function menerima state sebelumnya dan sebuah action, kemudian menghasilkan state baru tanpa menghapus state sebelumnya.

#### Workflow

Alur atau workflow sederhana dari contoh aplikasi yang menggunakan Redux.

![redux](https://user-images.githubusercontent.com/66278794/178373476-eaf7ebc9-b32a-4bf5-9f20-5a12571e812d.gif)

Penjelasan:

Ketika button Deposit $10 diklik, sebuah click event bernama deposit akan ditangkap oleh event handler.

Event handler memanggil function dispatch dan meneruskan sebuah action dengan type: deposit dan payload: 10. Payload adalah value yang ada di dalam action.

Kemudian store akan mengeksekusi function reducer yang sesuai dengan action yang diteruskan.

Reducer akan mengubah state dari $0 ke $10 untuk kemudian ditampilkan di sisi UI.

#### Redux Toolkit 

Adalah official tool yang disediakan oleh team Redux untuk mempermudah kita jika ingin menggunakan Redux pada suatu aplikasi.

```npm
npx create-react-app my-app

# NPM
npm install @reduxjs/toolkit
# Yarn
yarn add @reduxjs/toolkit

npm start
yarn start
```

#### Step by step
Membuat sebuah aplikasi counter sederhana dimana user dapat menambahkan deposit dan menarik deposit seperti aplikasi pada mesin ATM.

Terdiri dari dua bagian yaitu input dan output.

Input berupa dua button Deposit $10 dan Withdraw $10 sedangkan output adalah tampilan dari total deposit yang tersisa.

Membuat sebuah Redux ‘slice’ yang berisikan data total saldo yang sudah dideposit oleh user.

```
|-node_modules
|-public
|-src
  |-features
    |-balance
      |-balanceSlice.js
```

```js
// balanceSlice.js

import { createSlice } from "@reduxjs/toolkit";
const initialState = { total: 0 };
const balanceSlice = createSlice({
 name: 'balance',
 initialState,
 reducers: {}
});
export default balanceSlice.reducer;

// kita gunakan function createSlice dari Redux toolkit yang berfungsi untuk membuat function reducer.
// Yang harus ditambahkan ke dalam function createSlice adalah nama dari slice, state awal (initialState) dan reducer.
```

buat store dan tambahkan slice yang sudah dibuat ke dalam store.

```js
// my-app/store.js

import { configureStore } from '@reduxjs/toolkit';
import balanceReducer from '../features/balance/balanceSlice';
export default configureStore({
  reducer: {
    balance: balanceReducer
  }
});

// kita ingin Redux menambahkan field bernama balances ke dalam global state, dimana data yang disimpan didalamnya hanya bisa diupdate menggunakan balancesReducer.
```

```
yarn add react-redux
npm add react-redux
```

```js
// src/index.js:

import React from 'react';
import ReactDOM from 'react-dom';
import { Provider } from 'react-redux';
import store from './store';
import './index.css';
import App from './App';
import reportWebVitals from './reportWebVitals';
ReactDOM.render(
  <React.StrictMode>
    <Provider store={store}>
      <App />
    </Provider>
  </React.StrictMode>,
  document.getElementById('root')
);
reportWebVitals();

//Agar React dapat menggunakan semua data yang ada di dalam store, maka kita perlu menempatkan App component di dalam react-redux Provider.
```

```js
// src/features/balance/balance.js

import React from 'react'
import { useSelector } from 'react-redux'
const Balance = () => {
const balance = useSelector(state => state.balance)
return (
    <section>
      <h2>Total Saldo</h2>
      <p>{balance.total}</p>
    </section>
  )
}
export default Balance;
```

```js
// src/App.js

import logo from './logo.svg';
import './App.css';
import Balance from './features/balance/balance';
function App() {
  return (
    <div className="App">
      <img src={logo} className="App-logo" alt="logo" />
      <Balance />
    </div>
  );
}
export default App;

// Tampilkan component Balance ke halaman utama:
```

![image](https://user-images.githubusercontent.com/66278794/178381377-d5f5f525-2112-4930-ac38-23a9d0888240.png)


```js
// src/features/balance/balance.js:

import React from 'react'
import { useSelector } from 'react-redux'
const Balance = () => {
  const balance = useSelector(state => state.balance)
return (
    <>
    <section>
      <h2>Total Saldo</h2>
      <p>$ {balance.total}</p>
    </section>
    <section>
      <button type="button">Deposit $10</button>
      <button type="button">Withdraw $10</button>
    </section>
    </>
  )
}
export default Balance;

// Tambahkan Button yang berfungsi untuk deposit (menambah saldo )dan withdraw (mengurangi saldo).
```

```js
import { createSlice } from '@reduxjs/toolkit';
const initialState = { total: 0 };
const balanceSlice = createSlice({
  name: 'balance',
  initialState,
  reducers: {
    deposit(state, action) {
      return {
        ...state,
        total: state.total + action.payload,
      };
    },
    withdraw(state, action) {
      return {
        ...state,
        total: state.total - action.payload,
      };
    },
  },
});
export const { deposit, withdraw } = balanceSlice.actions;
export default balanceSlice.reducer;

// Total saldo akan diperbaharui setiap user melakukan deposit atau withdraw. Untuk itu kita perlu buat reducer untuk setiap action.
```

```js
// src/features/balance/balance.js 

import React from 'react'
import { useSelector, useDispatch } from 'react-redux'
import { deposit, withdraw } from './balanceSlice';
const Balance = () => {
const balance = useSelector(state => state.balance);
  const dispatch = useDispatch();
const handleDeposit = () => {
    dispatch(
      deposit(10)
    )
  };
const handleWithdraw = () => {
    dispatch(
      withdraw(10)
    )
  };
return (
    <>
    <section>
      <h2>Total Saldo</h2>
      <p>$ {balance.total}</p>
    </section>
    <section>
      <button type="button" 
       onClick={handleDeposit}>Deposit $10</button>
      <button type="button" 
       onClick={handleWithdraw}>Withdraw $10</button>
    </section>
    </>
  )
}
export default Balance;

// menambahkan function dispatch yang akan meneruskan action dari component ke store.
```

Setiap kali user click button Deposit $10 maka event handler handleDeposit akan mengeksekusi function dispatch dengan action deposit(10).

Kemudian redux akan mengeksekusi function reducer yang ada di dalam store yang sesuai dengan action yang diteruskan oleh function dispatch.

Dalam hal ini action deposit akan menambah total balance sebesar $10 secara akumulatif.

Total balance akan terus bertambah dengan kelipatan $10 sesuai jumlah deposit yang dilakukan oleh user.

Sebaliknya jika user click button Withdraw $10 maka event handler handleWithdraw akan mengeksekusi function dispatch dengan action withdraw(10).

Kemudian redux akan mengeksekusi function reducer yang ada di dalam store yang sesuai dengan action yang diteruskan oleh function dispatch.

Dalam hal ini adalah function reducer withdraw yang akan mengurangi total balance sebesar $10 setiap kali user melakukan withdraw.

![simple counter bank](https://user-images.githubusercontent.com/66278794/178382123-b7f1f5f5-7280-42d1-a2b3-1620586227df.gif)

***

## 2. React Redux Thunk

Redux Thunk adalah middleware yang memungkinkan Anda memanggil pembuat aksi yang mengembalikan fungsi sebagai ganti objek aksi. Fungsi itu menerima metode pengiriman penyimpanan, yang kemudian digunakan untuk mengirim aksi sinkron di dalam isi fungsi setelah operasi asinkron selesai.

```js
import axios from "axios"; // tools untuk mengambil data melalui http
import { createSlice, createAsyncThunk /*ambil data*/ } from "@reduxjs/toolkit";

const initialState = {
  loading: false, // menunggu
  users: [], // berhasil
  error: "", // gagal
};

// ekspor khusus fetchUser
export const fetchUsers = createAsyncThunk("user/fetchUsers", () => {
  return axios
    .get("https://jsonplaceholder.typicode.com/users")
    .then /*mencari respon*/ ((response) => response.data);
});

const userSlice = createSlice({
  name: "user",
  initialState,
  extraReducers: (item) => {
    // proses request data
    item.addCase(fetchUsers.pending, (state) => {
      state.loading = true; // loading diubah menjadi true
    });
    // ketika data berhasil didapatkan
    item.addCase(fetchUsers.fulfilled, (state, action) => {
      state.loading = false;
      state.users = action.payload; // parameter muatan data API
      state.error = "";
    });
    // data gagal didapatkan
    item.addCase(fetchUsers.rejected, (state, action) => {
      state.loading = false;
      state.users = [];
      state.error = action.error;
    });
  },
});

export default userSlice.reducer;
```

***

## 3. React Context

Context menyediakan cara untuk oper data melalui diagram komponen tanpa harus oper props secara manual di setiap tingkat.

Kelebihan react context;

<li>lebih simpel dan mudah penggunaanya dari pada redux</li>
<li>hanya perlu mengimpor dan export data dari reactnya langsung</li>
<li>tidak perlu menginstall tool/data apapun</li>

```js
// definisikan isi data context yg akan tersedia dalam komponen provider.
// src/context/UserContext.js

// import yang diperlukan
import { useState, createContext, useEffect } from "react";
import axios from "axios";

// buat dulu setup context dengan createContext
export const UserContext = createContext();

// komponen provider untuk menyediakan si data context
const UserContextProvider = (props) => { // konvensi
  const [user] = useState({ // mengeluarkan sebuah state
    // data yang ingin dikeluarkan
    name: "Mirza",
    batch: "Joyfull Jasper",
  });
  const [userData, setUserData] = useState([]);

  // memanggil data API
  useEffect(() => {
    const getData = async () => {
      const result = await axios.get(
        "https://jsonplaceholder.typicode.com/users"
      );
      setUserData(result.data);
    };

    getData();
    console.log(userData);
  }, []);

  return (
    <UserContext.Provider value={{ user, userData }}> // data yang dibuat dalam state dimasukkan ke dalam atribut value
      {props.children}
    </UserContext.Provider> // penyedia. konvensi untuk mengetahui isi data
  );
};
export default UserContextProvider;
```

```js
// tampilkan data UserContext ke dalam halaman user yang akan tersedia dalam komponen consumer.
// src/components/User.js

import { UserContext } from "../context/UserContext";

const User = () => {
  return (
    <UserContext.Consumer> // kebalikan dari provider
      {(userContext) => {
        // masukkan data dari value di userContext
        const { user } = userContext;
        const { userData } = userContext;
        console.log(userData);
        return (
          <div>
            // memanggil data
            <h1>User Context</h1>
            <h3>name: {user.name}</h3>
            <h3>name: {user.batch}</h3>
            {userData === []
              ? null
              : userData.map((item, key) =>
              <h1 key={key}>{item.name}</h1>)} // pemanggilan data array of object
          </div>
        );
      }}
    </UserContext.Consumer>
  );
};

export default User;
```

```js
// bungkus context provider ke bagian paling luar di dalam return App.js

import "./App.css";

import User from "./components/User";

import UserContextProvider from "./context/UserContext";

function App() {
  return (
    <div className="App">
      <UserContextProvider>
        <h1>React Context</h1>
        <User />
      </UserContextProvider>
    </div>
  );
}

export default App;
```


***

## 4. React Testing

React Testing adalah seperangkat helpers yang memungkinkan Anda mengetes komponen pada React tanpa bergantung pada detail implementasinya. Pendekatan ini membuat refactoring menjadi mudah dan juga mendorong Anda untuk menerapkan best practices untuk aksesbilitas.

npm run test => untuk melakukan testing.

nama testing bebas, seperti commit, tapi harus menggambarkan apa yg sedang di tes.

pada pemanggilan testing setiap karakter harus sesuai, tidak ada toleransi sedikitpun.

***

## 5. React Bootstrap

React Bootstrap adalah framework CSS Bootstrap yang dibagun ulang setiap componentnya dari awal, sehingga tidak memerlukan lagi jQuery di dalamnya. Dan mampu digunakan untuk membangun sebuah user interface dengan ekosistem yang besar.

https://react-bootstrap.github.io/

***

## 6. Material UI

Material-UI adalah library yang menyediakan komponen React untuk pengembangan web yang mudah dan cepat. 

https://mui.com/

***

> **Sharing is Learning** ❤️‍🔥
