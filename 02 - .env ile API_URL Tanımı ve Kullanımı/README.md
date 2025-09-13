# 02 - .env ile API_URL Tanımı ve Kullanımı

Bu bölümde, **Express.js** ile geliştirilen bir backend projesinde, `.env` dosyası kullanarak **API_URL** gibi global tanımlamaların nasıl yapıldığını öğreneceğiz.

Bu yöntem, gerçek hayattaki projelerde hem kodun taşınabilirliğini artırır hem de okunabilirliği iyileştirir.

---

## 🎯 Neden .env Dosyası Kullanılır?

- **Ortamlar arası geçiş kolaylığı:** Local, test ve production gibi farklı ortamlarda sadece `.env` dosyasını değiştirerek yapılandırma yapılabilir.
- **Hardcoded verilerden kaçınma:** Kod içine sabit URL, şifre, port vs. yazmak yerine `.env` ile merkezi kontrol sağlanır.
- **Temiz ve sürdürülebilir kod:** Değişken isimleriyle neyin ne olduğu daha rahat anlaşılır.
- **Güvenlik:** `.env` dosyası `.gitignore` içine eklenerek hassas veriler versiyon kontrol sistemine girmez.

---
## 🧱 Kurulum ve Kullanım

### 1️⃣ Gerekli Paketleri Kur

```bash
npm install dotenv
```
### 2️⃣ .env Dosyasını Oluştur
Proje dizininde .env adında bir dosya oluştur ve içine şu satırı yaz:
```env
API_URL=/api/v1
```
### 3️⃣ app.js Dosyasını Oluştur
```diff
// app.js

 const express = require('express');
 const app = express();

+ require('dotenv/config')  // .env dosyasını dahil ettik
+ const api = process.env.API_URL; // API_URL değişkenini tanımladık

- app.get('/', (req, res) => {
-     res.send("Merhaba, Express çalışıyor!");
- });

+ app.get(`${api}/`, (req, res) => {
+     res.send("Merhaba Dünya");
+ });

 app.listen(3000, () => {
     console.log('Server started on http://localhost:3000');
 });

```
- require('dotenv/config'):
 .env dosyasındaki değişkenleri process.env üzerinden projemize dahil etmemizi sağlar.
- const api = process.env.API_URL:
  API_URL artık sabit bir string yerine .env dosyasından okunuyor. Bu sayede, farklı ortamlarda bu URL'yi değiştirmek için sadece .env dosyasını güncellemek yeterli oluyor.
- app.get(${api}/, ...):
Önceden sadece '/' path'i dinlenirken, artık .env dosyasında tanımlı olan yol (örneğin /api/v1) dinleniyor.
Bu yapı daha sürdürülebilir ve taşınabilir bir proje mimarisi sağlar.
### 📁 Proje Klasör Yapısı
```bash
02-env-api-url/
├── node_modules/
├── .env
├── package.json
├── package-lock.json
├── app.js
```
### 📌 Özet
- .env dosyası ile API URL gibi değerler merkezi olarak yönetilir.
- dotenv paketi ile bu değişkenler Express projesine entegre edilir.
- Ortam değişse bile kodu değiştirmeden yapılandırma değiştirilebilir.
- Bu yapı daha büyük projelerde zorunlu bir ihtiyaç haline gelir.
