# TypeScript <!-- omit in toc -->

Setelah kita mengetahui mengenai Backend, pada modul ini kita akan sama-sama belajar tentang TypeScript. TypeScript sudah banyak digunakan oleh developer diseluruh dunia, dan TypeScript gampang untuk dipelajari. Jadi langsung saja kita masuk ke materi ini, dan disimak dengan baik ya.

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
  - [Any Types](#any-types)
  - [Unknown Types](#unknown-types)
  - [Type Aliases](#type-aliases)
  - [Functions](#functions)
  - [Generics](#generics)
- [Introduction to Framework](#introduction-to-framework)
  - [Install NestJS](#install-nestjs)
  - [Running NestJS](#running-nestjs)
- [Summary](#summary)

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

Sebelum menginstall TypeScript dibutuhkan Node.js sebagai JavaScript runtime. Untuk cara penginstallan dan download Node.js dapat dibaca di https://nodejs.dev/en/download/

Jika Node.js sudah terinstall, kita bisa langsung melakukan proses penginstallan TypeScript:

* Install lokal via npm  
  ```npm install typescript --save-dev```

* Install secara global  
  
  ```npm install -g typescript```

Perbedaan antara lokal dan global adalah, secara lokal TypeScript hanya akan terinstall pada project tertentu, sedangkan secara global TypeScrip akan terinstall ke seluruh project yang ada dan bisa dijalankan dimanapun.

Untuk melihat versi TypeScript yang telah diinstall dapat dilakukan dengan mengetik perintah berikut ini (jika menginstall secara global):

```tsc --version```

## TypeScript Syntax

TypeScript merupakan superset dari JavaSript, maka syntax dari TypeScript lebih kurang sama dengan JavaScript.

Namun, pada kali ini kita hanya akan membahas core syntax dan feature yang ada di TypeScript.

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

Array bisa diinisialisasikan dan deklarasi secara bersamaan 
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

Enum merupakan fitur tambahan dari TypeScript pada JavaScript. Enum memungkinkan untuk mendefenisikan satu set konstanta. TypeScript menyediakan tiga jenis enum: Numeric Enum, String Enum, Heterogeneous Enum.

Secara default enum akan bernilai number.

```
enum Role{
  TEACHER,
  ASSISTANT,
  STUDENT,
}

console.log(Role.TEACHER); // 0
console.log(Role.ASSISTANT); // 1
```

contoh string enum:

```
enum Role{
  TEACHER = "TEACHER",
  ASSISTANT = "ASSISTANT",
  STUDENT = "STUDENT,
}

console.log(Role.TEACHER); // TEACHER
```

Untuk lebih lengkapnya dapat dibaca di dokumentasi: https://www.typescriptlang.org/docs/handbook/enums.html

### Any Types

TypeScript memiliki tipe data spesial lainnya, ``any``.
Ketika suatu nilai variabel yang tipe datanya belum diketahui pada saat menulis program seperti inputan user atau dari library pihak ketiga / API ``any`` bisa digunakan.

```
let age: any = '100';
age = 100;
age = true;
```

Namun perlu diingat, sebisa mungkin untuk menghindari penggunaan ``any`` karna TypeScript akan melewatkan type-checking sehingga bisa menjadi bug dikemudian hari.

### Unknown Types

``Unknown types`` merepresentasikan any value, mirip seperti ``any`` tetapi lebih aman karena ``unknown`` lebih strict terhadap type-checking.

```
let personName: unknown;

personName = "John"; // Ok
personName = 20; // Ok
```

Ketika ``uknown`` di-assign ke tipe data ``string`` akan menyebabkan error.

```
let personName: unknown;
let studentName: string;

personName = "John";
personName = 20;

studentName = personName; // Type 'unknown' is not assignable to type 'string'.
```

Sedangkan dengan ``any`` tidak akan menyebabkan error. Oleh karena itu ``unknown`` akan lebih aman dari error atau bug dikemudian hari.

```
let personName: any;
let studentName: string;

personName = "John";
personName = 20;

studentName = personName; // Ok
```

### Type Aliases

``Type aliases`` digunakan untuk memeberi nama pada tipe data apapun. ``Type aliases`` mengurangi code duplikasi dan menjaga kode tetap *Don't repeat yourself* (DRY) sehingga bisa menggunakan jenis tipe data yang sama lebih dari sekali.

```
type User = {
  firstName: string,
  lastName: string,
}

let student: User = {firstName: "a", lastName: "b"};
let teacher: User = {firstName: "a", lastName: "b"};

console.log(student);
console.log(teacher);
```

### Functions

Function merupakan blok kode utama pada sebuah program. Function merupakan cara untuk passing data di JavaScript dan TypeScript mengizinkan untuk menentukan tipe data spesifik untuk input dan output dari function.

- Named Functions  
  Merupakan function yang memiliki nama, dan dipanggil menggunakan nama tersebut.

  ```
  function hello() {
    console.log("Hello);
  }

  hello()
  ```

- Parameter Type Annotations  
  Saat deklarasi function dapat ditambahkan ``type annotations`` untuk setiap parameter yang dapat diterima oleh function.
  
  ```
  function hello(name: string) {
      console.log("Hello, " + name.toUpperCase() + "!!");
  }
  ```

  Ketika function memiliki ``parameter type annotations``, maka argument pada function harus sesuai dengan parameter type.

  ```
  function hello(name: string) {
      console.log("Hello, " + name.toUpperCase() + "!!");
  }

  hello(10); // error
  ```

- Return Type Annontations
  Sebenarnya tidak selalu dibutuhkan sebuat return type karna TypeScript akan mereturn sesuai dengan return statement pada function.

  ```
  function add(a: number, b: number): number {
    return a + a;
  }
  ```

  Pada contoh diatas penambahan ``return type`` tidak merubah apapun karna di return statement sudah jelas bahwa akan mereturn hasil berupa number. Namun ``return type`` ditulis secara eksplisit untuk kebutuhan dokumentasi dan menghindari perubahan kode secara tidak sengaja atau hanya untuk kebutuhan preferensi pribadi.

- Optional Parameters

  TypeScript memiliki optional parameter pada function, parameter yang mungkin menerima value atau tidak menerima value yang dapat ditandai dengan tanda '?' setelah nama parameter.

  ```
  function greet(firstName: string, lastName?: string) {
    console.log(firstName + ' ' + lastName + '!');
  }

  greet('Jhon','Doe');// OK, returns "John Doe!"
  greet('Jhon'); // OK, returns "John undefined!".
  ```
  
  Dapat dilihat contoh di atas, jika argument-nya kosong tidak akan mengalami error.

- Default Parameters
  
  TypeScript juga menyediakan ``default parameter`` yang perilakunya sama seperti optional parameter. Jika argument-nya kosong tidak akan mengalami error tetapi akan mengambil nilai default-nya.

  ```
  function greet(firstName: string, age: number = 0) {
    console.log(firstName + ' ' + age + '!');
  }

  greet('Jhon', 22);// OK, returns "John 22"
  greet('Jhon'); // OK, returns "John 0".
  ```
  
- Anonymous Function  
  Sedikit berbeda dengan ``named function``, ``anonymous function`` tidak memiliki nama dan disimpan di variabel.

  ```
  let hello = function() {
    console.log("Hello TypeScript!!");
  };

  hello(); //Output: Hello TypeScript!!
  ```
  
### Generics

TypeScript ``generics`` memudahkan untuk menulis function, class, dan interface yang reusable dan generalize sehingga mengurangi menulis kode yang berulang.

```
function identity<T>(value: T): T {
  return value;
}

console.log(identity(123));
console.log(identity("abcd"));
```

Pada contoh diatas, dengan menggunakan ``generics`` function identity bisa di-assign dengan tipe data number dan string.

## Introduction to Framework

Ada sebuah tools yang memudahkan pekerjaan kita dalam membangun aplikasi Backend menggunakan TypeScript yaitu Framework. Lalu framework apa yang akan kita gunakan? Yap jawabannya adalah ``NestJS``. ``NestJS`` merupakan framework untuk membangun aplikasi server-side Node.js secara efisien dan scalable. NestJS menggunakan JavaScript progresif, dibangun dan didukung sepenuhnya untuk TypeScript dan menggabungkan element dari object-oriented programming (OOP), functional programming (FP), dan Functional Reactive Programming (FRP).

### Install NestJS

Untuk memulai, kita bisa install Nest CLI atau clone starter project yang sudah disediakan oleh NestJS.

```
npm i -g @nestjs/cli
nest new project-name
```

Cara alternatif dengan melakukan cloning menggunakan Git:

```
git clone https://github.com/nestjs/typescript-starter.git project
cd project
npm install
```

Setelah penginstallan berhasil, akan ada beberapa core file seperti:

```
src
 - app.controller.spec.ts
 - app.controller.ts
 - app.module.ts
 - app.service.ts
 - main.ts
```

Berikut penjelasan singkat dari file tersebut:

- app.controller.ts, merupakan basic controller dengan single route.
- app.controller.spec.ts, merupakan unit test untuk controller.
- app.module.ts, root modul dari aplkasi.
- app.service.ts, merupakan basic service dengan single method.
- main.ts, file aplikasi yang menggunakan core function NestFactory untuk membuat instance aplikasi Nest.

### Running NestJS

NestJS dapat dijalankan menggunakan command:

```
npm run start
```

Untuk auto reload server dan recompiling dapat menggunakan command:

```
npm run start:dev
```

Setelah dijalankan, bukalah alamat ``http://localhost:3000/`` di browser dan akan tampil sebuah pesan ``Hello World!``.

## Summary

Kita sudah mempelajari dasar-dasar dari TypeScript seperti:
-  Apa itu TypeScript.
-  Kenapa TypeScript.
-  Cara install TypeScript.
-  Basic syntax dan core feature TypeScript.
-  Pengenalan ke framework NestJs.

Tentu belum semua hal tentang TypeScript yang kita bahas pada modul ini, tapi modul ini merupakan langkah awal untuk mempelajari TypeScript kedepannya. Dokumentasi lengkap TypeScript dapat dibaca di https://www.typescriptlang.org/docs/.