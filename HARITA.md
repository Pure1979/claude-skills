# Yetenek Haritası

Claude skill setinin iskelet haritası. Burada şu an kurulu olan yetenekler ve ileride kurulabilecek aday kaynaklar duruyor.
Adayların içeriği bir kez tarandı ve özeti aşağıda. Yeniden taramaya gerek yok. Kaynak sürüm değiştiyse ya da kurulum yapılacaksa sadece ilgili repo yeniden incelenir.

## Kurulu yetenekler

Repoda `.claude/skills/<skill>/` altında durur. Bu repo bir oturuma bağlanınca Claude bunları otomatik yükler. "Hesapta" sütunu, skill'in claude.ai hesabına da kaydedilip kaydedilmediğini gösterir.

| Skill | Kategori | Kaynak | Hesapta | Kurulum |
|---|---|---|---|---|
| `humanizer` | içerik | A4 · Türkçe uyarlamalı | bekliyor | 2026-11-05 |
| `idea-refine` | düşünme | A5 | bekliyor | 2026-11-05 |
| `planning-and-task-breakdown` | düşünme | A5 | bekliyor | 2026-11-05 |
| `spec-driven-development` | düşünme / geliştirme | A5 | bekliyor | 2026-11-05 |

## Aday kaynaklar (kurulmamış)

Tarama tarihi: 2026-11-05. "Sürüm" sütunu, taradığımız commit'i gösterir.

| # | Kaynak | Tür | Lisans | Sürüm | Kategori | Öncelik |
|---|---|---|---|---|---|---|
| A1 | [heygen-com/hyperframes](https://github.com/heygen-com/hyperframes) | 9 skill + ~450 hazır blok | Apache 2.0 | `7bebcb9` (2026-11-05) | Video | Orta |
| A2 | [apify/apify-mcp-server](https://github.com/apify/apify-mcp-server) | MCP bağlantısı (skill değil) | MIT | `3577a57` (2026-11-05) | Veri / web | Orta |
| A3 | [nateherkai/scroll-craft](https://github.com/nateherkai/scroll-craft) | 1 skill (çok dosyalı) | MIT | `75d81f7` (2026-09-30) | Web / landing page | Orta |
| A4 | [blader/humanizer](https://github.com/blader/humanizer) | 1 skill | MIT | `0ef9fe5` (2026-10-28) | İçerik / yazı | ✅ Kuruldu |
| A5 | [addyosmani/agent-skills](https://github.com/addyosmani/agent-skills) | 25 skill | MIT | `301b02b` (2026-11-01) | Geliştirme + düşünme | ✅ 3'ü kuruldu, 22'si aday |
| A6 | [sindresorhus/awesome](https://github.com/sindresorhus/awesome) | Link listesi (622 başlık) | CC0 | `bc98e51` (2026-09-02) | Başvuru kaynağı | Düşük |

### A1 · HyperFrames (HeyGen)
HTML'i videoya dönüştürüyor: tanıtım filmleri, açıklayıcı videolar, dikey klipler, altyazı, grafik ve harita animasyonları.
- **Ana skill'ler** (`skills/`): `hyperframes` (önce bu okunur), `hyperframes-cli`, `hyperframes-registry` (~450 hazır blok), `media-use` (müzik, ses, görsel, seslendirme), `slideshow`, `figma`, `style-sampling`, `remotion-to-hyperframes`, `reverse-any-video`
- **Ek skill'ler** (`.claude/skills/`): `captions-overlay`, `changelog-video`, `cut-the-curve`, `motion-doctrine`, `oversized-cursor`, `seam-craft`
- **Bağımlılık:** HyperFrames CLI (Node/Bun) ve render ortamı. Bazı medya işleri HeyGen hesabı istiyor.
- **Not:** Repo büyük (~411 MB). Kurulumda sadece `skills/` klasörü alınır.

### A2 · Apify MCP
Web'den veri çekme, arama ve tarayıcı otomasyonu için binlerce hazır "Actor"a tek bağlantıdan erişim sağlıyor (Instagram, Google Maps, e-ticaret, SERP).
- **Kurulum şekli:** Skill olarak değil, claude.ai → Ayarlar → Connectors'tan özel bağlantı olarak eklenir: `https://mcp.apify.com` (OAuth).
- **Bağımlılık:** Apify hesabı. Actor'lar kullanım başına ücretli olabilir.
- **Repodaki skill'ler** (`dig`, `bug-triage`, `creating-mcp-agent-evals`) sadece bu reponun geliştiricileri için. Bize gerekmiyor.

### A3 · ScrollCraft
Kaydırdıkça hareketlenen premium landing page'ler üretiyor: katmanlı hero, sinematik geçişler, ayrı mobil kurgu, görsel doğrulama.
- **Skill:** `plugins/nateherk-design/skills/scroll-craft/` (460 satır + 5 yardımcı dosya)
- **Bağımlılık:** Görsel üretimi için isteğe bağlı kie.ai API anahtarı. Kendi fotoğraf ve videolarınla da çalışıyor.

### A4 · Humanizer
Yapay zekâ kokan metni anlamını değiştirmeden insan yazısına çeviriyor (Wikipedia'nın "Signs of AI writing" listesine dayanıyor).
- **Skill:** kökteki `SKILL.md` (397 satır, v3.1.0) + `agents/`, `scripts/`
- **Bağımlılık:** Yok. Kurulması en kolay olanı.
- **Not:** İngilizce metin için yazılmış. Türkçe içerikte kalıpların bir kısmı geçerli, gerekirse Türkçe uyarlaması yapılabilir.

### A5 · Agent Skills (Addy Osmani)
Yazılım geliştirme yaşam döngüsü için 25 skill. Bunların arasında genel işlerde de kullanılabilecek düşünme skill'leri var.
- **Genel kullanım:** `idea-refine` (fikir netleştirme), `interview-me` (ne istendiğini soru soru çıkarma), `planning-and-task-breakdown`, `doubt-driven-development` (kararları sorgulama), `documentation-and-adrs`
- **Geliştirme:** `spec-driven-development`, `incremental-implementation`, `test-driven-development`, `debugging-and-error-recovery`, `code-review-and-quality`, `code-simplification`, `api-and-interface-design`, `frontend-ui-engineering`, `browser-testing-with-devtools`, `performance-optimization`, `security-and-hardening`, `observability-and-instrumentation`, `git-workflow-and-versioning`, `ci-cd-and-automation`, `deprecation-and-migration`, `shipping-and-launch`, `source-driven-development`, `constraint-driven-development`, `context-engineering`, `using-agent-skills`
- **Bağımlılık:** Yok. Çoğu tek dosyalık skill.

### A6 · Awesome
Konulara göre derlenmiş "awesome" listelerinin ana listesi. Skill değil. Yeni araç ya da kaynak ararken bakılacak yer.

## Kategoriler

Claude skill'leri tek seviyeli bir klasörden (`.claude/skills/<skill>/`) yüklediği için kategoriler klasörle değil, yukarıdaki tablodaki "Kategori" sütunuyla tutulur:

- **içerik:** yazı, metin düzeltme
- **video:** video üretimi
- **web:** landing page, site
- **düşünme:** fikir, planlama, tasarım
- **geliştirme:** yazılım geliştirme

Bağlantılar (MCP) skill değildir. Kurulduklarında "Kurulu yetenekler" tablosuna "bağlantı" olarak eklenir.
