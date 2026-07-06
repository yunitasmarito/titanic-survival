
# Titanic Survival Prediction

Proyek data science untuk menganalisis dataset penumpang Titanic dan membangun model klasifikasi guna memprediksi apakah seorang penumpang **selamat (Survived)** atau tidak menggunakan algoritma **Linear Support Vector Classifier (LinearSVC)**.

## Deskripsi

Notebook ini mengimplementasikan alur kerja data science secara end-to-end, mulai dari eksplorasi data (**Exploratory Data Analysis/EDA**), visualisasi, preprocessing, feature engineering, pembangunan model, evaluasi performa, hingga menghasilkan file prediksi (`result.csv`) untuk data uji.

## Alur Pengerjaan

| No. | Tahapan                           | Deskripsi                                                                                                                                                                                                         |
| :-: | --------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
|  1  | **Importing Libraries**           | Mengimpor library yang dibutuhkan seperti `pandas`, `numpy`, `seaborn`, `matplotlib`, serta modul dari `scikit-learn` (`train_test_split`, `LinearSVC`, dan `metrics`).                                           |
|  2  | **Loading and Exploring Dataset** | Membaca dataset `train.csv`, menampilkan informasi data, membuat cross-tab berdasarkan jenis kelamin, serta visualisasi awal menggunakan violin plot dan count plot.                                              |
|  3  | **Data Preprocessing**            | Menangani missing values dengan mengisi kolom `Age` dan `Fare` menggunakan median, mengisi nilai kosong pada `Embarked` dengan `'S'`, serta menghapus kolom yang tidak digunakan (`Name`, `Ticket`, dan `Cabin`). |
|  4  | **Data Visualization**            | Membuat berbagai visualisasi seperti bar chart dan KDE plot untuk menganalisis hubungan antara fitur (`Pclass`, `SibSp`, `Fare`, dan `Age`) terhadap status `Survived`.                                           |
|  5  | **Feature Engineering**           | Mengubah data kategorikal menjadi numerik melalui encoding pada kolom `Sex` dan `Embarked`.                                                                                                                       |
|  6  | **Modeling & Evaluation**         | Membagi dataset menjadi data latih dan data uji (80:20), melatih model `LinearSVC`, kemudian mengevaluasi performa menggunakan accuracy, classification report, dan confusion matrix.                             |
|  7  | **Prediction**                    | Melakukan preprocessing yang sama pada `test.csv`, menghasilkan prediksi, dan menyimpan hasilnya ke dalam file `result.csv`.                                                                                      |

---

## Dataset

Proyek ini menggunakan dataset **Titanic: Machine Learning from Disaster** dari Kaggle yang terdiri dari dua file utama:

* **`train.csv`** — Dataset pelatihan yang berisi label `Survived`.
* **`test.csv`** — Dataset pengujian tanpa label `Survived` yang digunakan untuk menghasilkan prediksi.

### Fitur yang Digunakan

| Fitur      | Deskripsi                                                       |
| ---------- | --------------------------------------------------------------- |
| `Pclass`   | Kelas tiket (1 = Upper, 2 = Middle, 3 = Lower)                  |
| `Sex`      | Jenis kelamin (di-encode menjadi 0 = Male, 1 = Female)          |
| `Age`      | Usia penumpang                                                  |
| `SibSp`    | Jumlah saudara kandung atau pasangan yang ikut                  |
| `Parch`    | Jumlah orang tua atau anak yang ikut                            |
| `Fare`     | Harga tiket                                                     |
| `Embarked` | Pelabuhan keberangkatan (di-encode menjadi 1 = S, 2 = Q, 3 = C) |

> **Catatan**
>
> Repository ini menyertakan file `titanic_data.csv`, namun notebook membaca dataset `train.csv` dan `test.csv` menggunakan `google.colab.files.upload()`. Oleh karena itu, kedua file tersebut perlu diunggah secara manual saat menjalankan notebook di Google Colab.

---

## Requirements

```
pandas
numpy
matplotlib
seaborn
scikit-learn
```

### Instalasi

```bash
pip install pandas numpy matplotlib seaborn scikit-learn
```

---

## Cara Menjalankan

Notebook ini dikembangkan menggunakan **Google Colab**, namun juga dapat dijalankan secara lokal.

### 1. Menjalankan di Google Colab

1. Buka file `Test_DataScientist.ipynb` di Google Colab.
2. Jalankan sel pertama.
3. Unggah file `train.csv` ketika diminta oleh `files.upload()`.
4. Jalankan seluruh sel notebook secara berurutan.
5. Pada bagian **Prediction**, unggah file `test.csv`.
6. Hasil prediksi akan disimpan dalam file `result.csv`.

### 2. Menjalankan Secara Lokal (Jupyter Notebook)

Ganti kode berikut:

```python
uploaded = files.upload()
```

menjadi:

```python
train = pd.read_csv("train.csv", encoding="ISO-8859-1")
```

Lakukan hal yang sama pada pembacaan `test.csv`, kemudian jalankan notebook menggunakan:

```bash
jupyter notebook Test_DataScientist.ipynb
```

---

## Model

Model klasifikasi yang digunakan adalah **Linear Support Vector Classifier (LinearSVC)** dari `scikit-learn`.

| Parameter  | Nilai                                                 |
| ---------- | ----------------------------------------------------- |
| Algoritma  | LinearSVC                                             |
| Kernel     | Linear                                                |
| `C`        | 0.1                                                   |
| Data Split | 80% Training, 20% Testing                             |
| Evaluasi   | Accuracy, Classification Report, dan Confusion Matrix |

---

## Output

Notebook menghasilkan file **`result.csv`** yang berisi prediksi status **`Survived`** untuk setiap penumpang pada dataset pengujian.

Contoh struktur output:

| PassengerId | Survived |
| ----------- | -------- |
| 892         | 0        |
| 893         | 1        |
| 894         | 0        |
| ...         | ...      |

