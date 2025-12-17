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

Veri setinde toplam **160 adet görüntü** bulunmaktadır ve
her sınıf için **80 adet görsel** mevcuttur.
Veriler, eğitim sürecinin sağlıklı yürütülebilmesi için
**train / validation / test** olacak şekilde ayrılmıştır.

Her bir sınıf için dağılım aşağıdaki gibidir:

- **Eğitim (train):** 56 görüntü  
- **Doğrulama (val):** 12 görüntü  
- **Test:** 12 görüntü  

Bu dağılım sayesinde modelin hem eğitim sırasında öğrenme süreci
izlenmiş hem de daha önce görmediği test verileri üzerinde
genelleme performansı değerlendirilmiştir.
Etiketleme işlemi, klasör yapısı üzerinden otomatik olarak yapılmaktadır.

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

Transfer learning ve fine-tuning kullanılan Model 1, %95 test doğruluğu ile en yüksek performansı sunmuştur.
Model 3’te yapılan hiperparametre optimizasyonları ise, sıfırdan eğitilen modeller arasında en iyi sonucu sağlamıştır.

Bu çalışma, küçük veri setlerinde **doğru hiperparametre seçiminin,
model karmaşıklığından daha önemli olabileceğini** göstermektedir. ✅

## 🔍 Model 1, Model 2 ve Model 3 Genel Karşılaştırması

Bu çalışmada aynı veri seti üzerinde üç farklı yaklaşım uygulanmıştır:
Transfer learning tabanlı hazır bir mimari (Model 1),
sıfırdan oluşturulmuş bir CNN (Model 2)
ve hiperparametre optimizasyonu ile geliştirilen bir CNN (Model 3).

Elde edilen sonuçlar, her yaklaşımın avantaj ve sınırlılıklarını
açık bir şekilde ortaya koymaktadır.

---

### Model 1 – Transfer Learning ve Fine-Tuning (VGG16)

Model 1’de, ImageNet veri seti üzerinde önceden eğitilmiş
**VGG16 mimarisi** kullanılmıştır.
Transfer learning yaklaşımı sayesinde model,
kenar, köşe ve doku gibi temel görsel özellikleri
önceden öğrenmiş ağırlıklarla kullanmıştır.

Fine-tuning aşamasında VGG16’nın üst katmanlarının
bir kısmı yeniden eğitilmiş ve bu sayede model,
veri setine özgü ayrıntılara daha iyi uyum sağlamıştır.
Bu yaklaşım, sınırlı boyuttaki veri seti üzerinde
**en yüksek test doğruluğunun (%95)** elde edilmesini sağlamıştır.

Bu sonuç, hazır ve güçlü bir mimarinin,
doğru şekilde fine-tuning uygulanması durumunda
küçük veri setlerinde oldukça etkili olabileceğini göstermektedir.

---

### Model 2 – Basit CNN (Baseline Model)

Model 2, tamamen sıfırdan oluşturulmuş bir CNN mimarisi olup
herhangi bir önceden eğitilmiş ağırlık kullanmamaktadır.
Bu model, temel bir referans (baseline) performansı sunmuştur.

Ancak veri setinin sınırlı boyutta olması nedeniyle,
modelin karmaşık örüntüleri genelleme yeteneği
Model 1 ve Model 3’e kıyasla daha düşük kalmıştır.
Model 2, sonraki deneyler için karşılaştırma noktası olarak kullanılmıştır.

---

### Model 3 – Geliştirilmiş CNN (Deneysel Optimizasyon)

Model 3’te, Model 2 temel alınarak mimari ve hiperparametreler
deneysel olarak optimize edilmiştir.
Kernel size, öğrenme oranı, batch size, dropout oranları
ve veri artırımı gibi parametreler sistematik biçimde değiştirilmiştir.

Yapılan deneyler sonucunda,
Model 3’ün test doğruluğu Model 2’ye kıyasla
belirgin şekilde artırılmıştır.
Ancak Model 3, güçlü bir transfer learning mimarisi olan
Model 1’in fine-tuning sonrası elde ettiği
en yüksek performansın gerisinde kalmıştır.

---

