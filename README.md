<h1 align="center">  Creating anime characters using Deep Convolutional Generative Adversarial Networks (DCGANs) and Keras </h1>
<p align="center"> Proyek ini mengimplementasikan **Deep Convolutional Generative Adversarial Networks (DCGAN)** untuk menghasilkan gambar wajah anime baru. DCGAN adalah jenis jaringan saraf generatif yang dapat digunakan untuk menciptakan data baru yang menyerupai data pelatihan. Dalam proyek ini, model DCGAN dilatih menggunakan dataset wajah anime, sehingga mampu menghasilkan wajah anime yang realistis dan berkualitas tinggi. </p>

<div align="center">

<img src="https://img.shields.io/badge/python-3670A0?style=for-the-badge&logo=python&logoColor=ffdd54">
<img src="https://img.shields.io/badge/jupyter-%23FA0F00.svg?style=for-the-badge&logo=jupyter&logoColor=white">
<img src="https://img.shields.io/badge/tensorflow-%23FF6F00.svg?style=for-the-badge&logo=tensorflow&logoColor=white">
<img src="https://img.shields.io/badge/keras-D00000.svg?style=for-the-badge&logo=keras&logoColor=white">

</div>

<h2 align="center"> Tujuan </h2>

**Proyek ini bertujuan untuk:**  
1. Menggunakan DCGAN untuk mempelajari distribusi data pada wajah anime.  
2. Menghasilkan gambar karakter anime baru yang menyerupai data pelatihan.  
3. Memberikan pemahaman tentang arsitektur DCGAN serta proses pelatihannya.  

<h2 align="center"> Langkah-Langkah Proyek </h2> 

### 1. Pengaturan Awal
- Mengimpor pustaka yang diperlukan, seperti:
  - **TensorFlow** dan **Keras** untuk membangun model.
  - **NumPy** untuk manipulasi data.
  - **Matplotlib** untuk visualisasi hasil.  
- Mendefinisikan fungsi pembantu, seperti:  
  - `plot_distribution()` untuk visualisasi distribusi data.
  - `plot_array()` untuk memvisualisasikan hasil gambar yang dihasilkan.

### 2. Dataset
- Dataset yang digunakan adalah **Anime Face Dataset** dari Kaggle.  
- Dataset ini terdiri dari 63.632 gambar wajah anime berkualitas tinggi. Namun, dalam proyek ini hanya digunakan 20.000 sampel secara acak untuk mempercepat pelatihan.
- Dataset diproses menggunakan `image_dataset_from_directory` untuk memuat dan mengelola gambar secara efisien. Semua gambar diubah ukurannya menjadi 64x64 piksel dan dinormalisasi ke rentang [-1, 1].

### 3. Arsitektur Model
#### Generator  
- Generator bertugas membuat gambar baru dari vektor laten acak (berukuran 100 dimensi).  
- Menggunakan serangkaian lapisan *Conv2DTranspose* untuk meningkatkan ukuran gambar secara bertahap hingga menghasilkan output akhir berupa gambar 64x64 piksel dengan 3 saluran warna (RGB).  
- Aktivasi yang digunakan:  
  - ReLU untuk lapisan tersembunyi.  
  - Tanh untuk lapisan output.  

#### Diskriminator  
- Diskriminator bertugas membedakan antara gambar asli dari dataset dan gambar yang dihasilkan oleh Generator.  
- Menggunakan serangkaian lapisan *Conv2D* untuk mengurangi ukuran gambar secara bertahap hingga menjadi skalar probabilitas.  
- Aktivasi yang digunakan:  
  - LeakyReLU untuk lapisan tersembunyi.  
  - Sigmoid untuk lapisan output.  

### 4. Fungsi Kerugian dan Optimizer  
- **Fungsi Kerugian**:
  - Generator berusaha memaksimalkan peluang Diskriminator menganggap gambar palsu sebagai gambar asli.  
  - Diskriminator berusaha memaksimalkan kemampuan untuk membedakan gambar asli dan palsu.  
- **Optimizer**:  
  - Menggunakan **Adam Optimizer** untuk mempercepat konvergensi selama pelatihan.

### 5. Pelatihan Model
- Fungsi `train_step()` digunakan untuk melatih model DCGAN. Prosesnya:  
  1. Generator menghasilkan gambar palsu dari vektor laten acak.  
  2. Diskriminator dilatih untuk membedakan gambar asli dan palsu.  
  3. Generator dilatih untuk "menipu" Diskriminator.  
- Proses ini diulangi selama beberapa epoch hingga Generator mampu menghasilkan gambar yang realistis.  

### 6. Evaluasi dan Visualisasi
- Model menghasilkan gambar anime baru yang dapat divisualisasikan menggunakan fungsi `plot_array()`.  
- Progres pelatihan dievaluasi berdasarkan kualitas visual gambar yang dihasilkan.


<h2 align="center"> Hasil </h2>

- Setelah training selesai, model DCGAN mampu menghasilkan wajah anime baru.  
- Kualitas gambar yang dihasilkan bergantung pada beberapa faktor:  
  1. Ukuran dataset pelatihan.  
  2. Jumlah epoch pelatihan.  
  3. Arsitektur model Generator dan Diskriminator.  


<h2 align="center"> Setup </h2>

- Libraries yang dibutuhkan sebelum mulai:  
  *   [`pandas`](https://pandas.pydata.org/?utm_medium=Exinfluencer&utm_source=Exinfluencer&utm_content=000026UJ&utm_term=10006555&utm_id=NA-SkillsNetwork-Channel-SkillsNetworkCoursesIBMML0187ENSkillsNetwork31430127-2021-01-01) for managing the data.
  *   [`numpy`](https://numpy.org/?utm_medium=Exinfluencer&utm_source=Exinfluencer&utm_content=000026UJ&utm_term=10006555&utm_id=NA-SkillsNetwork-Channel-SkillsNetworkCoursesIBMML0187ENSkillsNetwork31430127-2021-01-01) for mathematical operations.
  *   [`sklearn`](https://scikit-learn.org/stable/?utm_medium=Exinfluencer&utm_source=Exinfluencer&utm_content=000026UJ&utm_term=10006555&utm_id=NA-SkillsNetwork-Channel-SkillsNetworkCoursesIBMML0187ENSkillsNetwork31430127-2021-01-01) for machine learning and machine-learning-pipeline related functions.
  *   [`seaborn`](https://seaborn.pydata.org/?utm_medium=Exinfluencer&utm_source=Exinfluencer&utm_content=000026UJ&utm_term=10006555&utm_id=NA-SkillsNetwork-Channel-SkillsNetworkCoursesIBMML0187ENSkillsNetwork31430127-2021-01-01) for visualizing the data.
  *   [`matplotlib`](https://matplotlib.org/?utm_medium=Exinfluencer&utm_source=Exinfluencer&utm_content=000026UJ&utm_term=10006555&utm_id=NA-SkillsNetwork-Channel-SkillsNetworkCoursesIBMML0187ENSkillsNetwork31430127-2021-01-01) for additional plotting tools.
  *   [`keras`](https://keras.io/?utm_medium=Exinfluencer&utm_source=Exinfluencer&utm_content=000026UJ&utm_term=10006555&utm_id=NA-SkillsNetwork-Channel-SkillsNetworkCoursesIBMML0187ENSkillsNetwork31430127-2021-01-01) for loading datasets.
  *   [`tensorflow`](https://www.tensorflow.org/?utm_medium=Exinfluencer&utm_source=Exinfluencer&utm_content=000026UJ&utm_term=10006555&utm_id=NA-SkillsNetwork-Channel-SkillsNetworkCoursesIBMML0187ENSkillsNetwork31430127-2021-01-01) for machine learning and neural network related functions.  
- Disarankan menggunakan GPU untuk mempercepat pelatihan model.  


<h2 align="center"> Note </h2>

1. **Optimasi Kinerja**:
   - Gunakan GPU/TPU untuk mempercepat pelatihan.  
   - Terapkan augmentasi data untuk meningkatkan performa model.  
2. **Evaluasi**:  
   - Gunakan skor FID (Frechet Inception Distance) untuk mengevaluasi kualitas gambar yang dihasilkan.  
3. **Pengembangan Lebih Lanjut**:  
   - Eksplor model **StyleGAN** untuk menghasilkan gambar dengan resolusi lebih tinggi dan kontrol yang lebih terarah pada atribut gambar (misalnya, warna rambut atau ekspresi).