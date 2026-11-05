# Son Durum

Kaldığımız yer burası. Her oturumda ilk okunacak dosya bu.

**Son güncelleme:** 2026-11-05 11:35

## Özet

- Repo kuruldu: `Pure1979/claude-skills`. GitHub bağlantısı çalışıyor.
- Yapı hazır: durum dosyası (bu dosya), yetenek haritası (`HARITA.md`) ve çalışma kuralları (`CLAUDE.md`).
- 6 kaynak repo tarandı ve `HARITA.md`'ye **aday (kurulmamış)** olarak işlendi: HyperFrames, Apify MCP, ScrollCraft, Humanizer, Agent Skills, Awesome.
- Henüz hiçbir skill kurulmadı.

## Sıradaki adımlar

- [ ] Hangi adayların kurulacağına karar vermek (öneri: önce Humanizer, sonra idea-refine ve interview-me)
- [ ] Kurulan skill'leri `skills/<kategori>/` altına yerleştirmek ve Claude hesabına eklemek
- [ ] Apify'ı istersek claude.ai Connectors'tan bağlamak

## Kurtarma noktaları

1 en yeni, 5 en eski. Her değişiklikte yeni kayıt 1'e girer, diğerleri birer aşağı kayar ve 5'teki en eski kayıt silinir.

| No | Tarih | Değişiklik | Kayıt |
|---|---|---|---|
| 1 | 2026-11-05 11:35 | Kurtarma noktaları 1–5 düzenine geçildi | güncel |
| 2 | 2026-11-05 11:30 | Geri dönüş yöntemi düzeltildi | `2c37497` |
| 3 | 2026-11-05 11:30 | İlk kurulum: durum, harita, 6 aday repo | `316fa2f` |
| 4 | — | — | — |
| 5 | — | — | — |

## Geri dönüş

Bir şey bozulursa Claude'a "**3 numaralı noktaya dön**" gibi demen yeterli:

1. O satırdaki kayıt (commit) bulunur ve dosyalar o haline geri yüklenir.
2. Geçmiş silinmez. Geri dönüş de yeni bir kurtarma noktası olarak 1'e yazılır, böylece istersen geri dönüşü de geri alabilirsin.
3. Bu dosya ve claude.ai projesindeki kopyası güncellenir.

5'ten eski noktalar listeden düşer ama GitHub'daki commit geçmişinde durmaya devam eder.
