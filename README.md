# 📘 Laporan Proyek Machine Learning - Analisis Performa Akademik Siswa

## 🧠 Domain Proyek

Dalam dunia pendidikan, pemahaman terhadap faktor-faktor yang memengaruhi performa siswa sangat penting untuk meningkatkan kualitas pembelajaran. Banyak lembaga pendidikan kini memanfaatkan data untuk membuat keputusan berbasis bukti, termasuk dalam hal prediksi hasil belajar siswa.

**Manfaat proyek ini:**
- Menentukan intervensi akademik lebih awal.
- Menyusun program pembelajaran yang lebih personal.
- Meningkatkan tingkat kelulusan siswa.

---

## 🎯 Business Understanding

### Problem Statements
1. Bagaimana cara memprediksi apakah seorang siswa akan lulus mata pelajaran matematika, membaca, dan menulis?
2. Fitur demografis dan sosial apa yang paling memengaruhi performa akademik siswa?

### Goals
1. Mengembangkan model klasifikasi untuk memprediksi kelulusan siswa pada tiga mata pelajaran utama.
2. Mengidentifikasi fitur-fitur yang paling memengaruhi nilai siswa dengan pendekatan regresi.

### Solution Statements
- Menggunakan Logistic Regression untuk klasifikasi kelulusan siswa.
- Menggunakan Linear Regression untuk memprediksi skor nilai dan menganalisis kontribusi fitur.
- Metrik evaluasi yang digunakan:  
  - **Klasifikasi**: Accuracy, Precision, Recall, F1-Score  
  - **Regresi**: RMSE

---

## 📊 Data Understanding

- **Sumber data**: [Kaggle - Students Performance](https://www.kaggle.com/datasets/spscientist/students-performance-in-exams)
- **Jumlah data**: 1000 baris, 8 kolom (fitur asli), dengan penambahan fitur klasifikasi.
- **Kondisi data**:
  - Tidak ada missing value
  - Tidak ada data duplikat
  - Skor dibatasi antara 0–100 (tidak ada outlier ekstrem)

### Fitur:
- `gender`: jenis kelamin siswa  
- `race/ethnicity`: kelompok etnis  
- `parental level of education`: pendidikan terakhir orang tua  
- `lunch`: status subsidi makan siang  
- `test preparation course`: apakah mengikuti pelatihan ujian  
- `math score`, `reading score`, `writing score`: nilai ujian siswa

---

## 🧹 Data Preparation

- Encoding fitur kategorikal (One-hot encoding)
- Membuat label klasifikasi kelulusan (threshold 65)
- Split data: 80% training, 20% testing

> Tujuan: memastikan data siap untuk proses machine learning dan evaluasi model.

---

## 🤖 Modeling

### Model 1: Logistic Regression (Klasifikasi)
- **Cara kerja**: Mengestimasi probabilitas kelulusan berdasarkan fungsi logit.
- **Parameter**: `max_iter=1000` (default lainnya digunakan)
- **Output**: Prediksi kelulusan (lulus/gagal) untuk setiap mata pelajaran.

### Model 2: Linear Regression (Regresi)
- **Cara kerja**: Mencari hubungan linier antara fitur dan skor ujian.
- **Parameter**: Default
- **Output**: Prediksi nilai numerik untuk matematika, membaca, dan menulis.

---

## ✅ Evaluation

### Klasifikasi
- **Metrik**: Accuracy, Precision, Recall, F1-score
- **Interpretasi**:
  - Accuracy: seberapa banyak prediksi yang tepat
  - Precision: ketepatan prediksi kelulusan
  - Recall: kemampuan model mendeteksi siswa yang benar-benar lulus
  - F1: rata-rata harmonis antara precision dan recall

**Hasil**:  
Model memberikan hasil baik, dengan accuracy berkisar di atas 66% dan recall cukup tinggi (~77%) menunjukkan model efektif mengenali siswa yang akan lulus.

### Regresi
- **Metrik**: RMSE (Root Mean Squared Error)
- **Interpretasi**: Rata-rata kesalahan prediksi nilai siswa.

**Hasil**:
- RMSE Matematika: ~14.16
- RMSE Membaca: ~11
- RMSE Menulis: ~10

Model regresi memiliki performa yang cukup baik untuk memperkirakan skor siswa.
