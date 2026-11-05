# Son Durum

Kaldığımız yer burası. Her oturumda ilk okunacak dosya bu.

**Son güncelleme:** 2026-11-05 11:54

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
- [ ] Apify hesabı açıp claude.ai Connectors'tan bağlamak (kullanıcı)
- [ ] Skill'leri claude.ai hesabına da kaydetmek

## Kurtarma noktaları

1 en yeni, 5 en eski. Her değişiklikte yeni kayıt 1'e girer, diğerleri birer aşağı kayar ve 5'teki en eski kayıt silinir.

| No | Tarih | Değişiklik | Kayıt |
|---|---|---|---|
| 1 | 2026-11-05 11:54 | ScrollCraft kuruldu | güncel |
| 2 | 2026-11-05 11:54 | HyperFrames video skill'leri kuruldu | `ade32d4` |
| 3 | 2026-11-05 11:53 | Agent Skills'ten 3 skill kuruldu | `3c3d3e3` |
| 4 | 2026-11-05 11:53 | Humanizer kuruldu (Türkçe uyarlamalı) | `ba24ab5` |
| 5 | 2026-11-05 11:35 | Kurtarma noktaları 1–5 düzenine geçildi | `91505b8` |

## Geri dönüş

Bir şey bozulursa Claude'a "**3 numaralı noktaya dön**" gibi demen yeterli:

1. O satırdaki kayıt (commit) bulunur ve dosyalar o haline geri yüklenir.
2. Geçmiş silinmez. Geri dönüş de yeni bir kurtarma noktası olarak 1'e yazılır, böylece istersen geri dönüşü de geri alabilirsin.
3. Bu dosya ve claude.ai projesindeki kopyası güncellenir.

5'ten eski noktalar listeden düşer ama GitHub'daki commit geçmişinde durmaya devam eder.
