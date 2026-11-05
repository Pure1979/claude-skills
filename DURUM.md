# Son Durum

Kaldığımız yer burası. Her oturumda ilk okunacak dosya bu.

**Son güncelleme:** 2026-11-05 · **Etiket:** `d-001`

## Özet

- Repo kuruldu: `Pure1979/claude-skills`. GitHub bağlantısı çalışıyor.
- Yapı hazır: durum dosyası (bu dosya), yetenek haritası (`HARITA.md`) ve çalışma kuralları (`CLAUDE.md`).
- 6 kaynak repo tarandı ve `HARITA.md`'ye **aday (kurulmamış)** olarak işlendi: HyperFrames, Apify MCP, ScrollCraft, Humanizer, Agent Skills, Awesome.
- Henüz hiçbir skill kurulmadı.

## Sıradaki adımlar

- [ ] Hangi adayların kurulacağına karar vermek (öneri: önce Humanizer, sonra idea-refine ve interview-me)
- [ ] Kurulan skill'leri `skills/<kategori>/` altına yerleştirmek ve Claude hesabına eklemek
- [ ] Apify'ı istersek claude.ai Connectors'tan bağlamak

## Son 5 değişiklik

En yenisi en üstte. Her değişiklik bir git etiketiyle işaretli. Geri dönmek için aşağıdaki talimata bak.

| Etiket | Tarih | Ne değişti |
|---|---|---|
| `d-001` | 2026-11-05 | İlk kurulum: DURUM, HARITA, CLAUDE.md, README. 6 aday repo haritaya işlendi. |

## Geri dönüş

Bir şey bozulursa Claude'a "**d-00X noktasına geri dön**" demen yeterli. Arka planda şunlar yapılır:

1. O etiketteki dosyalar geri yüklenir (`git checkout d-00X -- .`).
2. Bu, geçmişi silmeden **yeni bir değişiklik** olarak kaydedilir. Böylece istersen geri dönüşü de geri alabilirsin.
3. Bu dosya güncellenir ve claude.ai projesindeki kopya yenilenir.

Burada sadece son 5 değişiklik listelenir. Daha eskiler GitHub'daki etiket ve commit geçmişinde durmaya devam eder.
