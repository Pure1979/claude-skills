# Claude için çalışma kuralları

Bu repo, Pure1979'un Claude skill seti. Kullanıcı Türkçe konuşur, yanıtlar Türkçe olmalı.

## Oturum başında

1. Önce `DURUM.md`'yi oku. Kaldığımız yer orada yazıyor.
2. Skill ya da aday kaynakla ilgili bir iş varsa `HARITA.md`'ye bak.
3. **Kaynak repoları yeniden tarama.** `HARITA.md`'deki özetler yeterli. Bir repo sadece şu durumlarda yeniden incelenir: o aday kurulacaksa, kullanıcı güncel halini isterse ya da kaynağın sürümü (`HARITA.md`'deki commit) eskidiyse.

## Her değişiklikten sonra (durum protokolü)

Kullanıcının bir proje komutuyla repoda bir şey değiştiğinde:

1. `DURUM.md`'yi güncelle: "Son güncelleme" ve "Etiket" satırları, Özet, Sıradaki adımlar.
2. "Son 5 değişiklik" tablosunun en üstüne yeni satır ekle. 5'i aşarsa en alttaki satırı sil.
3. Gerekirse `HARITA.md`'yi güncelle (kurulan skill'i "Kurulu yetenekler"e taşı vb.).
4. Tek commit at. Mesajı bir sonraki sıra numarasıyla başlat: `[d-003] Ne değişti`. Sonra `git push origin main` ile gönder. (Git etiketi kullanma, oturum proxy'si etiket gönderimini reddediyor.)
5. `DURUM.md` ve `HARITA.md`'yi claude.ai projesine ("GitHUB Repo") yükle: proje yolları `claude/DURUM.md` ve `claude/HARITA.md` (Projects → project_write, local_path). Aynı yola yazınca eski kopyanın yerine geçer.

Sadece okuma ya da soru-cevap olan işlerde yeni numara verilmez.

## Geri dönüş

Kullanıcı "d-00X noktasına geri dön" derse:
- Commit'i bul: `git log --grep '\[d-00X\]' --format=%H -1` (d-001 = `316fa2f`). Sığ klon yetmezse önce `git fetch --depth=1000 origin main`.
- `git checkout <hash> -- .` çalıştır. O noktada olmayıp sonradan eklenen dosyaları da kaldır.
- Bunu yeni numaralı yeni bir commit olarak kaydet. Asla `git reset --hard` ya da force-push kullanma.
- Durum protokolünü uygula. Tabloya "d-00X noktasına geri dönüldü" yaz.

## Yapı

- `DURUM.md`: son durum ve son 5 değişiklik
- `HARITA.md`: kurulu yetenekler ve aday kaynaklar
- `skills/<kategori>/<skill>/SKILL.md`: kurulan skill'ler. Dışarıdan alınan her skill'in klasörüne kaynağı ve lisansı yazan bir `KAYNAK.md` konur.
