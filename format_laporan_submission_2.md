# Laporan Proyek Machine Learning - Muhammad Farhan

## Project Overview

Dalam era digital saat ini, di mana informasi tersedia melimpah ruah, industri hiburan, khususnya perfilman, menghadapi tantangan besar dalam membantu pengguna menemukan konten yang relevan. Dengan jutaan film yang tersedia di berbagai platform, pengguna seringkali mengalami *information overload*, kesulitan dalam memilih tontonan yang sesuai dengan preferensi mereka. Untuk mengatasi masalah ini, sistem rekomendasi telah muncul sebagai solusi cerdas yang memprediksi preferensi pengguna dan menyarankan film yang kemungkinan besar akan disukai, berdasarkan data historis dan pola perilaku. Tanpa sistem ini, pengguna menghabiskan waktu berharga untuk mencari film secara manual, seringkali berakhir dengan pilihan yang tidak memuaskan, sementara penyedia layanan kehilangan kesempatan untuk secara efektif mempromosikan koleksi film mereka. Proyek ini bertujuan untuk membangun sistem rekomendasi film sederhana menggunakan dataset metadata film TMDB 5000. Kami akan mengeksplorasi pendekatan: **Content-Based Filtering**, yang merekomendasikan film berdasarkan atribut intrinsik seperti genre, kata kunci, dan sinopsis, dengan fokus pada kesamaan konten. 

## Business Understanding

### 1. Pernyataan Masalah (Problem Statement)

Dalam lanskap industri hiburan digital yang terus berkembang, terutama di sektor _streaming_ film, terdapat beberapa tantangan signifikan yang dihadapi oleh pengguna maupun penyedia layanan:

* **1.1. _Information Overload_ bagi Pengguna:** Pengguna modern dihadapkan pada pilihan film yang sangat banyak dari berbagai platform. Ketersediaan ribuan hingga jutaan judul film seringkali menyebabkan kebingungan dan kesulitan bagi pengguna untuk menemukan konten yang sesuai dengan selera atau minat mereka. Ini dapat mengakibatkan *paradoks pilihan*, di mana semakin banyak pilihan justru mempersulit keputusan.

* **1.2. Kurangnya Efisiensi dalam Penemuan Konten:** Tanpa panduan, pengguna harus menghabiskan waktu yang tidak sedikit untuk menelusuri katalog, membaca sinopsis, atau mencari ulasan eksternal. Proses pencarian manual ini tidak efisien dan seringkali menghasilkan pengalaman yang kurang memuaskan jika film yang dipilih ternyata tidak sesuai harapan.

* **1.3. Potensi Kehilangan Keterlibatan Pengguna (User Engagement):** Jika pengguna secara konsisten kesulitan menemukan konten yang menarik, mereka cenderung akan frustrasi, mengurangi waktu yang dihabiskan di platform, atau bahkan beralih ke layanan lain yang menawarkan pengalaman penemuan konten yang lebih baik. Ini berimplikasi pada retensi pengguna dan pertumbuhan platform.

* **1.4. Pemasaran Konten yang Tidak Optimal bagi Penyedia Layanan:** Bagi platform _streaming_ atau penyedia konten, menyajikan seluruh katalog film secara pasif tidaklah efisien. Tanpa mekanisme untuk secara proaktif merekomendasikan film yang relevan kepada segmen audiens yang tepat, potensi penemuan film baru dan peningkatan konsumsi konten menjadi terbatas.

### 2. Tujuan Proyek (Project Goals)

Untuk mengatasi permasalahan di atas, proyek sistem rekomendasi film ini memiliki tujuan-tujuan utama sebagai berikut:

* **2.1. Meningkatkan Pengalaman Pengguna:**
    * **Menyediakan Rekomendasi Film yang Relevan:** Mengembangkan sistem yang mampu menyarankan film-film yang sesuai dengan preferensi dan minat pengguna, sehingga mengurangi *information overload* dan mempermudah proses pemilihan tontonan.
    * **Meningkatkan Efisiensi Penemuan Konten:** Mempersingkat waktu dan upaya yang diperlukan pengguna untuk menemukan film yang menarik, sehingga meningkatkan kepuasan dan mengurangi rasa frustrasi.

* **2.2. Mendorong Keterlibatan Pengguna dan Retensi:**
    * **Meningkatkan Waktu yang Dihabiskan di Platform:** Dengan menyajikan konten yang secara konsisten relevan, diharapkan pengguna akan lebih sering berinteraksi dengan platform dan menghabiskan lebih banyak waktu untuk menonton film.
    * **Mendorong Penemuan Konten Baru:** Membantu pengguna menemukan film-film yang mungkin belum pernah mereka pertimbangkan sebelumnya tetapi sesuai dengan profil minat mereka, sehingga memperkaya pengalaman menonton.

* **2.3. Membangun dan Membandingkan Model Rekomendasi:**
    * **Mengimplementasikan Content-Based Filtering:** Membangun model rekomendasi yang memanfaatkan metadata film (genre, keywords, overview, dll.) untuk mengidentifikasi kesamaan antar film dan merekomendasikan berdasarkan profil konten.
    * **Mengimplementasikan Dasar Collaborative Filtering (Item-Based):** Mengeksplorasi penggunaan metrik popularitas dan rata-rata _vote_ sebagai proxy data interaksi untuk menemukan kesamaan antar film dari perspektif "preferensi umum", meskipun tanpa data pengguna-item yang eksplisit.
    * **Menganalisis Perbedaan Pendekatan:** Memahami bagaimana kedua metode tersebut (Content-Based dan Collaborative Filtering sederhana) menghasilkan rekomendasi yang berbeda dan dalam kondisi seperti apa masing-masing metode lebih relevan, meskipun dengan keterbatasan dataset yang ada.

* **2.4. Membangun Dasar Teknis:**
    * **Memanfaatkan Dataset TMDB 5000:** Menggunakan dataset yang relevan untuk membangun fondasi sistem rekomendasi.
    * **Menerapkan Teknik Pemrosesan Teks:** Menggunakan teknik seperti TF-IDF untuk mengubah data tekstual menjadi format numerik yang dapat diproses oleh algoritma.
    * **Menghitung Kesamaan Item:** Mengaplikasikan metrik kesamaan (misalnya Cosine Similarity) untuk mengidentifikasi kemiripan antar film.
    * **Menyediakan Fungsi Rekomendasi yang Fungsional:** Mengembangkan kode yang dapat mengambil judul film dan mengembalikan daftar rekomendasi.

## Data Understanding
Bagian ini menjelaskan secara rinci tentang dataset yang digunakan dalam proyek sistem rekomendasi film, termasuk sumber data, jumlah data, kondisi data, dan deskripsi setiap variabel atau fitur.

### 1. Sumber Data dan Pengunduhan

Dataset yang digunakan dalam proyek ini adalah **TMDB 5000 Movie Dataset**. Dataset ini menyediakan informasi metadata dari sekitar 5000 film yang terdaftar di The Movie Database (TMDB).

Anda dapat mengunduh dataset ini dari Kaggle melalui tautan berikut:
* **Tautan Unduh:** [TMDB 5000 Movie Dataset on Kaggle](https://www.kaggle.com/datasets/tmdb/tmdb-movie-metadata)
    * File yang relevan untuk proyek ini adalah `tmdb_5000_movies.csv`.

### 2. Jumlah dan Kondisi Data

Setelah data dimuat ke dalam lingkungan kerja, observasi awal terhadap karakteristik dataset dilakukan:

* **Jumlah Baris (Observasi):** Dataset `tmdb_5000_movies.csv` berisi **4803 baris** atau entri film. Setiap baris merepresentasikan satu film.
* **Jumlah Kolom (Fitur/Variabel):** Dataset ini memiliki **20 kolom** yang berbeda, masing-masing berisi informasi spesifik tentang film.
* **Kondisi Data:**
    * **Nilai Hilang (Missing Values):** Beberapa kolom memiliki nilai yang hilang (`NaN`). Kolom-kolom seperti `homepage`, `tagline`, `overview`, `runtime`, `release_date`, dan `spoken_languages` adalah contoh kolom yang kemungkinan besar memiliki nilai hilang. Penanganan nilai hilang ini penting untuk memastikan kualitas data sebelum pemrosesan lebih lanjut, misalnya dengan mengisi dengan string kosong atau nilai rata-rata/modus tergantung pada jenis kolom.
    * **Tipe Data:** Sebagian besar kolom yang berisi informasi deskriptif seperti `genres`, `keywords`, `production_companies`, `production_countries`, `spoken_languages` adalah dalam format _stringified JSON_ (string yang merepresentasikan struktur JSON). Kolom-kolom ini memerlukan parsing khusus untuk mengekstrak informasi yang relevan (misalnya, daftar nama genre atau kata kunci).
    * **Duplikasi Data:** Perlu dilakukan pemeriksaan untuk memastikan tidak ada entri film yang terduplikasi berdasarkan ID film (`id`) atau judul (`title`) untuk menghindari bias dalam rekomendasi.

### 3. Informasi Variabel/Fitur

Berikut adalah uraian setiap variabel atau fitur yang terdapat dalam dataset `tmdb_5000_movies.csv`:

1.  **`budget` (numerik):** Anggaran produksi film dalam dolar Amerika Serikat.
2.  **`genres` (stringified JSON):** Daftar genre film (misalnya Action, Comedy, Drama). Disimpan sebagai string JSON yang perlu di-*parse* untuk mendapatkan daftar nama genre.
3.  **`homepage` (string):** Tautan URL ke halaman _homepage_ resmi film. Seringkali memiliki nilai hilang.
4.  **`id` (numerik):** ID unik film yang diberikan oleh TMDB. Penting untuk identifikasi unik film.
5.  **`keywords` (stringified JSON):** Kata kunci atau _tag_ yang relevan dengan film. Disimpan sebagai string JSON yang perlu di-*parse* untuk mendapatkan daftar nama kata kunci.
6.  **`original_language` (string):** Kode bahasa asli film (misalnya 'en' untuk English).
7.  **`original_title` (string):** Judul asli film sebelum diterjemahkan atau dilokalisasi.
8.  **`overview` (string):** Ringkasan singkat atau sinopsis plot film. Ini adalah fitur tekstual penting untuk _Content-Based Filtering_.
9.  **`popularity` (numerik):** Skor popularitas film yang dihitung oleh TMDB, seringkali berdasarkan metrik seperti jumlah tampilan halaman, favorit, daftar tonton, dll.
10. **`production_companies` (stringified JSON):** Daftar perusahaan produksi yang terlibat dalam pembuatan film. Disimpan sebagai string JSON.
11. **`production_countries` (stringified JSON):** Daftar negara tempat film diproduksi. Disimpan sebagai string JSON.
12. **`release_date` (string/tanggal):** Tanggal rilis film. Mungkin memerlukan konversi tipe data ke format tanggal.
13. **`revenue` (numerik):** Pendapatan yang dihasilkan film di seluruh dunia dalam dolar Amerika Serikat.
14. **`runtime` (numerik):** Durasi film dalam menit.
15. **`spoken_languages` (stringified JSON):** Daftar bahasa yang digunakan dalam film. Disimpan sebagai string JSON.
16. **`status` (string):** Status produksi film (misalnya 'Released', 'Rumored').
17. **`tagline` (string):** Slogan atau _tagline_ film. Seringkali memiliki nilai hilang.
18. **`title` (string):** Judul film yang umumnya ditampilkan. Ini adalah fitur utama untuk mengidentifikasi film.
19. **`vote_average` (numerik):** Rata-rata _vote_ atau rating film dari pengguna TMDB (skala 0-10). Fitur penting untuk Collaborative Filtering berbasis popularitas/rating.
20. **`vote_count` (numerik):** Jumlah total _vote_ yang diterima film dari pengguna TMDB. Penting sebagai bobot untuk `vote_average` dalam menghitung *weighted rating*.

## Data Preparation
Bagian ini menguraikan langkah-langkah persiapan data yang dilakukan untuk membersihkan, mengubah, dan mempersiapkan dataset TMDB 5000 agar siap digunakan dalam pembangunan model sistem rekomendasi, baik untuk pendekatan Content-Based Filtering maupun Collaborative Filtering (berbasis popularitas/rating). Teknik-teknik ini dilakukan secara berurutan untuk memastikan kualitas dan konsistensi data.

### 1. Penanganan Kolom Bertipe Stringified JSON

Beberapa kolom dalam dataset `tmdb_5000_movies.csv` menyimpan data dalam format string JSON, yang perlu di-*parse* untuk mengekstrak informasi yang dapat digunakan. Kolom-kolom ini antara lain `genres`, `keywords`, `production_companies`, `production_countries`, `spoken_languages`, `cast`, dan `crew`.

* **Teknik:** Fungsi kustom `parse_json_to_list` dibuat untuk:
    * Mendeteksi apakah nilai adalah string dan dapat di-*parse* sebagai JSON.
    * Mengurai string JSON menjadi daftar kamus (list of dictionaries).
    * Mengekstrak nilai dari kunci spesifik (misalnya 'name' untuk genre, keywords, cast, atau 'job' untuk crew) dan mengembalikannya sebagai daftar string.
    * Menangani kasus nilai `NaN` atau format yang tidak valid dengan mengembalikan daftar kosong `[]`.
* **Penerapan:** Fungsi ini diaplikasikan pada kolom `genres`, `keywords`, `cast` (diambil hingga 3 aktor utama), dan `crew`.

### 2. Ekstraksi Informasi Sutradara dari Kolom `crew`

Untuk _Content-Based Filtering_, informasi sutradara (director) adalah fitur penting yang dapat sangat memengaruhi kesamaan film.

* **Teknik:** Fungsi kustom `get_director` dibuat untuk:
    * Menerima daftar anggota kru yang sudah di-*parse* dari kolom `crew`.
    * Melakukan iterasi melalui daftar anggota kru dan mencari anggota dengan `job` 'Director'.
    * Mengembalikan nama sutradara jika ditemukan, atau string kosong jika tidak ditemukan.
* **Penerapan:** Fungsi ini diaplikasikan pada kolom `crew` yang telah diproses sebelumnya untuk membuat kolom baru `director`.

#3# 3. Pembersihan dan Normalisasi Data Tekstual

Untuk memastikan konsistensi dan efektivitas dalam pemrosesan teks, data tekstual dari fitur-fitur seperti `genres`, `keywords`, `cast`, dan `director` perlu dibersihkan.

* **Teknik:** Fungsi kustom `clean_data` dibuat untuk:
    * Mengubah semua teks menjadi huruf kecil (`.lower()`).
    * Menghapus spasi antar kata (misalnya, "Science Fiction" menjadi "sciencefiction") untuk memperlakukan frase sebagai satu entitas.
    * Menangani kasus di mana input adalah daftar (misalnya daftar genre) atau string tunggal.
    * Mengembalikan string kosong untuk nilai non-string atau non-list.
* **Penerapan:** Fungsi ini diaplikasikan pada kolom `genres`, `keywords`, `cast`, dan `director` (jika tersedia).

### 4. Penanganan Nilai Hilang pada Kolom `overview`

Kolom `overview` (sinopsis) adalah fitur tekstual krusial untuk _Content-Based Filtering_.

* **Teknik:** Mengisi nilai yang hilang (`NaN`) pada kolom `overview` dengan string kosong (`''`). Ini penting agar `TfidfVectorizer` tidak mengalami kesalahan saat memproses nilai yang hilang.
* **Penerapan:** `df['overview'].fillna('')`

### 5. Pembuatan 'Soup' Fitur (untuk Content-Based Filtering)

Untuk Content-Based Filtering, semua fitur tekstual yang relevan digabungkan menjadi satu string tunggal (disebut 'soup' atau 'bag of words') untuk setiap film.

* **Teknik:** Fungsi kustom `create_soup` dibuat untuk:
    * Menggabungkan konten dari kolom `genres`, `keywords`, `cast`, `director`, dan `overview` menjadi satu string besar.
    * Memastikan setiap komponen adalah string sebelum digabungkan untuk menghindari kesalahan.
    * Spasi digunakan sebagai pemisah antar fitur.
* **Penerapan:** Fungsi ini diaplikasikan pada DataFrame (`df.apply(create_soup, axis=1)`) untuk membuat kolom baru `soup`. Kolom `soup` ini akan menjadi input utama untuk _TF-IDF Vectorization_.

## Modeling
Bagian ini menjelaskan proses pembangunan model sistem rekomendasi film, mencakup dua pendekatan utama: Content-Based Filtering dan Collaborative Filtering (berbasis popularitas/rating). Model ini dirancang untuk mengatasi permasalahan *information overload* dan memberikan rekomendasi film yang relevan kepada pengguna.

### 1. Pendekatan Content-Based Filtering

Model Content-Based Filtering dibangun dengan memanfaatkan metadata film untuk menemukan kesamaan antar film. Inti dari pendekatan ini adalah mengubah deskripsi tekstual film menjadi representasi numerik yang dapat dibandingkan, kemudian menghitung kesamaan antara representasi tersebut.

##3# 1.1. TF-IDF Vectorization

Setelah tahap persiapan data di mana semua fitur tekstual relevan digabungkan menjadi satu string 'soup' untuk setiap film, langkah selanjutnya adalah mengubah 'soup' ini menjadi vektor numerik.

* **Teknik:** *Term Frequency-Inverse Document Frequency (TF-IDF)* digunakan untuk mengubah teks menjadi matriks fitur numerik.
    * **Term Frequency (TF):** Mengukur seberapa sering sebuah kata muncul dalam sebuah dokumen (film).
    * **Inverse Document Frequency (IDF):** Mengukur seberapa unik atau penting sebuah kata di seluruh koleksi dokumen (semua film). Kata-kata umum (seperti "the", "a", "is") akan memiliki IDF yang rendah, sementara kata-kata spesifik film akan memiliki IDF yang tinggi.
    * **`TfidfVectorizer` (Scikit-learn):** Digunakan untuk melakukan transformasi ini. Parameter `stop_words='english'` digunakan untuk menghapus kata-kata umum dalam bahasa Inggris yang tidak memberikan informasi deskriptif yang berarti (misalnya "and", "or", "but").
* **Penerapan:**
    1.  Inisialisasi `TfidfVectorizer`.
    2.  Melakukan `fit_transform()` pada kolom `soup` dari DataFrame (`tfidf_matrix = tfidf.fit_transform(df['soup'])`). Hasilnya adalah `tfidf_matrix`, sebuah matriks sparse di mana baris merepresentasikan film dan kolom merepresentasikan kata-kata (terms) dengan nilai TF-IDF-nya.

#### 1.2. Perhitungan Kesamaan Kosinus (Cosine Similarity)

Setelah film direpresentasikan sebagai vektor TF-IDF, langkah selanjutnya adalah menghitung seberapa mirip setiap film satu sama lain berdasarkan representasi vektornya.

* **Teknik:** *Cosine Similarity* digunakan untuk mengukur kesamaan antara dua vektor non-nol dalam ruang produk skalar. Nilainya berkisar antara 0 (tidak ada kesamaan) hingga 1 (kesamaan sempurna). Semakin tinggi nilai kesamaan kosinus, semakin mirip kedua film tersebut.
* **Formula:**
    $similarity = \cos(\theta) = \frac{A \cdot B}{\|A\| \|B\|} = \frac{\sum_{i=1}^{n} A_i B_i}{\sqrt{\sum_{i=1}^{n} A_i^2} \sqrt{\sum_{i=1}^{n} B_i^2}}$
    Di mana $A$ dan $B$ adalah vektor TF-IDF dari dua film.
* **Penerapan:**
    1.  Menggunakan fungsi `cosine_similarity` dari `sklearn.metrics.pairwise`.
    2.  `cosine_sim = cosine_similarity(tfidf_matrix, tfidf_matrix)` akan menghasilkan matriks kesamaan kosinus simetris di mana `cosine_sim[i][j]` adalah kesamaan antara film `i` dan film `j`.

#### 1.3. Fungsi Rekomendasi (Top-N Recommendation)

Fungsi ini menggabungkan semua langkah di atas untuk menghasilkan rekomendasi film berdasarkan judul film yang diberikan pengguna.

* **Teknik:**
    1.  **Pemetaan Judul ke Indeks:** Sebuah `pd.Series` dibuat untuk memetakan judul film ke indeks barisnya dalam DataFrame, memungkinkan pencarian cepat.
    2.  **Pengambilan Indeks Film:** Untuk judul film yang diberikan, indeks film yang sesuai diambil dari `indices` Series.
    3.  **Pengambilan Skor Kesamaan:** Baris yang sesuai dari matriks `cosine_sim` diambil (yang berisi skor kesamaan film target dengan semua film lain).
    4.  **Pengurutan Skor:** Skor kesamaan diubah menjadi daftar tuple `(index, similarity_score)` dan diurutkan dalam urutan menurun berdasarkan skor kesamaan.
    5.  **Pemilihan Top-N:** 10 film teratas (tidak termasuk film itu sendiri) dipilih dari daftar yang sudah diurutkan.
    6.  **Pengambilan Judul Film:** Indeks film-film teratas digunakan untuk mengambil judul film yang direkomendasikan dari DataFrame asli.
* **Penerapan:** Fungsi `get_recommendations(title)` menerima judul film dan mengembalikan daftar 10 judul film paling mirip.

#### 3. Output Model: Top-N Recommendation

Output dari kedua model adalah daftar **Top-N Recommendation**, yaitu daftar N film teratas (dalam kasus ini N=10) yang paling direkomendasikan berdasarkan film input yang diberikan.
**Contoh Output:**
Recommendations for The Dark Knight Rises (Content-Based):
65                              The Dark Knight
428                              Batman Returns
1359                                     Batman
299                              Batman Forever
119                               Batman Begins
3854    Batman: The Dark Knight Returns, Part 2
210                              Batman & Robin
9            Batman v Superman: Dawn of Justice
2507                                  Slow Burn
3819                                   Defendor
Name: title, dtype: object

Ketika fungsi rekomendasi dipanggil, hasilnya adalah daftar judul film.

## Evaluation

Bagian ini membahas metrik evaluasi yang relevan untuk sistem rekomendasi, serta menjelaskan hasil proyek berdasarkan metrik tersebut. Penting untuk dicatat bahwa evaluasi sistem rekomendasi, terutama tanpa data interaksi pengguna yang eksplisit atau hasil eksperimen A/B, dapat menjadi tantangan. Dalam konteks proyek ini, evaluasi akan lebih banyak berfokus pada **validitas kualitatif** dan **interpretabilitas** dari rekomendasi yang dihasilkan.

### 1. Metrik Evaluasi yang Digunakan

Untuk sistem rekomendasi berbasis kesamaan, metrik evaluasi yang umum terbagi menjadi dua kategori: *offline metrics* (berbasis data historis) dan *online metrics* (berbasis interaksi pengguna langsung). Mengingat keterbatasan dataset TMDB 5000 (tidak ada data rating atau interaksi pengguna eksplisit), kami tidak dapat menggunakan metrik *offline* berbasis prediksi rating (seperti RMSE, MAE) atau metrik berbasis *ranking* yang memerlukan *ground truth* preferensi pengguna (seperti Precision@K, Recall@K, F1-score, NDCG).

Oleh karena itu, evaluasi dalam proyek ini akan lebih difokuskan pada:

#### 1.1. Validitas Kualitatif/Relevansi (Interpretability)

* **Definisi:** Menguji seberapa relevan dan masuk akal rekomendasi yang diberikan secara subjektif oleh pengembang. Ini melibatkan pemeriksaan film-film yang direkomendasikan untuk film input tertentu dan menilai apakah film-film tersebut memiliki kesamaan yang jelas dalam konteks konten atau "rasa" (untuk Content-Based) atau dalam konteks popularitas/penilaian umum (untuk Collaborative Filtering yang disimulasikan).
* **Contoh Penerapan:**
    * Jika film input adalah "The Dark Knight Rises", apakah rekomendasi yang diberikan adalah film-film *Batman* atau film *action* bertema superhero lainnya?
    * Jika film input adalah "Minions", apakah rekomendasi yang diberikan adalah film animasi keluarga serupa?
* **Batasan:** Metrik ini bersifat subjektif dan tidak dapat diukur secara kuantitatif. Ini adalah cara dasar untuk mendapatkan indikasi awal kualitas model.

#### 1.2. Keberagaman (Diversity) - *Observasi Kualitatif*

* **Definisi:** Menilai apakah sistem merekomendasikan berbagai macam film (tidak terlalu homogen) atau apakah rekomendasinya sangat mirip satu sama lain.
* **Contoh Penerapan:** Jika rekomendasi untuk "The Dark Knight Rises" hanya berisi film *Batman* yang sama persis, itu kurang beragam. Jika ada variasi dalam sub-genre atau sutradara, itu lebih baik.
* **Batasan:** Sulit diukur tanpa definisi yang jelas tentang "keberagaman" dan seringkali bertentangan dengan "relevansi" (lebih relevan cenderung kurang beragam).

#### 1.3. Popularitas (Popularity Bias) - *Observasi Kualitatif*

* **Definisi:** Mengamati apakah model cenderung merekomendasikan film-film yang sudah sangat populer, terlepas dari preferensi spesifik. Collaborative Filtering berbasis popularitas cenderung memiliki bias ini.
* **Contoh Penerapan:** Jika untuk setiap film yang diinput, rekomendasi yang keluar selalu film-film *blockbuster* teratas, itu menunjukkan bias popularitas yang kuat.
* **Batasan:** Merupakan observasi kualitatif dan tidak selalu negatif; film populer seringkali memang disukai.

### 2. Hasil Proyek Berdasarkan Metrik Evaluasi

Berdasarkan pengujian kualitatif dengan beberapa film input, model sistem rekomendasi menunjukkan hasil sebagai berikut:

### 2.1. Content-Based Filtering

* **Relevansi Kualitatif:** Model Content-Based Filtering menunjukkan relevansi yang sangat baik. Untuk film input seperti "The Dark Knight Rises", rekomendasi yang diberikan secara konsisten adalah film-film dari *franchise* Batman lainnya ("The Dark Knight", "Batman Begins", "Batman & Robin", dll.) atau film superhero sejenis. Ini mengindikasikan bahwa fitur-fitur seperti `genres`, `keywords`, `overview`, dan `director` berhasil menangkap kesamaan konten dengan efektif. Contohnya:
    ```markdown
    Recommendations for The Dark Knight Rises (Content-Based):
    * The Dark Knight
    * Batman Returns
    * Batman
    * Batman Forever
    * Batman Begins
    * Batman: The Dark Knight Returns, Part 2
    * Batman & Robin
    * Batman v Superman: Dawn of Justice
    * Slow Burn
    * Defendor
    ```
    Daftar ini menunjukkan bahwa rekomendasi sangat relevan dengan film input, berfokus pada tema superhero/Batman. "Slow Burn" dan "Defendor" mungkin merupakan anomali atau memiliki kesamaan kata kunci yang tidak terlalu menonjol secara plot.

* **Keberagaman:** Rekomendasi cenderung kurang beragam dalam genre atau tema, namun sangat spesifik pada sub-genre yang mirip dengan film input. Ini adalah karakteristik umum dari Content-Based Filtering, di mana "jika Anda suka ini, Anda akan suka yang seperti ini".

* **Bias Popularitas:** Meskipun tidak sekuat Collaborative Filtering yang disimulasikan, model ini masih mungkin merekomendasikan film populer dalam kategori yang sama karena film populer cenderung memiliki lebih banyak metadata yang kaya dan relevan.

### 3. Kesimpulan Evaluasi

Secara keseluruhan, kedua model berhasil memberikan rekomendasi yang relevan, meskipun dengan karakteristik yang berbeda:

* **Content-Based Filtering** sangat efektif dalam menemukan film dengan **kesamaan konten yang eksplisit** (misalnya, film dari *franchise* yang sama, genre yang sangat spesifik, atau dengan aktor/sutradara yang sama). Ini ideal untuk pengguna yang ingin menjelajahi lebih banyak konten dalam niche yang sudah mereka sukai.
