# Makine Öğrenmesi ile Telco Müşteri Kaybı (Churn) Tahmini

## Proje Hakkında

Bu proje, Türkiye Yapay Zeka Akademisi Makine Öğrenmesi Final Ödevi kapsamında hazırlanmıştır.

Bir telekom şirketinin müşteri verileri (demografik bilgiler, alınan hizmetler, sözleşme ve fatura bilgileri) kullanılarak müşterinin şirketten ayrılıp ayrılmayacağını (churn) tahmin eden bir makine öğrenmesi modeli geliştirilmiştir.

Problem türü: **İkili Sınıflandırma (Binary Classification)**

## Veri Seti

* **Kaynak:** Kaggle - Telco Customer Churn (blastchar)
* **Boyut:** 7043 satır (temizlik sonrası 7032), 21 sütun
* **Hedef Değişken:** `Churn` (Yes/No)

Kaggle veri seti:

https://www.kaggle.com/datasets/blastchar/telco-customer-churn

## Kullanılan Kütüphaneler

* pandas
* numpy
* matplotlib
* seaborn
* scikit-learn

## Uygulanan Adımlar

* Veri temizleme ve EDA
* One-Hot Encoding
* Aykırı değer analizi
* Feature Engineering (`charges_per_tenure`, `total_services`)
* Korelasyon analizi
* Train/Validation/Test ayrımı
* StandardScaler ile ölçekleme
* Logistic Regression, KNN ve Random Forest modelleri
* GridSearchCV ile hiperparametre optimizasyonu
* Confusion Matrix ve Classification Report

## Model Karşılaştırması

| Model               | Accuracy | Precision | Recall | F1    |
| ------------------- | -------- | --------- | ------ | ----- |
| Logistic Regression | 0.794    | 0.634     | 0.532  | 0.578 |
| KNN                 | 0.766    | 0.571     | 0.485  | 0.524 |
| Random Forest       | 0.784    | 0.635     | 0.442  | 0.521 |

En başarılı model **Logistic Regression (C=100)** olarak seçilmiştir.

## En İyi Model Sonucu

* Accuracy: **0.804**
* Precision: **0.648**
* Recall: **0.572**
* F1-Score: **0.608**
* Confusion Matrix: `[[917, 116], [160, 214]]`

## Sonuç

Logistic Regression modeli en yüksek F1 skorunu elde etmiştir. Model katsayılarına göre uzun sözleşmeler, yüksek tenure ve Online Security hizmeti churn olasılığını azaltırken; Fiber Optic internet hizmeti, yüksek toplam ödeme miktarı ve Electronic Check ödeme yöntemi churn olasılığını artıran başlıca faktörler olarak belirlenmiştir.

Veri setindeki sınıf dengesizliği (%73 No, %27 Yes) nedeniyle değerlendirmede Accuracy yanında Precision, Recall ve F1-Score metrikleri de dikkate alınmıştır.

## Proje Dosyaları

* `telco-churn-notebook.ipynb`
* `requirements.txt`
* `README.md`

## Çalıştırma

```bash
pip install -r requirements.txt
```

Veri setini Kaggle linkinden indirin, ya da notebook'u doğrudan Kaggle üzerinde açıp veri setini "Add Input" ile ekleyin.

Daha sonra notebook dosyasını açıp tüm hücreleri Run All seçeneği ile çalıştırabilirsiniz.

## Kaggle Notebook

https://www.kaggle.com/code/seymensezgin/telco-churn-prediction

## Geliştirici

**Seymen Sezgin**

