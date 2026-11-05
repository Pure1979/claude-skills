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
4. Tek commit at, bir sonraki sıra numarasıyla etiketle (`d-001`, `d-002`, ...). Etiketi push'la: `git push origin main --tags`.
5. `DURUM.md` ve `HARITA.md`'yi claude.ai projesine ("GitHUB Repo") aynı adlarla yükle (Projects → project_write, local_path).

Sadece okuma ya da soru-cevap olan işlerde etiket atılmaz.

## Geri dönüş

Kullanıcı "d-00X noktasına geri dön" derse:
- `git checkout d-00X -- .` komutunu çalıştır. O etikette olmayıp sonradan eklenen dosyaları da kaldır.
- Bunu yeni bir commit ve yeni bir etiket olarak kaydet. Asla `git reset --hard` ya da force-push kullanma.
- Durum protokolünü uygula. Tabloya "d-00X noktasına geri dönüldü" yaz.

## Yapı

- `DURUM.md`: son durum ve son 5 değişiklik
- `HARITA.md`: kurulu yetenekler ve aday kaynaklar
- `skills/<kategori>/<skill>/SKILL.md`: kurulan skill'ler. Dışarıdan alınan her skill'in klasörüne kaynağı ve lisansı yazan bir `KAYNAK.md` konur.
