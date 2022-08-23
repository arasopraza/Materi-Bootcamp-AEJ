# TypeScript <!-- omit in toc -->

Outline:
- [What is TypeScript?](#what-is-typescript)
- [Why TypeScript?](#why-typescript)
- [Install TypeScript](#install-typescript)
- [TypeScript Syntax](#typescript-syntax)
  - [TS Types](#ts-types)
  - [Object Types](#object-types)
  - [Arrays](#arrays)
  - [Tuples](#tuples)
  - [Union Types](#union-types)
  - [Enums](#enums)
  - [Function](#function)

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

## TypeScript Syntax

TypeScript (TS) merupakan superset dari JavaSript (JS) maka syntax dari TS itu sendiri masih sama dengan JS.

Namun kita hanya akan membahas core syntax dan feature yang ada di TS.

### TS Types  
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

### Object Types  
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

  console.log(student.firstName)

  // Output: John
  ```

  

  ```
  function greet(student: Student) {
      return "Hello " + student.firstName;
  }

  console.log(greet({firstName: "John", lastName: "Doe", age: 21}))

  // Output: Hello John
  ```

  Kita tidak bisa memasukkan value tipe data primitif ke sebuah ``object``.

  ```
  let student: object;

  student = "Jhon";
  ```
  Outputnya akan error: 
  ```
  Type 'string' is not assignable to type 'object'.
  ```

### Arrays

Sama seperti JavaScript, TypeScript juga mendukung tipe data Array. Array merupakan tipe data spesial yang bisa berisi banyak data dari berbagai tipe data atau hanya tipe data tertentu yang didefinisikan diawal.

Array bisa diinisialisasikan dan deklrasi secara bersamaan 
```
let names: string[] = ["John", "Doe"]
```
atau terpisah
```
let age: Array<number>;
age = [21, 22, 23];
```

Array bisa diakses menggunakan indeks array, indeks array dimulai dari 0.
```
console.log(names[1])
```

Untuk menambahkan data ke array dapat menggunakan method ``push``.
```
names.push("Billy")
```

### Tuples

Tuple merupakan tipe lain dari array yang panjang element-nya tetap dan tipe data tetap di posisi yang spesifik. Contoh:

```
let student: [string, number] = ["John", 21];
```
Akan menghasilkan error karna tipe data tidak sesuai posisi:
```
let student: [string, number] = [21, "John"];
// Error: Type 'number' is not assignable to type 'string'.
```
Juga menghasilkan error karna kelebihan element string:
```
let student: [string, string] = ["John", "Doe", "Bill"]
// Error: Type '[string, string, string]' is not assignable to type '[string, string]'.
```

Lalu kenapa diperlukan sebuah tuple? tuple diperlukan untuk menyimpan data yang jumlah element dan tipe datanya tetap tidak berubah seperti data identitas pengguna.

### Union Types

TypeScript memiliki tipe data yang disebut ``union type`` yang bisa mengkombinasikan 2 atau lebih tipe data yang mungkin mewakili salah satu nilai tipe data.

Union berfungsi saat tipe data yang diharapkan berupa dua jenis tipe data misalnya ``number`` atau ``string``, contoh:

```
function combine(input1: number | string, input2: number | string) {
   let result
   if (typeof input1 === 'number' && typeof input2 === 'number') {
     result = input1 + input2;
   } else {
     result = input1.toString() + input2.toString();
   }
   return result;
}

const combines = combine(10, 12);
console.log(combines);
```

### Enums




### Function
