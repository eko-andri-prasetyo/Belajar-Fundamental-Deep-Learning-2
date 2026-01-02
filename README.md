# 🍎 Fruit Classification using CNN

Proyek klasifikasi gambar buah-buahan menggunakan Convolutional Neural Network (CNN) dengan TensorFlow/Keras. 

![Python](https://img.shields.io/badge/Python-3.8+-blue.svg)
![TensorFlow](https://img.shields.io/badge/TensorFlow-2.x-orange.svg)
![License](https://img.shields.io/badge/License-MIT-green.svg)

## 📋 Deskripsi Proyek

Proyek ini mengklasifikasikan gambar buah-buahan menggunakan model CNN dengan arsitektur Sequential. Model dilatih menggunakan dataset [Fruits 360](https://www.kaggle.com/datasets/moltean/fruits) dari Kaggle.

### ✨ Fitur Utama
- Klasifikasi 3 jenis buah: Apple Red, Banana, Orange
- Model CNN dengan arsitektur Sequential
- Data Augmentation untuk meningkatkan performa
- Konversi model ke TF-Lite dan TensorFlow. js
- Akurasi > 85%

## 🏗️ Arsitektur Model

```
Model:  Sequential CNN
_________________________________________________________________
Layer (type)                Output Shape              Param #   
=================================================================
conv2d (Conv2D)             (None, 148, 148, 32)      896       
max_pooling2d (MaxPooling2D)(None, 74, 74, 32)        0         
conv2d_1 (Conv2D)           (None, 72, 72, 64)        18,496    
max_pooling2d_1 (MaxPooling)(None, 36, 36, 64)        0         
conv2d_2 (Conv2D)           (None, 34, 34, 128)       73,856    
max_pooling2d_2 (MaxPooling)(None, 17, 17, 128)       0         
conv2d_3 (Conv2D)           (None, 15, 15, 128)       147,584   
max_pooling2d_3 (MaxPooling)(None, 7, 7, 128)         0         
flatten (Flatten)           (None, 6272)              0         
dropout (Dropout)           (None, 6272)              0         
dense (Dense)               (None, 512)               3,211,776 
dropout_1 (Dropout)         (None, 512)               0         
dense_1 (Dense)             (None, 3)                 1,539     
=================================================================
Total params:  3,454,147
Trainable params: 3,454,147
Non-trainable params: 0
```

## 📊 Dataset

- **Sumber**: [Fruits 360 Dataset - Kaggle](https://www.kaggle.com/datasets/moltean/fruits)
- **Kelas yang digunakan**: Apple Red 1, Banana, Orange
- **Total gambar**: 1000+ gambar
- **Split ratio**: 70% Training, 15% Validation, 15% Test

## 🚀 Cara Penggunaan

### 1. Clone Repository

```bash
git clone https://github.com/eko-andri-prasetyo/Belajar-Fundamental-Deep-Learning-2. git
cd Belajar-Fundamental-Deep-Learning-2
```

### 2. Install Dependencies

```bash
pip install tensorflow numpy matplotlib pillow scikit-learn seaborn
```

### 3. Jalankan di Google Colab

1.  Buka [Google Colab](https://colab.research.google.com/)
2. Upload file `notebook.ipynb`
3. Upload file `kaggle.json` untuk download dataset
4. Jalankan semua cell secara berurutan

### 4. Inference dengan Model

```python
import tensorflow as tf
import numpy as np

# Load model
model = tf. keras.models.load_model('saved_model')

# Preprocessing
def preprocess_image(image_path, target_size=(150, 150)):
    img = tf.keras.preprocessing.image. load_img(image_path, target_size=target_size)
    img_array = tf. keras.preprocessing.image.img_to_array(img)
    img_array = img_array / 255.0
    img_array = np.expand_dims(img_array, axis=0)
    return img_array

# Prediksi
img_array = preprocess_image('path/to/your/image.jpg')
predictions = model.predict(img_array)
labels = ['Apple Red 1', 'Banana', 'Orange']
predicted_class = labels[np.argmax(predictions[0])]
confidence = np.max(predictions[0]) * 100

print(f"Prediksi: {predicted_class} ({confidence:.2f}%)")
```

## 📁 Struktur Proyek

```
submission/
│
├── notebook.ipynb          # Notebook utama
├── README.md               # Dokumentasi proyek
├── requirements.txt        # requirement
├── notebook.py             # 
│
├── saved_model/            # Model dalam format SavedModel
│   ├── saved_model.pb
│   ├── fingerprint.pb
│   └── variables/
│
├── tflite/                 # Model TensorFlow Lite
│   ├── model.tflite
│   └── label. txt
│
├── tfjs_model/             # Model TensorFlow. js
│   ├── model.json
│   └── group1-shard*. bin
│
└── model_submission. keras        # Best model checkpoint
```

## 📈 Hasil Training

| Metrik | Training | Validation | Test |
|--------|----------|------------|------|
| Accuracy | >95% | >90% | >85% |
| Loss | <0.2 | <0.3 | <0.4 |

### Grafik Training
- Training dan Validation Accuracy meningkat seiring epoch
- Training dan Validation Loss menurun seiring epoch
- Tidak terjadi overfitting yang signifikan

## 🔄 Konversi Model

### TensorFlow Lite
```python
converter = tf.lite.TFLiteConverter.from_saved_model('saved_model')
converter.optimizations = [tf.lite. Optimize.DEFAULT]
tflite_model = converter.convert()

with open('model.tflite', 'wb') as f:
    f.write(tflite_model)
```

### TensorFlow.js
```bash
tensorflowjs_converter \
    --input_format=tf_saved_model \
    --output_format=tfjs_graph_model \
    saved_model \
    tfjs_model
```

## 🛠️ Teknologi yang Digunakan

- **Python** 3.8+
- **TensorFlow** 2.x
- **Keras** (High-level API)
- **NumPy** - Numerical computing
- **Matplotlib** - Visualisasi
- **Seaborn** - Statistical visualization
- **Scikit-learn** - Metrics & utilities
- **Pillow** - Image processing

## 📝 Callbacks yang Digunakan

1. **EarlyStopping** - Menghentikan training jika tidak ada improvement
2. **ModelCheckpoint** - Menyimpan model terbaik
3. **ReduceLROnPlateau** - Mengurangi learning rate saat plateau

## 🎯 Kriteria Submission

- [x] Dataset minimal 1000 gambar
- [x] Dataset dibagi menjadi Train, Validation, dan Test set
- [x] Model menggunakan Sequential dengan Conv2D dan MaxPooling
- [x] Akurasi minimal 85%
- [x] Menggunakan minimal 2 Callback
- [x] Model disimpan dalam format SavedModel
- [x] Model dikonversi ke TF-Lite
- [x] Model dikonversi ke TFJS

## 👤 Author

**Eko Andri Prasetyo**

- GitHub: [@eko-andri-prasetyo](https://github.com/eko-andri-prasetyo)

## 📄 License

Proyek ini dilisensikan di bawah [MIT License](LICENSE).

## 🙏 Acknowledgments

- [Dicoding Indonesia](https://www.dicoding.com/) - Platform pembelajaran
- [Kaggle](https://www.kaggle.com/) - Dataset Fruits 360
- [TensorFlow](https://www.tensorflow.org/) - Framework deep learning

---

⭐ Jika proyek ini membantu, jangan lupa beri star! 
