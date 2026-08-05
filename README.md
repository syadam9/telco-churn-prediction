# Telco Müşteri Kaybı (Churn) Tahmini

## Projenin Amacı
Bu proje, bir telekom şirketinin müşteri verilerinden (demografik bilgi, aldığı
hizmetler, fatura bilgisi) yola çıkarak müşterinin şirketten ayrılıp
ayrılmayacağını (churn) tahmin eden bir sınıflandırma modeli geliştirmeyi
amaçlar.

## Veri Seti
- **Kaynak:** Kaggle - Telco Customer Churn (blastchar)
- **Link:** https://www.kaggle.com/datasets/blastchar/telco-customer-churn
- **Boyut:** 7043 satır (temizlik sonrası 7032), 21 sütun
- **Hedef değişken:** `Churn` (Yes/No) → **Sınıflandırma problemi**

## Kaggle Notebook
https://www.kaggle.com/code/seymensezgin/telco-churn-prediction

## Nasıl Çalıştırılır
1. Veri setini [Kaggle linkinden](https://www.kaggle.com/datasets/blastchar/telco-customer-churn) indirin, ya da notebook'u doğrudan Kaggle üzerinde açıp veri setini "Add Input" ile ekleyin.
2. Gerekli kütüphaneleri kurun: `pip install -r requirements.txt`
3. Notebook'u açıp hücreleri sırayla çalıştırın.

## Sonuçlar
- 3 model karşılaştırıldı: Logistic Regression, KNN, Random Forest
- En iyi model: Logistic Regression (GridSearchCV ile `C=100`)
- Test performansı: Accuracy=0.804, Precision=0.648, Recall=0.572, F1=0.608
- Confusion Matrix: `[[917, 116], [160, 214]]`

## Sonuç Yorumu
En etkili değişkenler: uzun sözleşme süresi ve yüksek tenure churn olasılığını
azaltıyor; Fiber optic internet servisi ve Electronic check ödeme yöntemi churn
olasılığını artırıyor. Churn sınıfı dengesiz dağıldığı için (%73 No, %27 Yes)
model recall değerinde sınırlı kaldı; ölçeklemenin train/test ayrımından sonra
yapılması ileri seviye bir iyileştirme olurdu.
