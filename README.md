# 🎓 Student Success Classification Model
Nama : Sofia Ramanda
NIM  : TI22250040
Kelas: Tekhnik Informatika B
Mata Kuliah : Analisis Algoritma

Repository ini berisi proyek analisis data dan pembangunan model machine learning untuk memprediksi risiko kelulusan mahasiswa (**Lulus [0]** atau **Gagal [1]**). Proyek ini disusun sebagai pemenuhan tugas klasifikasi data menggunakan Python (Jupyter Notebook / Google Colab) secara end-to-end.

---

## 📌 Daftar Isi
- [Latar Belakang & Tujuan](#-latar-belakang--tujuan)
- [Struktur Repositori](#-struktur-repositori)
- [Tahapan Pengerjaan](#-tahapan-pengerjaan)
  1. [Data Understanding](#1-data-understanding)
  2. [EDA & Pemrosesan Data](#2-eda--pemrosesan-data)
  3. [Persiapan Data](#3-persiapan-data)
  4. [Modeling](#4-modeling)
  5. [Evaluasi Model](#5-evaluasi-model)
  6. [Tes Prediksi Data Random](#6-tes-prediksi-data-random)
- [Persyaratan System & Library](#-persyaratan-system--library)
- [Cara Menggunakan](#-cara-menggunakan)

---

## 🎯 Latar Belakang & Tujuan

Deteksi dini terhadap mahasiswa yang berisiko gagal sangat penting bagi lembaga pendidikan untuk memberikan intervensi atau bimbingan akademik secara tepat waktu. 

**Tujuan Utama:**
- Membangun model klasifikasi yang akurat untuk memprediksi kelas **Gagal (1)** dan **Lulus (0)**.
- Menentukan faktor/fitur paling dominan yang memengaruhi kelulusan mahasiswa.
- Menguji ketahanan model menggunakan data acak baru (simulasi real-world).

---

## 📂 Struktur Repositori

```text
├── data/
│   └── original.csv            # Dataset utama (input)
├── notebooks/
│   └── student_classification.ipynb  # Jupyter Notebook utama
├── reports/
│   └── student_classification.pdf    # Ekspor dokumen hasil notebook
├── README.md                   # Dokumentasi proyek
└── requirements.txt            # Library Python yang dibutuhkan
```

---

## 🛠️ Tahapan Pengerjaan

### 1. Data Understanding
- Memuat dataset `original.csv` dan memeriksa dimensi, tipe data, serta 5 baris pertama.
- Menganalisis distribusi variabel target (`target`).
- **Analisis Imbalance Data:** Mengidentifikasi ketidakseimbangan kelas antara proporsi mahasiswa lulus dan gagal.

### 2. EDA dan Pemrosesan Data
- **Pembersihan Data:** Identifikasi serta penanganan nilai kosong (*missing values*) dan duplikasi data.
- **Visualisasi Exploratory:**
  - Histogram & Boxplot fitur numerik.
  - Perbandingan distribusi fitur berdasarkan kelas label.
  - Heatmap korelasi variabel.
- **Handling Outlier:** Deteksi nilai abnormal (seperti nilai 0 pada kolom kuintil) dan penanganan yang sesuai.

### 3. Persiapan Data
- **Feature Selection:** Eliminasi fitur yang redundan/tidak relevan.
- **Train-Test Split:** Pembagian data $80:20$ dengan metode *Stratified Sampling* (`stratify=y`) untuk mempertahankan proporsi label.
- **Feature Scaling:** Penskalaan fitur menggunakan `StandardScaler`.
- **Handling Imbalance Class:** Penerapan teknik **SMOTE** (*Synthetic Minority Over-sampling Technique*) khusus pada data latih (*training set*) untuk mencegah kebocoran data (*data leakage*).

### 4. Modeling
- Membandingkan dua algoritma Machine Learning:
  1. **Logistic Regression** (Baseline model)
  2. **Random Forest Classifier** (Ensemble tree-based model)
- Melakukan **Cross-Validation (5-fold)** dan tuning hyperparameter menggunakan `GridSearchCV`.

### 5. Evaluasi Model
- Evaluasi performa pada data uji (*test set*) menggunakan:
  - Confusion Matrix
  - Accuracy, Precision, Recall, dan F1-Score.
- Metrik **Recall** dan **F1-Score** diprioritaskan untuk meminimalisir kesalahan *False Negative* (mahasiswa gagal yang terprediksi lulus).
- Analisis *Feature Importance* untuk menentukan variabel paling berpengaruh.

### 6. Tes Prediksi dengan Data Random
- Membuat 5 data mahasiswa baru secara sintetis menggunakan `numpy.random` dalam rentang nilai batas tiap fitur.
- Melakukan prapemrosesan (scaling) menggunakan *transformer* yang disesuaikan dengan data latih.
- Menampilkan hasil prediksi klasifikasi beserta nilai probabilitas kegagalannya.

---

## 💻 Persyaratan System & Library

Proyek ini membutuhkan Python versi `3.8+` dan library berikut:

```bash
pandas>=1.3.0
numpy>=1.21.0
matplotlib>=3.4.0
seaborn>=0.11.0
scikit-learn>=1.0.0
imbalanced-learn>=0.8.0
```

---

## 🚀 Cara Menggunakan

1. **Clone repositori ini:**
   ```bash
   git clone https://github.com/username/student-success-classification.git
   cd student-success-classification
   ```

2. **Install dependency:**
   ```bash
   pip install -r requirements.txt
   ```

3. **Jalankan Jupyter Notebook:**
   ```bash
   jupyter notebook notebooks/student_classification.ipynb
   ```
   *Atau buka file `.ipynb` langsung melalui Google Colab.*

---
*Dibuat untuk memenuhi Tugas Klasifikasi Machine Learning.*
