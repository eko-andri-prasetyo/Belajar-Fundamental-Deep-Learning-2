# Proyek Klasifikasi Gambar - Klasifikasi Buah-Buahan

## 📝 Deskripsi Proyek
Proyek ini merupakan submission untuk kelas **Belajar Fundamental Deep Learning** di Dicoding. Proyek ini mengimplementasikan klasifikasi gambar menggunakan Convolutional Neural Network (CNN) untuk mengklasifikasikan gambar buah-buahan.

## 👤 Informasi Pengembang
- **Nama:** [Nama Anda]
- **Email:** [Email Anda]
- **ID Dicoding:** [ID Dicoding Anda]

## 📊 Dataset
- **Sumber:** Data scraping dari [sumber data Anda]
- **Jumlah Gambar:** [jumlah] gambar
- **Kelas:** 
  - Apple (Apel)
  - Banana (Pisang)
  - Orange (Jeruk)

### Pembagian Dataset
| Split | Jumlah | Persentase |
|-------|--------|------------|
| Training | [jumlah] | 70% |
| Validation | [jumlah] | 15% |
| Testing | [jumlah] | 15% |

## 🏗️ Arsitektur Model
Model menggunakan arsitektur **Sequential CNN** dengan struktur:

```
Input (150x150x3)
    ↓
Conv2D (32 filters, 3x3) + ReLU
    ↓
MaxPooling2D (2x2)
    ↓
Conv2D (64 filters, 3x3) + ReLU
    ↓
MaxPooling2D (2x2)
    ↓
Conv2D (128 filters, 3x3) + ReLU
    ↓
MaxPooling2D (2x2)
    ↓
Conv2D (128 filters, 3x3) + ReLU
    ↓
MaxPooling2D (2x2)
    ↓
Flatten
    ↓
Dropout (0.5)
    ↓
Dense (512) + ReLU
    ↓
Dropout (0.3)
    ↓
Dense (3) + Softmax
    ↓
Output
```

## 📈 Hasil Training
| Metrik | Training | Validation | Testing |
|--------|----------|------------|---------|
| Accuracy | [nilai]% | [nilai]% | [nilai]% |
| Loss | [nilai] | [nilai] | [nilai] |

## 📁 Struktur Direktori
```
submission/
├── tfjs_model/
│   ├── group1-shard1of1.bin
│   └── model.json
├── tflite/
│   ├── model.tflite
│   └── label.txt
├── saved_model/
│   ├── saved_model.pb
│   └── variables/
├── notebook.ipynb
├── README.md
└── requirements.txt
```

## 🚀 Cara Menjalankan

### 1. Install Dependencies
```bash
pip install -r requirements.txt
```

### 2. Jalankan Notebook
Buka `notebook.ipynb` menggunakan Jupyter Notebook atau Google Colab.

### 3. Inference dengan SavedModel
```python
import tensorflow as tf
model = tf.keras.models.load_model('saved_model')
# Lakukan prediksi
```

### 4. Inference dengan TF-Lite
```python
import tensorflow as tf
interpreter = tf.lite.Interpreter(model_path='tflite/model.tflite')
interpreter.allocate_tensors()
# Lakukan prediksi
```

## ✅ Kriteria yang Terpenuhi

### Kriteria Utama
- [x] Dataset minimal 1000 gambar
- [x] Dataset bukan Rock-Paper-Scissors atau X-Ray
- [x] Pembagian Train, Validation, Test
- [x] Model Sequential dengan Conv2D dan Pooling
- [x] Akurasi minimal 85%
- [x] Plot akurasi dan loss
- [x] Model disimpan dalam SavedModel, TF-Lite, TFJS

### Saran Tambahan
- [x] Implementasi Callback (EarlyStopping, ModelCheckpoint, ReduceLROnPlateau)
- [x] Minimal 3 kelas
- [x] Inference dengan bukti
- [ ] Dataset 10000+ gambar
- [ ] Akurasi 95%+
- [ ] Gambar resolusi tidak seragam

## 📚 Referensi
- [TensorFlow Documentation](https://www.tensorflow.org/api_docs)
- [Keras Documentation](https://keras.io/api/)
- [Dicoding - Belajar Fundamental Deep Learning](https://www.dicoding.com/academies/185)

## 📄 Lisensi
Proyek ini dibuat untuk keperluan pembelajaran di Dicoding.