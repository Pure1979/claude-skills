# Claude için çalışma kuralları

Bu repo, Pure1979'un Claude skill seti. Kullanıcı Türkçe konuşur, yanıtlar Türkçe olmalı.

## Oturum başında

1. Önce `DURUM.md`'yi oku. Kaldığımız yer orada yazıyor.
2. Skill ya da aday kaynakla ilgili bir iş varsa `HARITA.md`'ye bak.
3. **Kaynak repoları yeniden tarama.** `HARITA.md`'deki özetler yeterli. Bir repo sadece şu durumlarda yeniden incelenir: o aday kurulacaksa, kullanıcı güncel halini isterse ya da kaynağın sürümü (`HARITA.md`'deki commit) eskidiyse.

## Her değişiklikten sonra (durum protokolü)

Kullanıcının bir proje komutuyla repoda bir şey değiştiğinde:

1. `DURUM.md`'de "Son güncelleme" satırını (tarih ve saat, İstanbul saati), Özet'i ve Sıradaki adımlar'ı güncelle.
2. **Kurtarma noktaları** tablosunu kaydır. Tablo her zaman tam 5 satırdır: 1 en yeni, 5 en eski.
   - 5'teki kayıt silinir. 4→5, 3→4, 2→3, 1→2 olarak birer aşağı kayar.
   - 2'ye inen eski 1 numaranın "Kayıt" sütunundaki "güncel" yazısını, değişiklikten önceki HEAD'in kısa hash'iyle değiştir (`git rev-parse --short HEAD`, commit atmadan önce al).
   - Yeni 1 numara: tarih + saat (`YYYY-AA-GG SS:DD`), değişikliğin **çok kısa** özeti (birkaç kelime), Kayıt = "güncel".
3. Gerekirse `HARITA.md`'yi güncelle (kurulan skill'i "Kurulu yetenekler"e taşı vb.).
4. Tek commit at. Mesaj: `Kurtarma noktası: <aynı kısa özet>`. Sonra `git push origin main` ile gönder. Git etiketi kullanma, oturum proxy'si etiket gönderimini reddediyor.
5. `DURUM.md` ve `HARITA.md`'yi claude.ai projesine ("GitHUB Repo") yükle: proje yolları `claude/DURUM.md` ve `claude/HARITA.md` (Projects → project_write, local_path). Aynı yola yazınca eski kopyanın yerine geçer.

Sadece okuma ya da soru-cevap olan işlerde kurtarma noktası oluşturulmaz.

## Geri dönüş

Kullanıcı "N numaralı noktaya dön" derse:
- Hash'i `DURUM.md`'deki N numaralı satırın "Kayıt" sütunundan al. 1 numara zaten güncel haldir.
- Sığ klonda o commit yoksa önce `git fetch --depth=1000 origin main`.
- `git checkout <hash> -- .` çalıştır. O noktada olmayıp sonradan eklenen dosyaları da kaldır (`git diff --name-only --diff-filter=A <hash> HEAD`).
- Asla `git reset --hard` ya da force-push kullanma. Geri dönüş yeni bir commit'tir.
- Durum protokolünü uygula. Yeni 1 numaranın özeti: "N numaralı noktaya (tarih) dönüldü". Geri yüklenen `DURUM.md` eski tabloyu getirir. Tabloyu, dönüşten hemen önceki halinden kaydırarak yeniden kur.

## Yapı

- `DURUM.md`: son durum ve 5 kurtarma noktası
- `HARITA.md`: kurulu yetenekler ve aday kaynaklar
- `.claude/skills/<skill>/SKILL.md`: kurulan skill'ler. Claude bu klasörü otomatik yüklediği için alt kategori klasörü açılmaz. Kategori `HARITA.md`'deki tabloda tutulur. Dışarıdan alınan her skill'in klasörüne kaynağı, lisansı ve yaptığımız değişiklikleri yazan bir `KAYNAK.md` konur, orijinal `LICENSE` korunur.
