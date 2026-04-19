# Klasifikasi Citra Tanaman Herbal dengan Metode SVM

Proyek ini menggunakan algoritma **Support Vector Machine (SVM)** untuk mengklasifikasikan citra tanaman herbal berdasarkan ekstraksi fitur warna (RGB/HSV), tekstur (GLCM), dan bentuk (kontur).

---

## Dataset

- **Nama Dataset:** TanamanHerbal
- **Jumlah Fitur:** 70 fitur numerik (60 warna, 5 tekstur GLCM, 5 bentuk)
- **Sumber Data:** Google Drive (Google Colab)
- **Format Gambar:** `.jpg`, `.jpeg`, `.png`
- **Format Penamaan File:** `NamaTanaman (nomor).jpg` → contoh: `Jahe (1).jpg`

**Link Dataset:**  
[Tanaman Herbal (Google Drive)](https://drive.google.com/drive/folders/1ilO65ekMcN9g2JBg2hNY33hbOk8QE9Bi?usp=sharing)
*(Tambahkan link Google Drive dataset di sini)*

---

## Metode yang Digunakan

- **Ekstraksi Fitur:**
  - **Warna (RGB/HSV):** mean & std channel RGB dan HSV → 12 fitur
  - **Histogram Warna:** 16 bins × 3 channel RGB → 48 fitur
  - **Tekstur (GLCM):** contrast, dissimilarity, homogeneity, energy, correlation → 5 fitur
  - **Bentuk (Kontur):** area, perimeter, diameter, solidity, roundness → 5 fitur
- **Preprocessing:** Label cleaning dengan regex, normalisasi dengan StandardScaler
- **Algoritma:** SVM dengan kernel RBF, dioptimalkan menggunakan GridSearchCV
  - `C`: [0.1, 1, 10, 100]
  - `gamma`: [1, 0.1, 0.01, 0.001]
  - Cross-validation: 3-fold
- **Evaluasi:** Accuracy, Precision, Recall, F1-Score, Confusion Matrix

---

## Pembagian Data

| Split | Proporsi |
|-------|----------|
| Training | 70% |
| Validasi | 15% |
| Testing | 15% |

Pembagian dilakukan secara **stratified** untuk menjaga proporsi kelas tetap seimbang.
