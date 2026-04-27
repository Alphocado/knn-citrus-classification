# Hasil Eksperimen Klasifikasi Jeruk dengan K-Nearest Neighbor (KNN)

## Ringkasan

Proyek ini mengklasifikasikan tiga kelas jeruk, yaitu **jeruk lemon**, **jeruk manis**, dan **jeruk nipis**, menggunakan metode **K-Nearest Neighbor (KNN)** dengan fitur warna dan tekstur.  
Eksperimen dilakukan pada tiga variasi jumlah data, yaitu **500**, **750**, dan **1000** gambar per skenario, lalu masing-masing dibagi menjadi **train**, **validation**, dan **test** dengan proporsi yang sama pada tiap skenario.

---

## Tujuan Pengujian

Pengujian dilakukan untuk melihat:

1. Performa model KNN pada jumlah data yang berbeda.
2. Pengaruh data validation dalam memilih nilai `K` terbaik.
3. Stabilitas performa model pada data uji.

---

## Metode Singkat

Alur pemrosesan pada tiap eksperimen adalah:

1. Ekstraksi fitur dari gambar.
2. Normalisasi fitur dengan standardisasi.
3. Pemilihan nilai `K` terbaik menggunakan data validation.
4. Evaluasi akhir pada data test.
5. Perhitungan:
   - Confusion Matrix
   - Accuracy
   - Error Rate
   - Recall
   - Specificity
   - Precision
   - F1-Score

---

## Hasil Eksperimen

### 1) Eksperimen Dataset 500

**Komposisi data:**
- Train: 900 gambar
- Validation: 300 gambar
- Test: 300 gambar

**K terbaik dari validation:** `K = 3`  
**Validation Accuracy:** `0.9867`  
**Test Accuracy:** `0.9533`

#### Confusion Matrix Test
| Aktual \ Prediksi | jeruk_lemon | jeruk_manis | jeruk_nipis |
|---|---:|---:|---:|
| jeruk_lemon | 99 | 0 | 1 |
| jeruk_manis | 8 | 92 | 0 |
| jeruk_nipis | 3 | 2 | 95 |

#### Interpretasi
- Model cukup baik mengenali semua kelas.
- Kesalahan paling sering terjadi pada **jeruk manis** yang diprediksi sebagai **jeruk lemon**.
- Akurasi test sudah melewati target 70% dengan sangat baik.

---

### 2) Eksperimen Dataset 750

**Komposisi data:**
- Train: 1350 gambar
- Validation: 450 gambar
- Test: 450 gambar

**K terbaik dari validation:** `K = 3`  
**Validation Accuracy:** `0.9800`  
**Test Accuracy:** `0.9422`

#### Confusion Matrix Test
| Aktual \ Prediksi | jeruk_lemon | jeruk_manis | jeruk_nipis |
|---|---:|---:|---:|
| jeruk_lemon | 145 | 1 | 4 |
| jeruk_manis | 13 | 137 | 0 |
| jeruk_nipis | 4 | 4 | 142 |

#### Interpretasi
- Performa tetap tinggi, tetapi sedikit turun dibanding dataset 500.
- Kesalahan paling banyak masih muncul pada kelas **jeruk manis**.
- Model masih stabil dan layak digunakan.

---

### 3) Eksperimen Dataset 1000

**Komposisi data:**
- Train: 1800 gambar
- Validation: 600 gambar
- Test: 600 gambar

**K terbaik dari validation:** `K = 1`  
**Validation Accuracy:** `0.9800`  
**Test Accuracy:** `0.9733`

#### Confusion Matrix Test
| Aktual \ Prediksi | jeruk_lemon | jeruk_manis | jeruk_nipis |
|---|---:|---:|---:|
| jeruk_lemon | 196 | 1 | 3 |
| jeruk_manis | 1 | 199 | 0 |
| jeruk_nipis | 7 | 4 | 189 |

#### Interpretasi
- Hasil terbaik diperoleh pada skenario dataset 1000.
- Model menjadi lebih stabil karena jumlah data lebih banyak.
- Kesalahan tetap ada, tetapi jumlahnya kecil.

---

## Perbandingan Hasil

| Dataset | K Terbaik | Validation Accuracy | Test Accuracy |
|---|---:|---:|---:|
| 500 | 3 | 0.9867 | 0.9533 |
| 750 | 3 | 0.9800 | 0.9422 |
| 1000 | 1 | 0.9800 | 0.9733 |

---

## Pembahasan

Dari tiga eksperimen yang dilakukan, terlihat bahwa model KNN mampu bekerja dengan baik pada klasifikasi tiga jenis jeruk. Semua skenario menghasilkan akurasi test di atas 90%, sehingga performa model tergolong sangat baik.

Skenario dengan **1000 data** memberikan hasil test terbaik, yaitu **97.33%**, menunjukkan bahwa penambahan jumlah data dapat membantu model belajar pola dengan lebih stabil. Pada skenario **500** dan **750**, performa juga tetap tinggi, tetapi masih terdapat beberapa kesalahan klasifikasi antara jeruk manis, jeruk nipis, dan jeruk lemon karena kemiripan ciri warna serta tekstur.

Nilai validation dan test yang cukup dekat menunjukkan bahwa model tidak mengalami overfitting yang parah. Pemilihan nilai `K` melalui data validation juga membantu mendapatkan parameter terbaik sebelum pengujian akhir.

---

## Kesimpulan

1. Metode KNN berhasil digunakan untuk mengklasifikasikan jeruk lemon, jeruk manis, dan jeruk nipis.
2. Seluruh eksperimen menghasilkan akurasi test di atas 90%.
3. Hasil terbaik diperoleh pada eksperimen **dataset 1000** dengan akurasi test **97.33%**.
4. Data validation efektif untuk memilih nilai `K` terbaik.
5. Penambahan jumlah data cenderung meningkatkan kestabilan dan performa model.

---

## Catatan

Project ini dibuat untuk kebutuhan **UAS Pengolahan Citra Digital** dan menggunakan pendekatan klasifikasi citra berbasis fitur sederhana, tanpa deep learning.
