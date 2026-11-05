# Son Durum

Kaldığımız yer burası. Her oturumda ilk okunacak dosya bu.

**Son güncelleme:** 2026-11-05 11:55

## Özet

- Repo kuruldu: `Pure1979/claude-skills`. GitHub bağlantısı çalışıyor.
- Yapı hazır: durum dosyası (bu dosya), yetenek haritası (`HARITA.md`) ve çalışma kuralları (`CLAUDE.md`).
- 6 kaynak repo tarandı ve `HARITA.md`'ye işlendi: HyperFrames, Apify MCP, ScrollCraft, Humanizer, Agent Skills, Awesome.
- **Hedef:** web otomasyonuyla gelir. Ayaklar: yapay zekâ destekli YouTube kanalı, saat nişi, dropshipping, rakip ve en çok izlenen video analizi, web sitesi, Instagram büyütme. Instagram için Buzzfy, zamanlı paylaşım için Postiz zaten açık.
- **YouTube kuralı (16.07.2026):** Şablonla seri üretilmiş, birbirine benzeyen yapay zekâ videoları ve finans/sağlık anlatan yapay zekâ personaları para kazanamıyor. Her video özgün değer katmalı.
- **Kurulum kararı (2026-11-05):** Humanizer, HyperFrames, ScrollCraft, Agent Skills'ten 3 skill (idea-refine, planning-and-task-breakdown, spec-driven-development) ve Apify bağlantısı kurulacak. Awesome sadece başvuru kaynağı.
- **Kurulu:** `humanizer` (Türkçe uyarlamalı), `idea-refine`, `planning-and-task-breakdown`, `spec-driven-development`, HyperFrames'in 9 video skill'i, `scroll-craft`.

## Sıradaki adımlar

- [ ] HyperFrames render testi: bu oturumda npm deposu kapalıydı. npm erişimi olan bir oturumda ya da kullanıcının bilgisayarında denenecek.
- [ ] Apify'ı bağlamak (kullanıcı): claude.ai → Ayarlar → Connectors → "Apify" → Connect, Apify hesabıyla giriş. Adımlar `HARITA.md` A2'de.
- [ ] Tek dosyalık skill'leri claude.ai hesabına kaydetmek (humanizer, planning-and-task-breakdown, spec-driven-development): kayıt kartları kullanıcıya sunuldu. Çok dosyalı olanlar (HyperFrames, ScrollCraft, idea-refine) bu repo bağlı oturumlarda otomatik yükleniyor.

## Kurtarma noktaları

1 en yeni, 5 en eski. Her değişiklikte yeni kayıt 1'e girer, diğerleri birer aşağı kayar ve 5'teki en eski kayıt silinir.

| No | Tarih | Değişiklik | Kayıt |
|---|---|---|---|
| 1 | 2026-11-05 11:55 | Apify bağlantı adımları eklendi | güncel |
| 2 | 2026-11-05 11:54 | ScrollCraft kuruldu | `a7b064c` |
| 3 | 2026-11-05 11:54 | HyperFrames video skill'leri kuruldu | `ade32d4` |
| 4 | 2026-11-05 11:53 | Agent Skills'ten 3 skill kuruldu | `3c3d3e3` |
| 5 | 2026-11-05 11:53 | Humanizer kuruldu (Türkçe uyarlamalı) | `ba24ab5` |

## Geri dönüş

Bir şey bozulursa Claude'a "**3 numaralı noktaya dön**" gibi demen yeterli:

1. O satırdaki kayıt (commit) bulunur ve dosyalar o haline geri yüklenir.
2. Geçmiş silinmez. Geri dönüş de yeni bir kurtarma noktası olarak 1'e yazılır, böylece istersen geri dönüşü de geri alabilirsin.
3. Bu dosya ve claude.ai projesindeki kopyası güncellenir.

5'ten eski noktalar listeden düşer ama GitHub'daki commit geçmişinde durmaya devam eder.
