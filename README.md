# dynamic-pricing-insurance-reinforcement-learning
Implementasi algoritma Deep Q-Network (DQN) untuk sistem penetapan harga dinamis pada asuransi kesehatan berdasarkan profil risiko.

Proyek ini bertujuan untuk menyelesaikan tantangan penetapan tarif premi di industri asuransi kesehatan dengan memanfaatkan algoritma kecerdasan buatan adaptif.

Dengan menggunakan algoritma Deep Q-Network (DQN), proyek ini membangun agen kecerdasan buatan yang mampu menyesuaikan pengali premi asuransi kesehatan secara dinamis berdasarkan profil risiko demografis pasien individu. Tujuan utama agen ini adalah untuk mengoptimalkan profitabilitas perusahaan asuransi sekaligus menghindari penalti berat yang diakibatkan oleh penetapan harga yang terlalu eksploitatif.

---

## Peringatan Kompatibilitas Lingkungan Python

Penting untuk diperhatikan bahwa proyek ini memiliki persyaratan spesifik terkait versi Python:

**Proyek ini wajib dijalankan pada lingkungan Python versi 3.12.**

Dilarang keras menggunakan Python versi 3.13. Beberapa dependensi utama yang menggerakkan model ini (seperti versi spesifik dari Gymnasium, Stable Baselines3, maupun struktur internal PyTorch) belum memiliki dukungan penuh untuk Python 3.13, sehingga eksekusi pada versi tersebut akan menyebabkan kegagalan instalasi maupun kesalahan sistem (error) secara langsung.

---

## Struktur File pada Repositori Ini

Repositori ini terdiri dari berbagai berkas yang disusun berdasarkan tahapan pengembangan. Berikut adalah penjelasan fungsionalitas dari masing-masing berkas:

1. **`01_preprocessing_dan_environment.ipynb`**
   Berkas ini mencakup tahapan awal yang berfokus pada eksplorasi data, prapemrosesan dataset (normalisasi fitur numerik dan penyandian fitur kategorikal), serta pendefinisian lingkungan kustom (Custom Environment) berbasis Gymnasium yang mengatur logika state, aksi, dan fungsi reward (keuntungan dan penalti).

2. **`02_pelatihan_dqn.ipynb`**
   Berkas ini mengimplementasikan logika pelatihan agen Deep Q-Network (DQN). Berkas ini menginisialisasi arsitektur jaringan syaraf tiruan, mendefinisikan seluruh hyperparameter, serta memuat proses iterasi pembelajaran agen terhadap lingkungan simulasi.

3. **`03_evaluasi_dan_qtable.ipynb`**
   Berkas ini digunakan untuk melakukan evaluasi performa model yang telah dilatih. Evaluasi dilakukan dengan membandingkan metrik keuntungan yang didapat agen DQN melawan strategi statis (baseline), serta mengekstrak nilai estimasi aksi (Q-Value) untuk diinterpretasikan ke dalam bentuk peta panas (heatmap).

4. **`04_full_pipeline.ipynb`**
   Berkas ini merupakan versi terpadu (lengkap) yang menggabungkan ketiga tahap di atas ke dalam satu rangkaian eksekusi mulai dari prapemrosesan awal hingga penyimpanan artefak evaluasi akhir. Pengguna yang ingin menjalankan kode secara keseluruhan dalam satu waktu dapat menggunakan berkas ini.

5. **`medical_insurance.csv`**
   Berkas dataset yang digunakan sebagai fondasi profil pasien. Dataset ini memuat informasi demografis seperti umur, jenis kelamin, indeks massa tubuh (BMI), tanggungan, status diskon (sebagai proksi risiko kesehatan), wilayah tempat tinggal, pengeluaran klaim medis, dan premi dasar.

6. **`requirements.txt`**
   Berkas yang merangkum daftar seluruh pustaka (library) Python eksternal beserta versinya yang dibutuhkan agar proyek dapat berjalan tanpa kendala teknis.

7. **`project_explanation.md`**
   Berkas dokumentasi teoretis yang menyajikan paparan analisis mendalam mengenai latar belakang penetapan harga dinamis, justifikasi penggunaan pendekatan Markov Decision Process (MDP), penjelasan fungsi komponen agen cerdas, serta kesimpulan interpretatif dari hasil evaluasi akhir.

---

## Panduan Instalasi dan Eksekusi

Silakan ikuti instruksi formal berikut untuk memastikan bahwa lingkungan kerja Anda sudah siap sebelum mengeksekusi kode:

### 1. Inisialisasi Repositori Lokal
Salin (clone) repositori ini ke dalam komputer lokal Anda:
```bash
git clone https://github.com/username_anda/dynamic-pricing-rl.git
cd dynamic-pricing-rl
```

### 2. Penyiapan Lingkungan Virtual Python 3.12
Penggunaan lingkungan virtual sangat direkomendasikan agar tidak terjadi benturan pustaka pada sistem operasi Anda.
```bash
# Pastikan Anda menggunakan Python versi 3.12
python3.12 -m venv venv

# Aktivasi lingkungan virtual untuk Mac/Linux:
source venv/bin/activate

# Aktivasi lingkungan virtual untuk Windows:
venv\Scripts\activate
```

### 3. Instalasi Pustaka Dependensi
Setelah lingkungan virtual aktif, jalankan perintah instalasi menggunakan daftar yang telah disediakan:
```bash
pip install -r requirements.txt
```

### 4. Eksekusi Proyek (Jupyter Notebook)
1. Instal antarmuka Jupyter pada lingkungan virtual Anda apabila belum tersedia:
   ```bash
   pip install jupyter
   ```
2. Jalankan peladen lokal Jupyter:
   ```bash
   jupyter notebook
   ```
3. Melalui antarmuka peramban (browser) yang terbuka secara otomatis, akses berkas `04_full_pipeline.ipynb`.
4. Jalankan kode mulai dari sel pertama hingga sel terakhir secara berurutan. Berkas akan mengeksekusi seluruh tahapan prapemrosesan, pelatihan agen selama ratusan ribu iterasi, hingga mencetak evaluasi metrik kinerja keuangan asuransi yang memperlihatkan keunggulan kecerdasan buatan.
