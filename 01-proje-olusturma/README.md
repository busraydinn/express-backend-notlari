# 01- Express.js ve Node.js ile İlk Backend Projesi
Bu bölümde, Node.js ortamında Express.js kullanarak temel bir backend projesinin nasıl oluşturulacağını adım adım öğreniyoruz.


## 🧱 Adım Adım Kurulum

### 1️⃣ Terminali Aç

İlk olarak proje klasörünü oluştur ve terminali o klasörde aç:

```bash
mkdir ilk-backend-projem
cd ilk-backend-projem
```
### 2️⃣ Projeyi Başlat (npm init)
- Bu komut, proje için gerekli olan package.json dosyasını oluşturur.
- Bu dosyada projenin adı, giriş dosyası (main), bağımlılıklar vs. tanımlanır.
- Biz giriş dosyası olarak app.js kullanacağız.
```bash
npm init
```
### 3️⃣ Geliştirme Aracı: Nodemon Kurulumu
- Nodemon, dosyalarda yapılan değişiklikleri otomatik olarak algılar ve uygulamayı yeniden başlatır.
```bash
npm install nodemon
```
✅ package.json içindeki "scripts" alanını güncelle:
```json
"scripts": {
  "start": "nodemon app.js"
}
```
### 4️⃣ Express Kurulumu
- Express, Node.js üzerinde çalışan minimalist ve esnek bir web framework'tür.
- Artık Express kullanarak sunucumuzu oluşturabiliriz.
```bash
npm install express
```
### 5️⃣ app.js Dosyasını Oluştur
Proje dizininde app.js adında bir dosya oluştur ve içine aşağıdaki kodları ekle:
```bash
const express = require('express');
const app = express();
const PORT = 3000;

app.get('/', (req, res) => {
  res.send('Merhaba, Express çalışıyor!');
});

app.listen(PORT, () => {
  console.log(`Sunucu çalışıyor: http://localhost:${PORT}`);
});
```
✅ Uygulamayı Çalıştır
Terminalde aşağıdaki komutu yaz:
```bash
npm start
```
Tarayıcıda http://localhost:3000 adresine giderek "Merhaba, Express çalışıyor!" mesajını görmelisin.
### 📁 Klasör Yapısı
```bash
ilk-backend-projem/
├── node_modules/
├── package.json
├── package-lock.json
├── app.js
```
### 📌 Özet

- npm init ile proje başlatıldı
- nodemon ile canlı geliştirme ortamı kuruldu
- express ile basit bir sunucu oluşturuldu
- app.js içine basit bir endpoint eklendi
