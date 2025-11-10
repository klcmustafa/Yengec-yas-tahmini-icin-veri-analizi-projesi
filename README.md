# 🦀 Yengeç Yaş Tahmini İçin Veri Analizi Projesi

Yengeçlerin fiziksel özelliklerine dayanarak yaşlarını tahmin eden kapsamlı bir makine öğrenmesi projesi. Bu proje, veri ön işleme tekniklerinden model optimizasyonuna kadar tam bir veri bilimi iş akışını içermektedir.

## 📋 Proje Hakkında

Bu proje, yengeçlerin yaşını tahmin etmek için fiziksel özelliklerini (boyut, ağırlık, kabuk kalınlığı vb.) kullanarak çeşitli makine öğrenmesi algoritmalarını karşılaştırmaktadır. Proje kapsamında:

- **Veri Ön İşleme**: Eksik veri analizi, ayrık veri dönüşümü, özellik seçimi
- **Görselleştirme**: Kapsamlı veri analizi ve korelasyon görselleştirmeleri
- **Model Geliştirme**: Üç farklı regresyon algoritmasının karşılaştırılması
- **Model Optimizasyonu**: Hiperparametre ayarlama ve istatistiksel testler
- **Performans Değerlendirmesi**: Detaylı başarı metrikleri

Bu çalışma, ticari yengeç yetiştiriciliğinde daha iyi kararlar alınmasına yardımcı olmayı amaçlamaktadır.

## 🎯 Araştırma Soruları

1. **Yengeçlerin hangi fiziksel özellikleri yaş ile en güçlü korelasyonu göstermektedir?**
   - Cevap: Shell Weight (Kabuk Ağırlığı) en yüksek korelasyon katsayısına (0.61) sahiptir.

2. **Fiziksel özelliklere dayalı olarak yengeçlerin yaşını tahmin etmek için en etkili regresyon modeli hangisidir?**
   - Cevap: Yapay Sinir Ağları (MLPR) algoritması Wilcoxon testi sonuçlarına göre en iyi performansı göstermiştir.

3. **Cinsiyet ve yaş arasında nasıl bir ilişki bulunmaktadır?**
   - Cevap: Cinsiyet ve yaş arasında neredeyse hiçbir ilişki bulunmamaktadır.

## 📊 Veri Seti

- **Kaynak**: [Kaggle - Crab Age Prediction Dataset](https://www.kaggle.com/datasets/sidhus/crab-age-prediction/data)
- **Boyut**: 3893 satır, 9 sütun
- **Özellikler**:
  - `Sex`: Cinsiyet (F, M, I)
  - `Length`: Uzunluk
  - `Diameter`: Çap
  - `Height`: Yükseklik
  - `Weight`: Ağırlık
  - `Shucked Weight`: Soyulmuş ağırlık
  - `Viscera Weight`: İç organ ağırlığı
  - `Shell Weight`: Kabuk ağırlığı
  - `Age`: Yaş (hedef değişken)

## 🔧 Kullanılan Teknolojiler

- **Python 3.x**
- **Pandas**: Veri manipülasyonu
- **NumPy**: Sayısal hesaplamalar
- **Scikit-learn**: Makine öğrenmesi algoritmaları
- **Matplotlib & Seaborn**: Görselleştirme
- **Jupyter Notebook**: Analiz ve geliştirme ortamı

## 📈 Proje İş Akışı

Proje, standart bir veri bilimi iş akışını takip ederek aşağıdaki aşamalardan oluşmaktadır:

### 1. Veri Keşfi ve İnceleme
Veri setinin detaylı analizi yapıldı. Boyutlar, sütun tipleri, tanımlayıcı istatistikler (ortalama, standart sapma, çeyreklikler) incelendi ve veri setinin genel yapısı anlaşıldı.

### 2. Veri Ön İşleme - Eksik Veri Analizi
Orijinal veri setinde eksik veri bulunmamasına rağmen, eksik veri analizi tekniklerini göstermek için sentetik eksik veriler oluşturuldu. Dört farklı doldurma yöntemi karşılaştırıldı:
- **Ortalama Atama Yöntemi** (seçilen ve kullanılan)
- En Son Değeri İleri Taşıma Yöntemi
- Hot Deck Yöntemi
- KNN Yöntemi

### 3. Veri Ön İşleme - Ayrık Veri Analizi
Kategorik değişkenler (Sex: F, M, I) label encoding ile sayısal değerlere dönüştürüldü. Aykırı değerler tespit edildi ve görselleştirildi (ancak analiz için silinmedi).

### 4. Özellik Seçimi ve Mühendisliği
İki farklı özellik seçimi yöntemi uygulandı:
- **Bilgi Kazancı Yöntemi**: Özelliklerin yaş ile ilişkisini ölçtü
- **PCA (Principal Component Analysis)**: Boyut indirgeme için kullanıldı

### 5. Veri Görselleştirme
Kapsamlı görselleştirme çalışmaları yapıldı:
- Boxplot, scatterplot, violinplot, pairplot grafikleri
- Heatmap ile değişkenler arası korelasyon analizi
- Cinsiyet ve yaş ilişkisinin detaylı görselleştirilmesi
- Fiziksel özelliklerin dağılımları

### 6. Model Geliştirme
Üç farklı regresyon algoritması uygulandı ve karşılaştırıldı:
- **K-En Yakın Komşu Regresyonu (KNNR)**: Basit ve etkili bir başlangıç modeli
- **Rastgele Orman Regresyonu (RFR)**: Ensemble yöntemi ile güçlü tahminler
- **Yapay Sinir Ağları Regresyonu (MLPR)**: Derin öğrenme yaklaşımı

### 7. Model Optimizasyonu
GridSearchCV kullanılarak her algoritma için en iyi hiperparametreler belirlendi:
- **KNNR**: `n_neighbors=9`
- **RFR**: `n_estimators=200`
- **MLPR**: `hidden_layer_sizes=(150, 75)`

### 8. İstatistiksel Model Karşılaştırması
Wilcoxon testi ile algoritmaların performansları istatistiksel olarak karşılaştırıldı. Tüm testler sonucunda **Yapay Sinir Ağları (MLPR)** algoritması en iyi performansı gösterdi.

### 9. Final Model ve Değerlendirme
En iyi performans gösteren MLPR modeli final model olarak seçildi. Eğitim ve test kümeleri için detaylı performans metrikleri hesaplandı ve raporlandı.

## 📊 Proje Sonuçları

### Final Model Performansı (Yapay Sinir Ağları - MLPR)

Proje sonunda, Wilcoxon testi ile istatistiksel olarak en iyi performans gösteren **Yapay Sinir Ağları (MLPR)** modeli final model olarak seçilmiştir.

**Eğitim Kümesi Performansı:**
- **RMSE**: 2.07
- **R² Skoru**: 0.57
- **MAE**: 1.52

**Test Kümesi Performansı:**
- **RMSE**: 2.07
- **R² Skoru**: 0.52
- **MAE**: 1.48

Model, eğitim ve test kümelerinde benzer performans göstermiştir, bu da modelin genelleme yeteneğinin iyi olduğunu göstermektedir.

### Sınıflandırma Metrikleri
Sınıflandırma problemi için değerlendirildiğinde model şu sonuçları vermiştir:
- **Accuracy (Doğruluk)**: %95.5
- **Precision (Kesinlik)**: 0.938
- **Recall (Duyarlılık)**: 0.968
- **F1 Score**: 0.953

## 🔍 Ana Bulgular ve Çıkarımlar

Proje kapsamında yapılan analizler sonucunda şu önemli bulgulara ulaşılmıştır:

1. **Kabuk Ağırlığı En Önemli Faktör**: Shell Weight (Kabuk Ağırlığı) değişkeni, yaş ile en yüksek korelasyon katsayısına (0.61) sahiptir. Bu, kabuk ağırlığının yaş tahmininde en kritik özellik olduğunu göstermektedir.

2. **Cinsiyet Faktörü Önemsiz**: Cinsiyet ve yaş arasında neredeyse hiçbir ilişki bulunmamıştır. Bu durum, yaş tahmin modellerinde cinsiyet bilgisinin dikkate alınmasına gerek olmadığını göstermektedir.

3. **Yapay Sinir Ağları En Etkili**: Üç farklı algoritma karşılaştırıldığında, Yapay Sinir Ağları (MLPR) algoritması Wilcoxon testi sonuçlarına göre istatistiksel olarak en iyi performansı göstermiştir. Bu, karmaşık ilişkileri öğrenme yeteneğinin bu problem için avantajlı olduğunu göstermektedir.

4. **Tüm Fiziksel Özellikler Önemli**: Tüm fiziksel özellikler yaş tahmininde önemli rol oynamaktadır. En düşük korelasyon katsayısı bile 0.41 seviyesindedir, bu da tüm özelliklerin model için değerli olduğunu göstermektedir.



## 📝 Önemli Notlar

Proje hakkında bilinmesi gereken önemli noktalar:

- **Eksik Veri**: Orijinal veri setinde eksik veri bulunmamaktadır. Ancak proje kapsamında eksik veri analizi tekniklerini göstermek için sentetik eksik veriler oluşturulmuş ve farklı doldurma yöntemleri karşılaştırılmıştır.

- **Aykırı Değerler**: Aykırı değerler tespit edilmiş ve görselleştirilmiştir, ancak analiz sırasında silinmemiştir. Bu karar, veri kaybını önlemek ve tüm veri noktalarının analize dahil edilmesi amacıyla alınmıştır.

- **Veri Bölünmesi**: Model eğitimi için veri seti %80 eğitim, %20 test olarak rastgele bir şekilde ayrılmıştır (`random_state=42` ile tekrarlanabilirlik sağlanmıştır).

- **Model Seçimi**: Üç farklı algoritma karşılaştırılmış ve Wilcoxon testi ile istatistiksel olarak en iyi performans gösteren Yapay Sinir Ağları (MLPR) modeli final model olarak seçilmiştir.


sorularınız veya önerileriniz için lütfen iletişime geçin.

