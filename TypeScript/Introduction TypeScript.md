# TypeScript <!-- omit in toc -->

Outline:
- [What is TypeScript?](#what-is-typescript)
- [Why TypeScript?](#why-typescript)
- [Install TypeScript](#install-typescript)
- [TypeScript](#typescript)

## What is TypeScript?
 
TypeScript merupakan bahasa strongly typed, object-oriented, yang dibangun diatas JavaScript. TypeScript sendiri menyebut dirinya sebagai "JavaScript with syntax for types". Sederhananya, TypeScript merupakan JavaScript dengan kemampuan tambahan. TypeScript juga bisa digunakan pada JavaScript environment seperti NodeJS dan Web browser.

TypeScript merupakan bahasa open-source yang sangat populer yang dikembangkan oleh Microsoft. TypeScript banyak digunakan oleh software developers di seluruh dunia.

!["TS"](materi-bootcamp/../Ts.png)

## Why TypeScript?

1. Static-typing  
   TypeScript bisa mendeteksi error pada kode sebelum  dijalankan yang disebut sebagai static checking. Ini bisa menghindari bug bahkan sebelum program dijalankan.

2. Object-oriented  
   TypeScript mendukung paradigma Object-Oriented Programming (OOP). Dengan OOP membuat pengembangan aplikasi berskala besar dan kompleks lebih mudah.

3. Mudah digunakan
   Kode TypeScript ketika dieksekusi akan dikonversi ke JavaScript, jadi kita bisa merubah file JavaScript (.js) ke TypeScript (.ts) dengan mudah. Dan bagi JavaScript programmer akan lebih mudah ketika menggunakan TypeScript karna TypeScript merupakan superset dari JavaSript.

## Install TypeScript

Sebelum menginstall TypeScript dibutuhkan Node.js sebagai JavaScript runtime. Cara menginstall dan download Node.js dapat dilihat di https://nodejs.dev/en/download/

Jika sudah kita bisa langsung menginstall TypeScript:

* Install lokal via npm  
  ```npm install typescript --save-dev```

* Install secara global  
  
  ```npm install -g typescript```

Perbedaan antara lokal dan global adalah, secara lokal hanya pada project tertentu saja sedangkan secara global pada seluruh project yang ada dan bisa dijalankan dimanapun di terminal.

Untuk melihat versi TypeScript yang telah diinstall dapat dilakukan dengan mengetik perintah berikut ini di terminal (jika menginstall secara global):

```tsc --version```

## TypeScript

Karna TypeScript (TS) merupakan superset dari JavaSript (JS) maka syntax dari TS itu sendiri masih sama dengan JS.

Namun kita hanya akan membahas core syntax dan feature yang ada di TS.

- Core Types  
  TypeScript memiliki tipe data primitif: string, number, dan boolean.  
  - String berisi text seperti "Hello, world"
  - Number berisi angka seperti 100. JavaScript tidak memiliki value spesial untuk bilangan seperti float, semuanya hanya number.
  - Boolean hanya berisi dua value, true dan false.  

    ```
    let nama = "Jhon";
    let umur = 22;
    let nikah = false;

    console.log(typeof nama); // string
    console.log(typeof umur); // number
    console.log(typeof nikah); // boolean
    ```

- Object Types  
  Tipe data ``object`` merupakan tipe data yang bukan tipe data primitive. Di dalam ``object`` terdiri dari properti dan value.

  ```
  let student: {
    firstName: string;
    lastName: string;
    age: number;
  } = {
    firstName: 'John',
    lastName: 'Doe',
    age: 21,
  };
  ```

  Atau dapat menggunakan ``interface``

  ```
  interface Student {
    firstName: string;
    lastName: string;
    age: number;
  }

  let student: Student = {
    firstName: 'John',
    lastName: 'Doe',
    age: 21,
  }
  ```

  Kita tidak bisa memasukkan value tipe data primitif ke sebuah ``object``.

- Array
  
- Tuples
- Enums
- Function
- 
