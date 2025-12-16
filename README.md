# 🧠 CNN_Siniflandirma — Görüntü Sınıflandırma Projesi (CNN & Transfer Learning)

Bu proje, iki sınıflı bir görüntü veri seti üzerinde **Convolutional Neural Network (CNN)**
tabanlı sınıflandırma modellerinin performansını incelemeyi amaçlamaktadır.

Çalışma, **Makine Öğrenmesi** dersi kapsamında gerçekleştirilmiş olup,
farklı model mimarileri ve hiperparametre ayarlarının sınıflandırma doğruluğu
üzerindeki etkileri karşılaştırmalı olarak analiz edilmiştir.

---

## 👩‍🎓 Geliştirici Bilgileri

**Ad:** Melek  
**Soyad:** ÇATAL  
**Okul Numarası:** 2212721039  

**GitHub Repo:**  
🔗 https://github.com/melekcatal/CNN_Siniflandirma

---

## 📑 İçindekiler
- Proje Açıklaması  
- Veri Seti  
- Kullanılan Teknolojiler  
- Model 1 – Transfer Learning ve Fine-Tuning (VGG16)  
- Model 2 – Basit CNN (Baseline)  
- Model 3 – Geliştirilmiş CNN ve Deneyler  
- Dosya Yapısı  
- Sonuç ve Değerlendirme  

---

## 📌 Proje Açıklaması

Bu projede, görsel olarak farklı iki sınıfa ait görüntülerin
otomatik olarak sınıflandırılması hedeflenmiştir.
Proje kapsamında üç farklı yaklaşım uygulanmıştır:

- **Transfer Learning tabanlı hazır mimari**
- **Sıfırdan oluşturulmuş CNN**
- **Hiperparametre denemeleri ile geliştirilmiş CNN**

Her model için eğitim, doğrulama ve test aşamaları ayrı ayrı yürütülmüş,
elde edilen sonuçlar karşılaştırmalı olarak değerlendirilmiştir.

---

## 📁 Veri Seti

Veri seti, iki sınıftan oluşmaktadır:

- `fare_disi`
- `kelebek`

Veriler, **train / val / test** olacak şekilde ayrılmıştır ve
etiketleme işlemi klasör yapısı üzerinden otomatik olarak yapılmaktadır.

```bash
dataset/
├── train/
│ ├── fare_disi/
│ └── kelebek/
├── val/
│ ├── fare_disi/
│ └── kelebek/
└── test/
├── fare_disi/
└── kelebek/
```

---

## 🛠️ Kullanılan Teknolojiler

- 🐍 Python
- 🧠 TensorFlow / Keras
- 🧩 CNN (Convolutional Neural Networks)
- 🏗️ VGG16 (Transfer Learning)
- 📊 Matplotlib
- ☁️ Google Colab

---

## ✅ Model 1 – Transfer Learning ve Fine-Tuning (VGG16)

Model 1’de, **ImageNet veri seti üzerinde önceden eğitilmiş VGG16 mimarisi**
kullanılmıştır.

### Kullanılan Yaklaşım
- **Transfer Learning:**  
  VGG16’nın evrişimsel katmanları özellik çıkarıcı (feature extractor)
  olarak kullanılmıştır.
- **Fine-Tuning:**  
  Üst katmanların bir kısmı açılarak düşük öğrenme oranı ile yeniden eğitilmiştir.
- Bu yaklaşım, küçük veri setlerinde daha hızlı ve daha güçlü öğrenme sağlamaktadır.

Modelin çıkış katmanı iki sınıfa uygun olacak şekilde yeniden düzenlenmiştir.

---

## ✅ Model 2 – Basit CNN (Baseline Model)

Model 2, tamamen **sıfırdan oluşturulmuş bir CNN mimarisi**dir ve
Model 3 için referans (baseline) olarak kullanılmıştır.

### Genel Yapı
- 3 adet Convolution + MaxPooling katmanı
- Flatten
- Dense(128) + Dropout
- Sigmoid çıkış katmanı (binary classification)

Bu model, transfer learning kullanılmadan elde edilebilecek temel performansı
göstermektedir.

---

## ✅ Model 3 – Geliştirilmiş CNN ve Deneyler

Model 3’te, Model 2 temel alınarak **8 farklı deney** gerçekleştirilmiştir.
Bu deneylerde aşağıdaki parametreler sistematik olarak değiştirilmiştir:

- Filtre sayıları
- Kernel size
- Batch size
- Dropout oranları
- Learning rate
- Epoch sayısı
- Veri artırımı (ImageDataGenerator)

Her deney için test doğruluğu hesaplanmış ve sonuçlar tablo halinde sunulmuştur.
En iyi performans **Deney 8** ile elde edilmiştir.

---

## 📁 Dosya Yapısı
```bash
CNN_Siniflandirma/
│
├── dataset/
│ ├── train/
│ ├── val/
│ └── test/
│
├── model1.ipynb # Transfer Learning + Fine-Tuning (VGG16)
├── model2.ipynb # Basit CNN (Baseline)
├── model3.ipynb # Geliştirilmiş CNN ve deneyler
│
└── README.md
```

---

## 📊 Sonuç ve Değerlendirme

Deneyler sonucunda, model performansını en çok etkileyen faktörlerin
**learning rate, kernel size, batch size ve dropout dengesi** olduğu görülmüştür.

Transfer learning kullanılan Model 1 güçlü bir başlangıç performansı sunarken,
Model 3’te yapılan hiperparametre optimizasyonları ile
en yüksek test doğruluğu elde edilmiştir.

Bu çalışma, küçük veri setlerinde **doğru hiperparametre seçiminin,
model karmaşıklığından daha önemli olabileceğini** göstermektedir. ✅

