# 🧬 Klasifikasi Potensi Keberhasilan Imunoterapi pada Kanker Ovarium

> Perbandingan performa **Random Forest**, **Decision Tree**, dan **Logistic Regression** dalam memprediksi respons imunoterapi pada pasien kanker ovarium menggunakan data klinis TCGA.

---

## 📌 Latar Belakang

Kanker ovarium merupakan salah satu keganasan ginekologi dengan tingkat mortalitas tertinggi. Imunoterapi hadir sebagai modalitas pengobatan yang menjanjikan, namun tidak semua pasien memberikan respons yang sama. Kemampuan untuk memprediksi potensi keberhasilan imunoterapi secara dini dapat membantu klinisi dalam pengambilan keputusan terapeutik yang lebih tepat sasaran.

Proyek ini memanfaatkan pendekatan **machine learning** untuk mengklasifikasikan pasien berdasarkan potensi respons mereka terhadap imunoterapi, menggunakan data klinis genomik dari **TCGA (The Cancer Genome Atlas) — Ovarian Cancer (OV)**.

---

## 🎯 Tujuan

- Membangun model klasifikasi prediktif yang dapat membedakan pasien dengan potensi keberhasilan imunoterapi **tinggi** dan **rendah**.
- Membandingkan performa tiga algoritma machine learning: Random Forest, Decision Tree, dan Logistic Regression.
- Menghindari *data leakage* dengan memisahkan biomarker pembuat label dari fitur training.

---

## 🔬 Metodologi

### 1. Sumber Data
Dataset klinis kanker ovarium dari **TCGA OV** (`ov_tcga_clinicaldata.tsv`), yang mencakup informasi genomik dan klinis pasien.

### 2. Pembuatan Label
Label klasifikasi dibuat berdasarkan dua biomarker imunoterapi klinis yang sudah tervalidasi:

| Biomarker | Keterangan |
|-----------|-----------|
| **TMB** (Tumor Mutational Burden) | Beban mutasi tumor — tinggi TMB mengindikasikan respons imunoterapi lebih baik |
| **MSIsensor Score** | Skor ketidakstabilan mikrosatelit — MSI-high berkaitan dengan respons imunoterapi positif |

Pasien diklasifikasikan sebagai **Berpotensi Berhasil** jika memenuhi ambang batas TMB dan MSI yang ditentukan.

### 3. Pencegahan Data Leakage
Setelah label dibuat, kolom **TMB** dan **MSIsensor Score** dihapus dari dataset fitur training untuk mencegah kebocoran informasi (*data leakage*) dan memastikan model belajar dari fitur klinis lainnya.

### 4. Algoritma yang Diuji

| Algoritma | Keunggulan |
|-----------|-----------|
| 🌲 **Random Forest** | Ensemble method, robust terhadap overfitting |
| 🌿 **Decision Tree** | Mudah diinterpretasi, transparan |
| 📈 **Logistic Regression** | Baseline yang kuat, efisien secara komputasi |

---

## 📁 Struktur Repository

```
├── penelitian_imunoterapi_FINAL.ipynb      # Notebook utama: analisis & pemodelan lengkap
├── ov_tcga_clinicaldata.tsv                # Dataset klinis TCGA OV
├── alur_penelitian_revisi_sesuai_petunjuk.png  # Diagram alur penelitian
└── README.md
```

---

## 🛠️ Teknologi & Library

- **Bahasa**: Python 3
- **Environment**: Jupyter Notebook
- **Library utama**:
  - `pandas`, `numpy` — manipulasi dan analisis data
  - `scikit-learn` — pemodelan machine learning
  - `matplotlib`, `seaborn` — visualisasi data

---

## 🚀 Cara Menjalankan

1. Clone repository ini:
   ```bash
   git clone https://github.com/faara-armadhanni/KLASIFIKASI-POTENSI-KEBERHASILAN-IMUNOTERAPI-PADA-KANKER-OVARIUM.git
   cd KLASIFIKASI-POTENSI-KEBERHASILAN-IMUNOTERAPI-PADA-KANKER-OVARIUM
   ```

2. Install dependensi yang dibutuhkan:
   ```bash
   pip install pandas numpy scikit-learn matplotlib seaborn jupyter
   ```

3. Jalankan Jupyter Notebook:
   ```bash
   jupyter notebook penelitian_imunoterapi_FINAL.ipynb
   ```

4. Jalankan seluruh sel secara berurutan untuk mereproduksi hasil penelitian.

---


---

## 📋 Hasil & Evaluasi

Model dievaluasi menggunakan metrik:
- **Accuracy** — akurasi keseluruhan prediksi
- **Precision & Recall** — relevan untuk data klinis yang tidak seimbang
- **F1-Score** — keseimbangan antara precision dan recall
- **Confusion Matrix** — distribusi prediksi benar dan salah

---

## ⚠️ Catatan Penting

- Dataset TCGA bersifat publik dan dapat diakses melalui [cBioPortal](https://www.cbioportal.org/) atau [GDC Data Portal](https://portal.gdc.cancer.gov/).
- Proyek ini merupakan penelitian akademis dan **tidak dimaksudkan untuk penggunaan klinis langsung**.
- Hasil prediksi model harus selalu dikonfirmasi dengan penilaian klinis oleh tenaga medis profesional.

---

## 👩‍🔬 Kontributor

**Faara Armadhanni** — Peneliti utama

---

## 📄 Lisensi

Repository ini dibuat untuk keperluan penelitian akademis. Penggunaan dataset mengikuti ketentuan lisensi TCGA.
