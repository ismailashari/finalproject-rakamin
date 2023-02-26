# **E-commerce Churn Prediction**

## **Stage 3 - Modeling**

Pada tahap ini dilakukan pemodelan pada dataset yang sebelumnya telah dilakukan preprocessing, sehingga dataset yang digunakan tidak terdapat nilai null ataupun duplikat. Langkah-langkah yang dilakukan pada proses modeling antara lain:

### **1. Split Data Train & Data Test**

Proses *split data* dilakukan sebelum *handling imbalance data*. Data setelah *preprocessing* berjumlah **5348 *rows***, kami melakukan pembagian untuk data train sebanyak **70%** dan data test sebanyak **30%**. Dari pembagian tersebut didapatkan:

- `X_train: 4278 row dan 11 columns`
- `y_train: 4278 row`
- `X_test: 1070 rows dan 11 columns`
- `y_test: 1070 rows`

Kemudian dilakukan *oversampling* untuk mengatasi ketimpangan nilai pada target dan didapatkan data sebagai berikut:

- `X_smote: 7104 rows dan 11 columns`
- `y_smote: 7104 rows  (0 → 3552, 1 → 3552)`

Data tersebut yang akan digunakan untuk pembelajaran model dalam memprediksi target.

### **2. Penentuan Metrics**

Kami lebih menitik beratkan pada evaluasi *metrics* *recall* yang bertujuan untuk menghindari atau **mengurangi nilai true negative** pada prediksi customer yang churn. Karena nilai true negative berarti customer tersebut diprediksi tidak churn tetapi kenyataannya churn dan hal tersebut akan membuat perusahan kehilangan customer yang ada. 

Oleh karena itu kami memilih untuk menggunakan *metrics* **Fbeta score** untuk mengevaluasi model kami. Fbeta score kami pilih karena *metrics* tersebut berfokus pada data yang imbalance dan mengevaluasi *metrics* *recall* dan precision. Nilai beta yang kami gunakan adalah 2 sehingga *metrics* ini biasa disebut juga **F2 Score**. Berikut adalah rumus fbeta score:

![alt text](f_beta.png)

### **3. Implementasi Algoritma**

Berdasarkan data yang kami gunakan, terdapat target yang memiliki tipe data kategorikal maka *machine learning* yang akan kami terapkan merupakan jenis **Supervised Learning: Classification**. Terdapat beberapa algoritma yang akan kami gunakan dalam permodelan diantaranya:

- Logistic Regression
- K-Nearest Neighbor
- Desicion Tree
- Random Forest
- Ada Boost
- Gradient Boosting
- XG Boost

Setelah dilakukan implementasi pemodelan terhadap berbagai algoritma diatas, kami memutuskan untuk memilih algoritma **XGboost** dengan perbandingan F2-Score pada data test dan data train berturut-turut adalah **0.887** dan **0.895**. <br>
Kemudian setelah dilakukan *Hyperparameter Tuning* pada algoritma XGBoost, diperoleh nilai F2-Score yang lebih bagus pada data test dan data train berturut-turut yaitu **0.959** dan **0.998**.

Sebelum menggunakan model, kita memiliki:
- `(True Positive)` 948 customers
- `(False Positive)` 4682 customers <br>
Jadi secara keseluruhan kita harus menjangkau **5630 customers** dalam upaya mencegah customer churn.

Sedangkan setelah di modelling, kita memiliki:
- `(True Positive)` 864 customers
- `(False Positive)` 65 customers <br>
Jadi secara keseluruhan kita hanya perlu menjangkau **929 customers**, dengan persentase customer churn sebesar **93%**

Dengan begini kita dapat melakukan pendekatan kepada customer secara lebih tepat, dan juga mengurangi marketing cost yang tidak on point.

### **4. Feature Importances**

