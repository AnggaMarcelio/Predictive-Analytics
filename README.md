# Laporan Proyek Machine Learning - Ch Angga Marcelio

## Domain Proyek
**Latar Belakang**

Sektor pertanian memainkan peran krusial dalam ketahanan pangan dan ekonomi nasional, terutama di negara berkembang seperti Indonesia. Salah satu tantangan utama adalah menentukan jenis tanaman yang paling sesuai untuk ditanam berdasarkan karakteristik tanah dan lingkungan, seperti tingkat pH, kadar nutrisi, curah hujan, dan suhu. Ketidaktepatan dalam pengambilan keputusan ini seringkali menyebabkan kerugian hasil panen dan penurunan pendapatan petani.

Perkembangan teknologi Machine Learning (ML) telah membuka peluang untuk mengatasi tantangan tersebut dengan pendekatan berbasis data. Sebuah studi melaporkan bahwa sistem rekomendasi tanaman berbasis algoritma Random Forest berhasil mencapai akurasi hingga 99,22% dalam memprediksi jenis tanaman yang sesuai berdasarkan parameter agrikultur seperti nitrogen, fosfor, dan kelembapan. [[1](https://doi.org/10.5935/jetia.v10i48.1186)] Penelitian lain mengembangkan sistem pendukung keputusan berbasis aplikasi Android yang menggunakan 13 algoritma klasifikasi berbeda, termasuk SVM dan Decision Tree, untuk merekomendasikan tanaman yang cocok secara lokal. Sistem ini terbukti mampu membantu petani dalam pengambilan keputusan yang lebih akurat dan efisien. [[2](https://doi.org/10.3390/agriculture14081256)]

Penelitian selanjutnya menunjukkan bahwa penggunaan teknik Machine Learning dapat memberikan efisiensi tinggi dalam rekomendasi tanaman, serta berkontribusi pada peningkatan hasil pertanian dan pengurangan risiko kegagalan panen. [[3](https://doi.org/10.5281/zenodo.11441063)] Sebuah prototipe sistem berbasis mobile juga telah dikembangkan untuk digunakan langsung oleh petani di lapangan. Sistem tersebut memanfaatkan algoritma Random Forest dan menghasilkan akurasi rekomendasi hingga 95%, membuktikan efektivitasnya dalam aplikasi dunia nyata [[4](https://www.ijert.org/crop-recommendation-system-using-machine-learning)]

Secara umum, pemanfaatan teknologi berbasis kecerdasan buatan seperti Machine Learning di sektor pertanian merupakan bagian dari transformasi menuju pertanian presisi (precision agriculture). Dengan kemampuan untuk menganalisis data dalam jumlah besar dan mengidentifikasi pola yang kompleks, Machine Learning memungkinkan sistem untuk memberikan rekomendasi berbasis prediksi yang sebelumnya sulit dicapai dengan pendekatan konvensional. Hal ini tidak hanya mendukung pengambilan keputusan yang lebih baik, tetapi juga berpotensi meningkatkan efisiensi sumber daya, mengurangi limbah pertanian, dan meningkatkan ketahanan terhadap perubahan iklim. Oleh karena itu, integrasi ML dalam sistem rekomendasi tanaman menjadi langkah strategis dalam mewujudkan pertanian yang berkelanjutan dan adaptif di masa depan.

**Mengapa dan bagaimana masalah ini harus diselesaikan?**

Masalah pemilihan tanaman yang tidak sesuai dengan kondisi tanah dan iklim lokal dapat berdampak signifikan terhadap produktivitas pertanian dan kesejahteraan petani. Banyak petani di daerah pedesaan masih mengandalkan pengalaman atau kebiasaan turun-temurun dalam menentukan jenis tanaman, tanpa mempertimbangkan data ilmiah terkait kualitas tanah, kebutuhan nutrisi, serta perubahan iklim yang kian tidak menentu. Akibatnya, tanaman yang ditanam sering kali tidak optimal, yang berujung pada hasil panen yang rendah, pemborosan sumber daya, dan kerugian finansial.

Masalah ini harus diselesaikan dengan pendekatan berbasis teknologi dan data, salah satunya melalui pemanfaatan Machine Learning. Dengan memproses data seperti kandungan nitrogen, fosfor, kalium, pH tanah, curah hujan, suhu, dan kelembapan, algoritma Machine Learning dapat mempelajari pola dan menghasilkan rekomendasi tanaman yang paling sesuai dengan kondisi tersebut. Implementasi sistem semacam ini dapat membantu petani dalam mengambil keputusan yang lebih tepat, meningkatkan hasil produksi, serta memperkuat ketahanan pangan secara nasional. Selain itu, penggunaan sistem otomatis dan digital akan mempercepat adopsi teknologi di sektor pertanian menuju pertanian modern yang efisien dan berkelanjutan.

## Business Understanding
### Problem Statements

Permasalahan utama yang melatarbelakangi proyek ini adalah:
- Petani mengalami kesulitan dalam menentukan jenis tanaman yang paling sesuai dengan kondisi tanah dan lingkungan seperti pH, kadar nutrisi, suhu, dan curah hujan.
- Keputusan yang tidak didasarkan pada data sering mengakibatkan tanaman tidak tumbuh optimal, hasil panen rendah, dan meningkatnya risiko kegagalan panen.
- Ketiadaan sistem rekomendasi tanaman yang akurat dan mudah diakses oleh petani memperparah masalah pengambilan keputusan di lapangan.

### Goals

Adapun tujuan yang ingin dicapai dalam proyek ini adalah:
- Mengembangkan sistem rekomendasi tanaman berbasis Machine Learning untuk membantu petani dalam memilih jenis tanaman terbaik sesuai kondisi agronomis.
- Meningkatkan akurasi dan efektivitas dalam pemilihan tanaman agar hasil panen dapat optimal.
- Menyediakan alat bantu pengambilan keputusan yang berbasis teknologi dan data untuk petani dan pemangku kepentingan terkait.

### Solution statements

Solusi yang diajukan dalam proyek ini meliputi:
- Pembuatan model klasifikasi Machine Learning (seperti Random Forest, Decision Tree dan K-Nearest Neighbors) yang dilatih menggunakan data parameter agrikultur penting.
- Model yang dikembangkan mampu memberikan rekomendasi tanaman secara otomatis berdasarkan input kondisi tanah dan lingkungan.
- Pengembangan sistem digital yang user-friendly dan dapat diakses langsung oleh petani maupun pihak terkait.
- Sistem ini bertujuan meningkatkan produktivitas pertanian dan mengurangi risiko kerugian dengan pengambilan keputusan berbasis data.

## Data Understanding

Dataset yang digunakan dalam proyek ini adalah Crop Recommendation Dataset yang tersedia secara publik di Kaggle (tautan dataset). Dataset ini berisi informasi agronomis yang digunakan untuk merekomendasikan jenis tanaman yang paling sesuai berdasarkan kondisi lingkungan dan tanah.

### Struktur Dataset
Dataset terdiri dari 2.200 baris data dan 8 fitur input (independen) serta 1 target label (dependen). Berikut penjelasan setiap kolom:

| A_id | N  | P  | K  | Temperature | Humidity  | pH       | Rainfall   | Label |
|------|----|----|----|-------------|-----------|----------|------------|--------|
| 0    | 90 | 42 | 43 | 20.879744   | 82.002744 | 6.502985 | 202.935536 | rice   |
| 1    | 85 | 58 | 41 | 21.770462   | 80.319644 | 7.038096 | 226.655537 | rice   |
| 2    | 60 | 55 | 44 | 23.004459   | 82.320763 | 7.840207 | 263.964248 | rice   |
| 3    | 74 | 35 | 40 | 26.491096   | 80.158363 | 6.980401 | 242.864034 | rice   |
| 4    | 78 | 42 | 42 | 20.130175   | 81.604873 | 7.628473 | 262.717340 | rice   |

### Variabel-variabel pada dataset adalah sebagai berikut:

- `N` : Kandungan nitrogen dalam tanah (ppm). Nutrisi penting yang memengaruhi pertumbuhan daun dan batang tanaman.
- `P` : Kandungan fosfor dalam tanah (ppm). Berperan dalam perkembangan akar dan pembungaan tanaman.
- `K` : Kandungan kalium dalam tanah (ppm). Mendukung kekebalan tanaman dan pembentukan buah.
- `Temperature` : Suhu rata-rata lingkungan (°C). Faktor lingkungan penting yang memengaruhi metabolisme tanaman.
- `Humidity` : Kelembapan udara (%). Mempengaruhi transpirasi dan penyerapan air oleh tanaman.
- `pH` : Tingkat keasaman tanah. Menentukan ketersediaan nutrisi dalam tanah bagi tanaman.
- `Rainfall` : Curah hujan tahunan (mm). Mempengaruhi kebutuhan air dan sistem irigasi tanaman.
- `Label` : Jenis tanaman yang direkomendasikan berdasarkan parameter agronomis di atas (misal: rice, maize, cotton, coffee, dll.).

**Exploratory Data Analysis (EDA)**:

![Univariate Analysis]([https://i.ibb.co/V2mQ2dK/EDA-Univariate.png](https://github.com/AnggaMarcelio/Predictive-Analytics/blob/main/image/Distribusi%20Variabel.png?raw=true))


## Data Preparation
**Teknik Data Preparation**

**Alasan Tahapan Data Preparation Dilakukan**

## Modeling

## Evaluation


**Referensi**

Dataset: https://www.kaggle.com/datasets/atharvaingle/crop-recommendation-dataset

[1] B. Mohapatra and V. Kale, “Crop Recommendation System Using Machine Learning,” ITEGAM J. Eng. Technol. Ind. Appl., vol. 10, no. 48, pp. 63–68, 2024. [Online]. Available: https://doi.org/10.5935/jetia.v10i48.1186

[2] M. K. Senapaty, A. Ray, and N. Padhy, “A Decision Support System for Crop Recommendation Using Machine Learning Classification Algorithms,” Agriculture, vol. 14, no. 8, p. 1256, 2024. [Online]. Available: https://doi.org/10.3390/agriculture14081256

[3] P. N. Kiran Kumar et al., “An Efficient Crop Recommendation System Using Machine Learning Mechanisms,” Int. J. Hum. Comput. Intell., 2024. [Online]. Available: https://doi.org/10.5281/zenodo.11441063

[4] S. Bhargavi and J. Shrinivasan, “Crop Recommendation System Using Machine Learning,” Int. J. Eng. Res. Technol., vol. 11, no. 6, 2023. [Online]. Available: https://www.ijert.org/crop-recommendation-system-using-machine-learning

[5] S. Sharma, S. Rai, and N. C. Krishnan, “Wheat Crop Yield Prediction Using Deep LSTM Model,” arXiv preprint, arXiv:2011.01498, 2020. [Online]. Available: https://arxiv.org/abs/2011.01498
