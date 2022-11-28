# Deploy app to Heroku <!-- omit in toc -->



Outline:
- [Apa itu deployment?](#apa-itu-deployment)
- [Apa itu heroku?](#apa-itu-heroku)
- [Heroku exercise](#heroku-exercise)
  - [Set up](#set-up)
  - [](#)

## Apa itu deployment?

Software deployment adalah proses membuat perangkat lunak tersedia untuk digunakan oleh pengguna dan program lain. Deployment bisa dilakukan secara manual maupun automasi.

## Apa itu heroku?

Heroku merupakan cloud service platform yang populer, gampang digunakan dan menjadi pilihan untuk development projects. Heroku termasuk ke dalam platform as a service (PaaS). Heroku mendukung banyak bahasa pemrograman seperti python, javascript, ruby, php, dan lain-lain. Jadi heroku bisa digunakan untuk deploy berbagai project.

## Heroku exercise 

Untuk mendeploy applikasi di heroku, dibutuhkan sebuah akun heroku dan juga git yang sudah terinstall di komputer lokal. 

### Set up

Langkah pertama adalah register akun di https://signup.heroku.com/login

Setelah berhasil, selanjutnya install heroku di komputer lokal dengan cara berikut ini:

- Untuk pengguna mac, jalankan perintah ``brew tap heroku/brew && brew install heroku`` di terminal
- Untuk pengguna windows, donwload installer x64-bit https://cli-assets.heroku.com/heroku-x64.exe dan installer x32-bit https://cli-assets.heroku.com/heroku-x86.exe

Setelah proses instalasi selesai, maka kita sudah bisa menggunakan perintah heroku di terminal. Untuk login ke heroku cli, gunakan perintah ``heroku login``. Perintah ini akan membuka halaman login page heroku di browser dan isi data login yang dibutuhkan.

### 

