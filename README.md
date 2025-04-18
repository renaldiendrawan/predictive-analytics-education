# Laporan Proyek Machine Learning - Analisis Performa Akademik Siswa

## Domain Proyek

Latar belakang:
Dalam dunia pendidikan, pemahaman terhadap faktor-faktor yang memengaruhi performa siswa sangat penting untuk meningkatkan kualitas pembelajaran. Banyak lembaga pendidikan kini memanfaatkan data untuk membuat keputusan berbasis bukti, termasuk dalam hal prediksi hasil belajar siswa.

Masalah ini penting diselesaikan karena bisa membantu pihak sekolah dan pemerintah untuk:
- Menentukan intervensi akademik lebih awal.
- Menyusun program pembelajaran yang lebih personal.
- Meningkatkan tingkat kelulusan siswa.

## Business Understanding

### Problem Statements
1. Bagaimana cara memprediksi apakah seorang siswa akan lulus mata pelajaran matematika, membaca, dan menulis?
2. Fitur demografis dan sosial apa yang paling memengaruhi performa akademik siswa?

### Goals
1. Mengembangkan model klasifikasi untuk memprediksi kelulusan siswa pada tiga mata pelajaran utama.
2. Mengidentifikasi fitur-fitur yang paling memengaruhi nilai siswa dengan pendekatan regresi.

### Solution Statements
- Menggunakan model Logistic Regression untuk klasifikasi kelulusan siswa.
- Menggunakan Linear Regression untuk prediksi nilai numerik dan analisis pentingnya fitur.
- Metrik evaluasi: Accuracy, Precision, Recall, F1-score (untuk klasifikasi) dan RMSE (untuk regresi).

## Data Understanding

Sumber data: [Kaggle - Students Performance](https://www.kaggle.com/datasets/spscientist/students-performance-in-exams)

Jumlah data:
- Baris: 1000
- Kolom: 8 (fitur asli), plus fitur turunan klasifikasi

Kondisi data:
- Tidak ada missing values.
- Tidak ada duplikat.
- Tidak ditemukan outlier ekstrem karena skor dibatasi 0-100.

Fitur:
- gender: jenis kelamin siswa
- race/ethnicity: kelompok etnis
- parental level of education: tingkat pendidikan orang tua
- lunch: status makan siang (standar atau subsidi)
- test preparation course: apakah mengikuti pelatihan ujian
- math score, reading score, writing score: nilai ujian siswa

## Data Preparation

- Label encoding fitur kategorikal menggunakan one-hot encoding.
- Membuat label klasifikasi baru untuk masing-masing pelajaran dengan batas kelulusan 65.
- Split data: 80% train, 20% test.

Alasan:
- Label encoding dibutuhkan untuk model ML berbasis numerik.
- Split agar dapat mengevaluasi generalisasi model.

## Modeling

### Model 1: Logistic Regression (Klasifikasi)
**Cara kerja**: Model mengestimasi probabilitas kelulusan berdasarkan logit dari kombinasi linear fitur input.
**Parameter**: max_iter=1000 (default lainnya digunakan).
**Output**: prediksi lulus atau tidak, untuk masing-masing mata pelajaran.

### Model 2: Linear Regression (Regresi)
**Cara kerja**: Model menghitung garis terbaik untuk memprediksi nilai berdasarkan fitur input.
**Parameter**: default.
**Output**: prediksi nilai numerik untuk setiap pelajaran.

## Evaluation

### Klasifikasi
Metrik: Accuracy, Precision, Recall, F1-score

- Accuracy: proporsi prediksi benar.
- Precision: dari semua prediksi positif, berapa yang benar.
- Recall: dari semua data positif, berapa yang terprediksi.
- F1: harmonisasi precision dan recall.

**Hasil**:
Model cukup baik dengan accuracy di atas 70% pada ketiga mata pelajaran.

### Regresi
Metrik: RMSE (Root Mean Squared Error)

- Mengukur rata-rata kesalahan prediksi.
- Lebih kecil → lebih baik.

**Hasil**:
- RMSE nilai matematika: ~11
- RMSE nilai membaca: ~9
- RMSE nilai menulis: ~10
