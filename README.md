# **Prediksi Bioaktivitas Senyawa terhadap Protein MTOR Menggunakan Pendekatan Random Forest Regressor dan Artificial Neural Network**
![alt text](mTOR.png?raw=true)
## Kelompok 8 Bioinformatika RB

- Meinisa - 121450076
- Ibnu Farhan Al-Ghifari - 121450121
- Anissa Luthfi Alifia - 121450093
- Angelica Noviana - 121450064
- Sella Dianka Fitri - 121450043
- Nadia Fitri Yani - 121450101

---

## 📱 **Tentang Proyek**

Proyek ini bertujuan untuk melakukan prediksi bioaktivitas senyawa terhadap protein MTOR (mechanistic Target of Rapamycin) menggunakan Artificial Neural Network (ANN) dan Random Forest Regressor (RFR). Kedua pendekatan tersebut digunakan untuk:

1. Mengklasifikasikan senyawa berdasarkan bioaktivitasnya (active, inactive, intermediate).
2. Memperkirakan nilai pIC50 sebagai ukuran kuantitatif efektivitas senyawa.

Protein ini penting dalam pengobatan kanker, diabetes, dan penyakit lainnya, sehingga penting untuk mengidentifikasi senyawa yang efektif menghambat aktivitasnya. Pendekatan utama adalah menggunakan teknik Virtual Drug Screening (VDS) berbasis Machine Learning, untuk mengembangkan inhibitor mTOR dengan tujuan untuk terapi kanker dan metabolik lainnya.

---

## 📋 Data 

- **Sumber**: Database ChEMBL.
- **Fitur Utama**:
  - Struktur molekul (SMILES).
  - Deskriptor fisiko-kimia: berat molekul, logP, donor hidrogen, akseptor hidrogen.
  - Fingerprint molekul (bit vektor binary).
- **Target**:
  - pIC50: Skala logaritmik dari IC50.
- **Ukuran Dataset**:
  - Data terdiri dari 4185 senyawa setelah proses pembersihan.

---

## 📂 Metode

**1. Data Collection**
  - Sumber: Database ChEMBL.
  - Data Awal: Bioaktivitas senyawa diambil berdasarkan nilai IC50 yang relevan dengan target MTOR.
    
**2. Data Preprocessing**
  - Normalisasi: Nilai IC50 diubah ke skala logaritmik (pIC50) untuk mengurangi skewness dan meningkatkan stabilitas model. Senyawa dengan nilai pIC50 tinggi dianggap lebih aktif.
  - Label Encoding: Senyawa dikelompokkan menjadi active, inactive, atau intermediate berdasarkan nilai ambang IC50 ≥ 10,000: inactive dan IC50 ≤ 1,000: active. Lainnya: intermediate.
  - Transformasi Struktur Molekul: Representasi SMILES (struktur kimia) diubah menjadi deskriptor molekul menggunakan PaDEL-Descriptor. Fitur deskriptor meliputi berat molekul, logP, donor/akseptor hidrogen, dan fingerprint.
    
**3. Feature Engineering**
  - Deskriptor Lipinski: Fitur drug-likeness dihitung seperti Berat molekul (Molecular Weight - MW), Hidrofobisitas (logP), jumlah donor hidrogen, dan umlah akseptor hidrogen.
  - Fingerprint Molekul: Representasi molekul dalam bentuk vektor binary.
    
**4. Membangun Model**
  - Random Forest Regressor (RFR): Untuk memprediksi nilai pIC50, dan evaluasi menggunakan R² dan Mean Squared Error (MSE).
  - Artificial Neural Network (ANN): Untuk mengklasifikasikan senyawa ke dalam kelas bioaktivitas (active, inactive, intermediate).
    
**5. Training dan Evaluasi**
  - Data Splitting: Data dibagi menjadi training set (80%) dan testing set (20%).
  - ANN Training:
    - Optimizer: Adam
    - Loss Function: binary_crossentropy
    - Jumlah Epoch: 100
    - Batch Size: 128
  - Visualisasi: Plot kurva akurasi dan loss untuk mengevaluasi performa pelatihan, serta confusion matrix untuk mengevaluasi performa klasifikasi.

---

## 🖥 Bahasa Pemrograman & Library 
![Python](https://img.shields.io/badge/-Python-3776AB?style=flat&logo=python&logoColor=white) 
![Pandas](https://img.shields.io/badge/-Pandas-150458?style=flat&logo=pandas&logoColor=white)  
![TensorFlow](https://img.shields.io/badge/-TensorFlow-FF6F00?style=flat&logo=tensorflow&logoColor=white)  
![Keras](https://img.shields.io/badge/-Keras-D00000?style=flat&logo=keras&logoColor=white)  
![RDKit](https://img.shields.io/badge/-RDKit-5C3EE8?style=flat&logo=python&logoColor=white)  
![PaDEL](https://img.shields.io/badge/-PaDEL-228B22?style=flat&logo=java&logoColor=white)  
![Matplotlib](https://img.shields.io/badge/-Matplotlib-11557C?style=flat&logo=python&logoColor=white)  
![Seaborn](https://img.shields.io/badge/-Seaborn-3776AB?style=flat&logo=python&logoColor=white)  
![Scikit-learn](https://img.shields.io/badge/-ScikitLearn-F7931E?style=flat&logo=scikit-learn&logoColor=white)  
![VisualKeras](https://img.shields.io/badge/-VisualKeras-FF6F00?style=flat&logo=keras&logoColor=white)  
![Lazypredict](https://img.shields.io/badge/-LazyPredict-483D8B?style=flat&logo=python&logoColor=white)  

---

## 📈 Hasil Model 
**1. Random Forest Regressor**
   - R² (Testing Set): 0.68, menunjukkan bahwa model dapat menjelaskan 68% variasi data uji.
   - Mean Squared Error (MSE): 0.17, mengindikasikan kesalahan prediksi yang rendah pada nilai pIC50.
     
**2. Artificial Neural Network**
   - Confusion Matrix: Menunjukkan bahwa model ANN dapat memisahkan kelas active, inactive, dan intermediate dengan baik.
   - Laporan Klasifikasi: Precision, recall, dan F1-score tinggi untuk kelas aktif.
   - Akurasi Pelatihan: Akurasi mendekati 1.0 pada data pelatihan dan validasi, menunjukkan performa model yang baik.

**Kesimpulan**: RFR merupakan model yang cukup baik dalam memprediksi nilai pIC50 dan memiliki akurasi yang tinggi dalam menangkap hubungan non-linear antar fitur. Serta ANN mampu mengklasifikasikan senyawa ke dalam kelas bioaktivitas dengan performa tinggi, serta efektif dalam melakukan klasifikasi multi-class.

---

## 📧 Kontak Tim Peneliti

- meinisa.121450076@student.itera.ac.id
- ibnu.121450121@student.itera.ac.id
- anissa.121450093@student.itera.ac.id
- angelica.121450064@student.itera.ac.id
- sella.121450043@student.itera.ac.id
- nadia.121450101@student.itera.ac.id



