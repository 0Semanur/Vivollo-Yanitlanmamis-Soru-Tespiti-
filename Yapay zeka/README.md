# DüğünBuketi Yanıtlanmamış Soru Tespiti (AI/NLP)

Bu proje, DüğünBuketi platformundan alınan müşteri konuşmalarını analiz ederek yanıtlanmamış soruları tespit eder ve duygu analizi yapar.

## 🎯 Proje Amacı

- JSON formatındaki sohbet geçmişlerini analiz etmek
- Yanıtlanmamış soruları tespit etmek  
- Duygu analizi (Pozitif/Negatif/Nötr)
- Kategori sınıflandırması (Düğün mekanı, Gelinlik, Fotoğrafçı, vb.)
- Amaç (Intent) belirleme (Mekan arıyor, Ürün arıyor, Bilgi soruyor, vb.)

## 📋 Özellikler

### Analiz Çıktıları
- **Yanıtlanmış mı?** → Evet / Hayır
- **Sentiment** → Pozitif / Negatif / Nötr  
- **Kategori** → Düğün mekanı, Gelinlik, Fotoğrafçı, Müzik/DJ, Çiçek/Dekorasyon, vb.
- **Intent** → Mekan arıyor, Ürün arıyor, Bilgi soruyor, Fiyat soruyor, vb.

### Çıktı Formatları
- CSV dosyası (.csv)
- SQLite veritabanı (.db)
- Görsel raporlar (PNG)

## 🚀 Kurulum

1. **Gerekli kütüphaneleri yükleyin:**
```bash
pip install -r requirements.txt
```

2. **NLTK verilerini indirin:**
```python
import nltk
nltk.download('punkt')
nltk.download('vader_lexicon')
```

## 💻 Kullanım

### Temel Kullanım

```python
from chat_analyzer import DugumBuketiChatAnalyzer

# Analiz sistemi oluştur
analyzer = DugumBuketiChatAnalyzer()

# JSON dosyasını analiz et
with open('your_chat_data.json', 'r', encoding='utf-8') as file:
    data = json.load(file)

results = analyzer.analyze_conversation(data)

# Sonuçları kaydet
analyzer.save_to_csv(results, 'analiz_sonuclari.csv')
analyzer.save_to_sqlite(results, 'analiz_sonuclari.db')
```

### Hızlı Test

```bash
python main.py
```

### Örnek Veri Oluşturma

```bash
python test_data_generator.py
```

### Görselleştirme

```python
from visualizer import ChatAnalysisVisualizer

# CSV'den görselleştirme
visualizer = ChatAnalysisVisualizer('analiz_sonuclari.csv')

# Grafikleri oluştur
visualizer.plot_sentiment_distribution()
visualizer.plot_category_distribution()
visualizer.create_comprehensive_report()
```

## 📊 Çıktı Örneği

| message_id | sender | yanıtlanmış_mı | sentiment | kategori | intent |
|------------|--------|----------------|-----------|----------|---------|
| 1 | müşteri_1 | Evet | Nötr | Düğün mekanı | Mekan arıyor |
| 2 | destek_1 | Hayır | Pozitif | Genel bilgi | Bilgi soruyor |
| 3 | müşteri_2 | Hayır | Negatif | Fiyat sorgusu | Fiyat soruyor |

## 🔧 Konfigürasyon

### Kategori Listesi
- Düğün mekanı
- Gelinlik  
- Fotoğrafçı
- Müzik/DJ
- Çiçek/Dekorasyon
- Davetiye
- Pasta/Catering
- Video çekimi
- Nikah şekeri
- Takı/Aksesuar
- Genel bilgi
- Fiyat sorgusu
- Rezervasyon

### Intent Listesi
- Mekan arıyor
- Ürün arıyor
- Bilgi soruyor
- Fiyat soruyor
- Rezervasyon yapıyor
- Şikayet ediyor
- Teşekkür ediyor
- İptal ediyor
- Değişiklik istiyor

## 📁 Dosya Yapısı