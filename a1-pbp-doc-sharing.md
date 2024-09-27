
# 🎓 **Introducing Kelompok A1**

Welcome to the presentation by **Kelompok A1**, a dedicated team of 7 members from Teknik Informatika who have explored and experimented with C++ in Arduino, specifically focusing on Object-Oriented Paradigm and Declarative vs Imperative programming. 🚀 We aim to showcase the depth of these programming paradigms within the context of IoT development using Arduino.

### 👥 **Team Members:**
1. **Nieto Salim Maula** (19)
2. **Farras Ahmad Rasyid** (06)
3. **Jizdan Mulkan Nailan** (11)
4. **Micho Dhani Firmansyah** (13)
5. **Ratna Puspitasari** (22)
6. **Satria Permata Sejati** (26)
7. **Zaki Abdillah** (32)

---

# 1️⃣ **Object-Oriented Paradigm di Arduino dengan C++**

## 🔍 Penjelasan dan Fakta/Data:
- **Problem signifikan**: Pada perangkat IoT seperti Arduino, pengembangan perangkat lunak sering menjadi rumit ketika proyek semakin besar. Ketika berbagai komponen (seperti sensor, aktuator, dan modul komunikasi) perlu diatur, kode procedural (imperatif) menjadi tidak terorganisir. 
- **Kekompleksan**: Pengelolaan struktur data, perilaku perangkat keras, dan komunikasi antar modul bisa membingungkan tanpa modularitas. OOP memberikan solusi dengan cara mengorganisir komponen-komponen ini ke dalam unit-unit yang lebih kecil, seperti **class** dan **object**.
- **Relevansi dengan industri**: Dalam pengembangan sistem embedded di industri (misalnya otomotif, smart home), OOP membantu mengelola kompleksitas dan meningkatkan maintainability kode. Pendekatan ini membuat pengembangan sistem lebih modular dan dapat diperluas dengan mudah.

## 📚 Definisi, Konsep, Prinsip Utama:
- **Definisi**: OOP adalah paradigma pemrograman yang memanfaatkan konsep **object** dan **class** untuk mengelola data dan fungsionalitas.
- **Konsep utama**: 
  - **Encapsulation**: Mengumpulkan data dan fungsi yang beroperasi pada data tersebut ke dalam satu unit.
  - **Inheritance**: Memungkinkan penggunaan kembali kode dengan memperluas class yang ada.
  - **Polymorphism**: Memungkinkan objek dari class yang berbeda untuk diperlakukan sebagai objek dari class yang sama.
- **Prinsip utama**: Abstraksi, enkapsulasi, dan modularitas memungkinkan pengelolaan sistem yang lebih terstruktur.

## ⚙️ Mekanisme Kerja:
Untuk membuktikan mengapa C++ lebih cocok menggunakan paradigma **Object-Oriented Programming (OOP)** dalam pengembangan **Internet of Things (IoT)** dibandingkan paradigma lainnya, mari kita bandingkan pendekatan OOP dengan pendekatan prosedural. Pendekatan OOP menawarkan berbagai keuntungan dalam hal modularitas, pemeliharaan kode, dan abstraksi, yang sangat penting dalam pengembangan sistem IoT yang kompleks.

### Keuntungan OOP dalam Pengembangan IoT:

1. **Modularitas dan Reusability**: Dalam OOP, kode dibagi menjadi objek yang dapat digunakan kembali. Pada IoT, perangkat yang terhubung (sensor, aktuator) bisa dimodelkan sebagai objek dengan sifat dan fungsi tersendiri.
   
2. **Abstraksi**: IoT sering melibatkan berbagai perangkat keras dan protokol komunikasi yang berbeda. Abstraksi yang disediakan oleh OOP memungkinkan kita untuk menyembunyikan detail implementasi perangkat keras di balik antarmuka yang lebih mudah digunakan.

3. **Enkapsulasi**: IoT melibatkan pengumpulan data dari sensor dan kontrol perangkat. OOP memungkinkan pengembang untuk menyembunyikan detail internal sensor dan perangkat keras lainnya, hanya memaparkan metode yang dibutuhkan pengguna, meningkatkan keamanan dan keandalan sistem.

4. **Inheritance dan Polymorphism**: Fitur ini memungkinkan penggunaan kembali kode yang sama untuk perangkat IoT yang serupa. Misalnya, semua sensor dapat berbagi fitur dasar yang sama, tetapi jenis sensor yang berbeda dapat menambahkan fungsionalitas spesifik mereka.

### Contoh Pembuktian Menggunakan Source Code

#### 1. **Pendekatan Prosedural**:
```cpp
#include <iostream>

struct Sensor {
    int id;
    float temperature;
};

void readTemperature(Sensor &sensor) {
    // Simulasi membaca data dari sensor
    sensor.temperature = 25.0 + (rand() % 10);  // nilai acak
}

void displayTemperature(Sensor sensor) {
    std::cout << "Sensor ID: " << sensor.id << ", Temperature: " << sensor.temperature << " C" << std::endl;
}

int main() {
    Sensor sensor1 = {1, 0.0};
    readTemperature(sensor1);
    displayTemperature(sensor1);

    return 0;
}
```

Pada pendekatan ini:
- Fungsi `readTemperature` dan `displayTemperature` dipanggil secara manual untuk setiap sensor.
- Tidak ada modularitas yang jelas; jika kita ingin menambahkan tipe sensor baru, kita harus membuat banyak fungsi baru.

#### 2. **Pendekatan OOP**:
```cpp
#include <iostream>
#include <cstdlib>

// Kelas dasar untuk Sensor
class Sensor {
protected:
    int id;
    float temperature;

public:
    Sensor(int id) : id(id), temperature(0.0) {}
    virtual void read() = 0;  // Metode abstrak
    void display() {
        std::cout << "Sensor ID: " << id << ", Temperature: " << temperature << " C" << std::endl;
    }
};

// Kelas turunan untuk sensor suhu
class TemperatureSensor : public Sensor {
public:
    TemperatureSensor(int id) : Sensor(id) {}

    void read() override {
        // Simulasi membaca data dari sensor suhu
        temperature = 25.0 + (rand() % 10);  // nilai acak
    }
};

int main() {
    // Membuat objek sensor suhu
    TemperatureSensor tempSensor(1);
    
    // Membaca dan menampilkan data sensor
    tempSensor.read();
    tempSensor.display();

    return 0;
}
```

Pada pendekatan OOP:
- **Modularitas**: Kelas `Sensor` sebagai kelas dasar yang mendefinisikan atribut dan metode umum untuk semua sensor.
- **Abstraksi**: Kelas `Sensor` memiliki metode abstrak `read()` yang harus diimplementasikan oleh setiap sensor. Ini memungkinkan penambahan sensor lain (misalnya, kelembaban, cahaya) dengan mudah, tanpa mengubah kode utama.
- **Inheritance**: `TemperatureSensor` mewarisi dari `Sensor`, dan kita hanya menambahkan metode `read()` untuk mengkhususkan perilaku.
- **Polymorphism**: Jika kita ingin menambah sensor lain, kita bisa mewarisi kelas `Sensor` tanpa harus mengubah fungsi display atau logika lain yang umum.

### Penjelasan Lebih Lanjut:
- **Modularitas** memungkinkan sensor baru atau perangkat baru ditambahkan dengan mudah tanpa mengubah kode utama secara signifikan. Pada IoT, ini penting karena arsitektur bisa berkembang seiring waktu dengan menambahkan lebih banyak perangkat atau sensor.
  
- **Abstraksi** memudahkan pengelolaan perangkat yang kompleks, terutama ketika kita bekerja dengan protokol komunikasi yang berbeda-beda (WiFi, Bluetooth, LoRa). Setiap perangkat dapat disembunyikan di balik antarmuka umum yang menyediakan fungsi standar.

- **Polymorphism dan inheritance** membuat kode lebih mudah dipelihara dan diperluas. Pada sistem IoT, kita mungkin bekerja dengan berbagai jenis perangkat, dan dengan inheritance kita bisa mengurangi duplikasi kode.

Berikut adalah tabel perbandingan antara pendekatan **Prosedural** dan **Object-Oriented Programming (OOP)** dalam penggunaan **C++** untuk pengembangan **Internet of Things (IoT)**:

| **Aspek**                    | **Pendekatan Prosedural**                                  | **Pendekatan OOP (Object-Oriented Programming)**                   |
|------------------------------|------------------------------------------------------------|--------------------------------------------------------------------|
| **Modularitas**               | Fungsi dan data terpisah, sulit digunakan ulang jika ada perubahan pada struktur data. | Kode dibagi menjadi kelas dan objek, sehingga lebih modular dan mudah digunakan ulang. |
| **Abstraksi**                 | Tidak ada lapisan abstraksi yang jelas, semua detail harus ditangani secara eksplisit. | Detail perangkat keras bisa disembunyikan melalui abstraksi kelas, hanya menyediakan metode yang relevan bagi pengguna. |
| **Pemeliharaan**              | Pemeliharaan sulit karena perubahan di satu bagian kode sering berdampak pada bagian lain. | Pemeliharaan lebih mudah karena setiap komponen (objek) berdiri sendiri dan hanya berkomunikasi melalui antarmuka yang jelas. |
| **Reusability (Penggunaan Ulang)** | Sulit untuk digunakan ulang karena fungsionalitas tersebar di berbagai fungsi dan struktur data. | Mudah digunakan ulang, objek dapat dibuat sekali dan digunakan dalam konteks yang berbeda tanpa perubahan kode besar. |
| **Enkapsulasi**               | Data dan fungsi tidak terikat erat, sehingga data bisa diakses dari mana saja. | Data dan fungsi disembunyikan dalam objek, sehingga akses data lebih terkontrol dan aman. |
| **Polymorphism (Polimorfisme)** | Tidak didukung secara langsung, harus diimplementasikan secara manual dengan kondisi logika. | Didukung penuh, memungkinkan objek yang berbeda untuk digunakan melalui antarmuka yang sama, sehingga kode lebih fleksibel. |
| **Inheritance (Pewarisan)**   | Tidak ada konsep pewarisan; fungsi harus didefinisikan ulang untuk setiap variasi perangkat. | Didukung, memungkinkan kelas untuk mewarisi sifat dan metode dari kelas lain, mengurangi duplikasi kode. |
| **Efisiensi Kode**            | Kode cenderung menjadi panjang dan berulang, terutama saat menangani perangkat yang berbeda. | Lebih efisien karena adanya pewarisan, polimorfisme, dan abstraksi yang mengurangi duplikasi kode. |
| **Skalabilitas**              | Kurang scalable, sulit untuk menambahkan perangkat baru tanpa memodifikasi banyak bagian kode. | Sangat scalable, mudah untuk menambahkan perangkat baru dengan membuat kelas baru yang mewarisi kelas dasar. |
| **Keamanan**                  | Data dan fungsi mudah diakses oleh bagian lain dari program, meningkatkan risiko kesalahan. | Enkapsulasi memungkinkan akses data dan fungsi dikontrol secara ketat, meningkatkan keamanan dan keandalan. |

### Kesimpulan:
Pendekatan OOP lebih cocok untuk pengembangan IoT karena memungkinkan pembuatan kode yang lebih modular, mudah dirawat, dan scalable.

## ⚖️ Kasus Dilematis:
- **Dilema**: Penggunaan OOP pada perangkat dengan sumber daya terbatas seperti Arduino dapat mempengaruhi efisiensi, seperti dalam penggunaan memori dan waktu eksekusi. Apakah manfaat modularitas dan maintainability yang ditawarkan oleh OOP sepadan dengan kompromi kinerja di perangkat rendah daya?

---

# 2️⃣ **Declarative vs Imperative Programming di Arduino**

## 🔍 Penjelasan dan Fakta/Data:
- **Problem signifikan**: Salah satu tantangan utama di IoT adalah menulis kode yang efisien dan mudah dipahami. Gaya imperative tradisional, yang memfokuskan pada langkah-langkah spesifik, seringkali sulit dibaca dan dimodifikasi ketika program menjadi lebih kompleks. 
- **Kekompleksan**: Gaya imperative memerlukan perintah eksplisit untuk setiap langkah operasi. Gaya deklaratif memungkinkan deskripsi lebih ringkas dan fokus pada **apa yang harus dilakukan** daripada **bagaimana melakukannya**.
- **Relevansi dengan industri**: Dalam pengembangan sistem IoT, terutama dalam hal otomasi, pendekatan deklaratif sering digunakan untuk meningkatkan keterbacaan dan pengelolaan logika program.

## 📚 Definisi, Konsep, Prinsip Utama:
- **Declarative Programming**: Sebuah pendekatan pemrograman yang lebih fokus pada hasil akhir daripada urutan instruksi. Ini sering digunakan di sistem yang bersifat reaktif atau event-driven.
- **Imperative Programming**: Sebuah paradigma pemrograman yang menginstruksikan komputer untuk menjalankan serangkaian perintah secara eksplisit.
- **Prinsip utama**: Dalam pemrograman imperatif, program dibuat berdasarkan langkah-langkah urutan logis yang jelas, sementara dalam pemrograman deklaratif, tujuan utama lebih penting dibandingkan mekanisme untuk mencapainya.

## ⚙️ Mekanisme Kerja:
Pendekatan **imperative** dan **declarative** sebenarnya bisa saling melengkapi. Mari kita bahas bagaimana kedua paradigma ini bekerja dalam satu kesatuan, secara detail dan spesifik, menggunakan konteks pembuktian sebelumnya.

### Mekanisme Kerja Imperative **dan** Declarative Programming secara Bersama

Dalam sistem berbasis **C++ OOP** seperti dalam pengembangan **IoT**, mekanisme kerja **imperative** dan **declarative** berjalan beriringan:

1. **Imperative Programming**:
   - **Imperative** adalah dasar dari banyak bahasa pemrograman, termasuk C++. Dalam paradigma ini, **instruksi-instruksi spesifik** diberikan kepada mesin untuk memodifikasi state sistem secara langsung dan eksplisit.
   - **Imperative programming** masih digunakan di level yang lebih rendah, di mana kita mengontrol cara operasi tertentu dilakukan dalam kelas OOP atau metode OOP. Dengan kata lain, setiap metode dalam OOP (seperti `read()` dan `display()` di kelas **TemperatureSensor**) adalah kumpulan perintah imperatif yang dijalankan dalam urutan tertentu.

   **Contoh dalam OOP C++:**
   Dalam metode `read()` dari kelas `TemperatureSensor`, kita melihat alur imperatif yang jelas—kita memerintahkan sistem untuk **mengubah state sensor** secara langsung:
   ```cpp
   void read() override {
       temperature = 25.0 + (rand() % 10);  // Ini instruksi imperatif
   }
   ```

   Di sini, kita memerintahkan program untuk melakukan operasi tertentu (mengubah nilai `temperature`), yang merupakan gaya pemrograman **imperative**. Ini adalah logika imperative yang berada di dalam konteks **OOP** (declarative).

2. **Declarative Programming**:
   - **Declarative programming** berfokus pada *apa yang harus dilakukan*, bukan *bagaimana melakukannya*. Dalam OOP, kita mengaplikasikan prinsip deklaratif dengan mendefinisikan **kelas dan objek** yang menangani tugas-tugas tertentu tanpa harus memikirkan secara mendetail langkah-langkahnya.
   - Dalam C++ OOP untuk IoT, **abstraksi, inheritance, dan polymorphism** adalah aspek deklaratif yang menyembunyikan detail pelaksanaan imperatif di balik antarmuka yang mudah digunakan.

   **Contoh dalam OOP C++:**
   Kita tidak peduli **bagaimana** sensor membaca suhu atau bagaimana **state** diubah dalam metode `read()`. Kita hanya mendeklarasikan bahwa objek `TemperatureSensor` memiliki kemampuan untuk membaca suhu:
   ```cpp
   tempSensor.read();  // Instruksi deklaratif
   tempSensor.display();  // Instruksi deklaratif
   ```
   Pada kode di atas, kita fokus pada apa yang harus dilakukan (membaca dan menampilkan data), tanpa perlu memikirkan bagaimana cara kerja internalnya. Inilah elemen deklaratif dari OOP.

### Kerjasama **Imperative** dan **Declarative** dalam Pengembangan IoT

#### 1. **Imperative dalam Declarative (OOP)**
Di dalam paradigma **OOP**, yang bersifat **declarative**, ada banyak elemen **imperative** yang berjalan di belakang layar. Misalnya, ketika kita memanggil `tempSensor.read()`, ada perintah imperatif yang terjadi di dalam metode tersebut untuk membaca nilai suhu dari sensor dan memperbarui state objek. Namun, dari perspektif developer, kita cukup memanggil metode ini tanpa harus memikirkan logika di baliknya.

Ini menunjukkan bahwa **imperative programming** bekerja di tingkat **metode atau fungsi** di dalam objek, sementara **declarative programming** ada di level desain sistem secara keseluruhan, di mana kita hanya mendefinisikan **apa** yang harus dilakukan oleh objek.

#### 2. **Declarative dalam Pengelolaan Objek dan Modularitas**
Dengan menggunakan **kelas dan objek**, kita bekerja dalam paradigma **declarative**: kita mendeklarasikan perilaku objek melalui definisi kelas tanpa harus merinci setiap langkah dalam penggunaan objek. Misalnya, dengan mendeklarasikan kelas sensor sebagai berikut:
```cpp
class Sensor {
protected:
    int id;
    float temperature;

public:
    Sensor(int id) : id(id), temperature(0.0) {}
    virtual void read() = 0;  // Metode deklaratif (abstrak)
    void display() {
        std::cout << "Sensor ID: " << id << ", Temperature: " << temperature << " C" << std::endl;
    }
};
```
Di sini, **declarative programming** mendefinisikan struktur, dan setiap sensor dapat menggunakan metode ini tanpa perubahan internal yang signifikan. Namun, di dalam metode `read()`, logika imperatif yang menjalankan operasi langsung pada state (`temperature`) tetap berlangsung.

#### 3. **Polymorphism sebagai Deklarasi Tindakan Berbeda**
Polimorfisme memungkinkan kita untuk memanggil metode yang berbeda pada objek yang berbeda secara deklaratif, meskipun objek tersebut berasal dari kelas yang sama. Ini adalah contoh lain dari deklaratif dan imperatif yang bekerja bersama.

```cpp
Sensor* sensor = new TemperatureSensor(1);
sensor->read();   // Secara deklaratif, kita memanggil metode ini tanpa tahu implementasinya
sensor->display();
```
Dalam panggilan `sensor->read()`, implementasi imperatif untuk `TemperatureSensor` dijalankan di dalam metode `read()`, tetapi di level yang lebih tinggi, kita tidak perlu tahu detailnya. Kita cukup mendeklarasikan bahwa objek `sensor` harus membaca data.

### Ringkasan Hubungan Keduanya:
1. **Imperative Programming**:
   - **Level Implementasi**: Digunakan di level implementasi metode. Di dalam objek, metode yang ada mengandung instruksi imperatif yang mengatur alur dan perubahan state secara eksplisit.
   - **State Management**: Memanipulasi state internal objek secara langsung melalui instruksi yang jelas (seperti memperbarui suhu sensor).

2. **Declarative Programming**:
   - **Level Desain**: Digunakan di level desain sistem secara keseluruhan. Pendekatan deklaratif digunakan untuk mendefinisikan bagaimana objek berperilaku dan bagaimana mereka saling berinteraksi tanpa harus memikirkan detail implementasi.
   - **Abstraksi**: Programmer mendefinisikan antarmuka dan perilaku umum dari objek, dan objek mengurus detail operasionalnya secara internal (seperti abstraksi pada OOP).

### Kesimpulan:
- **Imperative programming** bekerja di **tingkat implementasi fungsi/metode** di mana kita memberikan perintah eksplisit tentang apa yang harus dilakukan. Dalam sistem IoT berbasis OOP di C++, imperatif diperlukan untuk melakukan tugas-tugas rendah seperti pengambilan data dari sensor atau pengaturan state.
  
- **Declarative programming** bekerja di **tingkat struktur program** di mana kita mendeklarasikan objek, kelas, dan interaksi antar objek tanpa mendefinisikan secara eksplisit bagaimana langkah-langkah operasional harus dilakukan. Hal ini memungkinkan abstraksi, modularitas, dan kemudahan ekspansi dalam sistem IoT.

Dengan menggabungkan keduanya, kita mendapatkan fleksibilitas tinggi dalam pengembangan IoT: **imperative** untuk kontrol rendah, dan **declarative** untuk desain sistem yang scalable dan maintainable.

### **📝Tabel Kemampuan Declarative Programming**

Berikut adalah dua tabel yang menjelaskan kemampuan masing-masing dari **Declarative** dan **Imperative Programming**. Masing-masing tabel berisi aspek-aspek penting dari paradigma tersebut serta kemampuan yang dimilikinya.

| **Aspek**                         | **Kemampuan Declarative Programming**                                                                                                                                         |
|------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Fokus pada *Apa* yang Dicapai**  | Deklaratif berfokus pada hasil akhir yang diinginkan tanpa merinci langkah-langkah operasional atau implementasi detail.                                                      |
| **Abstraksi**                      | Memberikan tingkat abstraksi yang tinggi, di mana pengguna mendefinisikan apa yang harus dilakukan, dan detail operasional ditangani oleh sistem atau lapisan bawahnya.        |
| **Pemrograman Fungsional**         | Mampu bekerja dalam gaya pemrograman fungsional, yang lebih menekankan pada penggunaan fungsi tanpa state yang berubah dan menghindari efek samping.                         |
| **Query dan Konfigurasi**          | Cocok untuk menulis query (misalnya SQL, SPARQL) atau konfigurasi (misalnya YAML, JSON) di mana kita mendefinisikan spesifikasi tanpa peduli dengan cara eksekusi.           |
| **Maintainability (Pemeliharaan)** | Membantu dalam membuat kode yang lebih mudah dipelihara karena logika dipisahkan dari detail implementasi, meminimalkan efek perubahan pada bagian tertentu dari sistem.      |
| **Reusability (Penggunaan Ulang)** | Memungkinkan penggunaan kembali komponen atau modul lebih mudah karena modul dapat digunakan tanpa memerlukan pemahaman mendalam tentang cara kerjanya.                      |
| **Modularity (Modularitas)**       | Mendorong pemrograman modular, di mana komponen-komponen dideklarasikan secara independen dan dapat diintegrasikan dengan mudah ke dalam sistem yang lebih besar.             |
| **Parallelism (Paralelisme)**      | Memungkinkan pelaksanaan paralel yang lebih mudah dicapai, karena kita hanya mendeklarasikan apa yang ingin dicapai tanpa perlu memikirkan alur eksekusi yang mendasarinya.  |
| **Interoperability**               | Declarative programming seringkali lebih mudah diintegrasikan dengan sistem atau platform yang berbeda, karena fokusnya pada deskripsi tinggi daripada implementasi spesifik. |

---

### **📝Tabel Kemampuan Imperative Programming**

| **Aspek**                         | **Kemampuan Imperative Programming**                                                                                                                                   |
|------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Fokus pada *Bagaimana* Melakukan**| Imperatif berfokus pada bagaimana sesuatu dicapai dengan memberikan langkah-langkah eksplisit dan kontrol penuh atas alur eksekusi.                                    |
| **Kontrol Eksekusi yang Detail**   | Memberikan kontrol detail atas alur program, memungkinkan programmer untuk menentukan langkah-langkah logis yang spesifik, termasuk penggunaan loop, kondisi, dan perulangan. |
| **State Management**               | Mengizinkan pengelolaan state secara eksplisit dan langsung oleh programmer, termasuk modifikasi variabel global atau lokal selama runtime.                             |
| **Mutability (Perubahan)**         | Dapat mengubah state dan variabel secara dinamis selama eksekusi, memberikan fleksibilitas dalam memanipulasi data dan kontrol selama alur program.                     |
| **Prosedural dan Looping**         | Memungkinkan penggunaan struktur kontrol prosedural seperti `for`, `while`, `if`, dan `switch`, memberikan fleksibilitas dalam pengelolaan alur eksekusi program.       |
| **Efisiensi Eksekusi**             | Bisa lebih efisien dalam hal performa karena memberikan kontrol penuh atas setiap langkah eksekusi, terutama untuk operasi yang membutuhkan kinerja tinggi.             |
| **Debugging**                      | Memberikan kemudahan dalam debugging karena programmer bisa melacak setiap perubahan state atau variabel selama eksekusi program.                                       |
| **Resource Management**            | Dalam imperative programming, kita bisa mengelola sumber daya (misalnya memori dan proses) secara manual, yang berguna dalam aplikasi low-level seperti sistem embedded atau IoT. |
| **Interactivity**                  | Membolehkan implementasi program interaktif yang membutuhkan feedback instan dan real-time, karena alur program dapat dikontrol secara ketat sesuai dengan masukan pengguna atau sensor. |
| **Explicitness (Kejelasan Alur)**  | Programmer harus secara eksplisit mendefinisikan setiap langkah, membuat alur program lebih terlihat jelas, meskipun bisa menjadi lebih kompleks seiring berkembangnya sistem. |

---

### Penjelasan Tabel

#### **❕Declarative Programming**:
- Paradigma deklaratif menawarkan **abstraksi** dan **modularitas** tinggi. Programmer tidak perlu peduli tentang cara spesifik bagaimana operasi dilakukan, tetapi lebih kepada **apa yang diinginkan**. Kemampuan ini berguna untuk pembuatan sistem yang scalable, lebih mudah dipelihara, dan efisien dalam pengembangan sistem kompleks seperti IoT.
  
#### **❗Imperative Programming**:
- Paradigma imperatif menawarkan **kontrol penuh** atas alur eksekusi program dan pengelolaan **state** secara manual. Hal ini cocok untuk situasi di mana **kinerja** dan **pengelolaan sumber daya** sangat penting, seperti pada aplikasi low-level atau sistem yang membutuhkan optimasi tinggi, misalnya dalam IoT atau pengembangan sistem embedded.

## ⚖️ Kasus Dilematis:
- **Dilema**: Pendekatan deklaratif lebih mudah dibaca dan dimodifikasi, namun pada sistem dengan keterbatasan memori seperti Arduino, kode deklaratif bisa jadi memakan lebih banyak sumber daya daripada pendekatan imperative yang lebih langsung dan efisien. Apakah kemudahan membaca dan memodifikasi sebanding dengan biaya performa pada perangkat keras yang terbatas?

---

# 3️⃣ **Penggunaan C++ untuk Pengembangan IoT pada Arduino**

## 🔍 Penjelasan dan Fakta/Data:
- **Problem signifikan**: Pengembangan perangkat IoT memerlukan pengelolaan perangkat keras yang efisien dan efektif. Pengembang harus mengintegrasikan berbagai sensor, aktuator, dan modul komunikasi dengan sumber daya terbatas.
- **Kekompleksan**: Dalam skala besar, koordinasi antar perangkat IoT menjadi rumit. Bahasa seperti C++ menyediakan fitur seperti pointer dan control memory yang mempermudah pengelolaan perangkat keras dan pengolahan data.
- **Relevansi dengan industri**: Dalam banyak proyek IoT skala besar, C++ digunakan karena kemampuannya yang efisien dalam mengelola perangkat keras secara langsung. Ini sangat penting di industri seperti **otomotif**, **smart home**, dan **kesehatan**, di mana pengelolaan perangkat keras yang tepat adalah kunci.

## 📚 Definisi, Konsep, Prinsip Utama:
- **C++**: Bahasa pemrograman tingkat menengah yang memberikan kontrol penuh terhadap perangkat keras, dengan dukungan untuk OOP.
- **Prinsip utama**: Kemampuan untuk melakukan manajemen memori secara manual, pengendalian perangkat secara langsung, dan penggunaan paradigma OOP yang memungkinkan modularitas dan perluasan kode.

## ⚙️ Mekanisme Kerja:
- C++ pada Arduino memungkinkan pengguna untuk mengendalikan perangkat keras melalui **fungsi built-in** seperti `digitalWrite()`, `analogRead()`, dan juga melalui **class** yang lebih modular.
- **Pointer** dan **direct memory management** dapat digunakan untuk mengontrol lebih efektif perangkat dengan keterbatasan memori, seperti mikrokontroler.

## ⚖️ Kasus Dilematis:
- **Dilema**: Menggunakan fitur lanjutan C++ seperti dynamic memory allocation dapat menyebabkan **fragmentasi memori** dan mempengaruhi stabilitas pada perangkat dengan sumber daya terbatas seperti Arduino. Apakah penggunaan bahasa yang lebih rendah seperti C atau Assembly lebih cocok untuk aplikasi yang sangat teroptimasi?
