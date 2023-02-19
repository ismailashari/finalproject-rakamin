# **E-commerce Churn Prediction**

## Stage 2 - Data Preprocessing

Pada tahap ini dilakukan modifikasi data untuk memudahkan dalam proses modelling nantinya, dengan mengubah, menambahkan ataupun mengurangi fitur yang diperlukan. Beberapa hal yang kami lakukan dalam proses modifikasi tersebut antara lain:

### 1. Data Cleaning

Pada proses *data cleaning*, kami melakukan beberapa hal, yaitu:

#### Handle Missing Value

Berdasarkan hasil Statistical Descriptive, maka yang akan kami lakukan untuk mengatasi *missing value* sebagai berikut:
- `Tenure`: Imputasi menggunakan nilai median karena memiliki distribusi skewed
- `WarehouseToHome`: Imputasi menggunakan nilai median karena memiliki distribusi skewed
- `OrderAmountHikeFromlastYear`: Imputasi menggunakan nilai median karena memiliki distribusi skewed
- `CouponUsed`: Imputasi menggunakan nilai median karena memiliki distribusi skewed
- `OrderCount`: Imputasi menggunakan nilai median karena memiliki distribusi skewed
- `DaySinceLastOrder`: Imputasi menggunakan nilai median karena memiliki distribusi skewed
- `HourSpendOnApp`: Imputasi menggunakan nilai modus

#### Handling Duplicated Data

Pada proses *handling duplicated data*, setelah melakukan pengecekan duplikat data pada fitur `CustomerID` kami tidak menemukan adanya data yang duplikat.

#### Handling Outliers

Pada proses *handling outliers* kami menggunakan 2 metode yaitu IQR dan Z-Score, dan didapatkan hasil sebagai berikut:
- IQR: data yang terbuang sebanyak 1590 atau sebesar 28.2%
- Z-score: data yang terbuang sebanyak 282 atau sebesar 5%

Kami memutuskan menggunakan nilai **Z-score** untuk mengatasi nilai outliers dikarenakan jumlah data yang terbuang jauh lebih kecil dibandingkan IQR.

### 2. Feature Extraction

Dari hasil EDA, terdapat beberapa feature yang memerlukan penyesuaian seperti:
- `PreferredLoginDevice`, menggabungkan kategori **Phone** dan **Mobile Phone** -> **Phone**
- `PreferredPaymentMode`, menggabungkan kategori **CC** dan **Credit Card** -> **Credit Card**
- `PreferredPaymentMode`, menggabungkan ketegori **COD** dan **Cash on Delivery** -> **Cash on Delivery**
- `PreferedOrderCat`, menggabungkan kategori **Mobile** dan **Mobile Phone** -> **Mobile Phone**
- `MaritalStatus`, Menggabungkan ketegori **Divorced** dan **Single** -> **Single**

Terdapat feature baru yang bisa dibuat, antara lain:
- `AvgCashback`, Rata-rata cashback per item (`CashbackAmount` / `OrderCount`)

### 3. Feature Transformation

Pada proses *feature transformation* kami melakukan **log transformation** serta **standardization** untuk fitur-fitur tertentu.

- Log transformation: `WarehouseToHome` dan `AvgCashback` karena memiliki long right tailed.
- Standardization: Semua kolom yang right skew dan kolom yang telah di log transformasi.

### 4. Feature Encoding

Pada proses *feature encoding* kami melakukan perubahan pada fitur-fitur yang bersifat kategorikal, menjadi numerikal.

- Label Encoding: `Gender`, `MaritalStatus`
- One Hot Encoder: `PreferredLoginDevice`, `PreferredPaymentMode`, `PreferedOrderCat`

### 5. Feature Selection

Berdasarkan nilai korelasi pada heatmap, feature yang memiliki korelasi tertinggi dengan target adalah `Tenure_st` dengan nilai **-0.34**. Oleh karena itu, kami memutuskan untuk membuang feature yang memiliki korelasi dibawah **0.1**. Sehingga hanya terdapat 9 feature yang akan kami gunakan pada tahap selanjutnya.

### 6. Handling Imbalance Data

Dari nilai yang didapatkan berdasarkan `value_counts`, ada ketimpangan data pada target yaitu kolom `Churn`. Dimana customer yang Churn hanya sebesar 17% dari keseluruhan data pada target. Untuk mengatasinya akan dilakukan oversampling menggunakan SMOTE sehingga dapat meminimalisir terjadinya data duplikat.
