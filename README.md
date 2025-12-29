# Adult Income Prediction with Random Forest

**Proje özeti**
Bu proje, yetişkin (Adult) verisini kullanarak kişilerin yıllık gelir sınıfını (<=50K veya >50K) tahmin etmek üzere bir Random Forest sınıflandırıcısı uygular. Amaç, yeni müşteri kampanyalarında yüksek gelirli düşük riskli müşterileri önceden belirleyebilmektir.

**Kısa not**: Model ve ön işleme adımları `RANDOM FOREST.ipynb` içinde tanımlıdır. Bu README'de sonuçların gözden geçirilmesi için gerekli bağlantılar ve çalıştırma adımları yer almaktadır.

**Elde edilen skor**
- Model doğruluk (accuracy): `PUT_YOUR_REPORTED_ACCURACY_HERE`  
  (Not: Lütfen tam skor için notebook'ta en son hücreyi çalıştırın; örneğin şöyle yazdırabilirsiniz: `print(accuracy_score(y_test, y_pred))`)
- RandomizedSearchCV en iyi skor (cross-val): `PUT_YOUR_RSCV_BEST_SCORE_HERE`  
  (Notebook içindeki `rscv.best_score_` değerini kullanın.)

**Kaggle bağlantısı (projeye ait notebook veya profil)**
- Kaggle proje/notebook bağlantınızı buraya ekleyin: https://www.kaggle.com/code/tunahaneler/ir-s-datase  
  (Yer tutucu: kendi Kaggle notebook URL'nizi buraya koyun.)

**Veri seti**
- Kaggle (Adult Census Income):https://www.kaggle.com/datasets/lodetomasi1995/income-classification

> Bu repo içindeki `14-income_evaluation.csv` dosyası, yukarıdaki Adult veri setinden türetilmiş veya benzer bir CSV olabilir. Veri kaynağını doğrulamak için dosyayı inceleyin.

**Nasıl çalıştırılır (yerel)**
1. Gerekli paketleri yükleyin (örnek):

```powershell
pip install -r requirements.txt
# ya da
pip install pandas numpy scikit-learn matplotlib seaborn joblib
```

2. Jupyter Notebook ile çalıştırın:

```powershell
jupyter notebook "c:\Users\ahmet\Desktop\income dataset random forest\RANDOM FOREST.ipynb"
```

3. Tüm hücreleri (veya özellikle model eğitim ve tahmin hücrelerini) çalıştırın. Model doğruluğunu görmek için `accuracy_score` çıktısını kontrol edin.

**Önemli dosyalar**
- `RANDOM FOREST.ipynb` — Veri temizleme, ön işleme, feature engineering (kısmi), model eğitimi ve hyperparametre arama adımları.
- `14-income_evaluation.csv` — Projede kullanılan CSV veri dosyası.

**Model detayları ve öneriler**
- Model: `RandomForestClassifier` (notebook'ta önce 10, sonra 100 ağaç ile deneme yapılmış). Hyperparametre araması için `RandomizedSearchCV` kullanılmış.
- Ön işleme: Kategorik değişkenlerde `OneHotEncoder`, `native_country` için target-encoding (train set mean ile) uygulanmış.
- İyileştirme önerileri:
  - `Pipeline` ile ön işleme + modeli paketleyip `joblib.dump` ile kaydedin.
  - K-fold target-encoding ve smoothing uygulayın (leakage önlemek için).
  - `LightGBM`/`XGBoost` deneyin; genelde performans artışı olabilir.
  - Model izleme (drift, AUC, precision/recall) ve model registry (MLflow) ekleyin.

**Kullanım örneği — Yeni bir satır ile tahmin**
Notebook'a, bir ek örnek satır girip modellerle tahmin yapan bir hücre eklendi. Bu hücreyi çalıştırarak tek satırlık örnek verinin olası gelir sınıfını görebilirsiniz.

**Lisans & İletişim**
- Bu proje öğretici amaçlıdır. Kodda, veride veya sonuçlarda ticari garanti yoktur.
- Sorularınız varsa bana bildirin veya GitHub üzerinden iletişime geçin.

---

Not: README içindeki `PUT_YOUR_REPORTED_ACCURACY_HERE` ve `PUT_YOUR_RSCV_BEST_SCORE_HERE` alanlarını gerçek değerlerle güncellemek isterseniz, notebook'ta ilgili hücreleri çalıştırıp elde edilen sayıları buraya yapıştırabilirsiniz.
