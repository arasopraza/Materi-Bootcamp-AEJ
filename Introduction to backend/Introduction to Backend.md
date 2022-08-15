# Introduction to Backend <!-- omit in toc -->

Dalam web development kita mengenal istilah Front-end dan Back-end, namun pada materi ini kita hanya akan fokus membahas tentang Back-end. Kita akan bahas lebih dalam tentang Back-end, apa saja teknologi yang digunakan, dan apa saja tanggung jawab seorang Back-end developer. simak dengan seksama ya!

Outline:
- [Apa itu backend?](#apa-itu-backend)
- [Peran Back-end dalam pengembangan web](#peran-back-end-dalam-pengembangan-web)
- [Back-end development tools dan teknologi](#back-end-development-tools-dan-teknologi)
  - [Server](#server)
  - [Web server](#web-server)
  - [Web service](#web-service)
  - [Communication protocol (HTTP)](#communication-protocol-http)
    - [**HTTP request**](#http-request)
    - [**HTTTP Response**](#htttp-response)
  - [Database](#database)
  - [Language](#language)

## Apa itu backend?

**Back-end** merupakan pengembangan yang berfokus untuk memenuhi kebutuhan dan fungsional aplikasi yang tidak terlihat oleh user atau pengguna, berfokus pada **sisi server** dan **logika aplikasi** agar website berfungsi dengan baik seperti bagaimana data disimpan, diproses dan ditampilkan. Orang yang fokus pada Back-end disebut sebagai Back-end Developers. 

## Peran Back-end dalam pengembangan web

Untuk memahami peran Back-end dalam pengembangan web kita dapat analogikannya melalui kegiatan dunia nyata. Mari kita analogikan sebagai rumah makan padang.

Pada saat ingin membeli nasi padang di sebuah rumah makan, tampilan yang kita lihat di rumah makan seperti meja kasir, lauk makanan yang ada di piring, nasi dan meja makan itu bisa kita representasikan sebagai Front-end. Sedangkan dapur yang ada di belakang rumah makan padang kita representasikan sebagai Back-end yang berperan dalam memasak nasi, lauk dan membuat minuman.

Begitu juga dalam sebuah pengembangan aplikasi. Back-end developer berperan dalam mengurus aplikasi, database, dan server.

## Back-end development tools dan teknologi

Ada beberapa tools dan teknologi yang digunakan dalam Back-end development yang perlu dipahami, diantaranya:
### Server
  Server merupakan komputer atau sistem yang "melayani" komputer pengguna atau disebut juga dengan client dengan menyiapkan resource, data, dan service yang akan digunakan oleh komputer lain. 

### Web server
  Web server merupakan sebuah server yang menyimpan dan mengirimkan konten berupa teks, gambar, video dan data aplikasi ke pengguna yang melakukan permintaan. Web server berkomunikasi dengan browser menggunakan Hypertext Transfer Protocol (HTTP).

### Web service
  Web service merupakan sebuah protokol dan standar untuk pertukaran data diantara aplikasi atau sistem berbeda melalui jaringan internet. Web services bisa digunakan diberbagai program yang dibuat dengan bahasa pemrograman berbeda dan bisa saling berkomunikasi dan bertukar data.

### Communication protocol (HTTP)
  Hypertext Transfer Protocol (HTTP) yang merupakan dasar dari World Wide Web (WWWW), dan HTTP digunakan untuk memuat halaman web. HTTP merupakan application protocol yang berjalan pada TCP/IP (Transmission Control Protocol/Internet Protocol). TCP/IP adalah standar komunikasi data yang digunakan dalam proses tukar-menukar data dari satu perangkat ke perangkat lain (client-server) di dalam jaringan Internet. Versi terbaru dari HTTP adalah HTTP/2 yang diperkenalkan pada Mei 2015.

  #### **HTTP request**
  HTTP Request terjadi saat client mengakses suatu halaman website melalui borwser. HTTP request bertujuan untuk mengakses atau meminta resources yang ada pada server. 

  HTTP request terdiri dari:
  1. Request line.  
    Request line terdiri dari 3 items:  
    - **Method**, method terdiri dari satu kata yang memberitahukan server apa yang harus dilakukan dengan resource. Contohnya ketika method GET diminta oleh client maka server akan mengirimkan resource yang diminta.  
    - **Path**, path merupakan lokasi resource di server.  
    - **HTTP version**, menampilkan spesifikasi HTTP yang dilakukan oleh client.  
    Contoh dari request line: GET /user/user.html HTTP/1.1
  
  2. HTTP headers  
    HTTP headers untuk memberikan informasi tambahan tentang request ke server seperti nama host, jenis browser yang digunakan, pengirim dan cara berkomunikasi antara pengirim dan penerima. Setiap HTTP headers terdiri dari nama dan value.

  !["htpp headers"](materi-bootcamp/../http%20headers.jpeg)

  3. HTTP request body (optional)  
    Berisi informasi opsional yang server butuhkan untuk memproses request seperti username dan password atau data lainnya ketika disubmit melalui form.

  #### **HTTTP Response**

  HTTP response merupakan apa yang diterima oleh client dari server ketika melakukan HTTP request. HTTP response bertujuan untuk menyediakan resource yang client minta atau untuk memberikan informasi ke client jika permintaan yang diminta telah dilakukan, dan untuk menginformasikan ke client jika terjadi kesalahan dalam memproses permintaannya.

  HTTP response terdiri dari:
  1. Status line.  
      Status line setidaknya terdiri dari 3 items:
      - **HTTP version**, menampilkan spesifikasi HTTP yang dilakukan oleh server.
      - **Status code**, 3 digit angka yang mengindikasikan hasil dari HTTP request. Status code dibagi menjadi 5 block:  
        1. 1xx Informational  
        2. 2xx Success  
        3. 3xx Redirection  
        4. 4xx Client Error  
        5. 5xx Server Error   
   
      - **Reason phrase**, merupakan status code yang berupa text yang mudah dibaca.  
      Contoh dari response line: HTTP/1.1 200 OK

  2. HTTP headers  
	  Tidak beda jauh dari HTTP headers yang ada pada HTTP reqeust, HTTP response headers ditulis untuk memberikan informasi tambahan tentang respon server yang lebih lanjut dan informasi tentang server yang mengirim respon.

  3. HTTP response body (optional)  
    Berisi tentang respon dari server, ketika respon sukses maka akan berisi resource sesuai dengan permintaan client atau informasi status dari request client. Dan ketika permintaan dari client gagal maka akan berisi pesan error yang terjadi.
  
### Database


  
### Language

