# Son Durum

Kaldığımız yer burası. Her oturumda ilk okunacak dosya bu.

**Son güncelleme:** 2026-11-05 12:32

## Özet

- Repo kuruldu: `Pure1979/claude-skills`. GitHub bağlantısı çalışıyor.
- Yapı hazır: durum dosyası (bu dosya), yetenek haritası (`HARITA.md`) ve çalışma kuralları (`CLAUDE.md`).
- 6 kaynak repo tarandı ve `HARITA.md`'ye işlendi: HyperFrames, Apify MCP, ScrollCraft, Humanizer, Agent Skills, Awesome.
- **Hedef:** web otomasyonuyla gelir. Ayaklar: yapay zekâ destekli YouTube kanalı, saat nişi, dropshipping, rakip ve en çok izlenen video analizi, web sitesi, Instagram büyütme. Instagram için Buzzfy, zamanlı paylaşım için Postiz zaten açık.
- **YouTube kuralı (16.07.2026):** Şablonla seri üretilmiş, birbirine benzeyen yapay zekâ videoları ve finans/sağlık anlatan yapay zekâ personaları para kazanamıyor. Her video özgün değer katmalı.
- **Kurulum kararı (2026-11-05):** Humanizer, HyperFrames, ScrollCraft, Agent Skills'ten 3 skill (idea-refine, planning-and-task-breakdown, spec-driven-development) ve Apify bağlantısı kurulacak. Awesome sadece başvuru kaynağı.
- **Aktif proje: YouTube saat kanalı** (`projeler/youtube-saat/KONSEPT.md`). Kararlar: saat nişi, önce Türkçe sonra İngilizce, karma format (uzun + Shorts), yapay zekâ seslendirme, yüzsüz. 1. adım (konsept) ve 2. adım (niş analizi, `NIS-ANALIZI.md`) bitti. Ton: "meraklı anlatıcı", format: mini belgesel. İlk video önerisi: Kuvars Krizi. Sıradaki adım kanal kimliği ve ilk videonun onayı.
- **Kurulu:** `humanizer` (Türkçe uyarlamalı), `idea-refine`, `planning-and-task-breakdown`, `spec-driven-development`, HyperFrames'in 9 video skill'i, `scroll-craft`.

## Sıradaki adımlar

- [ ] **YouTube kanalı 3. adım: kanal kimliği** (isim, logo, banner, açıklama) ve ilk video konusunun onayı (öneri: Kuvars Krizi).
- [ ] Seslendirme servisi seçimi (4. adımdan önce).
- [ ] HyperFrames render testi: bu oturumda npm deposu kapalıydı. npm erişimi olan bir oturumda ya da kullanıcının bilgisayarında denenecek.
- [ ] Apify'ı bağlamak (kullanıcı, artık acil değil: niş analizi tarayıcıyla yapıldı): claude.ai → Ayarlar → Connectors → "Apify" → Connect, Apify hesabıyla giriş. Adımlar `HARITA.md` A2'de.
- [ ] `humanizer`'ı claude.ai hesabına kaydetmek: kayıt kartı kullanıcıya sunuldu (2026-11-05), kullanıcının "Kaydet"e basması gerekiyor. Diğer skill'ler bu repo bağlı oturumlarda otomatik yükleniyor. planning ve spec-driven istenirse hesaba da kart olarak sunulabilir.

## Kurtarma noktaları

1 en yeni, 5 en eski. Her değişiklikte yeni kayıt 1'e girer, diğerleri birer aşağı kayar ve 5'teki en eski kayıt silinir.

| No | Tarih | Değişiklik | Kayıt |
|---|---|---|---|
| 1 | 2026-11-05 12:32 | Niş analizi ve örnek video planı | güncel |
| 2 | 2026-11-05 12:08 | YouTube saat kanalı konsepti kaydedildi | `9081d74` |
| 3 | 2026-11-05 11:55 | Apify adımları ve hesap kaydı eklendi | `5aa7665` |
| 4 | 2026-11-05 11:54 | ScrollCraft kuruldu | `a7b064c` |
| 5 | 2026-11-05 11:54 | HyperFrames video skill'leri kuruldu | `ade32d4` |

## Geri dönüş

Bir şey bozulursa Claude'a "**3 numaralı noktaya dön**" gibi demen yeterli:

1. O satırdaki kayıt (commit) bulunur ve dosyalar o haline geri yüklenir.
2. Geçmiş silinmez. Geri dönüş de yeni bir kurtarma noktası olarak 1'e yazılır, böylece istersen geri dönüşü de geri alabilirsin.
3. Bu dosya ve claude.ai projesindeki kopyası güncellenir.

5'ten eski noktalar listeden düşer ama GitHub'daki commit geçmişinde durmaya devam eder.
