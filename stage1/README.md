# **Stage 1 - Exploratory Data Analysis**
Menganalisa data mentah yang didapatkan dari dataset https://www.kaggle.com/datasets/ankitverma2010/ecommerce-customer-churn-analysis-and-prediction, tanpa mengubah nilai ataupun informasi dari data yang diperoleh.

## Terdapat berbagai macam insight yang diperoleh, dibagi berdasarkan jenis grafik.

### **Berdasarkan Correlation Heatmap:**
1. Terdapat korelasi yang cukup kuat antara feature Tenure dan label (Churn) sebesar -0.35 (negative correlation) yang berarti semakin tinggi nilai tenure maka semakin kecil kemungkinan untuk churn.
2. Terdapat korelasi antara feature Complain dan label (Churn) sebesar 0.25 (positive correlation) yang berarti semakin tinggi nilai complain, semakin tinggi kemungkinan untuk churn.

### **Berdasarkan barplot:**
1. Customer yang berada pada CityTier 3 memiliki kemungkinan Churn tertinggi yaitu sebesar 21.4%
2. Customer laki-laki memiliki kemungkinan Churn yang lebih tinggi yaitu sebesar 17.7%
3. Customer yang melakukan Complain memiliki kemungkinan Churn yang lebih tinggi yaitu sebesar 31.7%
4. Customer yang menggunakan metode pembayaran COD kemungkinan Churn tertinggi yaitu 28.8%
5. Customer yang melakukan transaksi pada kategori Mobile dan Mobile Phone memiliki kemungkinan untuk Churn di atas 27%
6. Customer dengan status Single memiliki kemungkinan Churn yang lebih tinggi yaitu 26.7%
7. Customer yang Churn memiliki jarak yang lebih jauh dengan rata-rata jarak sebesar 17.13
8. Customer yang Churn melakukan order yang lebih sedikit dengan rata-rata order sebesar 2.82
9. Customer yang Churn mendapatkan Cashback yang lebih sedikit dengan rata-rata Cashback sebesar 160.37

### **Berdasarkan KDI-plot:**
1. Dari grafik di atas dapat diketahui pada Tenure di bawah 5 kemungkinan customer untuk Churn sangat tinggi dan semakin lama masa berlangganan maka semakin sedikit pula kemungkinan Customer untuk Churn.