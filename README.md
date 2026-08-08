# Makine Öğrenmesi ile Telco Müşteri Kaybı (Churn) Tahmini

## Proje Hakkında
Bu proje, Türkiye Yapay Zeka Akademisi Makine Öğrenmesi Final Ödevi kapsamında hazırlanmıştır.

Projede bir telekom şirketinin müşteri verileri (demografik bilgi, aldığı hizmetler, sözleşme ve fatura bilgisi) kullanılarak müşterinin şirketten ayrılıp ayrılmayacağı (churn) makine öğrenmesi algoritmaları ile tahmin edilmiştir.

Problem türü ikili sınıflandırma (Binary Classification) problemidir.

## Veri Seti
Bu projede kullanılan veri seti Kaggle üzerindeki Telco Customer Churn (blastchar) veri setidir.

- **Link:** https://www.kaggle.com/datasets/blastchar/telco-customer-churn
- **Boyut:** 7043 satır (temizlik sonrası 7032), 21 sütun

Hedef değişken:
`Churn`

Bu değişken;
- **Yes (1):** Müşterinin şirketten ayrıldığını
- **No (0):** Müşterinin şirkette kaldığını

ifade etmektedir.

## Kullanılan Kütüphaneler
- pandas
- numpy
- matplotlib
- seaborn
- scikit-learn

## Uygulanan Adımlar
Projede aşağıdaki makine öğrenmesi adımları uygulanmıştır:

- Veri setinin okunması
- Veri inceleme (EDA)
- Eksik değer kontrolü ve temizliği (`TotalCharges` sütunu)
- Kategorik değişkenlerin One-Hot Encoding yöntemi ile sayısal hale dönüştürülmesi
- Aykırı değer analizi (Boxplot)
- Öznitelik mühendisliği (charges_per_tenure, total_services)
- Korelasyon analizi ile öznitelik seçimi
- Train/Validation/Test veri ayrımı (Stratified Split)
- StandardScaler ile ölçekleme
- Logistic Regression modeli
- KNN modeli
- Random Forest modeli
- GridSearchCV ile hiperparametre optimizasyonu
- Confusion Matrix
- Classification Report
- Katsayı bazlı Feature Importance yorumu

## Model Karşılaştırması

| Model | Accuracy | Precision | Recall | F1 |
|---|---|---|---|---|
| Logistic Regression | 0.794 | 0.634 | 0.532 | 0.578 |
| KNN | 0.766 | 0.571 | 0.485 | 0.524 |
| Random Forest | 0.784 | 0.635 | 0.442 | 0.521 |

Yapılan karşılaştırmalar sonucunda Logistic Regression modeli en başarılı model olarak seçilmiştir.

## En İyi Model Sonucu
Seçilen model:
**Logistic Regression** (GridSearchCV ile en iyi parametre: `C=100`)

Test seti üzerinde:
- **Accuracy:** 0.804
- **Precision:** 0.648
- **Recall:** 0.572
- **F1-Score:** 0.608
- **Confusion Matrix:** `[[917, 116], [160, 214]]`

## Sonuç
Bu projede müşteri kaybını (churn) tahmin etmek amacıyla üç farklı sınıflandırma modeli karşılaştırılmıştır.

Karşılaştırma sonucunda en yüksek F1-skorunu (0.608) Logistic Regression modeli elde etmiştir.

Model katsayıları incelendiğinde;
- `tenure`
- `Contract_Two year`
- `Contract_One year`
- `OnlineSecurity_Yes`

değişkenleri churn olasılığını azaltan; buna karşılık

- `InternetService_Fiber optic`
- `TotalCharges`
- `PaymentMethod_Electronic check`

değişkenleri churn olasılığını artıran en önemli öznitelikler olarak belirlenmiştir.

Veri setinde müşterilerin büyük kısmının şirkette kalması (%73 civarında) nedeniyle veri seti dengesizdir. Bu nedenle model performansı değerlendirilirken yalnızca accuracy değil, precision, recall ve F1-score metrikleri de dikkate alınmıştır.

## Proje Dosyaları
Repository içerisinde aşağıdaki dosyalar bulunmaktadır:

- `telco-churn-notebook.ipynb`
- `requirements.txt`
- `README.md`

## Çalıştırma
Gerekli kütüphaneleri yüklemek için:
```
pip install -r requirements.txt
```

Veri setini [Kaggle linkinden](https://www.kaggle.com/datasets/blastchar/telco-customer-churn) indirin, ya da notebook'u doğrudan Kaggle üzerinde açıp veri setini "Add Input" ile ekleyin.

Daha sonra notebook dosyasını açıp tüm hücreleri Run All seçeneği ile çalıştırabilirsiniz.

## Kaggle Notebook
https://www.kaggle.com/code/seymensezgin/telco-churn-prediction

## Geliştirici

Türkiye Yapay Zeka Akademisi
Makine Öğrenmesi Final Projesi
