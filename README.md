# GYMbos — reklama sayti

Telegram’dagi [@gym_bosbot](https://t.me/gym_bosbot) ilovasiga olib keluvchi statik sayt:
ilova imkoniyatlari, «3 qadam», interaktiv kalkulyatorlar (kaloriya va oqsil, milliy taomlar,
mushaklar xaritasi, kuch darajasi), ilmiy manbalar, savol-javob.

- Sayt manzili: https://nshakhobiddin.github.io/gymbos.uz/
- Ilova (brauzerda): https://nshakhobiddin.github.io/kachok.uz/
- Barcha tugmalar `https://t.me/gym_bosbot?startapp=site_…` ni ochadi, shuning uchun
  foydalanuvchi qaysi tugmadan kelgani botda ko‘rinadi (`site_hero`, `site_kkal`, `site_taom` …).

Server kerak emas: hamma fayl tayyor, yo‘llar nisbiy.

## Saytni yoqish (GitHub Pages, bir marta)

1. GitHub’da repo → **Settings → Pages**.
2. **Source:** «Deploy from a branch».
3. **Branch:** saytni o‘z ichiga olgan branch (`main`), papka **/ (root)** → **Save**.
4. 1–2 daqiqadan keyin sayt https://nshakhobiddin.github.io/gymbos.uz/ da ochiladi.

## O‘z domeningizni ulash (masalan, gymbos.uz)

1. Ildizga `CNAME` faylini qo‘shing, ichida bitta qator: `gymbos.uz`.
2. Fayllardagi manzilni almashtiring (Telegram’dagi havola rasmi va Google uchun):

   ```bash
   sed -i 's#https://nshakhobiddin.github.io/gymbos.uz#https://gymbos.uz#g' index.html maxfiylik.html sitemap.xml robots.txt
   ```

3. Domen sotib olingan joyda (DNS sozlamalari) quyidagilarni yozing:
   - `A` yozuvlar, nom `@`: `185.199.108.153`, `185.199.109.153`, `185.199.110.153`, `185.199.111.153`
   - `CNAME` yozuv, nom `www`: `nshakhobiddin.github.io`
4. **Settings → Pages → Custom domain** ga `gymbos.uz` ni yozing, DNS tekshiruvidan o‘tgach
   **Enforce HTTPS** ni yoqing.

## Matn yoki dizaynni o‘zgartirish

Bu papkada faqat yig‘ilgan (build) fayllar bor. Manba kodi `kachok.uz` reposida, `site/` papkasida.

```bash
SITE_URL=https://nshakhobiddin.github.io/gymbos.uz npm run build:site
```

Natija `dist-site/` papkasiga chiqadi; uning ichidagi hamma narsani shu repoga ko‘chiring.

## Tarkib

| Fayl / papka | Nima |
| --- | --- |
| `index.html` | Bosh sahifa (kalkulyatorlar bilan) |
| `maxfiylik.html` | Maxfiylik va foydalanish shartlari |
| `assets/`, `fonts/` | Sayt kodi, uslublar, shriftlar |
| `shots/` | Ilova ekranlari |
| `thumbs/` | Mashq rasmlari (mushaklar bo‘limi) |
| `bodymap/` | Tana xaritasi (CC BY-SA 4.0, `bodymap/LICENSE.md`) |
| `og.png` | Havola ulashilganda chiqadigan rasm (1200×630) |
| `sitemap.xml`, `robots.txt` | Qidiruv tizimlari uchun |
