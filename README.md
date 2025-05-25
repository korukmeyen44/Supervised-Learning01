# Supervised-Learning01
kaggle link: https://www.kaggle.com/code/atagnkrkmez/bootcamp-proje-ipynb

# Araç Fiyatı Tahmini

## Giriş

Bu proje, 2. el araçların satış fiyatlarını tahmin etmek amacıyla oluşturulmuştur. Kaggle'dan alınan "Vehicle Sales Data" veri seti kullanılarak veri ön işleme, görselleştirme ve makine öğrenmesi, hiperparametre optimizasyonu modelleri ile fiyat tahmini yapılmıştır. Tahmin edilecek değişken "sellingprice" olurken diğer değişkenler bazı gereksiz veya eksik veri içerenler haricinde bu değişkenin tahmnininde kullanılmıştır.

Projede uygulanan temel adımlar:
- Veri analizi ve görselleştirme
- Eksik veri işleme ve temizleme
- Etiketleme ve ölçekleme işlemleri
- Regresyon modelleri ile tahmin
- Model karşılaştırmaları ve hiperparametre optimizasyonu

## Metrikler

### Kullanılan Modeller
- Random Forest Regressor
  Neden Random Forest Regressor:
  - Sayısal ve kategorik veriler aynı anda yer aldığı durumlarda etkilidir.
  - Çok sayıda karar ağacının ortalaması olduğu için overfittinge karşı dirençlidir.
  - Değişkenlerin ne kadar etkili olduğunu açıklamada iyidir.
  Neden diğer yöntemler olmaz:
  - Lineer Regresyon: Veri seti lineer olmayan durumlar,fazla kategorik değişken ve etkilişim içerdiğinden , bu veri seti için başarısızdır.
  - Knn Regressor: Yüksek boyutlu verilerde çok vakit alır.
  - Neural Network: Random forest regressore kıyasla daha komplike, daha büyük ölçekli veri setlerinde işlevsel.
- LightGBM Regressor (GridSearchCV ile hiperparametre optimizasyonlu)
  Neden LightGBm Regressor:
  - Daha hızlıdır ve belleği daha az kullanır.
  - Hiperparametre optimizasyonuna açıktır.
 
### Performans Ölçütleri

Test verisi üzerinden değerlendirme sonuçları:

- R² Skoru (Random Forest): 0.81
- Ortalama Kare Hata (MSE): 12,000,000
- Kök Ortalama Kare Hata (RMSE): 3,464
- Ortalama Mutlak Hata (MAE): 1,920 *yaklaşık değerler
  
LightGBM modeli için 3 katlı çapraz doğrulama sonucu:
- Ortalama R²: 0.83 *yaklaşık

GridSearch ile elde edilen en iyi hiperparametreler:
- num_leaves: 63
- learning_rate: 0.1
- n_estimators: 200

### Veri Ön İşleme
- Eksik değerler: Kategorik alanlar mod/“Other”, sayısal alanlar ortalama ile dolduruldu.
- Gereksiz sütunlar (örn. `vin`, `saledate`) kaldırıldı.
- Kategorik sütunlar Label Encoding ile sayısal hale getirildi.
- Tüm veriler StandardScaler ile ölçeklendirildi.
- Eğitim/test seti oranı: 80/20

### Görselleştirme
- Sayısal sütunların dağılım grafikleri
- En çok satılan ilk 15 marka için satış adedi grafiği

## Sonuç ve Geleceğe Yönelik Çalışmalar
Sonuç olarak bu proje, araç satış fiyatlarını tahmin etmeye yönelik uçtan uca bir makina öğrenimi çözümüdür ve tatmin edici bir başarı düzeyine sahiptir.
- Aynı fikir üzerinden daha güncel bir veri seti ile yeni veri setine bağlı olarak farklı modeller kullanarak daha gerçekçi ve başarılı sonuçlar bulan bir sistem üretilip bunu web veya aplikasyon üzerinden 2. el araç satıcılarının kullanımına sunarak, onların geleceğe yönelik planlamaları kolaylaştırılabilir.
