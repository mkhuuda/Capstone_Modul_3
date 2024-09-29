Problem Statement

Sebuah perusahaan Bike-Sharing ingin melakukana prediksi jumlah sepeda yang disewa (cnt) menggunakan data historis dari sistem penyewaan sepeda, dengan mempertimbangkan faktor-faktor seperti suhu, musim, kondisi cuaca, dan jam dalam sehari serta mungkin faktor-faktor lain yang mempengaruhi. Prediksi yang akurat akan membantu dalam pengelolaan sumber daya yang lebih baik, mengoptimalkan ketersediaan sepeda, dan meningkatkan efisiensi layanan serta dapat meningkatkan keuntungan.
Sistem Bike Sharing adalah generasi baru dari penyewaan sepeda tradisional di mana seluruh proses mulai dari keanggotaan, penyewaan, hingga pengembalian sepeda menjadi otomatis. Melalui sistem ini, pengguna dapat dengan mudah menyewa sepeda dari suatu lokasi dan mengembalikannya di lokasi lain. Saat ini, terdapat lebih dari 500 program berbagi sepeda di seluruh dunia yang melibatkan lebih dari 500 ribu sepeda. Sistem ini mendapat perhatian besar saat ini karena perannya yang penting dalam mengatasi masalah lalu lintas, lingkungan, dan kesehatan.
Selain aplikasi dunia nyata yang menarik dari Sistem Bike Sharing, karakteristik data yang dihasilkan oleh sistem ini menjadikannya menarik untuk penelitian. Tidak seperti layanan transportasi lain seperti bus atau kereta bawah tanah, durasi perjalanan, lokasi keberangkatan, dan lokasi kedatangan dicatat secara eksplisit dalam sistem ini. Fitur ini mengubah sistem berbagi sepeda menjadi jaringan sensor virtual yang dapat digunakan untuk memantau mobilitas di kota. Oleh karena itu, diharapkan bahwa peristiwa-peristiwa penting di kota dapat terdeteksi dengan memantau data ini.
Goals

Mengembangkan model prediksi jumlah penyewaan sepeda (cnt) berdasarkan fitur seperti temp (suhu), season (musim), weathersit (kondisi cuaca), hr (jam) dan beberapa fitur lain yang mungkin mempengaruhi.
Hasil Rule-Based Model: Model berbasis aturan (rule-based) telah diterapkan sebagai model baseline dengan hasil sebagai berikut:
Mean MAE: 537.61
Mean RMSE: 686.08
Penghitungan prediksi benefit dari jumlah unit penyewaan sepeda setelah dilakukan Pemodelan Machine Learning, dampak dari kesalahan prediksi terlalu tinggi dapat menyebabkan biaya operasional yang meningkat, sementara prediksi yang terlalu rendah dapat menyebabkan hilangnya pendapatan karena kekurangan stok sepeda.
Analytic Approach

Melakukan Data Understanding, Data Cleaning, Exploratory Data Analysis (EDA) untuk memahami pola dalam data, mengidentifikasi hubungan antar variabel, dan mempersiapkan data untuk pemodelan.
Mengembangkan model regresi (misalnya Regresi Linear, Decision Tree, Random Forest, XGBoost, dll.) untuk memprediksi cnt (penyewaan sepeda) berdasarkan fitur-fitur yang tersedia.
Membandingkan performa model machine learning dengan model rule based untuk melihat peningkatan akurasi prediksi.
Metric Evaluation

Dalam membuat prediksi ini akan digunakan metric evaluation sebagai berikut:
Mean Absolute Error (MAE): Memberikan rata-rata besar kesalahan prediksi tanpa memperhatikan arah kesalahan. Metrik ini lebih mudah diinterpretasikan dan membantu memahami rata-rata kesalahan per prediksi.
Root Mean Squared Error (RMSE): Mengukur deviasi standar dari kesalahan prediksi; cocok untuk kasus di mana kesalahan besar berdampak signifikan. Dalam konteks ini, memastikan ketersediaan sepeda saat dibutuhkan sangat penting, sehingga RMSE relevan.
Kedua Metric digunakan dengan mempertimbangkan:
Alasan Utama:
MAE memberikan ukuran kesalahan rata-rata yang lebih robust terhadap outliers, karena kesalahan absolut tidak dikuadratkan. Ini bisa memberi gambaran tentang kesalahan rata-rata yang terjadi tanpa memberi bobot berlebihan pada outliers.
RMSE memberikan penalti lebih besar pada kesalahan besar karena mengkuadratkan selisih antara prediksi dan nilai aktual. Ini berarti RMSE lebih sensitif terhadap outliers dan kesalahan besar dalam prediksi. Jika RMSE jauh lebih besar dari MAE, itu menunjukkan bahwa ada beberapa kesalahan besar dalam prediksi model yang mungkin perlu ditangani atau diperbaiki.
Manfaat:
MAE mengukur kesalahan rata-rata: MAE memberikan estimasi yang lebih stabil mengenai kesalahan rata-rata secara umum, tanpa memberikan penalti ekstra pada outliers. Ini membantu memahami seberapa baik model menangani kesalahan secara keseluruhan.
RMSE mengukur kesalahan besar: Karena mengkuadratkan kesalahan, RMSE menunjukkan seberapa baik model menangani kesalahan besar atau outliers. Dalam bisnis, ini bisa memberi sinyal apakah model cenderung menghasilkan prediksi yang tidak akurat pada beberapa sampel tertentu.
Kesimpulan: MAE bisa menjadi metrik utama untuk mengukur performa umum model, karena mudah diinterpretasikan dalam satuan asli (unit penyewaan sepeda dalam kasus ini) dan RMSE bisa digunakan untuk mendeteksi apakah ada kesalahan besar yang perlu diperhatikan lebih lanjut.



Modelling

Rule Based Model (Non ML)

Memahami Hubungan Antar Variabel
Target variabel: cnt (jumlah sepeda yang disewa)
Variabel independen:
Weathersit: berkorelasi negatif (cuaca yang buruk menurunkan jumlah sepeda yang dipinjam)
Season: berkorelasi positif (beberapa musim memiliki lebih banyak peminjaman)
Temp: berkorelasi positif (semakin hangat, semakin banyak sepeda yang dipinjam)
Hr: berkorelasi positif (waktu tertentu dalam sehari mungkin memiliki lebih banyak peminjaman)


Hasil evaluasi dari model rule-based (non machine learning) menunjukkan beberapa metrik performa sebagai berikut:
Mean_MAE (537.61): Mean Absolute Error (MAE) adalah rata-rata dari kesalahan absolut antara nilai aktual dan prediksi. Nilai 537.61 menunjukkan bahwa, rata-rata, prediksi model menyimpang dari nilai aktual sebesar 537.61. Ini memberikan gambaran yang lebih langsung tentang kesalahan prediksi dibandingkan RMSE, karena MAE tidak memperhitungkan kuadrat dari kesalahan.
Std_MAE (426.25): Standar Deviasi MAE juga menunjukkan variasi kesalahan prediksi, dengan nilai 426.25. Ini menunjukkan bahwa meskipun rata-rata kesalahan MAE cukup rendah, ada variasi yang cukup besar dalam kesalahan yang dialami model.
Mean_RMSE (686.08): Root Mean Squared Error (RMSE) mengukur rata-rata kesalahan prediksi dalam unit yang sama dengan target (cnt). Nilai RMSE sebesar 686.08 menunjukkan bahwa rata-rata kesalahan antara nilai aktual dan nilai prediksi adalah sekitar 686.08. Semakin rendah nilai RMSE, semakin baik model dalam memprediksi.
Std_RMSE (455.92): Standar Deviasi RMSE mengukur seberapa besar variasi kesalahan prediksi dari nilai rata-rata RMSE. Nilai 455.92 menunjukkan ada variasi yang signifikan dalam kesalahan prediksi model. Jika nilai ini tinggi, artinya model tidak konsisten dalam prediksi.
Kesimpulan Secara keseluruhan, hasil evaluasi ini menunjukkan bahwa model rule-based yang digunakan memiliki performa yang kurang memuaskan. Metrik seperti MAE dan RMSE menunjukkan kesalahan yang signifikan.



Experiment 1: Based Model

Pemodelan regresi menggunakan beberapa algoritma yang berbeda, yaitu Linear Regression, K-Neighbors Regressor, Decision Tree Regressor, Random Forest Regressor, dan XGBoost Regressor. Pemodelan dilakukan dalam skala logaritmik untuk meningkatkan akurasi dan stabilitas model, kemudian hasilnya akan diubah kembali ke skala aslinya menggunakan fungsi invers logaritma.


Berdasarkan hasil evaluasi dari beberapa model regresi yang telah dijalankan, berikut adalah analisis performa model:
1. Mean MAE (Mean Absolute Error)
XGBoost Regressor juga memiliki Mean MAE terendah (-68.57), diikuti oleh KNN Regressor (-72.65) dan Random Forest Regressor (-74.46).
Linear Regression lagi-lagi memiliki performa terburuk dalam hal MAE, yang menunjukkan kesalahan prediksi absolutnya lebih besar dibandingkan model lainnya.
2. Mean RMSE (Root Mean Squared Error)
XGBoost Regressor memiliki Mean RMSE terendah (-106.91), yang berarti bahwa prediksinya paling mendekati nilai sebenarnya dibandingkan model lain.
KNN Regressor dan Random Forest Regressor juga memiliki nilai RMSE yang lebih rendah daripada Linear Regression dan Decision Tree Regressor.
Linear Regression memiliki performa terburuk dalam hal RMSE, menunjukkan bahwa model linier tidak menangkap kompleksitas hubungan dalam data dengan baik.
3. Standard Deviation (Std)
KNN Regressor memiliki Std RMSE, dan Std MAE yang paling rendah, yang menunjukkan bahwa model ini memberikan hasil yang paling konsisten.
XGBoost Regressor dan Random Forest Regressor menunjukkan konsistensi yang cukup baik juga.
Linear Regression memiliki Standard Deviation tertinggi untuk MAE dan RMSE, menunjukkan bahwa performanya kurang stabil.
Kesimpulan
XGBoost Regressor adalah model terbaik dalam hal akurasi (dilihat dari RMSE dan MAE) dan menawarkan keseimbangan yang baik antara error yang kecil dan stabilitas model.
KNN Regressor juga menunjukkan performa yang baik, terutama dalam konsistensi, meskipun secara keseluruhan masih sedikit lebih buruk dari XGBoost.
Random Forest Regressor adalah pilihan bagus lainnya, namun XGBoost tetap unggul dalam semua metrik.
Linear Regression menunjukkan performa terburuk, yang menandakan model ini tidak cocok untuk dataset ini, kemungkinan karena ketidaklinearitas hubungan antar variabel.
Dari hasil ini, XGBoost Regressor dapat dianggap sebagai model terbaik untuk data ini, dan bisa dipertimbangkan sebagai model akhir untuk digunakan.
Selanjutnya akan dilakukan eksperiment kedua dengan menghapus outliers


Experiment 2: Hapus Outliers

Sama seperti eksperiment pertama, namun di sini dataset yang digunakan adalah dataset setelah dilakukan penghapusan outliers, yaitu df_new_without_outliers.

Berdasarkan hasil evaluasi setelah menghapus outliers dari dataset, berikut analisisnya dengan membandingkan model sebelum dan sesudah penghapusan outliers:
1. Mean MAE (Mean Absolute Error)
Semua model menunjukkan penurunan dalam MAE setelah penghapusan outliers.
XGBoost Regressor tetap yang terbaik dengan Mean MAE sebesar -62.00, yang lebih baik daripada performa sebelumnya sebesar -68.57.
KNN Regressor juga menunjukkan peningkatan besar, dari -72.65 menjadi -65.42.
Linear Regression mengalami penurunan dari -119.57 menjadi -106.13, namun tetap menunjukkan kesalahan prediksi absolut yang lebih tinggi daripada model non-linear lainnya.
2. Perbaikan Performansi pada Semua Model
Linear Regression: Mean RMSE turun dari -177.59 menjadi -152.60 setelah penghapusan outliers. Meskipun ini menunjukkan peningkatan, model ini tetap yang terburuk di antara semua model lain.
KNN Regressor: RMSE turun dari -112.77 menjadi -98.97, menunjukkan peningkatan yang signifikan setelah penghapusan outliers.
Decision Tree Regressor: RMSE juga berkurang dari -126.18 menjadi -111.73 setelah penghapusan outliers.
Random Forest Regressor: Perbaikan terlihat dengan RMSE turun dari -115.37 menjadi -100.77.
XGBoost Regressor: RMSE juga berkurang dari -106.91 menjadi -93.97, menjadikannya tetap model terbaik dengan performa yang lebih baik setelah penghapusan outliers.
3. Standard Deviation (Std)
Konsistensi model (dilihat dari Standard Deviation) umumnya membaik setelah penghapusan outliers, khususnya pada XGBoost Regressor dengan penurunan Std_MAE dan Std_RMSE yang lebih kecil, menunjukkan model ini tetap stabil.
Random Forest dan KNN Regressor juga menunjukkan stabilitas yang lebih baik.
Linear Regression masih memiliki Std yang cukup tinggi, menunjukkan performa yang tidak konsisten bahkan setelah penghapusan outliers.

Kesimpulan
XGBoost Regressor terus menjadi model terbaik baik sebelum maupun sesudah penghapusan outliers, dengan MAE dan RMSE terendah, serta konsistensi yang lebih baik setelah penghapusan outliers.
KNN Regressor dan Random Forest Regressor juga menunjukkan peningkatan signifikan setelah penghapusan outliers dan dapat dipertimbangkan sebagai alternatif, meskipun XGBoost masih unggul.
Linear Regression menunjukkan peningkatan performa, namun masih tertinggal jauh dibandingkan model lainnya. Ini mengindikasikan bahwa hubungan antara fitur dan target tidak sepenuhnya linear, dan model non-linear lebih sesuai.
Secara keseluruhan, menghapus outliers membantu meningkatkan performa semua model, terutama model yang lebih kompleks seperti XGBoost dan Random Forest. Penghapusan outliers bisa dipertimbangkan sebagai langkah penting dalam pre-processing data jika ingin mendapatkan prediksi yang lebih akurat.



XGBoost Regressor adalah model yang paling baik dari ketiga eksperimen yang dilakukan, baik dengan dan tanpa outliers, memberikan prediksi dengan kesalahan yang lebih rendah. Menghapus outliers memberikan efek positif terhadap performa semua model, terlihat dari penurunan nilai MAE dan RMSE secara keseluruhan.
Dengan mempertimbangkan analisis ini, maka direkomendasikan untuk melanjutkan penggunaan model XGBoost dengan dataset tanpa ouliers (df_without_ouliers) dan terus melakukan evaluasi serta tuning untuk meningkatkan performa model di masa mendatang.


Final Model

Predict to Test Set with the Benchmark Model
Prediksi pada test set dengan menggunakan model terbaik yaitu XGBoost


Hyperparameter Tuning

Random Search secara acak memilih kombinasi parameter dalam rentang yang ditentukan, yang sering kali lebih efisien daripada Grid Search. Sedangkan, Grid Search mencoba semua kombinasi dari parameter yang ditentukan.
Dalam hal ini, efisiensi menjadi pertimbangan penting, maka akan digunakan Random Search. Random Search juga merupakan metode yang valid dan efisien.
Random Search masih merupakan pilihan yang baik. Hasilnya cukup mendekati, dan Random Search bisa lebih cepat dalam situasi di mana ruang parameter sangat besar.
Selain itu, komputasi yang digunakan akan lebih ringan.


Analisis dari hasil tuning model XGBoost dengan Best_score dan Best_params menghasilkan beberapa kesimpulan yang penting untuk performa model, khususnya dalam konteks penurunan error dan peningkatan akurasi prediksi.
1. Best_score: -61.30
Best_score mengindikasikan nilai negatif Root Mean Squared Error (RMSE) terbaik sebesar 61.30. Dalam regresi, RMSE digunakan untuk mengukur seberapa jauh prediksi model dari nilai sebenarnya. Semakin rendah nilai RMSE, semakin baik model dalam melakukan prediksi. Karena nilai RMSE negatif (dari neg_mean_squared_error), nilai absolutnya sekitar 61.30 unit. Ini berarti bahwa model XGBoost yang telah di-tuning mampu memprediksi variabel target dengan error sekitar 61 unit rata-rata per prediksi. Jika dibandingkan dengan RMSE model sebelum tuning (misalnya, pada model rule-based dengan RMSE 686.08), hasil ini menunjukkan peningkatan yang sangat signifikan, dengan pengurangan error prediksi lebih dari 10 kali lipat.
2. Best_params:
Hyperparameter terbaik yang ditemukan untuk model XGBoost adalah sebagai berikut:
'model__subsample': 0.6: Hanya 60% dari data yang digunakan untuk setiap pohon, yang membantu model menghindari overfitting dan meningkatkan generalisasi.
'model__reg_alpha': 0.001: Penalti regularisasi L1 yang sangat kecil, yang memungkinkan model tetap fleksibel namun tetap menghindari overfitting secara moderat.
'model__n_estimators': 190: Jumlah total pohon yang digunakan oleh XGBoost. Nilai ini lebih tinggi dari model default (biasanya 100), yang menunjukkan bahwa lebih banyak pohon memberikan hasil yang lebih baik.
'model__max_depth': 5: Setiap pohon memiliki kedalaman maksimum 5, yang menjaga keseimbangan antara kompleksitas dan kemampuan prediksi model. Kedalaman yang lebih tinggi mungkin akan menyebabkan overfitting, sementara yang terlalu rendah dapat mengurangi kemampuan prediksi.
'model__learning_rate': 0.04: Tingkat pembelajaran yang relatif kecil, memastikan bahwa model belajar secara bertahap dan tidak melompati solusi optimal.
'model__gamma': 9: Model hanya akan melakukan split jika hasilnya cukup signifikan, membantu mengurangi pembagian pohon yang tidak diperlukan dan meningkatkan stabilitas model.
'model__colsample_bytree': 0.9: 90% dari fitur digunakan pada setiap pohon. Ini mengurangi risiko overfitting yang bisa muncul saat terlalu banyak fitur digunakan.
3. Performa Model yang Optimal:
Setelah tuning, model XGBoost menunjukkan hasil yang lebih baik dengan RMSE yang lebih rendah. Ini menandakan bahwa model ini lebih baik dalam memprediksi variabel target dibandingkan dengan model lain yang diuji atau dibandingkan dengan versi sebelum tuning. Dengan set hyperparameter ini, model menunjukkan keseimbangan yang baik antara kompleksitas dan generalisasi, yang terlihat dari regularisasi yang kecil namun efektif (reg_alpha), subsampling data, dan pemilihan pohon yang optimal.
4. Kesimpulan:
Model XGBoost setelah tuning mampu menghasilkan prediksi dengan error sekitar 61.30, jauh lebih baik daripada model awal. Hyperparameter yang digunakan (subsample, reg_alpha, n_estimators, max_depth, learning_rate, gamma) semuanya berperan penting dalam meningkatkan performa model sambil menjaga keseimbangan antara fleksibilitas model dan overfitting.
Jika diterapkan dalam skenario bisnis, model ini memberikan prediksi yang lebih akurat, memungkinkan pengambilan keputusan yang lebih tepat, seperti prediksi permintaan yang lebih baik atau optimasi sumber daya di bike-sharing system yang sedang dianalisis.
Potensi Langkah Lanjut:
Dengan hasil ini, maka dapat dilakukan perhitungan profit berdasarkan perbedaan RMSE antara model rule-based dan XGBoost. Perbedaan error yang besar menunjukkan peluang pengurangan kesalahan prediksi, yang bisa diterjemahkan ke dalam penghematan biaya atau peningkatan efisiensi operasional.



Analisis Hasil:
1. Penurunan MAE dan RMSE:
MAE setelah tuning turun dari 60.53 menjadi 59.16, menunjukkan penurunan sebesar 1.37 poin. Ini berarti rata-rata kesalahan absolut dalam prediksi telah berkurang, sehingga prediksi model lebih mendekati nilai aktual setelah tuning. RMSE setelah tuning turun dari 89.34 menjadi 85.71, dengan penurunan sebesar 3.63 poin. RMSE, yang lebih sensitif terhadap kesalahan besar, juga berkurang, menandakan bahwa model telah mengurangi beberapa kesalahan prediksi besar yang mungkin terjadi sebelumnya.
2. Peningkatan Akurasi:
Penurunan RMSE dan MAE setelah tuning menunjukkan bahwa tuning hyperparameter berhasil meningkatkan performa model XGBoost. Karena RMSE menghukum kesalahan besar lebih berat, penurunan pada RMSE yang lebih signifikan dibandingkan MAE menunjukkan bahwa model setelah tuning tidak hanya lebih baik dalam rata-rata prediksi, tetapi juga dalam menangani outliers atau prediksi dengan kesalahan besar.
3. Manfaat dalam Konteks Bisnis:
Penurunan MAE dan RMSE menandakan bahwa setelah tuning, model lebih mampu memprediksi hasil dengan lebih akurat. Dalam konteks project bike-sharing, hal ini berarti: Prediksi permintaan sepeda menjadi lebih tepat, yang dapat berdampak langsung pada efisiensi operasional (misalnya, pengelolaan jumlah sepeda di stasiun, alokasi sumber daya, dll.). Pengurangan kesalahan besar (RMSE) berarti bahwa cenderung menghindari skenario di mana prediksi salah jauh dari realitas, seperti memprediksi terlalu banyak atau terlalu sedikit sepeda di stasiun tertentu, yang bisa menyebabkan kerugian operasional besar (misalnya kekurangan sepeda atau kelebihan stok).
4. Kesimpulan:
Hasil tuning menunjukkan perbaikan yang nyata dalam performa model, baik dari segi akurasi prediksi rata-rata (MAE) maupun kemampuan model dalam menangani kesalahan besar (RMSE).
Dalam konteks bisnis, pengurangan error ini dapat diartikan sebagai pengurangan biaya, peningkatan efisiensi dalam manajemen sumber daya, dan peningkatan profitabilitas karena prediksi permintaan yang lebih akurat. Secara keseluruhan, tuning hyperparameter ini memberikan peningkatan performa yang menguntungkan, dan bisa menjadi dasar untuk pengambilan keputusan strategis dalam operasi sistem bike-sharing.



Interpretasi Feature Importance
1. scaler__hr (0.356281): Fitur ini memiliki nilai penting tertinggi (35.6%), menandakan bahwa jam dalam sehari adalah faktor yang paling signifikan dalam model prediksi. Ini menunjukkan bahwa pola penggunaan atau permintaan sangat dipengaruhi oleh waktu, di mana waktu-waktu sibuk seperti pagi atau sore hari, atau waktu sepi seperti tengah malam,berkontribusi besar terhadap prediksi.
2. one hot__weathersit_3 (0.154854): Fitur ini mewakili kondisi cuaca "Hujan/Salju ringan" dan memiliki nilai penting sebesar 15.5%. Ini mengindikasikan bahwa cuaca buruk, seperti hujan ringan atau salju, berdampak besar terhadap prediksi, mungkin karena layanan (misalnya, penggunaan sepeda) cenderung menurun dalam kondisi cuaca seperti ini.
3. one hot__season_4 (0.128666): Musim gugur (season 4) memiliki kontribusi signifikan (12.9%). Ini mengindikasikan bahwa penggunaan layanan berkurang atau berubah selama musim gugur, mungkin karena kondisi cuaca yang lebih dingin atau perubahan preferensi pengguna di musim ini.
4. binary__season (0.118074): Fitur ini menyatakan apakah data berada dalam musim tertentu, dalam format biner. Dengan kontribusi sebesar 11.8%, fitur ini menunjukkan bahwa faktor musiman secara keseluruhan (mungkin perbedaan antara musim dingin dan lainnya) cukup berpengaruh terhadap prediksi, menandakan adanya pergeseran pola penggunaan berdasarkan musim.
5. scaler__temp (0.108004): Suhu yang telah dinormalisasi berkontribusi 10.8% terhadap prediksi. Hal ini menunjukkan bahwa suhu adalah faktor penting, di mana suhu yang lebih tinggi mungkin mendorong peningkatan penggunaan layanan (seperti bersepeda), sedangkan suhu yang lebih rendah dapat menghambat aktivitas.
6. binary__weathersit (0.075430): Fitur ini mewakili keadaan cuaca secara umum dalam format biner, dengan kontribusi sebesar 7.5%. Ini menunjukkan bahwa kondisi cuaca (apakah cerah atau tidak) juga mempengaruhi prediksi, namun tidak sebesar fitur lain.
7. one hot__season_2 (0.021137): Musim semi (season 2) hanya berkontribusi sebesar 2.1%. Ini menunjukkan bahwa musim semi tidak memiliki pengaruh yang besar terhadap pola penggunaan, yang mungkin berarti bahwa pengguna lebih aktif pada musim lain seperti musim panas atau gugur.
8. one hot__weathersit_2 (0.018911): Fitur ini mewakili kondisi cuaca "Berawan" dengan kontribusi 1.9%. Ini menunjukkan bahwa cuaca berawan hanya sedikit mempengaruhi keputusan pengguna dalam menggunakan layanan.
9. one hot__season_3 (0.018642): Musim panas (season 3) juga memiliki kontribusi yang sangat kecil (1.9%). Meskipun biasanya musim panas adalah waktu yang lebih hangat, dampaknya terhadap pola penggunaan tidak terlalu signifikan, mungkin karena faktor lain seperti kondisi cuaca atau preferensi pengguna.
Kesimpulan
Fitur Utama: Fitur yang paling signifikan dalam prediksi adalah scaler__hr dan one hot__weathersit_3. Jam dalam sehari memainkan peran penting dalam memprediksi pola penggunaan, yang mungkin dikaitkan dengan aktivitas rutin harian pengguna. Selain itu, kondisi cuaca buruk (hujan ringan/salju) juga memberikan pengaruh besar terhadap keputusan pengguna.
Fitur Pendukung: Faktor musiman, seperti yang diwakili oleh one hot__season_4 dan binary__season, serta suhu (scaler__temp), memberikan kontribusi penting namun lebih rendah dibandingkan fitur utama. Hal ini menunjukkan bahwa pola penggunaan bergantung pada konteks musiman dan cuaca, yang dapat membantu dalam perencanaan strategis untuk meningkatkan layanan.



Limirasi


Hasil Analisa:
Weathersit 2 (cuaca berawan) dan Season 1 (musim dingin) muncul sebagai kondisi cuaca dan musim optimal. Ini mungkin menunjukkan bahwa meskipun cuaca dan musim tidak ideal, model ini memprediksi penyewaan yang cukup stabil dalam kondisi tersebut.
Suhu dalam rentang luas (0.02 hingga 0.96) memperlihatkan bahwa penyewaan sepeda terjadi dalam berbagai suhu, tetapi cenderung menghindari suhu yang sangat ekstrem.
Waktu (Hr) optimal sepanjang hari menunjukkan bahwa pola penyewaan sepeda cukup merata di berbagai jam dalam sehari, meskipun kemungkinan ada puncak di waktu-waktu tertentu seperti jam kerja atau rekreasi.


Berdasarkan dua visualisasi residual berikut analisanya:

Residual Plot:
Plot residual menunjukkan pola yang melebar secara vertikal seiring dengan kenaikan nilai prediksi. Hal ini mengindikasikan adanya heteroskedastisitas, di mana varians residual tidak konstan sepanjang nilai prediksi. Heteroskedastisitas dapat menyebabkan model menjadi kurang akurat dalam memprediksi pada berbagai level output. Implikasi: Model mungkin perlu ditingkatkan dengan memperbaiki teknik pemodelan atau melakukan transformasi terhadap variabel tertentu untuk mengurangi ketidakstabilan varians residual.

Distribusi Residual:
Histogram menunjukkan distribusi residual yang agak simetris di sekitar nol, tetapi dengan ekor panjang di kedua sisi (terutama ke kanan). Ini mengindikasikan bahwa residual berdistribusi tidak sepenuhnya normal dan menunjukkan adanya beberapa outliers yang signifikan. Implikasi: Meskipun sebagian besar residual berkisar di sekitar nol, adanya outliers yang besar mungkin menunjukkan bahwa model belum optimal dalam menangani beberapa data, mungkin karena adanya fitur yang tidak cukup terwakili dalam model atau transformasi fitur yang belum sesuai.
Kesimpulan:
Heteroskedastisitas dalam residual plot menunjukkan bahwa model mungkin tidak sesuai untuk seluruh rentang data, terutama di nilai prediksi yang lebih tinggi.
Distribusi residual yang tidak sepenuhnya normal, meski cenderung simetris, mengindikasikan adanya beberapa outliers yang perlu dianalisis lebih lanjut atau mungkin model perlu disesuaikan dengan menggunakan metode yang lebih robust terhadap outliers.
Beberapa perbaikan yang dapat dicoba termasuk transformasi variabel, menggunakan model yang lebih kompleks, atau melakukan regularisasi tambahan pada model.



Estimasi Keuntungan

Dalam menghitung keuntungan sepeda dalam konteks project bike-sharing, RMSE akan menjadi metrik yang lebih baik dibandingkan MAE. Alasannya adalah karena RMSE menghukum kesalahan besar lebih berat, sehingga lebih relevan dalam mengukur potensi kerugian atau keuntungan dari prediksi yang lebih tepat. Berikut adalah beberapa alasan mengapa RMSE lebih tepat dalam kasus ini:
Kesalahan Besar Lebih Berdampak pada Keuntungan Operasional: Misalnya, memprediksi terlalu rendah akan menyebabkan kekurangan sepeda, sementara memprediksi terlalu tinggi akan menyebabkan kelebihan sepeda di stasiun tertentu.RMSE lebih memperhatikan outliers atau kesalahan yang signifikan karena menghitung kuadrat dari kesalahan.
RMSE Lebih Sensitif Terhadap Variabilitas dalam Prediksi: MAE menghitung rata-rata kesalahan absolut tanpa mempertimbangkan seberapa besar kesalahan tersebut. Ini berarti MAE memberikan nilai yang sama untuk semua kesalahan, terlepas dari apakah kesalahan itu besar atau kecil. Dalam hal pengelolaan stok sepeda, kesalahan besar lebih merugikan daripada kesalahan kecil. RMSE menangkap aspek ini, sehingga lebih relevan untuk menghitung potensi keuntungan dari penurunan kesalahan prediksi.
Penggunaan RMSE untuk Menghitung Potensi Keuntungan: Dengan menurunkan RMSE, akan mengurangi potensi kerugian besar yang bisa terjadi dari kesalahan prediksi. Hal ini penting untuk mengoptimalkan ketersediaan sepeda dan alokasi sumber daya di berbagai stasiun, sehingga operasi menjadi lebih efisien.


Keuntungan Jumlah Sepeda Tersewa

Dari hasil di atas dapat disimpulkan bahwa adanya peningkatan benefit sebesar 600 unit sepeda yang disewa setelah dilakukan pemodelan dengan Machine Learning

Keuntungan Biaya Sewa

Dalam Hal ini diestimasikan keuntungan biaya sewa satu unit sepeda bernilai $100, maka dapat dihitung peningkatan keuntungan setelah dilakukan pemodelan dengan Machine Learning.

Dari hasil di atas dapat disimpulkan bahwa adanya peningkatan benefit sebesar $60.037,62 setelah dilakukan pemodelan dengan Machine Learning



Kesimpulan dan Rekomendasi

Kesimpulan

1. Model Terbaik yang Digunakan: Model terbaik yang digunakan dalam analisis ini adalah XGBoost, yang merupakan algoritma pembelajaran mesin berbasis pohon keputusan yang dikenal dengan performa yang sangat baik dalam prediksi.
2. Hyperparameter yang Digunakan: Random Search, Hyperparameter yang dioptimalkan untuk model XGBoost mencakup:
subsample: 0.6
reg_alpha: 0.001
n_estimators: 190
max_depth: 5
learning_rate: 0.04
gamma: 9
colsample_bytree: 0.9
3. Akurasi Model: Setelah dilakukan tuning hyperparameter, model XGBoost menghasilkan RMSE sebesar 85.71 dan MAE sebesar 59.16, yang menunjukkan peningkatan signifikan dibandingkan rule based model (RMSE 686,083 dan MAE 537,61).
4. Keuntungan Menggunakan Machine Learning: Dengan menggunakan model machine learning, keuntungan biaya sewa diperkirakan meningkat sebesar $60.037,62. Ini menunjukkan bahwa pendekatan ini dapat memberikan peningkatan keuntungan yang signifikan dalam melakukan prediksi sepeda sewaan.

   
Rekomendasi untuk model

1. Kekurangan Model
Meskipun XGBoost menunjukkan hasil yang baik, model ini mungkin masih terpengaruh oleh outliers dan ketidaknormalan dalam distribusi data. Selain itu, kompleksitas model dapat menyulitkan interpretasi hasil secara langsung.
Pengembangan lebih lanjut dapat mencakup eksplorasi model lain seperti Random Forest atau Neural Networks untuk membandingkan performa dan meningkatkan akurasi.
2. Pengembangan Model ke Depan
Pertimbangkan untuk mengintegrasikan fitur baru, seperti data cuaca lebih rinci, lokasi geografis pengguna, dan pola penggunaan berdasarkan waktu.
Penelitian lebih lanjut tentang pengaruh interaksi antar fitur juga bisa menjadi fokus utama untuk meningkatkan akurasi model.


Rekomendasi untuk Bisnis

1. Fokus pada Feature Importances
Berdasarkan hasil analisis feature importances, beberapa fitur menunjukkan dampak yang signifikan terhadap jumlah penyewaan sepeda. Misalnya, suhu dan jam (hr) memiliki pengaruh besar. Oleh karena itu, bisnis sebaiknya memfokuskan strategi pemasaran pada periode-periode dengan suhu optimal dan jumlah jam sewa tertinggi.
2. Strategi Pemasaran dan Penawaran
Mengembangkan program promosi pada hari-hari dengan cuaca yang mendukung dan selama jam sibuk untuk meningkatkan pemanfaatan sepeda.
Pertimbangkan untuk menawarkan diskon atau paket sewa di saat cuaca buruk untuk menjaga arus kas.
3. Peningkatan Layanan Pelanggan
Untuk meningkatkan pengalaman pengguna, fokus pada edukasi pengguna tentang penggunaan sepeda selama musim tertentu dan bagaimana cuaca mempengaruhi penggunaan.
Sediakan informasi real-time mengenai ketersediaan sepeda dan kondisi cuaca.

