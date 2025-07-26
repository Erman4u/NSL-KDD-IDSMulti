NSL-KDD: Sistem Deteksi Intrusi Jaringan Multi-Kelas
!(https://placehold.co/800x400/aabbcc/ffffff?text=Deteksi+Intrusi+Jaringan+Multi-Kelas)

Proyek ini adalah aplikasi web sederhana berbasis Flask untuk mendeteksi berbagai jenis intrusi (serangan) dan trafik normal pada jaringan menggunakan beberapa model Machine Learning yang berbeda. Pengguna dapat memasukkan parameter trafik jaringan dan memilih model klasifikasi yang ingin digunakan untuk prediksi.

Fitur Utama
Pilihan Model: Pengguna dapat memilih antara berbagai model Machine Learning untuk prediksi, termasuk:

Logistic Regression

Random Forest

Support Vector Machine (SVM)

Naive Bayes

K-Nearest Neighbors (KNN)

Prediksi Multi-Kelas: Model akan memprediksi kategori intrusi spesifik (misalnya, DoS, Probe, R2L, U2R) atau mengidentifikasi trafik sebagai Normal.

Probabilitas Kelas: Menampilkan probabilitas untuk setiap kelas yang mungkin, memberikan pemahaman yang lebih baik tentang keyakinan model terhadap setiap kategori.

Isi Data Contoh: Tombol praktis untuk mengisi formulir dengan contoh data trafik "Normal" atau berbagai jenis serangan (DoS, Probe, R2L, U2R) untuk pengujian cepat.

Antarmuka Pengguna Sederhana: Antarmuka berbasis web yang intuitif untuk memasukkan data trafik.

Struktur Proyek
NSL-KDD/
├── app.py                  # Aplikasi utama Flask
├── model/
│   ├── logistic_regression_model.pkl
│   ├── random_forest_model.pkl
│   ├── svm_model.pkl
│   ├── naive_bayes_model.pkl
│   ├── knn_model.pkl
│   ├── encoder_flag.pkl
│   ├── encoder_protocol_type.pkl
│   ├── encoder_service.pkl
│   ├── scaler.pkl
│   └── target_encoder.pkl  # (Opsional) Encoder untuk label target, atau digunakan untuk validasi kelas
└── templates/
    └── index.html          # UI/UX form input & hasil prediksi

Model yang Digunakan
Proyek ini menggunakan model-model klasifikasi berikut yang telah dilatih pada dataset deteksi intrusi jaringan (seperti NSL-KDD):

Logistic Regression: Model linier untuk klasifikasi.

Random Forest: Ensemble dari decision tree yang kuat, baik untuk data kompleks.

Support Vector Machine (SVM): Model yang mencari hyperplane optimal untuk memisahkan kelas.

Naive Bayes (GaussianNB): Model probabilistik berdasarkan Teorema Bayes.

K-Nearest Neighbors (KNN): Model berbasis instansi yang mengklasifikasikan data berdasarkan tetangga terdekat.

Semua model dan preprocessor (seperti LabelEncoder untuk fitur kategorikal dan StandardScaler untuk fitur numerik) disimpan dalam format .pkl di direktori model/.

Persyaratan Sistem
Python 3.x

pip (manajer paket Python)

Instalasi dan Setup
Ikuti langkah-langkah di bawah ini untuk menjalankan aplikasi di lingkungan lokal Anda:

Kloning Repositori:
Buka Command Prompt (CMD) atau terminal Anda dan kloning repositori ini:

git clone https://github.com/NamaPenggunaAnda/Deteksi-Intrusi-Jaringan.git
cd Deteksi-Intrusi-Jaringan

(Ganti NamaPenggunaAnda/Deteksi-Intrusi-Jaringan.git dengan URL repositori Anda yang sebenarnya.)

Buat dan Aktifkan Virtual Environment (Sangat Disarankan):
Sangat disarankan untuk menggunakan virtual environment untuk mengelola dependensi.

python -m venv venv

Untuk Windows:

.\venv\Scripts\activate

Untuk macOS/Linux:

source venv/bin/activate

Instal Dependensi:
Setelah virtual environment aktif, instal semua library yang diperlukan:

pip install Flask joblib pandas scikit-learn

Siapkan Model (Penting!):
Pastikan Anda telah melatih dan menyimpan semua model (logistic_regression_model.pkl, random_forest_model.pkl, svm_model.pkl, naive_bayes_model.pkl, knn_model.pkl) serta preprocessor (encoder_flag.pkl, encoder_protocol_type.pkl, encoder_service.pkl, scaler.pkl) di dalam folder model/ di direktori proyek Anda. Jika Anda tidak memiliki model-model ini, aplikasi tidak akan berjalan.

Jika Anda menggunakan target_encoder.pkl untuk inverse transform label target (meskipun aplikasi ini menggunakan pemetaan langsung), pastikan file tersebut juga ada di folder model/.

Menjalankan Aplikasi
Setelah semua dependensi terinstal dan virtual environment aktif, Anda dapat menjalankan aplikasi Flask:

python app.py

Anda akan melihat output di terminal yang menunjukkan bahwa aplikasi sedang berjalan. Cari baris seperti:

 * Running on http://127.0.0.1:5000

Mengakses Aplikasi
Buka browser web Anda dan kunjungi alamat yang tertera di terminal (biasanya http://127.0.0.1:5000/ atau http://localhost:5000/).

Cara Menggunakan Aplikasi
Pilih Model: Gunakan dropdown "Pilih Model" untuk memilih salah satu model klasifikasi yang tersedia.

Isi Data Trafik:

Anda dapat mengisi setiap kolom input secara manual dengan nilai-nilai trafik jaringan.

Atau, gunakan tombol "Isi Contoh Normal", "Isi Contoh DoS", "Isi Contoh Probe", "Isi Contoh R2L", atau "Isi Contoh U2R" untuk mengisi formulir secara otomatis dengan contoh data spesifik.

Lakukan Prediksi: Klik tombol "Prediksi".

Lihat Hasil: Hasil prediksi (Prediksi Kelas: [Nama Kelas]) dan probabilitas untuk setiap kelas akan ditampilkan di bawah formulir.

Catatan Penting
Mode Debug: Aplikasi berjalan dalam mode debug (debug=True) untuk pengembangan. Jangan gunakan mode ini untuk deployment produksi.

Versi Scikit-learn: Anda mungkin melihat peringatan InconsistentVersionWarning jika versi scikit-learn saat model dilatih berbeda dengan versi yang terinstal. Untuk mengatasi ini, disarankan untuk melatih ulang model Anda dengan versi scikit-learn yang sama dengan yang Anda gunakan untuk deployment, atau sesuaikan versi scikit-learn di virtual environment Anda.

Selamat menggunakan aplikasi Deteksi Intrusi Jaringan ini!
