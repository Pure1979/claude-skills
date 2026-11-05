# YouTube Saat Kanalı

İlk YouTube kanalı. Başlangıç: 2026-11-05.

## Kararlar

| Konu | Karar | Not |
|---|---|---|
| Niş | Saatler | Marka hikayeleri, model incelemeleri, saat dünyasından olaylar. Kesin açı niş analizinden sonra seçilecek. |
| Dil | Önce Türkçe, sonra İngilizce | Görseller ve kurgu iki dilde ortak kullanılır. İngilizce sürüm için sadece seslendirme, altyazı ve metin yenilenir. |
| Format | Karma | Uzun videolar (8–15 dk) asıl gelir kaynağı. Her uzun videodan 2–3 Shorts kesilir, keşfedilme için. |
| Ses | Yapay zekâ seslendirme | Servis seçimi 4. adımdan önce yapılacak (HeyGen, ElevenLabs vb.). |
| Yüz | Yüzsüz kanal | Yapay zekâ seslendirme kararından çıkıyor. Görseller grafik, ürün fotoğrafı ve animasyon. |

## YouTube kuralına uyum

16.07.2026'dan beri şablonla seri üretilmiş, birbirine çok benzeyen yapay zekâ videoları para kazanamıyor. Bu kanal için anlamı:

- Her videonun kendine özgü bir araştırması ve bakış açısı olacak. Aynı kalıbı sadece konu değiştirerek tekrar etmeyeceğiz.
- Senaryolar gerçek kaynaklara dayanacak, kaynaklar açıklamada yer alacak.
- Seslendirme yapay zekâ olsa da gerçek bir kişiyi taklit eden bir "persona" kullanılmayacak.
- Görsel stil her video için uyarlanacak. Tek bir hazır şablon tekrar tekrar kullanılmayacak.

## Yol haritası

| # | Adım | Durum |
|---|---|---|
| 1 | Kanal konsepti | ✅ 2026-11-05 |
| 2 | Niş analizi: en çok izlenen videolar, rakip kanallar, tutan başlık ve süreler | ⏳ Apify bağlantısı bekleniyor |
| 3 | Kanal kimliği: isim, logo, banner, açıklama | — |
| 4 | İlk video: senaryo → Humanizer → seslendirme → görseller ve kurgu → render | — |
| 5 | Yayın: başlık, açıklama, kapak görseli, Postiz ile zamanlama | — |

## Ön tarama (2026-11-05, web araması)

Apify bağlanmadan önce yapılan kaba bir arama. İzlenme verisi içermiyor.

- **Erk Koçak:** Türkçe saat içeriğinin bilinen adı. Yüzü görünen, kişisel anlatımlı içerikler: fiyat aralığına göre saat önerileri, saat alışverişi vlogları, kendi ürettirdiği saat. [Örnek özet](https://recapio.com/digest/en-iyi-saat-onerileri-17-farkli-saat-500-altinda-by-erk-kocak)
- Türkçe saat içeriği web aramasında az görünüyor. Bu, rekabetin düşük olabileceğine işaret ediyor ama kesin sonuç için Apify ile izlenme verisi gerekiyor.

**Test edilecek fikir:** Yüzü görünen inceleme kanallarıyla kafa kafaya gitmek yerine, yüzsüz bir **hikâye ve belgesel** formatı. Marka kuruluş hikayeleri, ikonik modellerin arka planı, saat dünyasının skandalları ve rekorları. Bu format yüzsüz anlatıma ve sonradan İngilizceye çevrilmeye uygun. Niş analizi bu fikri doğrulayacak ya da çürütecek.

## Teknik durum

- Video üretimi için HyperFrames skill'leri kurulu. Ancak bu oturumda npm/pip kapalı olduğu için CLI kurulamıyor.
- Yedek plan: Ortamdaki Chromium + Playwright + ffmpeg ile HTML animasyonları kare kare render edilebilir. Seslendirme dışarıdan (servis) gelecek.
