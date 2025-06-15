# Laporan Proyek Machine Learning - Muhammad Farhan

## Project Overview

Dalam era digital saat ini, platform pembelajaran daring seperti Coursera, edX, dan Udemy telah menjadi sumber utama bagi individu yang ingin memperdalam pengetahuan dan keterampilan mereka. Seiring dengan meningkatnya jumlah kursus yang tersedia, banyak pengguna merasa kesulitan untuk memilih kursus yang paling sesuai dengan minat, tingkat keahlian, dan tujuan belajar mereka. 

Salah satu tantangan utama yang dihadapi oleh platform pembelajaran daring adalah memberikan rekomendasi yang tepat dan relevan kepada penggunanya. Rekomendasi yang baik dapat meningkatkan pengalaman pengguna, mempercepat proses pembelajaran, dan membantu pengguna mencapai tujuan pendidikan mereka. Oleh karena itu, sistem rekomendasi yang efektif sangat penting untuk platform pembelajaran daring.

Proyek ini bertujuan untuk mengembangkan **Sistem Rekomendasi Kursus** yang memanfaatkan data tentang kursus, termasuk nama kursus, tingkat kesulitan, rating, deskripsi kursus, dan keterampilan yang diajarkan. Dengan menggunakan pendekatan **Content-based Filtering**, sistem ini akan memberikan rekomendasi kursus yang relevan bagi pengguna berdasarkan kemiripan deskripsi kursus dan keterampilan yang ingin mereka pelajari.

Tujuan utama dari proyek ini adalah untuk membantu pengguna memilih kursus yang sesuai dengan minat dan kebutuhan mereka, sehingga mereka dapat meningkatkan keterampilan mereka secara lebih efisien. Sistem rekomendasi ini akan menggunakan dataset yang terdiri dari informasi kursus yang ditawarkan oleh berbagai universitas dan institusi melalui platform Coursera.

## Business Understanding

### Problem Statements

Seiring dengan berkembangnya platform pembelajaran daring, terutama Coursera, pengguna sering kali merasa kesulitan dalam memilih kursus yang sesuai dengan kebutuhan, minat, dan tujuan pembelajaran mereka. Dengan banyaknya kursus yang tersedia, proses pencarian kursus yang tepat menjadi semakin rumit. Hal ini disebabkan oleh beberapa faktor, seperti:

1. **Terlalu Banyak Pilihan**: Platform pembelajaran daring memiliki ratusan bahkan ribuan kursus yang ditawarkan, dan tidak semua kursus relevan dengan kebutuhan pengguna.
2. **Kurangnya Personalisasi**: Rekomendasi yang diberikan sering kali tidak cukup dipersonalisasi untuk memenuhi kebutuhan spesifik pengguna, sehingga pengguna kesulitan dalam menemukan kursus yang sesuai dengan tingkat keahlian atau tujuan belajar mereka.
3. **Deskripsi Kursus yang Umum**: Deskripsi kursus yang terlalu umum atau tidak cukup menggambarkan dengan detail isi dan manfaat kursus bisa menyebabkan kebingungannya pengguna dalam memilih.

Masalah ini dapat menyebabkan pengalaman pengguna yang kurang optimal, meningkatkan tingkat pembatalan kursus, dan mengurangi keterlibatan pengguna di platform tersebut.

### Goals

Tujuan utama dari proyek ini adalah untuk mengembangkan sistem rekomendasi kursus yang efektif dan relevan berdasarkan data yang ada pada platform Coursera. Beberapa tujuan yang lebih spesifik meliputi:

1. **Meningkatkan Pengalaman Pengguna**: Sistem rekomendasi yang dibuat bertujuan untuk memberikan rekomendasi kursus yang lebih sesuai dengan kebutuhan dan minat individu pengguna, sehingga mereka lebih mudah menemukan kursus yang relevan.
2. **Personalisasi Rekomendasi**: Membangun sistem yang dapat memberikan rekomendasi yang dipersonalisasi berdasarkan deskripsi kursus dan keterampilan yang diajarkan, serta tingkat kesulitan kursus.
3. **Meningkatkan Keterlibatan Pengguna**: Dengan adanya rekomendasi yang relevan dan tepat, diharapkan pengguna akan lebih terlibat dalam platform, memperkaya pengetahuan mereka, dan menyelesaikan lebih banyak kursus.
4. **Efisiensi Proses Pemilihan Kursus**: Mengurangi waktu yang dibutuhkan pengguna untuk memilih kursus yang tepat, serta mengurangi kebingungan dan ketidakpastian dalam memilih materi yang akan dipelajari.

## Data Understanding

Dataset dapat diunduh di: [Coursera courses dataset 2021](https://www.Kaggle.Com/datasets/khusheekapoor/Coursera-courses-dataset-2021).

### Sample data

Tabel 1. Contoh Data pada Dataset
| Course Name                                               | University                               | Difficulty Level | Course Rating | Course URL                                          | Course Description                                 | Skills                                           |
|-----------------------------------------------------------|------------------------------------------|------------------|---------------|-----------------------------------------------------|----------------------------------------------------|--------------------------------------------------|
| Write A Feature Length Screenplay For Film Or ...          | Michigan State University                | Beginner         | 4.8           | [Course URL](https://www.coursera.org/learn/write-a-feature...)              | Write a Full Length Feature Film Script In th...   | Drama Comedy peering screenwriting film D...     |
| Business Strategy: Business Model Canvas Analy...          | Coursera Project Network                 | Beginner         | 4.8           | [Course URL](https://www.coursera.org/learn/canvas-analysis...)              | By the end of this guided project, you will be... | Finance business plan persona (user experien... |
| Silicon Thin Film Solar Cells                              | �cole Polytechnique                      | Advanced         | 4.1           | [Course URL](https://www.coursera.org/learn/silicon-thin-fi...)              | This course consists of a general presentation... | chemistry physics Solar Energy film lambda... |
| Finance for Managers                                        | IESE Business School                     | Intermediate     | 4.8           | [Course URL](https://www.coursera.org/learn/operational-fin...)              | When it comes to numbers, there is always more... | accounts receivable dupont analysis analysis... |
| Retrieve Data using Single-Table SQL Queries                | Coursera Project Network                 | Beginner         | 4.6           | [Course URL](https://www.coursera.org/learn/single-table-sq...)              | In this course you�ll learn how to effectively... | Data Analysis select (sql) database manageme... |
| Building Test Automation Framework using Selen...          | Coursera Project Network                 | Beginner         | 4.7           | [Course URL](https://www.coursera.org/learn/building-test-a...)              | Selenium is one of the most widely used functi... | maintenance test case test automation scree... |
| Doing Business in China Capstone                            | The Chinese University of Hong Kong       | Advanced         | 3.3           | [Course URL](https://www.coursera.org/learn/doing-business-...)              | Doing Business in China Capstone enables you t... | marketing plan Planning Marketing consumpti... |
| Programming Languages, Part A                               | University of Washington                 | Intermediate     | 4.9           | [Course URL](https://www.coursera.org/learn/programming-lan...)              | This course is an introduction to the basic co... | inference ml (programming language) higher-o... |
| The Roles and Responsibilities of Nonprofit Bo...          | The State University of New York          | Intermediate     | 4.3           | [Course URL](https://www.coursera.org/learn/nonprofit-gov-2)                | This course provides a more in-depth look at t... | Planning Peer Review fundraising strategic ... |
| Business Russian Communication. Part 3                     | Saint Petersburg State University         | Intermediate     | Not Calibrated | [Course URL](https://www.coursera.org/learn/business-russia...)              | Russian is considered to be one of the most di... | Russian market (economics) tax exemption co... |

### Variabel-variabel pada dataset Coursera Courses 2021 adalah sebagai berikut:

- Course Name: Nama kursus.
- University: Universitas yang menyelenggarakan kursus.
- Difficulty Level: Tingkat kesulitan kursus (Beginner, Intermediate, Advanced).
- Course Rating: Nilai atau peringkat kursus oleh pengguna.
- Course URL: Tautan URL kursus di Coursera.
- Course Description: Deskripsi singkat tentang kursus.
- Skills: Keterampilan atau topik yang terkait dengan kursus tersebut.

Tabel 2. Tipe Data Tiap Kolom pada Dataset
```sh
RangeIndex: 3522 entries, 0 to 3521
Data columns (total 7 columns):
 #   Column              Non-Null Count  Dtype 
---  ------              --------------  ----- 
 0   Course Name         3522 non-null   object
 1   University          3522 non-null   object
 2   Difficulty Level    3522 non-null   object
 3   Course Rating       3522 non-null   object
 4   Course URL          3522 non-null   object
 5   Course Description  3522 non-null   object
 6   Skills              3522 non-null   object
dtypes: object(7)
```
### Struktur dan Tipe Data

Langkah pertama adalah memuat data dan memeriksa informasi dasarnya menggunakan fungsi `df.info()`.

Berdasarkan hasil analisis, diketahui bahwa:
* Dataset terdiri dari **3.522 baris** data dan **7 kolom**.
* Tidak ditemukan adanya nilai yang hilang (*missing values*) pada setiap kolom.
* Seluruh 7 kolom memiliki tipe data `object`, yang menandakan bahwa kolom-kolom numerik seperti `Course Rating` perlu diubah tipenya pada tahap *Data Preparation*.

### Statistik Deskriptif

Untuk mendapatkan wawasan lebih lanjut, dilakukan analisis statistik deskriptif menggunakan fungsi `df.describe()`. Karena semua kolom bersifat kategorikal (tipe `object`), analisis ini memberikan informasi mengenai jumlah data, nilai unik, nilai yang paling sering muncul (*top*), dan frekuensinya (*freq*).

Berikut adalah ringkasan statistik untuk beberapa kolom utama:

| Atribut            | Jumlah Data | Nilai Unik | Nilai Paling Sering Muncul                                | Frekuensi |
| :----------------- | :---------: | :--------: | :-------------------------------------------------------- | :-------: |
| **Course Name** | 3.522       | 3.416      | `Google Cloud Platform Fundamentals: Core Infrastructure` | 8         |
| **University** | 3.522       | 184        | `Coursera Project Network`                                | 562       |
| **Difficulty Level**| 3.522       | 5          | `Beginner`                                                | 1.444     |
| **Course Rating** | 3.522       | 31         | `4.7`                                                     | 740       |

Dari tabel di atas, dapat disimpulkan beberapa poin penting:
* Terdapat **3.416** nama kursus yang unik dari total 3.522 data, yang menunjukkan adanya beberapa kursus duplikat.
* **Coursera Project Network** adalah penyedia kursus terbanyak dalam dataset ini dengan total **562** kursus.
* Sebagian besar kursus ditujukan untuk level **Beginner**, yaitu sebanyak **1.444** kursus.
* Rating yang paling umum diberikan adalah **4.7**, yang muncul pada **740** kursus.

## Data Preparation

Tahap *Data Preparation* adalah proses transformasi data mentah menjadi format yang bersih, terstruktur, dan siap untuk digunakan dalam pemodelan sistem rekomendasi. Berdasarkan hasil dari tahap *Data Understanding*, beberapa langkah pengolahan data dilakukan secara berurutan.

Proses persiapan data yang dilakukan adalah sebagai berikut:

1.  **Pengecekan Nilai Hilang (*Missing Value Check*)**
    Langkah pertama adalah memastikan tidak ada data yang hilang dalam dataset. Berdasarkan hasil pengecekan menggunakan fungsi `df.isnull().sum()`, dikonfirmasi bahwa tidak ada nilai yang hilang di setiap kolom.

2.  **Pemilihan Fitur (*Feature Selection*)**
    Untuk membangun model *content-based filtering*, tidak semua kolom dari dataset asli diperlukan. Hanya fitur-fitur yang paling relevan dengan konten kursus yang dipilih, yaitu `Course Name`, `Course Rating`, `Course Description`, dan `Skills`. Kolom-kolom ini kemudian disimpan dalam sebuah DataFrame baru bernama `data_courses`.

3.  **Penggantian Nama Kolom (*Column Renaming*)**
    Untuk kemudahan akses dan konsistensi dalam kode, nama kolom diubah menjadi format yang lebih singkat. Sebagai contoh, `Course Name` diubah menjadi `courseName` dan `Course Rating` menjadi `rating`.

4.  **Penggabungan Data (*Data Merging*)**
    Sesuai dengan alur notebook, sebuah operasi `merge` dilakukan pada DataFrame `data_courses` dengan subset dari dirinya sendiri (`data_courses[['courseName', 'description']]`) berdasarkan kolom `courseName`. Langkah ini menghasilkan duplikasi pada kolom deskripsi, yang kemudian menjadi `description_x` dan `description_y`.

5.  **Pembersihan Data Rating (*Rating Data Cleaning*)**
    Kolom `rating` teridentifikasi memiliki tipe data `object` dan mengandung nilai non-numerik seperti `'Not Calibrated'`. Baris data yang mengandung nilai tidak valid ini dihapus dari dataset untuk menjaga kualitas data.

6.  **Konversi Tipe Data (*Data Type Conversion*)**
    Setelah dibersihkan, tipe data kolom `rating` diubah dari `object` menjadi tipe data numerik (float) menggunakan fungsi `pd.to_numeric`. Langkah ini krusial agar nilai rating dapat digunakan dalam perhitungan matematis.

7.  **Reset Indeks (*Index Resetting*)**
    Setelah menghapus beberapa baris pada langkah sebelumnya, indeks DataFrame diatur ulang menggunakan `reset_index(drop=True)` untuk memastikan urutan indeks kembali normal dan menghindari potensi kesalahan pada proses selanjutnya.

Setelah melalui semua tahapan di atas, dataset `data_courses` kini berisi **3.740 baris** data yang bersih dan siap untuk digunakan pada tahap pemodelan.

### Ekstraksi Fitur dengan TF-IDF

Langkah pertama dalam pemodelan adalah mengubah data teks (judul kursus) menjadi representasi numerik yang dapat diolah oleh mesin. Untuk tujuan ini, teknik **TF-IDF (Term Frequency-Inverse Document Frequency)** digunakan. TF-IDF bekerja dengan mengukur seberapa penting sebuah kata dalam sebuah dokumen (dalam hal ini, judul kursus) relatif terhadap keseluruhan koleksi dokumen (seluruh judul kursus).

- **Term Frequency (TF)**: Menghitung frekuensi kemunculan sebuah kata dalam satu judul kursus.
- **Inverse Document Frequency (IDF)**: Mengukur seberapa unik atau langka sebuah kata di seluruh dataset. Kata-kata umum seperti "dan" atau "pengenalan" akan memiliki skor IDF yang rendah, sementara kata-kata yang lebih spesifik akan memiliki skor yang lebih tinggi.

Proses ini dilakukan pada kolom `courseName` dan menghasilkan sebuah matriks TF-IDF dengan dimensi **(3740, 3628)**. Ini berarti model merepresentasikan 3.740 kursus dengan 3.628 fitur kata unik.

### Perhitungan Kemiripan Kursus

Setelah setiap kursus direpresentasikan sebagai vektor numerik TF-IDF, langkah selanjutnya adalah menghitung tingkat kemiripan antara setiap pasang kursus.

## Modeling

Pada proyek ini menerapkan tipe model, yaitu *Content-Based Filtering*.

### *Content-Based Filtering*
*Content-Based Filtering* adalah pendekatan dalam sistem rekomendasi yang mengandalkan analisis konten dari item yang direkomendasikan. 

Dalam konteks sistem rekomendasi kursus Coursera, pendekatan ini akan menganalisis fitur-fitur konten dari kursus, seperti deskripsi kursus, topik, rating, atau keterampilan yang terkait, untuk memberikan rekomendasi yang relevan kepada pengguna.

Kelebihan *Content-Based Filtering*:
1. Personalisasi: Pendekatan *Content-Based Filtering* memungkinkan personalisasi yang tinggi, karena rekomendasi didasarkan pada preferensi pengguna yang diungkapkan melalui analisis konten kursus.
2. Tidak tergantung pada data pengguna lain: Pendekatan ini tidak memerlukan informasi tentang preferensi pengguna lain, sehingga tidak bergantung pada data kolaboratif atau historis dari pengguna lainnya.
3. Memperhitungkan kepentingan unik pengguna: Pendekatan ini memperhitungkan preferensi pengguna yang spesifik dan tidak terpengaruh oleh tren atau preferensi umum.

Kekurangan *Content-Based Filtering*:
1. Terbatas pada fitur yang diamati: Pendekatan ini terbatas pada fitur-fitur yang diamati dan dianalisis dalam konten kursus. Rekomendasi mungkin kurang beragam jika tidak ada fitur yang signifikan dalam analisis konten yang dapat membedakan kursus secara signifikan.
2. Tidak memperhitungkan preferensi baru: Pendekatan ini tidak secara otomatis menyesuaikan dengan perubahan preferensi pengguna. Jika preferensi pengguna berubah atau berkembang, rekomendasi mungkin tetap berfokus pada preferensi yang lebih lama.

Teknik Perhitungan Similarity:
1. *Cosine Similarity*: *Cosine Similarity* mengukur kesamaan antara dua vektor dengan menghitung kosinus sudut antara vektor-vektor tersebut. Dalam konteks *Content-Based Filtering*, *Cosine Similarity* digunakan untuk mengukur kesamaan antara vektor representasi fitur kursus berdasarkan deskripsi, topik, atau keterampilan. Nilai *Cosine Similarity* berkisar antara -1 hingga 1, di mana nilai 1 menunjukkan kesamaan yang sempurna dan nilai -1 menunjukkan perbedaan yang sempurna.

2. **Euclidean Distance**: **Euclidean Distance** mengukur jarak antara dua titik dalam ruang Euclidean. Dalam konteks *Content-Based Filtering*, **Euclidean Distance** digunakan untuk mengukur jarak antara vektor representasi fitur kursus. Semakin kecil nilai **Euclidean Distance**, semakin mirip kedua kursus dalam hal fitur-fitur yang diamati.

### Tahapan yang dilakukan dengan pendekatan *Content-Based Filtering*
Selama pendekatan ini, proses modeling dilakukan berdasar urutan sebagai berikut ini:

1. *Cosine Similarity*: Setelah mendapatkan vektor fitur menggunakan *TF-IDF Vectorizer*, tahap selanjutnya adalah menghitung kesamaan antara kursus menggunakan metode *Cosine Similarity*. *Cosine Similarity* mengukur kesamaan arah antara dua vektor dalam ruang vektor. Pada konteks Content-Based Filtering, *Cosine Similarity* digunakan untuk mengukur kesamaan antara vektor fitur kursus berdasarkan deskripsi, topik, atau keterampilan yang terkait. Semakin tinggi nilai *Cosine Similarity*, semakin mirip kedua kursus dalam hal fitur-fitur yang diamati.

2. *Euclidean Distance*: Selain *Cosine Similarity*, tahap Content-Based Filtering juga dapat menggunakan *Euclidean Distance* untuk mengukur jarak antara vektor fitur kursus. *Euclidean Distance* menghitung jarak antara dua titik dalam ruang Euclidean. Dalam konteks *Content-Based Filtering*, *Euclidean Distance* digunakan untuk mengukur jarak antara vektor fitur kursus. Semakin kecil nilai *Euclidean Distance*, semakin mirip kedua kursus dalam hal fitur-fitur yang diamati.

### Hasil Rekomendasi Model
Sebagai contoh, model diuji dengan memberikan input kursus **'Software Security'**. Dengan menggunakan *Cosine Similarity*, model berhasil memberikan 10 rekomendasi kursus teratas yang relevan.

Berikut adalah 5 dari 10 rekomendasi teratas yang dihasilkan:

| courseName | rating (Similarity Score) |
| :--- | :--- |
| Cloud Systems Software | 1.000000 |
| Software Architecture | 0.481082 |
| Agile Software Development | 0.475195 |
| Introduction to Software Testing | 0.427880 |
| Software Design as an Element of the Software Development Lifecycle | 0.422111 |

Hasil ini menunjukkan bahwa model mampu menemukan kursus lain yang terkait dengan "Software", "Security", dan "Development", yang membuktikan bahwa pendekatan *Content-Based Filtering* ini bekerja dengan baik sesuai dengan data yang ada.

## Evaluation

Tahap evaluasi bertujuan untuk mengukur performa dan kualitas dari model sistem rekomendasi yang telah dibangun. Pengujian ini penting untuk memastikan bahwa rekomendasi yang diberikan tidak hanya mirip berdasarkan judul, tetapi juga relevan dari segi konten atau keahlian yang ditawarkan.

### 5.1. Metrik Evaluasi: Precision@k

Metrik yang digunakan untuk evaluasi adalah **Precision@k**. Metrik ini mengukur proporsi item yang relevan dari total `k` item teratas yang direkomendasikan. Metrik ini sangat cocok untuk sistem rekomendasi karena pengguna umumnya hanya memperhatikan beberapa rekomendasi teratas.

Rumus Precision@k adalah:

$$ \text{Precision@k} = \frac{\text{Jumlah Rekomendasi Relevan dalam Top-k}}{k} $$

Dalam proyek ini, nilai `k` yang digunakan adalah 10, sehingga kita mengukur **Precision@10**.

### 5.2. Definisi Relevansi

Karena tidak ada data umpan balik eksplisit dari pengguna, relevansi didefinisikan berdasarkan fitur yang tersedia dalam dataset. Model ini dibangun berdasarkan kemiripan `courseName`. Oleh karena itu, kolom `skills` digunakan sebagai "kunci jawaban" atau *ground truth* untuk menentukan apakah sebuah rekomendasi relevan.

Definisi relevansi yang digunakan adalah sebagai berikut:
> Sebuah kursus yang direkomendasikan dianggap **"relevan"** jika kursus tersebut memiliki **setidaknya satu skill yang sama** dengan kursus input yang dicari.

Sebuah fungsi kustom bernama `evaluate_model_precision` dibuat untuk mengotomatiskan proses ini, dengan cara membandingkan set *skills* dari kursus input dengan setiap set *skills* dari kursus yang direkomendasikan.

### 5.3. Hasil dan Analisis

Model dievaluasi dengan menggunakan kursus **'Software Security'** sebagai input untuk mendapatkan 10 rekomendasi teratas dari model *Cosine Similarity*.

Setelah rekomendasi didapatkan, skor presisi dihitung menggunakan fungsi `evaluate_model_precision`. Hasil dari evaluasi tersebut adalah sebagai berikut:

- **Precision@10 Score: 1.00**

Skor presisi 1.00 menunjukkan bahwa **100%** dari 10 kursus yang direkomendasikan untuk 'Software Security' memiliki setidaknya satu skill yang tumpang tindih dengan kursus input. Berdasarkan metrik dan definisi relevansi yang telah ditetapkan, hasil ini menandakan bahwa model memiliki performa yang sangat baik dalam memberikan rekomendasi yang relevan secara konten.
