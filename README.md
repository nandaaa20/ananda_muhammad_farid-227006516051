**Ananda Muhammad Farid**
**227006516051**
**UAS Machine Learning**

# Prediksi Luas Area Kebakaran Hutan

## 🎯 Tujuan Proyek
Proyek ini bertujuan untuk memprediksi **luas area kebakaran hutan** berdasarkan kondisi cuaca dan faktor lingkungan yang tercatat dalam **Forest Fires Dataset** dari UCI Machine Learning Repository. Prediksi ini diharapkan dapat membantu dalam pengelolaan risiko kebakaran hutan dan perencanaan mitigasi.

## 🤖 Algoritma yang Digunakan
Algoritma utama yang digunakan adalah **Random Forest Regressor**. Alasan pemilihan algoritma ini:
1. **Mampu menangani hubungan non-linear** antar fitur dan target.
2. **Tahan terhadap outlier** dan data dengan distribusi tidak normal.
3. **Dapat mengukur pentingnya fitur** untuk interpretasi model.
4. Memberikan performa baik tanpa memerlukan banyak preprocessing.

Selain itu, dilakukan **Hyperparameter Tuning** menggunakan `GridSearchCV` untuk mencari kombinasi parameter terbaik seperti:
- `n_estimators` (jumlah pohon)
- `max_depth` (kedalaman maksimum pohon)
- `min_samples_split` (minimal sampel untuk split)
- `min_samples_leaf` (minimal sampel di leaf node)

## 📊 Analisis Dataset
Dataset `forestfires.csv` berisi data cuaca dan kondisi lingkungan yang mempengaruhi kebakaran hutan.

**Jumlah data:** 517 baris
**Jumlah fitur:** 13 fitur input + 1 target (`area`)

**Fitur-fitur utama:**
- `X`, `Y`: koordinat lokasi
- `month`, `day`: bulan dan hari
- `FFMC`, `DMC`, `DC`, `ISI`: indeks cuaca kebakaran
- `temp`: suhu (°C)
- `RH`: kelembapan relatif (%)
- `wind`: kecepatan angin (km/h)
- `rain`: curah hujan (mm/m²)
- `area`: luas kebakaran (ha) **(target)**

**Insight awal:**
- Distribusi `area` sangat skewed, banyak data dengan area 0 (tidak ada kebakaran signifikan).
- Variabel cuaca seperti `temp`, `wind`, `RH` memiliki hubungan dengan `area`, namun korelasinya tidak selalu linear.
- `rain` bernilai 0 pada sebagian besar data, menunjukkan curah hujan jarang terjadi pada periode pencatatan.

## 📈 Hasil Model
Setelah tuning hyperparameter, model **Random Forest Regressor** memberikan hasil evaluasi:
- **RMSE (Test Data):** sekitar 4.467506893283511
- **R² Score (Test Data):** sekitar 0.9481728672462346

Model cukup baik dalam menangkap pola data meskipun prediksi pada kasus ekstrem masih perlu diperbaiki.

