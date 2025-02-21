# **Prophet Time Series Forecasting with Hyperparameter Tuning**

## **Deskripsi Proyek**

Proyek ini bertujuan untuk membangun model forecasting menggunakan **Prophet**, sebuah alat yang dikembangkan oleh Facebook/Meta, untuk memprediksi tren berdasarkan data historis. Model ini dioptimalkan dengan **hyperparameter tuning** untuk meningkatkan akurasi prediksi. Selain itu, proyek ini juga mencakup evaluasi model menggunakan metrik seperti **Mean Absolute Error (MAE)** dan **Mean Absolute Percentage Error (MAPE)**.

Dataset yang digunakan adalah file `cast.csv`, yang berisi data time-series dengan kolom `ds` (tanggal) dan `y` (nilai yang akan diprediksi). Untuk meningkatkan performa model, beberapa fitur tambahan seperti **holiday index** dan **macro factor** dibuat secara sintetis.

---

## **Tujuan Proyek**

1. **Membangun Model Forecasting**
   - Menggunakan **Prophet** untuk memprediksi tren berdasarkan data historis.
   - Menangani pola musiman (**seasonality**) dan perubahan tren (**changepoints**) secara efektif.

2. **Optimasi Hyperparameter**
   - Melakukan **grid search** untuk menemukan kombinasi hyperparameter terbaik.
   - Parameter yang dioptimalkan meliputi:
     - Changepoint prior scale
     - Seasonality prior scale
     - Mode seasonality (additive/multiplicative)
     - Fourier order untuk seasonality tahunan
     - Changepoint range

3. **Evaluasi Model**
   - Menggunakan metrik **MAE** dan **MAPE** untuk mengevaluasi performa model.
   - Membandingkan hasil prediksi dengan data aktual untuk mengukur akurasi.

4. **Forecasting Masa Depan**
   - Melatih model dengan seluruh dataset untuk melakukan prediksi 365 hari ke depan.

---

## **Dataset**

Dataset yang digunakan adalah file `cast.csv` dengan struktur sebagai berikut:

| **Kolom**       | **Deskripsi**                                                                 |
|------------------|-----------------------------------------------------------------------------|
| `ds`             | Tanggal dalam format `YYYY-MM-DD`.                                            |
| `y`              | Nilai target yang akan diprediksi.                                           |

Selain itu, dua fitur tambahan dibuat secara sintetis:
- **Holiday Index**: Representasi pengaruh liburan terhadap nilai target.
- **Macro Factor**: Representasi faktor makroekonomi atau eksternal.

---

## **Fitur Utama Analisis**

1. **Hyperparameter Tuning**
   - Dilakukan **grid search** untuk menemukan kombinasi parameter terbaik.
   - Parameter yang diuji meliputi:
     - `changepoint_prior_scale`
     - `seasonality_prior_scale`
     - `seasonality_mode` (additive/multiplicative)
     - `fourier_order` untuk seasonality tahunan
     - `changepoint_range`

2. **Evaluasi Model**
   - **MAE (Mean Absolute Error)**: Mengukur rata-rata kesalahan absolut antara nilai prediksi dan aktual.
   - **MAPE (Mean Absolute Percentage Error)**: Mengukur persentase kesalahan relatif terhadap nilai aktual.

3. **Forecasting**
   - Model dilatih dengan seluruh dataset untuk memprediksi 365 hari ke depan.
   - Hasil prediksi divisualisasikan menggunakan grafik.

4. **Visualisasi**
   - Grafik tren historis dan prediksi masa depan.
   - Visualisasi komponen musiman dan tren.

---

## **Cara Menggunakan Program**

### **Prasyarat**
- Pastikan Anda memiliki Python versi 3.x terinstal di sistem Anda.
- Instal modul yang diperlukan dengan menjalankan perintah berikut:
  ```bash
  pip install pandas numpy prophet scikit-learn matplotlib cmdstanpy
  ```

### **Langkah-langkah Penggunaan**

1. **Muat Dataset**
   Muat dataset `cast.csv` ke dalam program menggunakan `pandas`:
   ```python
   df = pd.read_csv("cast.csv").drop(columns=['Unnamed: 0'])
   df['ds'] = pd.to_datetime(df['ds'], format='%Y-%m-%d')
   ```

2. **Jalankan Program**
   Jalankan skrip untuk melakukan hyperparameter tuning, pelatihan model, dan evaluasi:
   ```python
   python nama_file.py
   ```

3. **Simpan Hasil**
   Hasil prediksi dapat disimpan ke file CSV untuk referensi lebih lanjut:
   ```python
   forecast.to_csv('forecast_results.csv', index=False)
   ```

---

## **Insight Utama**

1. **Hyperparameter Terbaik**
   - Kombinasi parameter terbaik yang ditemukan adalah:
     ```
     Best Params: (0.1, 0.1, 'multiplicative', 30, 0.85, 12)
     Best MAE: 905.89, MAPE: 5.55%
     ```

2. **Performa Model**
   - Model mampu memprediksi tren dengan akurasi yang baik, dengan **MAE** sebesar **905.89** dan **MAPE** sebesar **5.55%**.

3. **Forecasting Masa Depan**
   - Model berhasil memprediksi tren 365 hari ke depan dengan mempertimbangkan pola musiman dan changepoints.

---

## **Keunggulan Program**

- **Otomatisasi Hyperparameter Tuning**: Menggunakan grid search untuk menemukan kombinasi parameter terbaik.
- **Evaluasi Komprehensif**: Menggunakan metrik **MAE** dan **MAPE** untuk mengevaluasi performa model.
- **Visualisasi Interaktif**: Menggunakan library `matplotlib` untuk menghasilkan grafik tren dan komponen musiman.
- **Prediksi Masa Depan**: Model dilatih dengan seluruh dataset untuk melakukan prediksi jangka panjang.

---

Terima kasih telah menggunakan **Prophet Time Series Forecasting with Hyperparameter Tuning**! Kami harap proyek ini dapat membantu Anda memprediksi tren dengan lebih akurat dan mendukung pengambilan keputusan bisnis yang lebih baik. 😊
