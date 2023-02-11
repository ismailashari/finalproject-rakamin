# **E-commerce Churn Prediction**

## Stage 1 - EDA

Pada tahap ini dilakukan proses analisis untuk memahami karakteristik data agar data tersebut dapat digunakan untuk proses pembelajaran model tanpa mengubah nilai ataupun informasi dari data yang diperoleh. Kami melakukan analisa dengan menggunakan data yang kami peroleh [disini](https://www.kaggle.com/datasets/ankitverma2010/ecommerce-customer-churn-analysis-and-prediction). Pada tahap ini kami melakukan analisa melalui beberapa langkah, antara lain:

### 1. Statistical Descriptive

Untuk dapat memahami karakteristik data, kita dapat melihat dari ringkasan statistik dari setiap kolom yang memberikan gambaran besar keadaan data. Kami menggunakan `df.info()` dan `df.describe()` untuk melihat informasi serta ringkasan statistik pada data.

Setelah melihat ringkasan statistik dari setiap kolom, kami memperoleh beberapa informasi sebagai berikut:

1. Terdapat beberapa kolom yang perlu diubah tipe datanya:
   - CustomerID → object
   - CityTier → Object
   - CouponUsed → Int64
   - DaySinceLastOrder → Int64
   - OrderCount → int64
2. Terdapat beberapa kolom yang memiliki null value seperti: 
   - Tenure
   - WarehouseToHome
   - HourSpendOnApp
   - OrderAmountHikeFromlastYear
   - CouponUsed
   - OrderCount
   - DaySinceLastOrder
   - CashbackAmount
3. Terdapat beberapa kolom yang memiliki data yang agak aneh seperti:
   - WarehouseToHome, nilai mean (15.6) berbeda jauh dengan nilai max (127)
   - NumberOfAddress, nilai mean (4.2) berbeda jauh dengan nilai max (22)
   
### 2. Univariate Analysis

Selain melihat ringkasan statistik dari tiap kolom, kita juga dapat melakukan visualisasi pada tiap kolom sehingga dapat melihat distibusi nilainya secara detail. Kami menggunakan `boxplot` untuk melihat nilai outliers dan `kdeplot` untuk melihat distribusi data pada tiap kolom. Pada data ketegorikal kami menggunakan `countplot` untuk melihat distribusi datanya.

Setelah melakukan analisa, kami memperoleh beberapa informasi sebagai berikut:

1. Hampir keseluruhan feature memiliki nilai outliers kecuali SatisfactionScore
2. Terdapat beberapa feature yang memiliki distribusi right skew, seperti:
   - Tenure
   - WarehouseToHome
   - NumberOfAddress
   - OrderAmountHikeFromlastYear
   - CouponUsed
   - OrderCount
   - DaySinceLastOrder
3. Terdapat beberapa feature yang memiliki bimodal, seperti HourSpendOnApp, NumberOfDeviceRegistered dan SatisfactionScore
4. Pada feature kategorikal terdapat beberapa kolom yang memiliki kategori yang serupa seperti:
    - PreferredLoginDevice → (Mobile Phone - Phone)
    - PreferredPaymentMethod → (Cash on Delivery - COD) dan (CC dan Credit Card)
    - PreferredOrderCat → (Mobile - Mobile Phone)
    
### 3. Multivariate Analysis

Selanjutnya kami melakukan analisis beberapa kolom sekaligus untuk mengetahui hubungan antar kolom baik antara feature dengan target maupun korelasi pada tiap kolomnya. Kami menggunakan `heatmap` untuk melihat nilai korelasi pada tiap kolomnya dan `barplot` untuk membandingkan data antara dua kolom.

Setelah melakukan analisa, kami memperoleh beberapa informasi sebagai berikut:

1. Terdapat korelasi yang cukup kuat antara feature Tenure dan label (Churn) sebesar -0.35 (negative correlation) yang berarti semakin tinggi nilai tenure maka semakin kecil kemungkinan untuk churn.
2. Terdapat korelasi antara feature Complain dan label (Churn) sebesar 0.25 (positive correlation) yang berarti semakin tinggi nilai complain, semakin tinggi kemungkinan untuk churn.
3. Customer yang berada pada CityTier 3 memiliki kemungkinan Churn tertinggi yaitu sebesar 21.4%
4. Customer laki-laki memiliki kemungkinan Churn yang lebih tinggi yaitu sebesar 17.7%
5. Customer yang melakukan Complain memiliki kemungkinan Churn yang lebih tinggi yaitu sebesar 31.7%
6. Customer yang menggunakan metode pembayaran COD kemungkinan Churn tertinggi yaitu 28.8%
7. Customer yang melakukan transaksi pada kategori Mobile dan Mobile Phone memiliki kemungkinan untuk Churn di atas 27%
8. Customer dengan status Single memiliki kemungkinan Churn yang lebih tinggi yaitu 26.7%
9. Customer yang Churn memiliki jarak yang lebih jauh dengan rata-rata jarak sebesar 17.13
10. Customer yang Churn melakukan order yang lebih sedikit dengan rata-rata order sebesar 2.82
11. Customer yang Churn mendapatkan Cashback yang lebih sedikit dengan rata-rata Cashback sebesar 160.37
12. Customer yang memiliki Tenure di bawah 5 memiliki kemungkinan untuk Churn sangat tinggi dan semakin lama masa berlangganan maka semakin sedikit pula kemungkinan Customer untuk Churn.