# projek-tbi
"Sistem Temu Balik Informasi Diagnosis Penyakit Hewan Berbasis Kemiripan Teks Menggunakan TF-IDF dan Latent Semantic Indexing"
# Deskripsi projek:
projek ini merupakan implementasi Temu Balik Informasi (Information Retrieval) untuk mencari kemungkinan diagnosis penyakit hewan berdasarkan gejala yang dimasukkan pengguna dalam bahasa Indonesia. Sistem menghitung kemiripan antara gejala yang dimasukkan dengan data gejala pada dataset, lalu menampilkan diagnosis yang paling relevan beserta penanganannya.
# Dataset:
- Sumber: kaggle (https://www.kaggle.com/datasets/mafalaz/diagnosis-of-disease-in-cattle)
- Kolom yang digunakan: Diagnosa, Gejala, dan Penanganan
- Data asli: 504 data
- Data setelah augmentasi: 744 data
# metode yang digunakan:
1. Augmentasi data gejala
   - Penggantian sinonim berbasis FastText (cc.id.300.bin)
   - Variasi struktur kalimat
2. Preprocessing teks Bahasa Indonesia
   - Case folding
   - Penghapusan angka dan simbol
   - Tokenisasi
   - Stopword removal (Sastrawi)
   - Stemming (Sastrawi)
3. Pembobotan TF-IDF (max_df = 0.95, min_df = 2)
4. Latent Semantic Indexing (TruncatedSVD, 100 komponen)
5. Pencarian diagnosis berbasis Cosine Similarity
   - Mengambil gejala dengan kemiripan tertinggi untuk setiap diagnosis
   - Threshold kemiripan 0.25
   - Pengurutan (ranking) dan Top-K (default 5)
# Tools yang digunakan:
Python, pandas, scikit-learn, Sastrawi, FastText, Google Colab
# hasil
Sistem menerima gejala dalam bentuk teks bebas dan menampilkan ranking diagnosis beserta penanganan dan nilai kemiripannya.

Contoh input:
```
liur berlebihan, borok pada kulit, bulu rontok, demam
```
Contoh output (peringkat 1):
- Diagnosis: Scabies
- Similarity: 0.7198
