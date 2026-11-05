# Son Durum

Kaldığımız yer burası. Her oturumda ilk okunacak dosya bu.

**Son güncelleme:** 2026-11-05 · **Etiket:** `d-002`

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

En yenisi en üstte. Her değişiklik, GitHub'daki commit mesajının başına yazılan bir işaretle (`[d-00X]`) kayıtlı. Geri dönmek için aşağıdaki talimata bak.

| Etiket | Tarih | Ne değişti |
|---|---|---|
| `d-002` | 2026-11-05 | Geri dönüş noktaları git etiketi yerine commit mesajındaki `[d-00X]` işaretiyle tutuluyor (GitHub etiket gönderimine izin vermiyor). |
| `d-001` | 2026-11-05 | (commit `316fa2f`) İlk kurulum: DURUM, HARITA, CLAUDE.md, README. 6 aday repo haritaya işlendi. |

## Geri dönüş

Bir şey bozulursa Claude'a "**d-00X noktasına geri dön**" demen yeterli. Arka planda şunlar yapılır:

1. O değişikliğin commit'i bulunur (`git log --grep '\[d-00X\]'`, d-001 için `316fa2f`) ve dosyalar o noktadaki haline geri yüklenir.
2. Bu, geçmişi silmeden **yeni bir değişiklik** olarak kaydedilir. Böylece istersen geri dönüşü de geri alabilirsin.
3. Bu dosya güncellenir ve claude.ai projesindeki kopya yenilenir.

Burada sadece son 5 değişiklik listelenir. Daha eskiler GitHub'daki commit geçmişinde durmaya devam eder.
