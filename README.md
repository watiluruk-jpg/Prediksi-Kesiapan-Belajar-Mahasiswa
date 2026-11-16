# Prediksi-Kesiapan-Belajar-Mahasiswa
Project Uas
Tujuan Proyek: Membangun model machine learning untuk memprediksi tingkat kesiapan belajar mahasiswa (Rendah, Sedang, Tinggi) berdasarkan indikator akademik dan aktivitas mereka. Evaluasi ini bertujuan membantu institusi mengidentifikasi mahasiswa yang memerlukan pendampingan lebih awal.
Dataset: Menggunakan data akademis mahasiswa sebanyak 1.000 baris dengan 5 parameter input dan 1 parameter output:
Fitur Input:
Jam Belajar (jam/minggu)
Tugas Selesai (%)
Nilai Kuis
Nilai UAS
Kehadiran (%)
Target Output: Tingkat Kesiapan Belajar (Kategori: Rendah, Sedang, Tinggi)
Cara Menjalankan (Langkah Singkat)
Persiapan Library: Jalankan instalasi dependensi file Excel jika diperlukan:
pip install xlrd openpyxl
Load & Eksplorasi Data: Membaca dataset dari Google Drive menggunakan pandas.read_excel() dan memastikan tidak ada data kosong (isna()) atau duplikat.
Praproses Data: Memisahkan fitur dan target, kemudian mengubah target kategori menjadi numerik menggunakan LabelEncoder.
Split Data: Membagi dataset dengan rasio 80% data latih (training) dan 20% data uji (testing) menggunakan train_test_split.
Pelatihan & Evaluasi Model: Menjalankan model klasifikasi (Random Forest & KNN) dan mengevaluasi hasilnya menggunakan matriks kebingungan (Confusion Matrix) dan laporan klasifikasi.
Hyperparameter yang Dicoba dan Hasil Terbaik
Model 1: Random Forest Classifier (Model Terbaik)
Hyperparameter: n_estimators=100, random_state=42
Akurasi: 91.00%
Model 2: K-Nearest Neighbors (KNN)
Hyperparameter: n_neighbors=5, dikombinasikan dengan StandardScaler() dalam pipeline.
Akurasi: 90.00%
 Metrik Evaluasi: Akurasi, Precision, Recall, & F1-Score
Random Forest (Akurasi: 91.00%)
Kelas	Precision	Recall	F1-Score	Support
Rendah	1.00	0.55	0.71	20
Sedang	0.90	0.99	0.94	147
Tinggi	0.96	0.76	0.85	33
KNN (Akurasi: 90.00%)
Kelas	Precision	Recall	F1-Score	Support
Rendah	1.00	0.50	0.67	20
Sedang	0.89	0.99	0.94	147
Tinggi	0.93	0.76	0.83	33
 Keterbatasan dan Ide Perbaikan
Keterbatasan:
Ketidakseimbangan Data (Imbalanced Class): Jumlah sampel untuk kelas "Rendah" (20) dan "Tinggi" (33) sangat sedikit dibandingkan kelas "Sedang" (147). Hal ini menyebabkan nilai recall untuk kelas Rendah cukup rendah (0.50 - 0.55), yang berarti banyak mahasiswa yang sebenarnya "Rendah" tidak terdeteksi oleh model.
Hyperparameter Tuning Terbatas: Belum dilakukan pencarian hyperparameter optimal (Hyperparameter Tuning) secara komprehensif.
Ide Perbaikan:
Penyeimbangan Data: Menerapkan metode seperti SMOTE (Synthetic Minority Over-sampling Technique) untuk menyeimbangkan jumlah sampel kelas minoritas agar sensitivitas (recall) model meningkat.
Tuning Parameter: Menggunakan GridSearchCV atau RandomizedSearchCV untuk mencari kombinasi parameter terbaik (seperti max_depth pada RF atau jumlah n_neighbors terbaik pada KNN).
Mencoba Model Lain: Mengeksplorasi algoritma boosting seperti XGBoost atau LightGBM yang umumnya sangat kuat pada dataset tabular.

