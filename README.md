# Telco Müşteri Kaybı (Churn) Tahmini

## Amaç
Bu proje, bir telekom şirketinin müşteri verilerinden yola çıkarak müşterinin 
şirketten ayrılıp ayrılmayacağını (churn) tahmin eden bir sınıflandırma 
modeli geliştirmeyi amaçlar.

## Veri Seti
Kaggle - Telco Customer Churn (blastchar), 7032 satır (temizlik sonrası), 
21 sütun. Demografik bilgi, hizmet bilgisi ve fatura bilgisi içerir.
Hedef değişken: Churn (Yes/No) → Sınıflandırma problemi.

## Nasıl Çalıştırılır
1. Notebook'u Kaggle veya Jupyter ortamında açın
2. requirements.txt içindeki kütüphaneleri kurun: `pip install -r requirements.txt`
3. Hücreleri sırayla çalıştırın

## Sonuçlar
- 3 model karşılaştırıldı: Logistic Regression, KNN, Random Forest
- En iyi model: Logistic Regression (GridSearchCV ile C=100)
- Test performansı: Accuracy=0.804, Precision=0.648, Recall=0.572, F1=0.608

## Sonuç Yorumu
En etkili değişkenler: uzun sözleşme süresi ve yüksek tenure churn'ü azaltıyor; 
Fiber optic internet ve Electronic check ödeme yöntemi churn'ü artırıyor. 
Model, dengesiz sınıf dağılımı (%73-%27) nedeniyle recall'da sınırlı kaldı.