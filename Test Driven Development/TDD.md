# Test Driven Development <!-- omit in toc -->

Ada satu kesalahan kecil yang terjadi ketika kita sedang membangun suatu program atau aplikasi. Coba tebak apa itu? Selamat bagi yang menjawab testing (pengujian) karena jawabannya benar, testing. Jangan khawatir karena kita akan mempelajari testing khususnya ``unit test`` pada modul ini dan juga belajar tentang ``"Test Driven Development (TDD)"``. 

Dalam pengembangan suatu program atau aplikasi, agar mengurangi bug dan memastikan kode yang ditulis sudah benar diperlukan sebuah testing. Testing memiliki banyak jenis seperti automated test dan manual test. Jika kode yang ditulis sudah mencapai ribuan baris, menguji secara manual mungkin sudah tidak memungkin. 

Outline:
- [Automated Test](#automated-test)
  - [Tipe automated test](#tipe-automated-test)
- [Unit Test](#unit-test)
- [Test Driven Development](#test-driven-development)
- [Framework Testing](#framework-testing)
- [Hands-On TDD dengan NestJS](#hands-on-tdd-dengan-nestjs)
  - [Create Project](#create-project)
  - [Test Scenario](#test-scenario)
  - [Implementation Code](#implementation-code)
- [Summary](#summary)

## Automated Test

Automated test merupakan sebuah pengujian yang dilakukan menggunakan tools atau program untuk memastikan kode yang ditulis sesuai dengan yang diharapkan. Automated test menghemat banyak waktu dan memudahkan dalam pengujian dibandingkan dengan manual test.

### Tipe automated test

- Unit test  
  Pengujian yang berfokus pada unit dan komponen terkecil yang berupa class, method, dan function. 
- Integration test  
  Pengujian tidak hanya pada unit atau komponen tertentu tetapi pengujian ke semua class, method, dan function untuk memastikan semua unit dan komponen terhubung dan berfungsi dengan sesuai harapan dari sebuah fitur.
- End-to-end test (E2E Test) 
  Pengujian untuk memastikan seluruh aplikasi seperti alur aplikasi, data, dan komunikasi dengan sistem eksternal berjalan dengan baik sesuai harapan dari awal sampai akhir proses. 

## Unit Test

Unit test merupakan test pada unit individu atau komponen program yang biasanya berupa class, method, dan function. Unit merupakan kode yang terisolasi dan dapat diuji tanpa menjalankan seluruh aplikasi. Test case merupakan satu set input, satu atau lebih panggilan function, dan pernyataan output yang diharapkan dari kode.

Ada prinsip yang harus diikut dalam menulis unit test, yaitu F.I.R.S.T principle:

- Fast, tulis test yang cepat dan simpel.
- Isolated/Independent, tulis test yang tidak memiliki ketergantungan dengan test case lainnya. 
- Repeatable, tulis test yang bisa dijalankan berulang di environment apapun.
- Self-validating, tulis test yang tidak perlu dilakukan validasi manual setelah test dilakukan.
- Timely/Thorough, tulis test dengan berbagai banyak skenario.

Unit test membantu dalam fixing bugs dalam fase development, mengurangi biaya development dan unit test yang baik juga bisa dijadikan sebagai dokumentasi.

## Test Driven Development

Test driven development (TDD) merupakan sebuah praktik menulis test terlebih dahulu sebelum menulis code. Sesuai dengan namanya, kita akan disetir oleh test dalam pengembangan nantinya. TDD memiliki alur kerja yang unik yaitu red-green-refactor.

!["tdd cycle"](materi-bootcamp/../tdd%20cycle.png)

- Red Stage, tulis test yang gagal.
  Pada fase ini, tulis test untuk perilaku yang diharapkan tanpa menulis implementasi kode sehingga test akan gagal (merah).
- Green Stage, tulis implementasi agar test pass.
  Pada fase ini, tulislah implementasi kode dan fokuslah bagaimana cara agar test menjadi hijau (lolos) tanpa memikirkan cara yang efektif dalam menulis kode. 
- Refactor Stage, improve code yang sudah ditulis.
  Pada fase ini, lakukan improvisasi pada implementasi kode dan memastikan testnya masih tetap hijau.

## Framework Testing

Ada banyak framework testing untuk JavaScript dan TypeScript yang populer dikalangan developer, salah satunya yang akan kita gunakan yaitu Jest.

Jest merupakan framework testing yang berfokus pada penyederhanaan pasalnya mengunakan jest sangat mudah dan tidak membutuhkan konfigurasi pada saat pertama kali digunakan. Jest dibuat oleh Facebook yang dapat digunakana pada Node JS, Typescript, dan berbagai macam framework lainnya seperti React, Angular, dan Vue.

## Hands-On TDD dengan NestJS

Setelah mempelejari apa itu TDD dan fase apa saja yang ada di TDD, saatnya kita akan praktik agar dapat memahami konsep TDD. Yup tanpa berlama-lama lagi langsung saja kita mulai.

### Create Project

Kita akan membuat program sederhana yang menampilkan data student dengan menerapkan TDD. 

Di modul sebelumnya, kita sudah memasang NestJs, untuk membuat project baru, jalankan perintah berikut ini di terminal:

```
nest new tdd-hands-on
```

Selanjutnya bukalah project tersebut di Visual Studio Code.

### Test Scenario

Dalam praktik TDD kita akan mulai dengan membuat skenario test yang paling sederhana.

Skenario yang akan kita buat adalah test case yang menampilkan seluruh data student. Bukalah file ``app.controller.spec.ts`` dan hapus test case yang digenerate oleh nest kemudian tulislah kode dibawah ini:

```
describe('AppController', () => {
  let appController: AppController;
  let appService: AppService;

  beforeEach(async () => {
    const app: TestingModule = await Test.createTestingModule({
      controllers: [AppController],
      providers: [AppService],
    }).compile();

    appService = app.get<AppService>(AppService);
    appController = app.get<AppController>(AppController);
  });

  describe('findAll', () => {
    it('should return an array of weights', async () => {
      const result: Student[] = [
        {
          studentId: 1,
          firstName: 'John',
          lastName: 'Bill',
          age: 21,
          gender: 5,
        },
      ];
      jest.spyOn(appService, 'findAll').mockImplementation(() => result);

      expect(await appController.findAll()).toBe(result);
    });
  });
});
```

Save file tersebut, kemudian run ``npm test``. Akan tampil pesan error berikut ini:

!["test fail"](materi-bootcamp/../test%20fail.png)

Jangan khawatir, karena memang ini yang kita harapkan. Ini merupakan fase red (test gagal). Agar test-nya menjadi green (test passed) maka selanjutnya kita akan tulis implementasi kodenya.

### Implementation Code

Pertama, kita akan membuat sebuah interface bernama ``Student``. Buatlah sebuah folder baru bernama ``interfaces`` dan didalamnya tambahkan file bernama ``student.interface.ts``. Kemudian di dalam file ``student.interface.ts`` tambahkan kode berikut ini:

```
export interface Student {
  studentId: number;
  firstName: string;
  lastName: string;
  age: number;
  gender: string;
}
```

Interface student akan berisi data personal dari student yang akan kita gunakan nantinya.

Selanjutnya, kita akan membuat service findAll untuk menampilkan seluruh data student. Untuk itu bukalah file ``app.service.ts`` dan tambahkan kode berikut ini:

```
findAll(): Student[] {
    return [
      {
        studentId: 1,
        firstName: 'John',
        lastName: 'Bill',
        age: 21,
        gender: 'Male',
      },
      {
        studentId: 2,
        firstName: 'Anna',
        lastName: 'Bill',
        age: 21,
        gender: 'Female',
      },
    ];
  }
```

Function ``findAll`` akan mengembalikan array yang berisi student.

Selanjutnya kita akan membuat implementasinya pada controller. Bukalah file ``app.controller.ts``. Kemudian tambahkan constructor pada class ``AppController`` yang berisi app service.

```
constructor(private readonly appService: AppService) {}
```

Setelah itu tambahkan kode dibawah ini ke dalam class ``AppController``.

```
  @Get()
  async findAll(): Promise<Student[]> {
    return this.appService.findAll();
  }
```

Pada function ``findAll`` di controller inilah kita memanggil service yang telah dibuat di ``app.service.ts``

Kemudian run ``npm test``. Akan tampil pesan berikut ini:

!["test pass"](materi-bootcamp/../test%20pass.png)

Kita sudah berada di fase green, jika implementasi kode bisa dilakukan improvisasi maka lakukanlah refactor. Dan jika tidak maka cukup sampe di fase ini. Selanjutnya untuk latihan bisa ditambahkan test case lainnya seperti menampilkan student berdasarkan student ID.

## Summary

Sejauh ini, kita sudah mengetahui pengertian dari automated test, unit-test dan TDD. TDD memiliki siklus: red-green-refactor.  

Adapun tahap dalam TDD sebagai berikut:
1. Buat test skenario dari yang paling mudah dan sederhana.
2. Implementasi kode sesuai dengan test skenario.
3. Lakukan improvisasi pada implementasi kode.

Mengalami kesulitan saat pertama kali melakukan praktik TDD merupakan hal yang wajar, dengan seringnya melakukan praktik TDD nantinya akan menjadi lebih mudah.
