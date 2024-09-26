
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
- Pada Arduino, class mewakili perangkat keras seperti LED, sensor, atau aktuator.
- Ketika sebuah object dibuat, fungsi-fungsi seperti `on()`, `off()`, atau `read()` mengendalikan perangkat keras terkait tanpa pengguna harus mengetahui detil internalnya.
- Misalnya, class `LED` dapat mengontrol LED di berbagai pin tanpa perlu menulis ulang kode untuk setiap LED yang berbeda.

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
