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

## Temel kural: ajan arka ofistir, yönetmen değil

Kanalın yaratıcı şablonu bizde kalır. Ajan sadece şablonun üretim ve yayın kısmını tamamlar. Ajanı tek başına uçtan uca çalıştırmak kanalı "seri üretilmiş yapay zekâ videosu" kalıbına düşürür ve YouTube'un şablon kuralına takılma riski doğurur.

| Katman | Kim yapar | Nasıl |
|---|---|---|
| Konu, araştırma, ton, içerik sütunları | **Biz** | `projeler/youtube-saat/KONSEPT.md` ve `NIS-ANALIZI.md`. Ajanın konu önerileri sadece fikir havuzudur. |
| Senaryo | **Biz** | Claude senaryoyu yazar, `humanizer` ile Türkçe kalıplardan arındırır, ajanın sahne metinlerine girer. Ajanın yazdığı taslak sadece iskelet. |
| Kaynak masası | Ajan | Her iddia kaynağa bağlanır. Kaynaksız iddia çıkarılır. |
| Seslendirme | Ajan | ElevenLabs / Gemini / OpenAI. Sahne metni değişince sadece o sahnenin sesi yenilenir. |
| Görseller | **Biz** (HyperFrames) | Özel sahneler ajana sahne sahne yüklenir. Ajanın slayt görseli sadece önemsiz ara sahnelerde kalabilir. |
| Kurgu, MP4, altyazı | Ajan | Sahne yükledikten sonra yeniden derleme. |
| Shorts | Ajan | Onaylı uzun videodan 3 dikey taslak. |
| Yükleme, zamanlama, analitik, yorumlar | Ajan | Her yayın ve onay kullanıcıya sorulur. |
| Otonom operatör | **Kapalı** | Yaratıcı kararları bize bırakmalı. Açılması kullanıcının açık kararını gerektirir ve bu tablo yeniden değerlendirilir. |

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

1. **Konu ve brif:** Konu `projeler/youtube-saat/NIS-ANALIZI.md`'deki plandan seçilir. Claude kısa bir brif yazar (konu, sütun, ton, ana iddialar ve kaynakları, istenen süre) ve panelde fikir olarak ekler. Üretim oradan başlatılır.
2. **Senaryo bizim:** Ajanın ilk taslağı sadece sahne iskeleti olarak kullanılır. Claude bizim senaryomuzu yazar, `humanizer` ile doğallaştırır ve sahne sahne ajanın sahne metinlerine girer. Ardından sadece değişen sahnelerin sesi yenilenir.
3. **Kaynak masası (Evidence desk):** Her tarih, rakam ve iddia doğrulanmış bir kaynağa bağlanır. Kaynaksız iddia ya düzeltilir ya da senaryodan çıkarılır. Kaynaklar video açıklamasına da eklenir.
4. **Görseller bizim:** Önemli sahneler (giriş, ana anlatı, rakamlar, haritalar, zaman çizelgeleri) HyperFrames ile üretilir ve ajana yüklenir:
   - Panelde: Scene Repair Studio → sahne → görseli değiştir → dosyayı seç → telif onayını işaretle.
   - API'de: `PUT /api/content/:productionId/scenes/:sceneId/asset`. Gövde ham dosya (`image/*` ya da `video/*`, en fazla 100 MB, video MP4 uyumlu olmalı). Başlıklar: `x-file-name`, `x-rights-confirmed: true` (sadece haklar gerçekten bizdeyse), `x-synthetic-media: true` (yapay üretimse).
   - Yüklemeden sonra `POST /api/content/:productionId/scenes/rebuild` ile video yeniden derlenir ve yeniden onaya düşer.
   - Sahne süresi ile seslendirme süresi uyumlu olmalı. HyperFrames sahnesi, sahnenin ses süresine göre render edilir. (İlk videoda ajanın uzun ya da kısa klibi nasıl kırptığı doğrulanacak.)
   - Ajanın slayt görseli sadece kısa ara sahnelerde kalabilir. Ardışık iki videoda aynı görsel kalıp kullanılmaz.
5. **Medya hakları:** Marka ve basın fotoğrafları izinsiz kullanılmaz. Onay ekranındaki ve yüklemedeki telif beyanı ancak bu kontrol yapıldıysa işaretlenir.
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

## Pratik sınırlar

- **Bilgisayar açık olmalı.** Zamanlanmış yüklemeler ajan çalışırken yapılır (15 dakikada bir kontrol). Yayın saatinde bilgisayar kapalıysa yayın kayar.
- **Haftalık Google girişi.** Google Cloud projesi "Testing" modundayken YouTube girişi 7 günde bir yenilenmeli. Claude haftalık kontrolde bunu hatırlatır.
- **HyperFrames render'ı** da kullanıcının bilgisayarında yapılır (aynı makinede Node.js zaten kurulu olacak). Render edilen dosyayı panele kullanıcı yükler. Claude'un bulut ortamındaki dosyalar panele doğrudan gönderilemez.

## YouTube kuralı (16.07.2026)

Şablonla seri üretilmiş, birbirine benzeyen yapay zekâ videoları para kazanamaz. Bu ajan seri üretime çok uygun olduğu için kurallar burada daha da önemli:
- Üretim ritmi düşük tutulur, her video kendi araştırmasıyla yapılır.
- Aynı görsel kalıp üst üste kullanılmaz.
- Kaynak masası boş bir video onaya gönderilmez.
