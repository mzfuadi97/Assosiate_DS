#  Prediksi Keberadaan Diabetes pada Pasien Perempuan Indian Pima Berusia Minimal 21 Tahun menggunakan Pengukuran Diagnostik

Dokter ADS-C ingin melakukan prediksi berdasarkan pengukuran diagnostik apakah seorang pasien menderita diabetes atau tidak. Secara khusus, semua pasien di sini adalah perempuan berusia minimal 21 tahun keturunan Indian Pima 

## Domain Proyek

> Dataset yang digunakan adalah Pima Indians Diabetes Database yang merupakan data dari  the National Institute of Diabetes and Digestive and Kidney Diseases.
Sumber data tersebut didapatkan dari data publik yang dapat diunduh melalui Data World dengan link berikut: 
(rahasia)

## Business Understanding
### - Problem Statement
- Dokter ADS-C ingin melakukan prediksi berdasarkan pengukuran diagnostik apakah seorang pasien menderita diabetes atau tidak. Secara khusus, semua pasien di sini adalah perempuan berusia minimal 21 tahun keturunan Indian Pima ?
- Bagaimana kita dapat memanfaatkan data pengukuran medis yang tepat untuk membantu dokter dalam mengambil keputusan yang lebih akurat dalam mendiagnosis pasien dan memberikan perawatan yang sesuai?

### - Goals
- Mengambil keputusan diagnostik yang lebih akurat terkait keberadaan diabetes pada pasien perempuan Indian Pima berusia minimal 21 tahun.
- Menentukan perawatan yang paling sesuai dan efektif berdasarkan hasil prediksi model dan pengukuran medis yang relevan.

### - Solution Statement
- Menggunakan algoritma RandomForest dan membandingkan algoritma decision tree seperti dengan PCA serta cross validation untuk meningkatkan akurasi prediksi data.

## Data Understanding

Dataset rahasia

Selanjutnya uraikanlah seluruh variabel atau fitur pada data. Sebagai contoh:  

| Informasi | Penjelasan |
| ------ | ------ |
| Jumlah Baris | 768 |
| Jumlah Kolom | 9 |
| Missing Value | 374 |

Keterangan kolom data :

| Nama | Keterangan |
| ------ | ------ |
| Pregnancies | Berapa kali hamil |
| Glucose | Konsentrasi glukosa plasma 2 jam setelah tes toleransi glukosa oral |
| BloodPressure | Tekanan darah diastolik (mm Hg) |
| SkinThickness | Ketebalan lipatan kulit trisep (mm) |
| Insulin | Insulin serum 2 jam (mu U/ml) |
| BMI | Indeks massa tubuh (berat dalam kg/(tinggi dalam m)^2) |
| DiabetesPedigreeFunction | Fungsi silsilah diabetes |
| Age | Usia pasien |
| Outcome | Variabel Kelas penderita diabetes atau tidak:
1 = penderita diabetes
0 = bukan penderita diabetes |

![Describe-Data](https://github.com/mzfuadi97/Assosiate_DS/assets/70827786/246bf312-307a-4d0c-a386-ac274d9c23f5)

Gambar 1. Distribusi Data

Pada gambar 1. Terdapat missing value, outlier, beberapa baris memiliki nilai yang sama, sehingga akan dilakukan :


## Data Preparation
Pada bagian ini Anda menerapkan dan menyebutkan teknik data preparation yang dilakukan. 

- Menerapkan dan menyebutkan teknik data preparation yang dilakukan. (Data Imbalancing, data normalization)
- Data Imbalancing mengatasi masalah ini dengan menyeimbangkan distribusi kelas sehingga model atau algoritma lebih akurat dalam memprediksi kedua kelas.
- Data Normalization meningkatkan akurasi dan kecepatan dalam pemrosesan data serta meningkatkan interpretasi hasil analisis.
- Dengan melakukan data preparation, hasil analisis dan model yang dihasilkan akan lebih akurat dan efektif.
- Pembagian dataset training dan dataset testing yaitu 80% banding 20% untuk mempercepat proses mesin belajar dan evaluasi model.

Correlation Matrix
![Correlation Matriks- No](https://github.com/mzfuadi97/Assosiate_DS/assets/70827786/4712a150-da77-4a36-a83a-cf75828a3648)
Gambar 2. Heatmap dataset diabetes

> Terlihat pada feature “no” memiliki nilai korelasi terhadap nilai label sebesar 0,038, sehingga drop feature “no” tersebut. Namun beberapa memiliki korelasi negatif, artinya jika glokosa tinggi maka kemungkinan tidak memiliki penyakit diabetes.
> Dipilih feature predictor yang tidak mendekati 0, sehingga feature yang digunakan yaitu : Pregnant, Glucose, Bloodpredcit, SkinThic, Insulin, BMI, DiabetesDiagree, dan Age

![Result-Normalization](https://github.com/mzfuadi97/Assosiate_DS/assets/70827786/bef9b097-fa6c-4921-9860-149838189353)
Gambar 3. Hasil Normalisasi

## Data Modelling

Model menggunakan RandomForest, serta Tree Decision karena dilakukan cross validation dan PCA, akurasi terbaik yaitu menggunakan algoritma murni Random Forest. 

> Sebelum dilakukan PCA dan CV, dibandingkan beberapa algorithma yaitu : Decision Tree, Random Forest, ID3.
> Proses pelabelan data dengan memilih feature target berdasarkan rumusan masalh yang sudah ditentukan kemudian, dibagi menjadi proporsi 80:20, 90:10, 60:40 serta 70:30. Tahap ini dapat mempengaruhi dalam membangun model. Jadi, ouputnya menjadi 2 yaitu data training dan data testing, sesuai dengan proporsi yang ditentukan. Data training untuk melatih model serta data testing untuk melakukan pengetesan performa model.
> RandomForest mengatur beberapa parameter, yaitu dataset, parameter number of trees = 100, jumlah fold yang digunakan (nfold=5), metrics yang ingin digunakan untuk evaluasi (metrics="auc"), criterion menggunakan gain_ration, serta maximal_depth = 10.
> Setelah melakukan cross validation, Optimasi parameter model algoritma, mengasumsikan metode “cross validation” untuk meningkatan akurasi model, namun ketika uji coba, hasil outputnya menurunkan peforma model, sehingga cross validation hanya menjadi uji coba saja. Selain itu, dilakukan untuk menentukan parameter-parameter model untuk mendapatkan peforma terbaik. Salah satu cara yaitu melakukan hyperparameter tuning untuk mendapatk parameter-parameter model yang optimal.


## Evaluation

Pada hasil evaluasi memiih kasus klasifikasi dan menggunakan metrik **akurasi, precision, recall, dan F1 score**. Jelaskan mengenai beberapa hal berikut:


- DecisionTree :  membuat keputusan berdasarkan serangkaian aturan dan pertanyaan (tree) yang digunakan untuk memprediksi target variabel, memprediksi tentang pelanggan yang akan beralih dengan menguji aturan berdasarkan fitur-fitur yang diberikan.
- RandomForest : mirip dengan Decision Tree, namun beroperasi dengan menggabungkan beberapa decision tree, mirip dengan Decision Tree, namun beroperasi dengan menggabungkan beberapa decision tree.

![perform RF](https://github.com/mzfuadi97/Assosiate_DS/assets/70827786/212c5cb8-1bbe-44b7-b619-030b6c4ce7c9)
Gambar 4. Confussion Matriks menggunakan Random Forest

![perform DT](https://github.com/mzfuadi97/Assosiate_DS/assets/70827786/9f40877e-d7bf-42bc-903a-d916308aa98f)
Gambar 5. Confussion Matriks menggunakan Decision Tree

Pada Gambar 4. Model Random Forest dan DT memiliki akurasi yang cukup tinggi yaitu 0.82. Namun, jika diperhatikan juga nilai standard deviation (std), model DT memiliki nilai akurasi yang lebih rendah yaitu 0.77 dibandingkan dengan model Random Forest yang memiliki nilai std 0.82. Nilai std yang lebih rendah menunjukkan bahwa model DT memiliki stabilitas performa yang lebih baik ketika diuji dengan data yang berbeda-beda, sehingga dapat dipertimbangkan sebagai model terbaik. Sehingga pada model algoritma yang digunakan pada permasalahan diabetes classification ini menggunakan RandomForest.

![perform RF](https://github.com/mzfuadi97/Assosiate_DS/assets/70827786/8e62d8a7-0b59-4b42-b2fd-cbf8fb1f3bba)
Gambar 6. Confussion Matrix

Pada Gambar 6. dapat dilihat :


Dari model paling optimal pada kasus ini menggunakan model Random Forest yang memiliki akurasi sebesar 82,80% dengan ketentuan, precision positif : 96% precision negatif : 79%, recall positif : 51,90%, serta recall negatif: 98,99%, artinya :

> precision diabetes : semua data yang diprediksi sebagai diabetes oleh model 96%, yaitu benar-benar diabetes
> precision normal : semua data yang diprediksi sebagai normal oleh model 79%, yaitu benar-benar normal
> recall diabetes : model berhasil menemukan 51,90% dari semua data diabetes sebenarnya
> recall normal : model berhasil menemukan 98,99% dari semua data normal sebenarnya.

Dari informasi sebelumnya, bahwa model cenderung lebih akurat memprediksi kelas normal, tetapi memiliki kekurangan dalam prediksi diabetes.

