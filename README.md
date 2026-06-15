# Petlio Web Sitesi — Yayınlama Rehberi

Bu klasör Petlio'nun tanıtım sitesi ve yasal sayfalarını içerir. Saf statik
HTML/CSS — derleme gerektirmez, doğrudan herhangi bir statik hosting'e yüklenir.

## Dosyalar
- `index.html` — Ana tanıtım sayfası (özellikler, türler, ücretsiz/reklam modeli, diller, indirme)
- `privacy.html` — Gizlilik Politikası  → Play Console + AdMob + App Store **zorunlu URL**
- `terms.html` — Kullanım Koşulları
- `delete-data.html` — Veri/Hesap Silme  → Play Console **zorunlu URL**
- `app-ads.txt` — AdMob yetkili satıcı doğrulaması (publisher pub-5936273575442919)
- `assets/` — logo, tür görselleri, stil dosyası


## Görseller hakkında
- App ikonu (favicon, apple-touch, indirme bölümü, paylaşım): `assets/app_icon.png` —
  yüklediğin orijinal 4096px ikondan üretildi (512/192/64 boyutları).
- Hero halkası ve "her tür" bölümü: `assets/dog|cat|bird|fish|turtle.webp`
- Breed kütüphanesi: `assets/breeds/` (14 cins, orijinal Breeds.zip'ten optimize edildi)
- Header/footer logosu: `assets/petlio_mark.png`
İkonu değiştirmek istersen yeni dosyayı aynı isimlerle koyman yeterli.

## E-posta adresini değiştirmek
Şu an her yerde `petlio.team@gmail.com` yazılı. Başka bir adres kullanacaksan
tüm dosyalarda toplu değiştir (find & replace):
  petlio.team@gmail.com  →  yeni adres
(4 HTML dosyasında geçer: index, privacy, terms, delete-data)

═══════════════════════════════════════════════════════════════
## AŞAMA 1 — GitHub Pages'te ücretsiz yayınla
═══════════════════════════════════════════════════════════════

1. GitHub'da yeni bir repo aç:  petlio-web  (public olmalı — Pages ücretsiz
   sürümü public ister) ya da private + Pages destekli plan.

2. Bu klasördeki TÜM dosyaları repo köküne yükle (index.html kökte olmalı).
   Windows PowerShell ile:
       cd petlio-site
       git init
       git add .
       git commit -m "Petlio web sitesi"
       git branch -M main
       git remote add origin https://github.com/KULLANICI_ADIN/petlio-web.git
       git push -u origin main

3. GitHub'da repo → Settings → Pages:
       Source: Deploy from a branch
       Branch: main  /  (root)
       Save

4. 1-2 dakika sonra siten yayında olur:
       https://KULLANICI_ADIN.github.io/petlio-web/

5. Bu URL'leri not al — formlarda kullanacaksın:
       Gizlilik:     https://KULLANICI_ADIN.github.io/petlio-web/privacy.html
       Veri silme:   https://KULLANICI_ADIN.github.io/petlio-web/delete-data.html
       Koşullar:     https://KULLANICI_ADIN.github.io/petlio-web/terms.html

NOT: app-ads.txt'in çalışması için sitenin AdMob'daki mağaza/web alanıyla
eşleşmesi gerekir; tam etki domain bağlandıktan sonra netleşir (Aşama 2).

═══════════════════════════════════════════════════════════════
## AŞAMA 2 — Google'dan domain alıp bağla (ör. petlio.app)
═══════════════════════════════════════════════════════════════

1. Domain satın al:
   - Google Domains kapandı; Google'ın yönlendirdiği **Squarespace Domains**
     veya Cloudflare/Namecheap üzerinden petlio.app / petlio.com al.

2. GitHub repo → Settings → Pages → "Custom domain" kutusuna domaini yaz
   (ör. www.petlio.app), Save. GitHub repoya bir `CNAME` dosyası ekler.

3. Domain sağlayıcının DNS panelinde kayıtları gir:
   - www için CNAME →  KULLANICI_ADIN.github.io
   - kök (apex) için A kayıtları (GitHub Pages IP'leri):
         185.199.108.153
         185.199.109.153
         185.199.110.153
         185.199.111.153

4. DNS yayılınca (birkaç saat) GitHub Pages → "Enforce HTTPS" işaretle.

5. Artık temiz URL'lerin olur:
       https://petlio.app/privacy.html
       https://petlio.app/delete-data.html
       https://petlio.app/app-ads.txt

6. Domain bağlanınca formlardaki gizlilik URL'lerini bu yeni adreslerle
   güncelle (AdMob, Play Console, App Store Connect).

═══════════════════════════════════════════════════════════════
## Bu URL'ler nereye girilecek (checklist bağlantısı)
═══════════════════════════════════════════════════════════════
- AdMob → Privacy & messaging → European regulations → Privacy policy URL
      = privacy.html
- Play Console → App content → Privacy policy
      = privacy.html
- Play Console → App content → Data deletion
      = delete-data.html
- App Store Connect → App Privacy → Privacy Policy URL
      = privacy.html

## Güncelleme
İçeriği değiştirmek için ilgili .html dosyasını düzenle, tekrar
`git add . && git commit && git push` yap. GitHub Pages otomatik yeniler.
