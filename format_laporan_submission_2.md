# Laporan Proyek Machine Learning - Muhammad Farhan

## Project Overview
Proyek ini bertujuan untuk mengembangkan sistem rekomendasi berbasis konten untuk video game dengan menggunakan dataset yang mencakup informasi tentang genre, platform, rating pengguna, dan penjualan global game. Dengan banyaknya pilihan game yang tersedia, sistem rekomendasi berbasis konten ini diharapkan dapat membantu pengguna menemukan game yang relevan dengan preferensi mereka, berdasarkan kesamaan konten seperti genre, platform, dan penerbit. Sistem ini menggunakan **Cosine Similarity** untuk menghitung kesamaan antar game dan memberikan rekomendasi yang lebih personal tanpa memerlukan data interaksi pengguna sebelumnya. Sistem ini bertujuan untuk meningkatkan pengalaman pengguna dengan membantu mereka menemukan game yang sesuai dengan minat mereka, serta memberikan solusi untuk tantangan yang dihadapi pengguna dalam mencari game yang tepat di pasar yang sangat luas.

## Business Understanding

### Problem Statements

- Pengguna sering kali kesulitan menemukan game yang sesuai dengan preferensi pribadi mereka di pasar yang penuh dengan pilihan.
- Dengan banyaknya genre, platform, dan penerbit yang berbeda, banyak pengguna tidak mengetahui game mana yang paling sesuai dengan minat mereka.
- Platform distribusi game seperti Steam, PlayStation, dan lainnya menghadapi tantangan dalam menyarankan game yang relevan, terutama bagi pengguna baru atau mereka yang belum memiliki preferensi yang jelas.
- Pengguna yang tidak dapat menemukan game yang sesuai dengan minat mereka mungkin merasa frustrasi, yang dapat berdampak negatif pada kepuasan dan keterlibatan mereka.

### Goals

- Mengembangkan sistem rekomendasi berbasis konten yang dapat memberikan saran game yang relevan kepada pengguna berdasarkan fitur konten game (seperti genre, platform, dan penerbit).
- Mengatasi masalah pengguna yang kesulitan menemukan game sesuai dengan minat mereka tanpa memerlukan data interaksi pengguna sebelumnya.
- Menggunakan **Cosine Similarity** untuk menghitung kesamaan antar game berdasarkan fitur-fitur konten mereka, untuk memberikan rekomendasi yang lebih personal dan relevan.
- Meningkatkan pengalaman pengguna dengan membantu mereka menemukan game yang sesuai dengan preferensi mereka, sehingga meningkatkan kepuasan dan keterlibatan pengguna di platform distribusi game.
   
## Data Understanding
### Informasi Umum Dataset

Dataset yang digunakan dalam proyek ini adalah dataset **Video Games Sales** yang diambil dari Kaggle, yang mencakup data mengenai video game yang dirilis hingga 22 Desember 2016. Dataset ini berisi informasi tentang penjualan game, rating, dan berbagai fitur lainnya yang terkait dengan game.

#### Tautan Sumber Data:
- Dataset dapat diunduh melalui tautan berikut: [Video Games Sales Dataset on Kaggle](https://www.kaggle.com/datasets/therohk/million-airline-data)

#### Jumlah Data
- Dataset ini terdiri dari **16.598 baris** data yang mencakup 11 kolom.
- Setiap baris mewakili satu game yang telah dirilis, dengan informasi mengenai penjualan dan atribut lainnya.

### Kondisi Data
- Dataset ini berisi beberapa nilai kosong (missing values) pada beberapa kolom seperti `Critic_Score`, `User_Score`, dan `Rating`. Oleh karena itu, beberapa baris data perlu dibersihkan atau diproses sebelum digunakan dalam analisis atau model.
- Kolom yang mengandung nilai `NaN` perlu ditangani agar sistem rekomendasi dapat berjalan dengan lancar tanpa mengganggu perhitungan similarity antar game.

### Informasi Mengenai Variabel/Fitur dalam Dataset

Dataset ini memiliki beberapa variabel (fitur) yang digunakan untuk analisis dan pembuatan sistem rekomendasi, di antaranya:

1. **Name**:  
   - Tipe: Kategorikal  
   - Deskripsi: Nama dari game.
   
2. **Platform**:  
   - Tipe: Kategorikal  
   - Deskripsi: Platform tempat game ini dirilis, seperti 'Wii', 'PS4', 'PC', dll.

3. **Year_of_Release**:  
   - Tipe: Numerik  
   - Deskripsi: Tahun saat game tersebut dirilis. Beberapa nilai tahun mungkin hilang, sehingga harus diperiksa lebih lanjut.

4. **Genre**:  
   - Tipe: Kategorikal  
   - Deskripsi: Genre game, seperti 'Action', 'Sports', 'Racing', 'Platform', dll.

5. **Publisher**:  
   - Tipe: Kategorikal  
   - Deskripsi: Nama penerbit game, seperti 'Nintendo', 'EA Sports', dll.

6. **NA_Sales**:  
   - Tipe: Numerik  
   - Deskripsi: Penjualan game di wilayah North America (Amerika Utara), dalam juta unit.

7. **EU_Sales**:  
   - Tipe: Numerik  
   - Deskripsi: Penjualan game di wilayah Eropa, dalam juta unit.

8. **JP_Sales**:  
   - Tipe: Numerik  
   - Deskripsi: Penjualan game di wilayah Jepang, dalam juta unit.

9. **Other_Sales**:  
   - Tipe: Numerik  
   - Deskripsi: Penjualan game di wilayah lain, dalam juta unit.

10. **Global_Sales**:  
    - Tipe: Numerik  
    - Deskripsi: Total penjualan game secara global, dalam juta unit.

11. **Critic_Score**:  
    - Tipe: Numerik  
    - Deskripsi: Skor dari kritik atau ulasan profesional untuk game tersebut, dalam skala 1-100.

12. **Critic_Count**:  
    - Tipe: Numerik  
    - Deskripsi: Jumlah kritik yang memberikan ulasan untuk game tersebut.

13. **User_Score**:  
    - Tipe: Numerik  
    - Deskripsi: Skor yang diberikan oleh pengguna pada game tersebut, dalam skala 1-10.

14. **User_Count**:  
    - Tipe: Numerik  
    - Deskripsi: Jumlah pengguna yang memberikan skor untuk game tersebut.

15. **Developer**:  
    - Tipe: Kategorikal  
    - Deskripsi: Nama pengembang game.

16. **Rating**:  
    - Tipe: Kategorikal  
    - Deskripsi: Rating yang diberikan untuk game (misalnya, 'E' untuk Everyone, 'T' untuk Teen).

#### Keterangan
- **Data Missing**: Beberapa kolom seperti `Critic_Score`, `User_Score`, dan `Rating` mengandung nilai yang hilang. Penanganan nilai kosong ini akan dilakukan selama tahap preprocessing, seperti menghapus baris yang mengandung nilai `NaN` atau mengisi nilai kosong dengan estimasi berdasarkan distribusi data lainnya.
  
- **Variabel yang Digunakan untuk Rekomendasi**: Kolom **Name**, **Genre**, **Platform**, dan **Publisher** akan digunakan untuk membuat fitur yang akan digunakan dalam sistem rekomendasi berbasis konten.

Dengan memahami struktur dan kondisi data ini, kita dapat lebih mudah mempersiapkan data untuk proses **preprocessing** dan kemudian menggunakannya untuk membangun model rekomendasi berbasis konten yang lebih efektif.

## Data Preparation
Pada tahap ini, kami melakukan beberapa langkah untuk mempersiapkan data yang akan digunakan dalam pembangunan model sistem rekomendasi berbasis konten. Langkah-langkah ini termasuk pembersihan data, pengisian nilai kosong, serta transformasi data untuk memastikan bahwa dataset siap digunakan dalam analisis dan pembuatan model. Berikut adalah teknik yang diterapkan dalam persiapan data:

### 1. Menghapus Baris yang Mengandung Nilai Kosong

Langkah pertama adalah menghapus baris yang memiliki nilai kosong pada kolom yang penting untuk model, seperti **Name**, **Genre**, **Platform**, dan **User_Score**. Data yang tidak lengkap dapat mengganggu perhitungan kesamaan antar game, sehingga baris-baris yang tidak memiliki informasi ini dihapus.

```python
# Menghapus baris yang memiliki nilai kosong pada kolom penting
df_cleaned = df.dropna(subset=['Name', 'Genre', 'Platform', 'User_Score', 'Publisher'])
```
### 2. Mengatasi Nilai NaN pada Kolom Critic_Score dan User_Score

Beberapa kolom seperti Critic_Score dan User_Score mengandung nilai NaN. Untuk data numerik ini, kami memutuskan untuk mengisi nilai kosong dengan mean atau median skor dari kolom tersebut, karena nilai-nilai ini dapat memberi gambaran yang lebih representatif daripada menghapus seluruh baris.

```python
# Mengisi nilai kosong di 'Critic_Score' dengan nilai rata-rata
df_cleaned['Critic_Score'].fillna(df_cleaned['Critic_Score'].mean(), inplace=True)

# Mengisi nilai kosong di 'User_Score' dengan nilai rata-rata
df_cleaned['User_Score'].fillna(df_cleaned['User_Score'].mean(), inplace=True)
```
### 3. Menggabungkan Fitur Teks (Genre, Platform, Publisher)

Untuk keperluan sistem rekomendasi berbasis konten, kami menggabungkan kolom Genre, Platform, dan Publisher menjadi satu kolom content. Hal ini dilakukan untuk menyederhanakan representasi fitur yang akan digunakan dalam perhitungan kesamaan antar game.

```python
# Menggabungkan kolom Genre, Platform, dan Publisher untuk membuat fitur 'content'
df_cleaned['content'] = df_cleaned['Genre'] + ' ' + df_cleaned['Platform'] + ' ' + df_cleaned['Publisher']
```
### 4. Menghapus Duplikasi Game
Dataset ini mungkin mengandung duplikasi, misalnya game yang sama yang tercatat lebih dari sekali. Oleh karena itu, kami memeriksa dan menghapus duplikasi berdasarkan kolom Name.

```python
# Menghapus duplikasi berdasarkan kolom 'Name'
df_cleaned = df_cleaned.drop_duplicates(subset=['Name'])
```
### 5. Pengolahan Teks dengan TF-IDF Vectorizer
Selanjutnya, kami mengubah teks yang terdapat pada kolom content (gabungan dari Genre, Platform, dan Publisher) menjadi representasi numerik menggunakan TF-IDF Vectorizer. Ini memungkinkan kami untuk mengukur kesamaan antar game berdasarkan fitur teks.

```python
from sklearn.feature_extraction.text import TfidfVectorizer

# Membuat TF-IDF Matrix dari kolom 'content'
tfidf = TfidfVectorizer(stop_words='english')
tfidf_matrix = tfidf.fit_transform(df_cleaned['content'])
```

## Modeling

### 1. Pendekatan Model

#### 1.1. Pemilihan Model: Sistem Rekomendasi Berbasis Konten

Untuk menyelesaikan masalah yang dihadapi pengguna dalam mencari game yang sesuai dengan preferensi mereka, kami mengembangkan sistem rekomendasi berbasis konten yang menggunakan informasi tentang **genre**, **platform**, dan **publisher** game. Sistem ini mengandalkan **Cosine Similarity** untuk mengukur kesamaan antar game berdasarkan fitur teks yang telah digabungkan.

Sistem rekomendasi berbasis konten ini memanfaatkan teknik **TF-IDF Vectorizer** untuk mengubah teks (gabungan dari genre, platform, dan publisher) menjadi representasi numerik. Selanjutnya, kami menggunakan **Cosine Similarity** untuk menghitung seberapa mirip suatu game dengan game lainnya.

#### 1.2. Langkah-Langkah Pembangunan Model
1. **Data Preprocessing**:
   - Menghapus baris dengan nilai kosong pada kolom penting.
   - Mengisi nilai `NaN` dengan rata-rata pada kolom `Critic_Score` dan `User_Score`.
   - Menggabungkan kolom **Genre**, **Platform**, dan **Publisher** menjadi satu kolom **content**.
   
2. **Matriks TF-IDF**:
   - Menggunakan **TF-IDF Vectorizer** untuk mengubah teks dari kolom **content** menjadi fitur numerik.
   
3. **Menghitung Cosine Similarity**:
   - Menggunakan **Cosine Similarity** untuk mengukur kesamaan antara game berdasarkan fitur yang ada.

4. **Pemberian Rekomendasi**:
   - Fungsi `get_top_n_recommendations` digunakan untuk memberikan rekomendasi game yang paling mirip dengan game yang dipilih oleh pengguna, berdasarkan hasil perhitungan cosine similarity.

### 2. Hasil Model

Setelah membangun model rekomendasi, kami menguji sistem dengan memberikan rekomendasi untuk beberapa game populer dalam dataset. Berikut adalah contoh **Top-N Recommendation** untuk game **"Wii Sports"** yang dihasilkan oleh sistem rekomendasi berbasis konten.

#### 2.1. Contoh Top-10 Rekomendasi untuk Game "Wii Sports"

```python
# Mengambil 10 rekomendasi teratas untuk game "Wii Sports"
top_n_recommended_games = get_top_n_recommendations('Wii Sports', n=10)

# Menampilkan rekomendasi
print("Top 10 Rekomendasi untuk game 'Wii Sports':")
print(top_n_recommended_games)
```

## Evaluation

### 1. Pendahuluan
Pada bagian ini, sistem rekomendasi yang dikembangkan akan dievaluasi dengan menggunakan dua metrik utama: **Precision at K** dan **Recall at K**. Evaluasi dilakukan dengan cara mengukur seberapa baik sistem dalam merekomendasikan item yang relevan kepada pengguna berdasarkan daftar rekomendasi yang diberikan oleh sistem.

### 2. Metrik Evaluasi

#### 2.1 Precision at K
Precision at K adalah metrik yang mengukur proporsi item relevan di antara K rekomendasi teratas yang diberikan oleh sistem. Semakin tinggi nilai precision, semakin baik sistem dalam memberikan rekomendasi yang relevan.

#### 2.2 Recall at K
Recall at K adalah metrik yang mengukur proporsi item relevan yang ditemukan dalam K rekomendasi teratas dibandingkan dengan total jumlah item relevan yang ada. Metrik ini menunjukkan seberapa banyak item relevan yang ditemukan dalam daftar rekomendasi.

### 3. Implementasi dan Evaluasi

Pada bagian ini, dilakukan evaluasi terhadap sistem rekomendasi menggunakan dua metrik tersebut pada sebuah contoh kasus. Dalam hal ini, dilakukan evaluasi pada game **"Wii Sports"** dengan menggunakan data permainan yang relevan.

```python
# Fungsi Precision at K
def precision_at_k(recommended, relevant, k=10):
    recommended_at_k = recommended[:k]  # Mengambil K rekomendasi teratas
    relevant_recommended = [item for item in recommended_at_k if item in relevant]
    return len(relevant_recommended) / k

# Fungsi Recall at K
def recall_at_k(recommended, relevant, k=5):
    recommended_at_k = recommended[:k]  # Mengambil K rekomendasi teratas
    relevant_recommended = [item for item in recommended_at_k if item in relevant]
    return len(relevant_recommended) / len(relevant)

# Contoh Evaluasi untuk game "Wii Sports"
recommended_games = get_top_n_recommendations('Wii Sports')
# Misalkan kita punya daftar game relevan untuk "Wii Sports" (berdasarkan genre atau rating yang serupa)
relevant_games = ['Super Mario Bros.', 'Mario Kart Wii', 'Wii Sports Resort', 'Pokemon Red/Pokemon Blue']

# Menghitung Precision at 5 dan Recall at 5
precision = precision_at_k(recommended_games.tolist(), relevant_games, k=5)
recall = recall_at_k(recommended_games.tolist(), relevant_games, k=5)

# Menampilkan hasil
print(f"Precision at 5: {precision}")
print(f"Recall at 5: {recall}")
```

