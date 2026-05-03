# cinematch-web

CinaMatch landing page + mağaza-zorunlu yasal sayfalar. Saf HTML/CSS, build adımı yok.

## Sayfalar

| URL | Amaç |
|---|---|
| `/index.html` | Landing — hero, özellikler, akış, SSS, indirme CTA |
| `/privacy.html` | Gizlilik politikası (KVKK + GDPR uyumlu metin) |
| `/terms.html` | Kullanıcı sözleşmesi (yaş, davranış, sorumluluk, içerik lisansı) |
| `/delete-account.html` | Hesap silme — uygulama içi adımlar + web talep formu (mailto) |
| `/support.html` | Destek e-postaları + geri bildirim formu + hızlı çözümler |

## Yerelde aç

```bash
cd cinematch-web
python3 -m http.server 5173
# → http://localhost:5173
```

Veya doğrudan `index.html`'i tarayıcıda aç (file:// — relatif assetler çalışır).

## Mağaza gereksinimleri için kullanım

App Store Connect ve Google Play Console içerisinde aşağıdaki alanları doldurman gerekir:

- **Privacy Policy URL** → `https://cinematch.app/privacy.html`
- **Account Deletion URL** (Apple zorunlu — Haziran 2022'den beri) → `https://cinematch.app/delete-account.html`
- **Support URL** → `https://cinematch.app/support.html`
- **Marketing URL / Website** → `https://cinematch.app/`

## Yayınlama

### GitHub Pages (en hızlı)
```bash
cd cinematch-web
gh repo create cinematch-web --public --source=. --push
gh repo edit --enable-pages --pages-branch=main
# → https://<user>.github.io/cinematch-web/
```

### Cloudflare Pages
1. GitHub'a push et.
2. Cloudflare Pages → "Create project" → repo seç.
3. Build command: `(boş)` · Output directory: `/`.

### Custom domain
DNS A/AAAA kayıtlarını static host'a yönlendir, host paneline `cinematch.app` ekle.

## Tasarım notları

- Renkler ve tipografi mobil app ile aynı (`bg1`, `ember`, `gold`, Inter font).
- Logo işareti CSS ile çizildi (`brand__mark` — daire + iç içe ember nokta).
- iOS/Android badge'leri stilize edilmiş placeholder'dır; resmi badge görsellerini Apple/Google indirme sayfalarından alıp `assets/`'e koyup `<img>` ile değiştirebilirsin.
- Form'lar şimdilik `mailto:` POST kullanıyor — backend bağlamak istersen `action`'ı değiştir.

## Tek dilden çoğa

Şu an TR-only. EN versiyonu istersen her sayfanın kopyasını `en/` klasörüne çıkarıp metinleri çevir; navigation linklerine "EN" toggle ekle.
