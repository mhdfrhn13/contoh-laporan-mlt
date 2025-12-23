# Proyek Klasifikasi Gambar Fashion MNIST dengan CNN

## Deskripsi Proyek
Proyek ini bertujuan untuk membangun dan melatih model Convolutional Neural Network (CNN) menggunakan TensorFlow dan Keras untuk mengklasifikasikan gambar dari dataset Fashion MNIST. Model ini dirancang untuk mengidentifikasi 10 kategori item pakaian yang berbeda.

Dataset Fashion MNIST terdiri dari 70.000 gambar skala abu-abu (grayscale) berukuran 28x28 piksel dari 10 kelas pakaian. Model yang dikembangkan di sini menggunakan arsitektur Sequential dengan lapisan Conv2D dan Pooling Layer untuk mencapai akurasi klasifikasi yang tinggi.

## Fitur Proyek
- **Klasifikasi Gambar**: Mengidentifikasi kategori pakaian dari gambar input.
- **Dataset**: Menggunakan dataset Fashion MNIST yang populer.
- **Model CNN**: Implementasi model Sequential dengan lapisan Conv2D, MaxPooling2D, dan BatchNormalization.
- **Pembagian Data**: Dataset dibagi menjadi Train Set, Validation Set, dan Test Set.
- **Visualisasi**: Plot akurasi dan loss model selama pelatihan.
- **Penyimpanan Model**: Model disimpan dalam berbagai format untuk deployment yang berbeda:
    - SavedModel
    - TF-Lite
    - TFJS (TensorFlow.js)
    - File Labels: Menyertakan file `labels.txt` untuk interpretasi output model TF-Lite.

## Struktur Direktori
Proyek ini akan menghasilkan struktur direktori sebagai berikut:

├── fashion_mnist_classification.ipynb # Notebook Colab/Jupyter utama
└── fashion_mnist_model/ # Direktori output model
├── saved_model/ # Model dalam format SavedModel
│ ├── saved_model.pb
│ └── variables/
│ └── ...
├── fashion_mnist_model.tflite # Model dalam format TensorFlow Lite
├── labels.txt # File teks dengan nama kelas untuk TF-Lite
└── tfjs_model/ # Model dalam format TensorFlow.js
├── model.json
└── weights.bin


## Persyaratan Sistem
- **Python 3.7+**
- **TensorFlow 2.x**
- **NumPy**
- **Matplotlib**
- **TensorFlow.js** (untuk menyimpan model ke format TFJS)

## Instalasi dan Setup

### Clone Repositori (Opsional)
Jika ada repositori yang tersedia, clone menggunakan perintah berikut:
```bash
git clone <URL_REPOSitori_ANDA>
cd <NAMA_FOLDER_REPOSitori>
```

Buat Lingkungan Virtual (Opsional, tapi Direkomendasikan)
python -m venv venv
source venv/bin/activate  # Linux/macOS
# venv\Scripts\activate   # Windows

Buat Lingkungan Virtual (Opsional, tapi Direkomendasikan)
pip install tensorflow numpy matplotlib
pip install tensorflowjs # Diperlukan untuk menyimpan model TFJS

Catatan untuk Google Colab:
Jika Anda menjalankan ini di Google Colab, Anda tidak perlu menginstal Python atau lingkungan virtual. Cukup jalankan perintah instalasi tensorflowjs di salah satu cell notebook:
```!pip install tensorflowjs```

Cara Menjalankan Proyek
Buka Notebook:
Buka file fashion_mnist_classification.ipynb menggunakan Google Colab atau Jupyter Notebook.

Jalankan Setiap Cell:
Jalankan setiap cell secara berurutan dari atas ke bawah. Notebook sudah terstruktur dengan langkah-langkah yang jelas:
- Mengimpor library.
- Memuat dan memproses dataset Fashion MNIST.
- Membagi data menjadi train, validation, dan test set.
- Membangun arsitektur model CNN.
- Melatih model.
- Mengevaluasi model pada test set.
- Membuat plot akurasi dan loss.
- Menyimpan model ke berbagai format (.tflite, SavedModel, TFJS) dan membuat labels.txt.

Periksa Output:
Setelah semua cell dijalankan, Anda akan melihat output di konsol, termasuk ringkasan model, metrik pelatihan, dan akurasi evaluasi. Plot akurasi dan loss akan ditampilkan. Direktori fashion_mnist_model juga akan dibuat, berisi model yang telah disimpan dan file labels.txt.

Hasil yang Diharapkan
Model diharapkan mencapai akurasi di atas 85% pada training dan testing set. Plot akan menunjukkan konvergensi loss dan peningkatan akurasi selama pelatihan.

Cara Menggunakan Model yang Disimpan
SavedModel: Dapat dimuat kembali di TensorFlow/Keras untuk inferensi lebih lanjut atau pelatihan lanjutan.

python
import tensorflow as tf
loaded_model = tf.keras.models.load_model('fashion_mnist_model/saved_model')
TF-Lite: Cocok untuk deployment pada perangkat mobile (Android, iOS) atau embedded device. File labels.txt akan digunakan bersama dengan model .tflite untuk menginterpretasikan hasil prediksi.

TFJS: Ideal untuk deployment model di lingkungan web (browser) menggunakan JavaScript.

Kontribusi
Kontribusi disambut baik! Jika Anda ingin berkontribusi pada proyek ini, silakan fork repositori, buat branch baru, dan ajukan pull request dengan perubahan Anda.

Lisensi
Proyek ini dilisensikan di bawah MIT License.










