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
## Data Preparation
Berikut adalah tahapan-tahapan yang dilakukan:

1. Mengatasi missing value: Melakukan penanganan terhadap nilai yang hilang pada dataset, seperti menghapus baris atau mengisi nilai yang hilang dengan metode tertentu, seperti mean atau median.
2. Mengambil kolom yang diperlukan dan merubah nama kolom: Memilih kolom-kolom yang relevan untuk analisis dan memberikan nama baru jika diperlukan.
3. Exclude rating yang ingin dihapus dari dataset: Menghapus data dengan rating tertentu yang ingin dikecualikan dari analisis.
4. Reset index dataframe untuk menghindari error: Mereset indeks dataframe setelah melakukan operasi penghapusan atau pemrosesan data agar indeks kembali terurut secara berurutan.
5. Convert "rating" column to int64 data type: Mengubah tipe data kolom "rating" menjadi tipe data int64 untuk mempermudah analisis numerik.
6. Mendapatkan list unik kolom kursus dan keahlian: Mengidentifikasi dan mendapatkan daftar unik kolom "courseName" dan "skills" dalam dataset.


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

1. *TF-IDF Vectorizer*: Tahap ini melibatkan penggunaan TF-IDF (Term Frequency-Inverse Document Frequency) Vectorizer untuk mengubah teks pada deskripsi kursus menjadi representasi numerik. TF-IDF mengukur pentingnya suatu kata dalam dokumen berdasarkan frekuensi kemunculan kata tersebut dalam dokumen dan inversi frekuensi kemunculan kata tersebut dalam seluruh koleksi dokumen. *TF-IDF Vectorizer* menghasilkan vektor fitur yang merepresentasikan konten kursus.

2. *Cosine Similarity*: Setelah mendapatkan vektor fitur menggunakan *TF-IDF Vectorizer*, tahap selanjutnya adalah menghitung kesamaan antara kursus menggunakan metode *Cosine Similarity*. *Cosine Similarity* mengukur kesamaan arah antara dua vektor dalam ruang vektor. Pada konteks Content-Based Filtering, *Cosine Similarity* digunakan untuk mengukur kesamaan antara vektor fitur kursus berdasarkan deskripsi, topik, atau keterampilan yang terkait. Semakin tinggi nilai *Cosine Similarity*, semakin mirip kedua kursus dalam hal fitur-fitur yang diamati.

3. *Euclidean Distance*: Selain *Cosine Similarity*, tahap Content-Based Filtering juga dapat menggunakan *Euclidean Distance* untuk mengukur jarak antara vektor fitur kursus. *Euclidean Distance* menghitung jarak antara dua titik dalam ruang Euclidean. Dalam konteks *Content-Based Filtering*, *Euclidean Distance* digunakan untuk mengukur jarak antara vektor fitur kursus. Semakin kecil nilai *Euclidean Distance*, semakin mirip kedua kursus dalam hal fitur-fitur yang diamati.

## Evaluation

# Evaluation

## Metrik Evaluasi yang Digunakan

Untuk mengevaluasi kinerja sistem rekomendasi yang dikembangkan dalam proyek ini, kami menggunakan **Precision** sebagai metrik utama. Precision adalah salah satu metrik yang paling sering digunakan dalam sistem rekomendasi untuk mengukur seberapa relevan rekomendasi yang diberikan oleh sistem.

### Definisi Precision
Precision dihitung dengan rumus:
```sh
Precision = TP / (TP + FP)
```
Dimana:
- **Jumlah rekomendasi relevan** adalah jumlah kursus yang relevan dan sesuai dengan preferensi pengguna dari semua kursus yang direkomendasikan.
- **Jumlah rekomendasi yang diberikan** adalah total kursus yang direkomendasikan oleh sistem.

Precision memberikan gambaran tentang kualitas rekomendasi yang diberikan oleh sistem, dengan nilai lebih tinggi menunjukkan bahwa sistem memberikan lebih banyak rekomendasi yang sesuai dengan kebutuhan atau minat pengguna.

## Hasil Proyek Berdasarkan Metrik Evaluasi

Setelah melakukan evaluasi sistem rekomendasi dengan menggunakan metrik **Precision**, hasil yang didapatkan adalah **precision = 1**, yang menunjukkan bahwa **100%** dari kursus yang direkomendasikan oleh sistem adalah kursus yang relevan atau sesuai dengan kriteria yang telah ditentukan.

### Penjelasan Hasil:
- **Precision 1** menunjukkan bahwa **semua kursus yang direkomendasikan oleh sistem relevan** dengan preferensi atau kebutuhan pengguna. Dalam hal ini, setiap kursus yang direkomendasikan sesuai dengan kriteria relevansi yang telah ditetapkan, seperti kursus dengan rating tinggi atau kursus yang telah dipilih oleh pengguna sebelumnya.
  
  Sebagai contoh, jika sistem merekomendasikan 5 kursus dan semua 5 kursus tersebut berada dalam daftar **relevant_courses**, maka precision akan menjadi 1. 

### Implikasi Hasil:
- **Precision yang tinggi (1)** menunjukkan bahwa sistem sangat efektif dalam memilih kursus yang relevan, artinya pengguna hanya menerima rekomendasi yang sesuai dengan minat atau preferensi mereka.
- Meskipun hasil ini sangat positif, penting untuk dicatat bahwa **precision yang tinggi tidak menjamin bahwa sistem akan memberikan rekomendasi yang sangat beragam**. Sistem mungkin tidak merekomendasikan kursus yang bisa saja relevan namun tidak tercakup dalam daftar rekomendasi.
  
### Langkah Perbaikan:
Walaupun precision sebesar 1 menunjukkan kinerja yang sangat baik dalam memberikan rekomendasi yang relevan, untuk meningkatkan sistem lebih lanjut, beberapa langkah yang dapat diambil adalah:
1. **Meningkatkan Keragaman Rekomendasi**: Sistem dapat diperluas untuk mencakup kursus yang relevan tetapi kurang sering direkomendasikan, untuk menghindari "overfitting" pada kursus yang sangat populer atau sudah dikenal oleh pengguna.
2. **Evaluasi dengan Metrik Lain**: Menggunakan metrik lain seperti **Recall** atau **F1-score** untuk memastikan bahwa tidak hanya kursus relevan yang diberikan, tetapi juga untuk mengukur seberapa banyak kursus relevan yang berhasil ditemukan oleh sistem.
3. **Fine-Tuning Model**: Menambahkan lebih banyak fitur seperti deskripsi kursus, keterampilan yang diajarkan, atau sejarah pembelajaran pengguna untuk meningkatkan kualitas rekomendasi lebih lanjut.

Secara keseluruhan, **precision 1** menunjukkan bahwa sistem memberikan rekomendasi yang sangat tepat dan sesuai dengan kriteria relevansi yang telah ditetapkan. Namun, meskipun hasil ini sangat baik, masih ada ruang untuk memperbaiki sistem dalam hal keragaman rekomendasi dan seberapa banyak kursus relevan yang bisa ditemukan dan direkomendasikan oleh sistem.
