
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
- **Imperative**: Pemrograman imperative mengontrol alur program dengan memberikan instruksi spesifik (misalnya, menyalakan atau mematikan LED dengan `digitalWrite()`).
- **Declarative**: Dengan pendekatan deklaratif, kamu cukup menggambarkan tujuan (misalnya, “nyalakan LED”) tanpa harus mengkhawatirkan detail implementasi.
- Di Arduino, implementasi deklaratif dapat dilakukan dengan fungsi atau lambda, sedangkan imperative menggunakan instruksi langsung untuk setiap tindakan.

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
