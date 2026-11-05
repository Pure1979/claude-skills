# YouTube Saat Kanalı: Devir Özeti

Son durum: 2026-11-05 17:10. Bu dosya YouTube projesinde kaldığımız yerden devam etmek için hazırlandı. Önceki çalışma "GitHUB Repo" projesinde ve `Pure1979/claude-skills` reposunda yapıldı.

## Nerede kaldık?

1. ✅ Kanal konsepti
2. ✅ Niş analizi
3. ⏭ **Sıradaki: kanal kimliği** (isim, logo, banner, açıklama) ve ilk video konusunun onayı. Önerilen ilk video: Kuvars Krizi.
4. İlk video: senaryo → Humanizer → seslendirme → görseller ve kurgu → render
5. Yayın: başlık, açıklama, kapak görseli, Postiz ile zamanlama

## Genel hedef

Web otomasyonuyla gelir. YouTube kanalı bunun ilk ayağı. Diğer ayaklar: dropshipping, rakip analizi, web sitesi, Instagram büyütme.

## Kanal kararları

| Konu | Karar |
|---|---|
| Niş | Saatler |
| Dil | Önce Türkçe, sonra İngilizce. Görseller ortak, sadece ses ve metin değişir. |
| Format | Karma: haftada 1 uzun video (8–12 dk) + ondan kesilen 3 Shorts |
| Ses | Yapay zekâ seslendirme. Servis henüz seçilmedi (HeyGen, ElevenLabs vb.). |
| Yüz | Yüzsüz kanal |
| Format türü | Mini belgesel / hikâye anlatımı |
| Ton | "Meraklı anlatıcı": bilen ama gösteriş yapmayan, sen diliyle konuşan, her iddiayı kaynağa dayandıran |

## YouTube kuralı (16.07.2026)

Şablonla seri üretilmiş, birbirine çok benzeyen yapay zekâ videoları ve finans/sağlık anlatan yapay zekâ personaları para kazanamıyor. Bizim uygulamamız:
- Her videoda özgün araştırma. Kaynaklar açıklamada yer alır.
- Gerçek bir kişiyi taklit eden persona yok.
- Görsel stil her videoya göre uyarlanır. Tek şablon tekrar tekrar kullanılmaz.

## Niş analizi (2026-11-05)

6 kanalın en popüler videoları incelendi. B = bin, Mn = milyon izlenme.

**Türkiye:**
- Erk Koçak (233 B abone): "Markaları sıraladı" 1,1 Mn · "Piyasadaki saatlerin çoğu dandik" 1 Mn · "Dünyanın en pahalı saatleri" 881 B · **"Rolex neden bu kadar pahalı? (mini belgesel)" 690 B**
- Horobox (51 B abone): "Rolex almayın!" 161 B · "Prim yapacak saatler" 96 B

**Dünya:**
- Teddy Baldassarre: "20 Affordable Watches Even Snobs Can't Hate" 4,3 Mn · "Watches of World Leaders" 3,4 Mn · "13 Watches That Look More Expensive" 2,9 Mn · "Grand Seiko Spring Drive nasıl çalışır" 2,8 Mn
- Andrew Morgan (340 B abone): "The Swiss Are Panicking About Fake Watches" 1 ayda 1,2 Mn · "The Decline of Rolex" 155 B
- Hodinkee (468 B abone): ünlülerle sohbetler (John Mayer 5,7 Mn)
- About Effing Time (70 B abone): fikir ve tartışma (Rolex Rant, Overrated vs Underrated)

Kullanıcının verdiği diğer referans kanallar (henüz taranmadı): Chisholm Hunter, Swiss Watch Gang, Subdial, The 1916 Company, WatchChris, Teddy Baldassarre Reviews, Watches with Abdullah, TurkishWatchGuy, Britt Pierce, Bark & Jack, Time & Tide, Minutemon, The Movement Podcast.

**Tutan kalıplar:** (1) para merakı, (2) liste ve sıralama, (3) karşı görüş, (4) ünlüler ve tarihi figürler, (5) açıklayıcı / mini belgesel, (6) sektör dramı ve haber.

**Bulgu:** Baktığımız Türkçe kanallarda düzenli mini belgesel üreten yok. Tek örnek olan Erk Koçak'ın Rolex videosu 690 B izlenmiş. Örneklem küçük.

**Başlık dili:** Türkçede 1–2 kelime büyük harfle vurgulanıyor (NEDEN, EN PAHALI). İngilizcede iddialı fiiller öne çıkıyor (Panicking, Avoid).

## İçerik sütunları

1. "Neden bu kadar pahalı?" serisi
2. Saat dünyasının dönüm noktaları ve skandalları
3. Tarihi anların ve ünlülerin saatleri
4. Güncel sektör dosyaları

**Kaçınılacaklar:** yatırım tavsiyesi gibi görünen başlıklar, elde olmayan ürünün "incelemesi", izinsiz marka ya da basın fotoğrafının bolca kullanılması.

## İlk 3 video planı

| # | Çalışma başlığı | Shorts kesitleri |
|---|---|---|
| 1 | **İSVİÇRE Saatçiliğini Neredeyse BİTİREN Japon İcadı** (Kuvars Krizi) | 1969'da bir saat her şeyi değiştirdi · Swatch İsviçre'yi nasıl kurtardı? · İsviçre'de kaç saatçi işsiz kaldı? |
| 2 | **SAHTE Saat Sektörü: İsviçre Neden PANİKTE?** (Türkiye'deki sahte saat pazarı yerel kanca) | Sahteyi ayırmanın 1 yolu · Sahte saat yakalanınca ne olur? · Sektör ne kadar büyük? |
| 3 | **Bir Saate Neden EV FİYATI Ödenir?** (komplikasyonlar, el işçiliği) | Bir saatte kaç parça var? · En pahalı komplikasyon · Bir ustanın bir saate harcadığı süre |

İlk video önerisi #1. Habere bağlı değil, büyük kısmı grafik ve haritayla anlatılabilir, İngilizceye birebir taşınır. Tüm tarih ve rakamlar senaryo aşamasında kaynaklarla doğrulanacak.

## Araçlar ve teknik durum

- **Video skill'leri** `Pure1979/claude-skills` reposunda: HyperFrames (9 skill: video üretimi, altyazı, stil kopyalama, video yeniden kurma), Humanizer (Türkçe uyarlamalı), ScrollCraft, idea-refine, planning-and-task-breakdown, spec-driven-development. **YouTube projesindeki bir oturumda bu skill'leri kullanmak için o oturuma `Pure1979/claude-skills` reposunu bağlamak gerekiyor.** Humanizer ayrıca hesaba kaydedilebilir (kayıt kartı sunulmuştu).
- **Render:** HyperFrames CLI henüz test edilemedi, çünkü önceki oturumlarda npm/pip paket depoları kapalıydı. Yedek plan: Chromium + Playwright + ffmpeg ile HTML animasyonları kare kare render etmek. Seslendirme dışarıdan bir servisle yapılacak.
- **Veri toplama:** YouTube verileri masaüstü uygulamasının tarayıcısıyla çekildi (youtube.com için izin verildi). Apify bağlanmadı; şu an acil değil.
- **YouTube Automation Agent (2026-11-05'te eklendi):** Kanalı uçtan uca yöneten, kullanıcının bilgisayarında çalışan açık kaynak uygulama ([darkzOGx/youtube-automation-agent](https://github.com/darkzOGx/youtube-automation-agent)). Senaryo, seslendirme, MP4, onay, zamanlanmış yükleme, analitik ve Shorts çıkarmayı yapıyor. Kurulumu ve bizim kanal ayarları `youtube-otomasyon-ajani` skill'inde. Rolü: YouTube'a yükleme, zamanlama, analitik ve yorumlar. Görseller HyperFrames ile desteklenecek, çünkü varsayılan slayt görünümü şablon kuralı açısından risk.
- **Hesapta açık araçlar:** Buzzfy (Instagram analizi ve paylaşım), Postiz (YouTube dahil 28 kanala zamanlı paylaşım).

## Açık işler

- [ ] Kanal kimliği: isim önerileri, logo, banner, açıklama
- [ ] İlk video konusunun onayı (öneri: Kuvars Krizi)
- [ ] YouTube Automation Agent'ı bilgisayara kurmak (Node.js, Google Cloud OAuth, metin + ses anahtarı)
- [ ] Seslendirme servisi seçimi (ajanın desteklediği ElevenLabs / OpenAI / Gemini TTS arasından, Türkçe ses testiyle)
- [ ] HyperFrames render testi (npm erişimi olan bir oturumda ya da kullanıcının bilgisayarında)
- [ ] Gerekirse kalan referans kanalların taranması

## Yeni projede ilk mesaj için öneri

> Bu dosyadaki YouTube saat kanalı çalışmasına kaldığımız yerden devam ediyoruz. Sıradaki adım kanal kimliği: önce kanal ismi önerileriyle başla.
