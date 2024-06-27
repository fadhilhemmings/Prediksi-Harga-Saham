# Prediksi-Harga-Saham

# Latar Belakang
Saham adalah bukti dari kepemilikan suatu perusahaan atau perseroan terbatas atas penghasilan atau kekayaan. Saham merupakan salah satu instrumen investasi untuk jangka panjang. Pemilik saham juga memiliki hak untuk mendapatkan dividen sesuai dengan saham yang dimilikinya. Untuk memprediksi harga saham diperlukan peranan Machine Learning. Salah satu metode yang digunakan untuk prediksi adalah Autoreggressive Integrated Moving Average (ARIMA). ARIMA sering juga disebut metode runtun waktu Box-Jenkins. ARIMA cocok digunakan untuk peramalan jangka pendek, sedangkan untuk peramalan jangka panjang kurang baik.  ARIMA cocok jika observasi dari deret waktu (time series) secara statistik berhubungan satu sama lain (dependent). ARIMA menggunakan nilai masa lalu dan sekarang dari variabel dependen untuk menghasilkan peramalan jangka pendek yang akurat.

# Dataset
Dataset yang digunakan adalah saham dari perusahaan PT. Telkom yang didapatkan dari situs Kaggle. Dataset ini terdiri dari 1422 baris dan 7 kolom. Kolom atau label terdiri dari: Date, Open, High, Close, Adj Close, dan Volume.
![image](https://github.com/fadhilhemmings/Prediksi-Harga-Saham/assets/87648911/34b3316c-6c3c-4a4d-803c-bdbf82d09382)

# Data Exploration
Untuk memndapatkan hasil akhir harga saham maka label yang diperlukan hanya 2 yaitu: Data dan Close. Hal ini bertujuan untuk mengurangi beban kinerja dan agar hasil akhirnya lebih stabil. 
![image](https://github.com/fadhilhemmings/Prediksi-Harga-Saham/assets/87648911/4cbabdfc-8a84-4dc4-b3e7-56251f77900f)

Langkah selanjutnya adalah mengubah Date menjadi index untuk memudahkan dalam pemprosesan data.
![image](https://github.com/fadhilhemmings/Prediksi-Harga-Saham/assets/87648911/87b943a2-93ea-46d8-ae8a-8e1f15b0d121)

Berikut adalah grafik dari harga saham selama 5 tahun
![image](https://github.com/fadhilhemmings/Prediksi-Harga-Saham/assets/87648911/96beb2ae-174c-4b7b-b952-9b3074a91002)

# Modeling
Sebelum melakukan processing data diperlukan pembelajaran mesin (training phase) yang digunakan untuk menemukan pola-pola dalam data sebagai bahan dasar pengetahuan sistem untuk membuat keputusan atau melakukan prediksi. Hal pertama yang harus dilakukan adalah mengecek stasioneritas data. Untuk mengetahui data tersebut stasioner atau tidak perlu dilakukan analisis statistik untuk menguji hipotesis. Hal ini digunakan untuk menentukan apakah data hipotesis ditolak atau diterima. Untuk menolak atau menerima hipotesis, dapat menggunakan nilai p (p-value). Ambang batas yang paling umum adalah p-value < 0,05. Apabila hasil pengujian statistik didapatkan p-value ≤ 0,05 maka peluang kesalahan yang didapatkan masih dalam toleransi, sehingga dikatakan signifikan. 
![image](https://github.com/fadhilhemmings/Prediksi-Harga-Saham/assets/87648911/cca2297f-bde3-4599-9bb2-a0210f159399)

Pada gambar diatas pergerakan standar deviasi tidak konstan pada rata-rata dan data original, sehingga data tersebut tidak stasioner. Data dikatakan tidak stasioner dikarenakan p-value > 0,05. Agar data menjadi stasioner maka diperlukan proses stasionerisasi data yang namanya differencing.

# Evaluation
Differencing (pembedaan) digunakan untuk menstasionerkan data yang tidak stasioner. Jika pembedaan pertama (first difference) berhasil membuat data menjadi stasioner, berarti diperoleh orde d = 1 untuk ARIMA. Dalam metode deret berkala (time series) pengujian kestasioneran data sangat diperlukan, dimana apabila data tersebut sudah stasioner maka dapat digunakan untuk melakukan peramalan di masa yang akan datang. Jadi, Stasioneritas adalah tidak terdapat pertumbuhan atau penurunan pada data dan harus horizontal sepanjang waktu. Dengan kata lain, fluktuasi data berada di sekitar suatu nilai rata-rata yang konstan, tidak tergantung pada waktu dan varians dari fluktuasi tersebut serta tetap konstan setiap waktu.
![image](https://github.com/fadhilhemmings/Prediksi-Harga-Saham/assets/87648911/dcbc4c28-7af8-40e9-9334-58745d4bb8b3)

Setelah melalui proses differencing dihasilkan gambar diatas dan menunjukan data menjadi stationer. Hal ini dapat dilihat dari p-value < 0,05.  Langkah selanjutnya adalah melakukan evaluasi yang dimana ini bertujuan untuk mendapatkan hasil terbaik dari prediksi yang dilakukan. Arima memiliki model ARIMA = (p, d, q). p merupakan nilai Autoregressive. d merupakan nilai differencing. Dan q merupakan nilai moving average. Untuk melakukan evaluasi penulis menggunakan model RMSE (Root-Mean Square Error).
![image](https://github.com/fadhilhemmings/Prediksi-Harga-Saham/assets/87648911/46e3d537-a907-4f8c-8d62-15bbb29340ab)

Cara kerja model ini adalah dengan mencari tingkat kesalahan hasil prediksi, dimana semakin kecil (mendekati 0) nilai RMSE maka hasil prediksi akan semakin akurat. Root Mean Squared Error (RMSE) merupakan salah satu cara untuk mengevaluasi model dengan mengukur tingkat akurasi hasil perkiraan suatu model. Jika dilihat berdasarkan gambar maka dapat disimpulkan bahwa ARIMA (p, d, q) atau ARIMA (2, 1, 1) adalah model terbaik karena memiliki nilai yang paling kecil diantara hasil yang lainnya.

![image](https://github.com/fadhilhemmings/Prediksi-Harga-Saham/assets/87648911/9f59c33c-e385-4222-9d83-38675e73fe76)

Gambar diatas adalah hasil akhir dari serangkaian langkah-langkah metode ARIMA. Prediksi ini dilakukan menggunakan model ARIMA (2, 1, 1). Hasil dari prediksi ini dapat digunakan untuk empat hari kedepan. Jika diurutkan dengan data yang sudah ada harga saham kembali mengalami penurunan
