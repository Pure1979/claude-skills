---
name: youtube-otomasyon-ajani
description: >
  Operate the self-hosted YouTube Automation Agent (darkzOGx/youtube-automation-agent) for the
  Turkish watch documentary channel: setup checklist, channel settings, producing a video,
  evidence and approval gates, Shorts repurposing, scheduling, analytics learning loop.
  Use for "YouTube otomasyon ajanı", "ajanı kur", "videoyu ajanla üret", "ajanda onay bekleyenler",
  "Shorts'ları çıkar", "yayın takvimi", "kanal analitiği", or anything on http://localhost:3456.
---

# YouTube Otomasyon Ajanı

Kaynak uygulama: [darkzOGx/youtube-automation-agent](https://github.com/darkzOGx/youtube-automation-agent) (MIT, incelenen sürüm 2.11.0, commit `e973d51`, 2026-10-26).
Bu skill uygulamanın kendisi değil. Uygulamayı bizim saat kanalı için nasıl kuracağımızı ve kullanacağımızı anlatır.

## Uygulama ne yapar?

Kullanıcının bilgisayarında çalışan bir Node.js uygulaması. Bir YouTube kanalını uçtan uca yönetir:
konu araştırma → senaryo → seslendirme ve görseller → MP4 → başlık, açıklama, etiket → onay → zamanlanmış yükleme → analitikten öğrenme.
Panel `http://localhost:3456` adresinde açılır. Her video yayından önce kullanıcı onayı bekler. Otonom mod açık olsa bile kaynak ve medya hakkı kontrolleri atlanmaz.

## Nerede çalışır, Claude ona nasıl ulaşır?

- Uygulama **kullanıcının bilgisayarında** çalışır. Claude'un bulut çalışma alanında çalıştırılmaz (npm erişimi yok, YouTube hesabı kullanıcınındır).
- Claude panele **masaüstü uygulamasının yerleşik tarayıcısıyla** `http://localhost:3456` adresinden ulaşır. Tarayıcı paneli kullanıcının bilgisayarında çalıştığı için bu adres oradan açılır. İlk seferde site izni istenir.
- Uygulama çalışmıyorsa (sayfa açılmıyorsa) Claude kullanıcıdan terminalde `npm start` çalıştırmasını ister.
- API çağrıları gerekirse panel sayfasında `fetch` ile yapılır. `.env` içinde `API_KEY` tanımlıysa değişiklik yapan istekler `x-api-key` başlığı ister. Anahtarı kullanıcı panele girer. **Claude API anahtarı, şifre ya da token yazmaz ve sohbette istemez.**

## Kurulum (kullanıcı yapar, Claude adım adım eşlik eder)

1. Node.js 18.17+ kurulu olmalı.
2. Terminalde:
   ```bash
   git clone https://github.com/darkzOGx/youtube-automation-agent.git
   cd youtube-automation-agent
   npm install
   npx playwright install chromium
   npm run walkthrough
   ```
3. **Google Cloud:** proje oluştur → YouTube Data API v3 ve YouTube Analytics API'yi aç → "Desktop app" türünde OAuth istemcisi oluştur → JSON'u `config/credentials.json` olarak kaydet → Google Auth Platform → Audience altında kanal sahibi hesabı **test kullanıcısı** olarak ekle. (Test modunda giriş 7 günde bir yenilenir.)
4. **Metin sağlayıcı:** en az bir anahtar. Gemini'nin ücretsiz katmanı var. OpenRouter ile Claude modelleri de seçilebilir.
5. **Seslendirme:** ElevenLabs, OpenAI ya da Gemini TTS. Türkçe sesi kurulumdan sonra "Production readiness" testinde dinleyip seç.
6. `npm start` → panelde **Production readiness → Run verified check**. Hiçbir şey yüklemeden metin, ses, kanal erişimi ve test MP4'ünü doğrular.

## Kanal ayarları (bizim kanal için)

`.env` ve panelde:

| Ayar | Değer | Neden |
|---|---|---|
| `CHANNEL_NAME` | Kanal kimliği adımında seçilen isim | |
| `TARGET_AUDIENCE` | Saatlerle ilgilenen, markaların ve ikonik modellerin hikâyesini merak eden Türkçe izleyiciler | |
| `YOUTUBE_REGION` | `TR` | |
| `DEFAULT_PRIVACY_STATUS` | `private` | Her video önce gizli yüklenir, son kontrol kullanıcının |
| `API_KEY` | Kullanıcının belirlediği rastgele bir değer | Panel üzerinden değişiklikleri korur |
| `VIDEO_PROVIDER` | `slideshow` (başlangıç) | Ücretsiz. Ücretli klip sağlayıcı açılırsa `VIDEO_MAX_GENERATED_SECONDS` ile tavan koy |
| `MAX_CONCURRENT_JOBS` | `1` | |
| Telemetri | Kapalı bırak (varsayılan) | |

**Strateji (Autonomous operator ekranı):**
- Hedef: mini belgesel saat kanalı, ton "meraklı anlatıcı", sen dili, Türkçe.
- İçerik sütunları: (1) "Neden bu kadar pahalı?", (2) saat dünyasının dönüm noktaları ve skandalları, (3) tarihi anların ve ünlülerin saatleri, (4) güncel sektör dosyaları.
- Ritim: **haftada 1 uzun video** (8–12 dk) + o videodan 3 Shorts. Günlük üretim açılmaz.
- Engellenen konular: yatırım tavsiyesi ("prim yapacak saatler"), elde olmayan ürünün incelemesi, gerçek kişiyi taklit eden yapay zekâ anlatıcı.
- Otonomi: ilk 4 videoda **kapalı**. Her video tek tek "create a single video" ile üretilir.

## Bir video üretme akışı

1. **Konu:** `projeler/youtube-saat/NIS-ANALIZI.md`'deki planlı videolardan biri. Panelde fikir olarak eklenir ve oradan üretilir.
2. **Senaryo kontrolü:** Ajan senaryoyu yazınca Claude sahne metinlerini okur ve `humanizer` skill'iyle Türkçe kalıplardan arındırır. Düzeltmeler sahne düzenleme ekranından girilir.
3. **Kaynak masası (Evidence desk):** Her tarih, rakam ve iddia doğrulanmış bir kaynağa bağlanır. Kaynaksız iddia ya düzeltilir ya da senaryodan çıkarılır. Kaynaklar video açıklamasına da eklenir.
4. **Görsel kontrol:** Slayt gösterisi her videoda aynı görünmeye başlarsa (YouTube'un şablon kuralı riski) sahneler tek tek yenilenir ya da bazı sahneler HyperFrames ile özel üretilir. Dışarıda üretilmiş bir sahnenin "replace" ile içeri alınıp alınamadığı ilk videoda doğrulanacak.
5. **Medya hakları:** Marka ve basın fotoğrafları izinsiz kullanılmaz. Onay ekranındaki medya hakkı beyanı ancak bu kontrol yapıldıysa işaretlenir.
6. **Onay ve zamanlama:** Onay, yayın ve "publish now" geri alınması zor işlemlerdir. Claude bunları **her seferinde kullanıcıya sorup açık "evet" aldıktan sonra** yapar.
7. **Shorts:** Onaylanan videodan "Shorts Repurposing" ile 3 dikey taslak çıkarılır. Başlıkları `NIS-ANALIZI.md`'deki Shorts kesitlerinden uyarlanır. Her biri ayrıca onaylanır.

## Öğrenme döngüsü

- Ajan her videonun 24 saat ve 7 gün sonuçlarını toplar ve öneri çıkarır. Öneriler kullanıcı onayı olmadan sonraki videolara uygulanmaz.
- Claude haftalık olarak önerileri özetler, kanal stratejisiyle çelişenleri (ör. "daha sık ve kısa video") işaretler.
- Başlık ve kapak görseli A/B testleri ("growth experiments") sadece kullanıcı onayıyla başlatılır.

## Diğer araçlarla iş bölümü

| İş | Araç |
|---|---|
| YouTube'a yükleme, zamanlama, YouTube analitiği, yorum yönetimi | Bu ajan |
| Instagram, TikTok ve diğer kanallara paylaşım | Postiz / Buzzfy |
| Özel motion grafik sahneleri, kapak görseli tasarımı | HyperFrames |
| Metin doğallaştırma | humanizer |
| Rakip ve niş analizi | Yerleşik tarayıcı (gerekirse Apify) |

## YouTube kuralı (16.07.2026)

Şablonla seri üretilmiş, birbirine benzeyen yapay zekâ videoları para kazanamaz. Bu ajan seri üretime çok uygun olduğu için kurallar burada daha da önemli:
- Üretim ritmi düşük tutulur, her video kendi araştırmasıyla yapılır.
- Aynı görsel kalıp üst üste kullanılmaz.
- Kaynak masası boş bir video onaya gönderilmez.
