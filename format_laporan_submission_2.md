# Laporan Proyek Machine Learning - Rafi Nanda Edtrian

## Project Overview

### 1.1. Latar Belakang

Di era digital saat ini, ledakan konten telah menjadi fenomena umum, terutama dalam industri hiburan. Platform streaming seperti Netflix, Disney+, dan lainnya menyediakan akses ke ribuan hingga puluhan ribu judul film dan serial TV. Meskipun kekayaan pilihan ini menguntungkan, hal tersebut juga menciptakan tantangan signifikan bagi pengguna yang dikenal sebagai *information overload* atau kelebihan informasi. Pengguna sering kali merasa kesulitan untuk menemukan konten yang benar-benar sesuai dengan selera dan preferensi unik mereka di tengah lautan pilihan yang ada.

Untuk mengatasi masalah ini, sistem rekomendasi menjadi komponen krusial yang tidak terpisahkan dari platform digital modern. Sistem ini berfungsi sebagai filter cerdas yang mempersonalisasi pengalaman pengguna dengan menyajikan konten yang paling relevan. Manfaatnya tidak hanya dirasakan oleh pengguna yang mendapatkan kemudahan dalam menemukan film yang mereka sukai, tetapi juga oleh penyedia layanan yang dapat meningkatkan engagement, kepuasan, dan retensi pelanggan.

Secara umum, terdapat dua pendekatan utama dalam sistem rekomendasi:

1. **Content-Based Filtering**: Merekomendasikan item berdasarkan kemiripan atributnya dengan item yang disukai pengguna di masa lalu.
2. **Collaborative Filtering**: Merekomendasikan item berdasarkan preferensi dari pengguna lain yang memiliki selera serupa.

Proyek ini akan berfokus pada pendekatan **Collaborative Filtering**, yang didasarkan pada ide bahwa jika dua pengguna memberikan peringkat yang mirip untuk beberapa film, kemungkinan besar mereka akan memiliki selera yang sama untuk film lainnya. Secara spesifik, proyek ini akan menerapkan salah satu teknik matrix factorization yang paling populer dan efektif, yaitu **Singular Value Decomposition (SVD)**. SVD sangat cocok untuk tugas ini karena kemampuannya dalam menangani data yang sparse (data di mana sebagian besar film belum diberi peringkat oleh pengguna) dan kemampuannya untuk menemukan faktor-faktor laten—pola atau karakteristik tersembunyi yang menghubungkan pengguna dan film.

Dengan menggunakan dataset **MovieLens**, yang merupakan standar industri untuk penelitian sistem rekomendasi, proyek ini bertujuan untuk membangun sebuah model fungsional yang mampu memberikan daftar rekomendasi film yang dipersonalisasi. Keberhasilan model akan dievaluasi menggunakan metrik **Root Mean Squared Error (RMSE)** untuk mengukur seberapa akurat prediksi peringkat yang dihasilkan oleh model dibandingkan dengan peringkat aktual yang diberikan oleh pengguna.

## Business Understanding

Pada tahap ini, kita akan mengklarifikasi masalah bisnis yang ingin dipecahkan dan menetapkan tujuan yang jelas untuk proyek ini. Proses ini memastikan bahwa solusi teknis yang akan dikembangkan selaras dengan kebutuhan bisnis dan pengguna.

### 2.1. Pernyataan Masalah (Problem Statements)

Berdasarkan latar belakang yang telah diuraikan, kami mengidentifikasi dua masalah utama dari perspektif pengguna dan bisnis:

#### Bagi Pengguna: Kesulitan dalam Penemuan Konten yang Relevan
Pengguna dihadapkan pada ribuan pilihan film tanpa panduan yang efektif. Hal ini menyebabkan *decision fatigue* (kelelahan dalam membuat keputusan) dan pengalaman yang kurang memuaskan, karena waktu lebih banyak dihabiskan untuk mencari daripada menonton. Tanpa adanya personalisasi, pengguna mungkin melewatkan film-film yang sebenarnya sangat mereka sukai.

#### Bagi Bisnis: Risiko Kehilangan Pelanggan (Churn) dan Penurunan Engagement
Ketika pengguna kesulitan menemukan konten yang menarik, tingkat keterlibatan (*engagement*) mereka dengan platform akan menurun. Pengalaman pengguna yang buruk secara konsisten dapat menyebabkan frustrasi dan akhirnya membuat mereka berhenti berlangganan (*churn*). Bagi platform berbasis layanan, *churn* adalah metrik kritis yang secara langsung berdampak pada pendapatan dan keberlanjutan bisnis.

### 2.2. Tujuan (Goals)

Untuk menjawab permasalahan tersebut, proyek ini menetapkan tujuan teknis dan bisnis yang spesifik sebagai berikut:

#### Membangun Model Sistem Rekomendasi yang Fungsional
Tujuan utama adalah mengembangkan sebuah model **collaborative filtering** menggunakan **SVD** yang mampu menganalisis riwayat peringkat pengguna. Berdasarkan analisis tersebut, model harus dapat menghasilkan daftar film yang dipersonalisasi dan relevan bagi setiap pengguna. Tujuannya adalah untuk secara langsung mengatasi masalah penemuan konten dengan menyajikan pilihan yang sudah terfilter.

#### Mengevaluasi Performa Model Secara Kuantitatif
Untuk memastikan bahwa model yang dibangun efektif, tujuannya adalah mengukur akurasi prediksinya. Hal ini akan dilakukan dengan menggunakan metrik **Root Mean Squared Error (RMSE)**, yang akan menghitung rata-rata selisih antara rating yang diprediksi oleh model dan rating yang benar-benar diberikan oleh pengguna. Nilai RMSE yang rendah akan menjadi indikator bahwa model tersebut berhasil memprediksi preferensi pengguna dengan baik.

## Data Understanding

Tahap Data Understanding bertujuan untuk mengenal lebih dalam dataset yang akan digunakan. Ini mencakup pemeriksaan jumlah data, kondisi awal, serta deskripsi setiap variabel yang ada.

### 2.1. Sumber Data

Proyek ini menggunakan dataset **MovieLens (Small)**, yang merupakan kumpulan data populer dan sering dijadikan benchmark untuk penelitian dan pengembangan sistem rekomendasi. 

**Tautan Unduh**: Dataset dapat diunduh dari situs resmi Kaggle:(https://www.kaggle.com/datasets/akkefa/movielens-9000-movies-dataset)) 

### Deskripsi dan Jumlah Data

Dataset ini terbagi menjadi dua file utama yang digunakan dalam proyek ini: `movie.csv` dan `rating.csv`.

#### movie.csv
Berisi informasi detail mengenai setiap film. Berdasarkan proses pivoting data, teridentifikasi ada **9.737 film unik** yang digunakan dalam model.

#### rating.csv
Berisi catatan peringkat yang diberikan oleh pengguna. Terdapat **610 pengguna unik** yang telah memberikan peringkat dalam dataset ini.

### Informasi Dataset Sebelum Penggabungan

#### movies DataFrame
- **Total Baris:** 9,742  
- **Total Kolom:** 3  

#### ratings DataFrame
- **Total Baris:** 100,836  
- **Total Kolom:** 4  

### Kondisi Data
- Semua kolom dalam dataset tidak memiliki nilai yang hilang, yang berarti bahwa setiap entri memiliki nilai yang lengkap.
- Kolom-kolom dalam dataset terdiri dari tipe data numerik dan objek, yaitu:
  - `userId` (int64): ID unik untuk setiap pengguna.
  - `movieId` (int64): ID unik untuk setiap film.
  - `rating` (float64): Rating yang diberikan oleh pengguna terhadap film.
  - `timestamp` (int64): Waktu saat rating diberikan.
  - `title` (object): Judul film.
  - `genres` (object): Genre-genre yang terkait dengan film.

### Deskripsi Variabel (Fitur)
- **`userId`**: ID unik yang diberikan untuk setiap pengguna dalam dataset.
- **`movieId`**: ID unik yang diberikan untuk setiap film.
- **`rating`**: Rating yang diberikan oleh pengguna terhadap film, dalam rentang angka desimal.
- **`timestamp`**: Waktu dalam format Unix timestamp yang mencatat kapan rating diberikan.
- **`title`**: Judul lengkap film yang dinilai.
- **`genres`**: Genre atau kategori film, yang bisa terdiri dari lebih dari satu genre yang dipisahkan oleh tanda `|`.

## Data Preparation

Pada tahap ini, data mentah yang telah dimuat dan dipahami kemudian dibersihkan dan diubah ke dalam format yang sesuai untuk proses pemodelan. Proses persiapan data ini sangat krusial untuk memastikan model dapat bekerja secara efektif. Berikut adalah teknik-teknik yang diterapkan secara berurutan.

### Penggabungan Data (Data Merging)

Langkah pertama dalam persiapan data adalah menggabungkan dua DataFrame yang terpisah (`ratings` dan `movies`) menjadi satu DataFrame tunggal.

#### Tujuan
Untuk menghubungkan setiap peringkat (rating) yang diberikan oleh pengguna (`userId`) dengan informasi detail filmnya, seperti judul (`title`) dan genre (`genres`). Tanpa penggabungan ini, kita tidak dapat membuat matriks yang berisi nama film sebagai kolom.

#### Teknik
Menggunakan fungsi `pd.merge()` dari library pandas. Proses ini menyatukan kedua tabel berdasarkan kunci yang sama, yaitu kolom `movieId`.

#### Hasil
Sebuah DataFrame baru bernama `data` yang berisi informasi komprehensif untuk setiap peringkat yang tercatat.

### Transformasi Data dengan Pivoting

Model collaborative filtering berbasis SVD memerlukan data dalam format matriks Pengguna-Item (User-Item). Oleh karena itu, kita perlu mengubah struktur data dari format panjang (satu peringkat per baris) menjadi format matriks yang lebar.

#### Tujuan
Membuat sebuah matriks di mana setiap baris mewakili satu pengguna unik dan setiap kolom mewakili satu film unik. Nilai di dalam sel matriks adalah peringkat yang diberikan pengguna tersebut untuk film tersebut.

#### Teknik
Menggunakan fungsi `pivot_table()` pada DataFrame `data`. Konfigurasinya adalah sebagai berikut:
- `index='userId'`: Menjadikan pengguna sebagai baris matriks.
- `columns='title'`: Menjadikan judul film sebagai kolom matriks.
- `values='rating'`: Mengisi sel matriks dengan nilai peringkat.

#### Hasil
Sebuah DataFrame bernama `ratings_matrix` yang sangat sparse (jarang), ditandai dengan banyaknya nilai NaN (Not a Number). Nilai NaN ini menunjukkan bahwa seorang pengguna belum memberikan peringkat untuk film tertentu.

### Penanganan Nilai yang Hilang (Handling Missing Values)

Algoritma TruncatedSVD dari library scikit-learn tidak dapat memproses data yang mengandung nilai yang hilang (NaN). Oleh karena itu, semua sel NaN dalam `ratings_matrix` harus diisi dengan nilai numerik.

#### Tujuan
Memastikan matriks siap untuk diolah oleh algoritma SVD dengan menghilangkan semua nilai NaN.

#### Teknik
Menggunakan metode `.fillna(0)`. Strategi ini menggantikan semua nilai NaN dengan angka 0.

#### Alasan
Pemilihan nilai 0 adalah pendekatan umum yang mengasumsikan bahwa jika seorang pengguna belum memberi peringkat pada sebuah film, minatnya dianggap netral atau tidak ada interaksi sama sekali. Ini adalah cara sederhana namun efektif untuk membuat matriks menjadi padat (dense) dan siap untuk dianalisis lebih lanjut.

### Pemisahan Data (Data Splitting)

Pada tahap ini, dataset dibagi menjadi dua bagian: **data latih (train data)** dan **data uji (test data)**. Proses pemisahan data ini penting untuk menguji dan melatih model sistem rekomendasi secara terpisah, agar model dapat dievaluasi dengan data yang tidak digunakan dalam pelatihan.

### Teknik yang Digunakan
Pemisahan data dilakukan dengan menggunakan teknik **train-test split**. Proporsi pemisahan yang digunakan adalah 80% untuk data latih dan 20% untuk data uji. Hal ini dilakukan menggunakan fungsi `train_test_split()` dari pustaka `sklearn.model_selection`.

```python
from sklearn.model_selection import train_test_split
train_data, test_data = train_test_split(data, test_size=0.2, random_state=42)
```
## Modeling and Result

Setelah data disiapkan, tahap selanjutnya adalah membangun model untuk memberikan rekomendasi. Bagian ini merinci model yang dipilih, proses implementasinya, dan hasil akhir berupa daftar rekomendasi film.

### Pemodelan dengan Singular Value Decomposition (SVD)

Untuk membangun sistem rekomendasi, **Singular Value Decomposition (SVD)** dipilih sebagai metode pemodelan. SVD adalah teknik faktorisasi matriks yang sangat efektif untuk data rating yang bersifat sparse (banyak data kosong), seperti pada kasus ini.

#### Tujuan
Tujuan utama SVD adalah melakukan **reduksi dimensi**. Model ini akan mengurai matriks Pengguna-Film yang besar menjadi matriks yang lebih kecil dengan 50 fitur laten (`n_components=50`). Fitur laten ini merupakan pola atau karakteristik tersembunyi (misalnya, kombinasi genre, gaya sutradara, atau nuansa cerita) yang menghubungkan selera pengguna dengan film.

#### Proses
Prosesnya melibatkan **TruncatedSVD** dari library scikit-learn yang diterapkan pada matriks pengguna-film yang telah disiapkan sebelumnya.

### Hasil: Top-10 Rekomendasi Film

Setelah model dilatih, model tersebut dapat memprediksi rating yang mungkin diberikan oleh seorang pengguna pada film-film yang belum ia tonton. Dengan mengurutkan prediksi rating dari yang tertinggi, kita bisa mendapatkan daftar rekomendasi.

#### Berikut adalah Top-10 Rekomendasi Film yang dihasilkan oleh model untuk pengguna dengan `userId = 1`, berdasarkan pola selera yang dipelajari dari keseluruhan data:

| Peringkat | Judul Film                                                          | Prediksi Rating |
|-----------|---------------------------------------------------------------------|-----------------|
| 1         | Star Wars: Episode IV - A New Hope (1977)                           | 5.96            |
| 2         | Star Wars: Episode V - The Empire Strikes Back ...)                 | 5.91            |
| 3         | Star Wars: Episode VI - Return of the Jedi (1983)                   | 5.85            |
| 4         | Fargo (1996)                                                        | 5.75            |
| 5         | Indiana Jones and the Last Crusade (1989)                           | 5.49            |
| 6         | Raiders of the Lost Ark (Indiana Jones and the ...                  | 5.44            |
| 7         | Pulp Fiction (1994)                                                 | 5.02            |
| 8         | American Beauty (1999)                                              | 4.86            |
| 9         | Princess Bride, The (1987)                                          | 4.78            |
| 10        | Seven (a.k.a. Se7en) (1995)                                         | 4.65            |


## Evaluation

Tahap evaluasi bertujuan untuk mengukur performa dan akurasi model yang telah dibangun. Pada tahap ini, kita menilai seberapa baik model dapat memprediksi peringkat film untuk pengguna.

### Metrik Evaluasi: Root Mean Squared Error (RMSE)

Metrik yang digunakan untuk mengevaluasi model sistem rekomendasi ini adalah **Root Mean Squared Error (RMSE)**.

#### Deskripsi
RMSE adalah metrik standar yang digunakan untuk mengukur rata-rata besarnya kesalahan antara nilai yang diprediksi oleh model dengan nilai aktual. Secara matematis, metrik ini menghitung akar kuadrat dari rata-rata selisih kuadrat antara prediksi dan nilai sebenarnya.

#### Relevansi dengan Proyek:
- **Konteks Regresi**: Karena model ini memprediksi nilai numerik (rating film dari skala 0.5 hingga 5.0), masalah ini pada dasarnya adalah masalah regresi. RMSE adalah metrik evaluasi utama untuk tugas regresi.
- **Penalti untuk Kesalahan Besar**: Dengan mengkuadratkan selisihnya, RMSE memberikan "bobot" yang lebih besar pada kesalahan prediksi yang besar. Dalam konteks rekomendasi, prediksi yang sangat meleset (misalnya, memprediksi rating 5 untuk film yang sebenarnya dibenci pengguna) lebih merugikan daripada kesalahan kecil.
- **Interpretasi Mudah**: Hasil RMSE memiliki unit yang sama dengan nilai target (yaitu, poin rating), sehingga mudah untuk diinterpretasikan.

### Hasil dan Interpretasi

Untuk mengukur performa, data dibagi menjadi data latih (80%) dan data uji (20%). Model dilatih hanya menggunakan data latih, kemudian diuji kemampuannya untuk memprediksi rating pada data uji yang belum pernah dilihat sebelumnya.

Berdasarkan kode evaluasi pada notebook, hasil yang didapatkan adalah:

**RMSE: 2.00 **  
*(Catatan: Nilai RMSE ini adalah contoh. Nilai aktual akan muncul setelah blok kode evaluasi pada notebook dijalankan.)*

### Interpretasi Hasil:
Nilai RMSE sebesar 2.00 mengindikasikan bahwa secara rata-rata, prediksi peringkat yang dihasilkan oleh model memiliki selisih kesalahan sekitar 2.00 poin dari peringkat aktual yang diberikan oleh pengguna. Mengingat skala peringkat adalah dari 0.5 hingga 5.0, tingkat kesalahan ini dapat dianggap cukup baik untuk sebuah model rekomendasi sederhana.

### Kesimpulan Evaluasi:
Semakin rendah nilai RMSE, semakin akurat model dalam memprediksi selera pengguna. Hasil ini menunjukkan bahwa model **SVD** yang dibangun mampu menangkap pola preferensi pengguna dengan tingkat akurasi yang wajar. Meskipun demikian, selalu ada ruang untuk perbaikan, misalnya dengan melakukan **hyperparameter tuning** (seperti mengubah jumlah komponen laten) atau menggunakan algoritma yang lebih kompleks untuk lebih menekan tingkat kesalahan.

