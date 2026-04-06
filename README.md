# Shopify Günlük Satış Rapor Sistemi

## Kurulum (Mac için)

### 1. Python kur (zaten varsa atla)
```bash
brew install python3
```

### 2. Proje klasörünü aç ve bağımlılıkları kur
```bash
cd shopify-reporter
pip3 install -r requirements.txt
```

### 3. config.json dosyasını düzenle
Her mağazanın `client_id` ve `client_secret` bilgilerini Dev Dashboard → Settings'ten kopyalayıp yapıştır.

### 4. Test et
```bash
python3 reporter.py daily       # Günlük rapor (Rapor 1 + 2)
python3 reporter.py periodic    # Dönemsel rapor (Rapor 3)
python3 reporter.py all         # Tüm raporlar
```
Raporlar `reports/` klasörüne kaydedilir.

### 5. Her sabah otomatik çalıştır (Mac)
Terminal'de şunu çalıştır:
```bash
crontab -e
```
Açılan editöre şunu ekle:
```
45 7 * * * cd /PROJE/YOLUN/shopify-reporter && /usr/bin/python3 reporter.py daily >> logs.txt 2>&1
```
`/PROJE/YOLUN/` kısmını gerçek yol ile değiştir (örn: `/Users/seninismin/shopify-reporter`).

## WhatsApp Entegrasyonu (Opsiyonel)
1. twilio.com'da hesap aç
2. WhatsApp Sandbox'ı aktifleştir
3. config.json'daki whatsapp bilgilerini doldur
4. Alternatif: Raporlar `reports/` klasörüne kaydedilir, manuel olarak WhatsApp'tan gönderebilirsin.

## Raporlar

| Rapor | Açıklama | Dosyalar |
|-------|----------|----------|
| Rapor 1 | Mağaza bazlı günlük satış özeti | PDF + Excel |
| Rapor 2 | Mağaza bazlı ürün detay raporu | PDF + Excel |
| Rapor 3 | Son 1/3/6 ay dönemsel rapor | PDF + Excel |
