# GYMbos — reklama sayti

Telegram’dagi [@gym_bosbot](https://t.me/gym_bosbot) ilovasiga olib keluvchi statik sayt:
ilova imkoniyatlari, «3 qadam», interaktiv kalkulyatorlar (kaloriya va oqsil, milliy taomlar,
mushaklar xaritasi, kuch darajasi), ilmiy manbalar, savol-javob.

- Sayt manzili: https://gymbos.uz/
- Ilova (brauzerda): https://nshakhobiddin.github.io/kachok.uz/
- Barcha tugmalar `https://t.me/gym_bosbot?startapp=site_…` ni ochadi, shuning uchun
  foydalanuvchi qaysi tugmadan kelgani botda ko‘rinadi (`site_hero`, `site_kkal`, `site_taom` …).

Server kerak emas: hamma fayl tayyor, yo‘llar nisbiy.

## Saytni yoqish (GitHub Pages, bir marta)

1. GitHub’da repo → **Settings → Pages**.
2. **Source:** «Deploy from a branch».
3. **Branch:** `main`, papka **/ (root)** → **Save**.
4. **Custom domain** maydonida `gymbos.uz` turadi (u `CNAME` faylidan olinadi).

## Domen DNS yozuvlari (sayt.uz → gymbos.uz → «DNS-серверы и зонные записи» → «Изменить»)

DNS serverlari o‘zgarmaydi (`ns8.sayt.uz`, `dns8.sayt.uz`), faqat zona yozuvlari qo‘shiladi.
`@` uchun avvaldan turgan boshqa `A` yozuv (masalan, «parkovka» sahifasi) bo‘lsa, uni o‘chiring.

| Turi | Nom (host) | Qiymat |
| --- | --- | --- |
| A | @ | 185.199.108.153 |
| A | @ | 185.199.109.153 |
| A | @ | 185.199.110.153 |
| A | @ | 185.199.111.153 |
| CNAME | www | nshakhobiddin.github.io |

DNS tarqalishi bir necha daqiqadan bir necha soatgacha olishi mumkin. Keyin
**Settings → Pages** da DNS tekshiruvi yashil bo‘lgach, **Enforce HTTPS** ni yoqing.

## Matn yoki dizaynni o‘zgartirish

Bu papkada faqat yig‘ilgan (build) fayllar bor. Manba kodi `kachok.uz` reposida, `site/` papkasida.

```bash
SITE_URL=https://gymbos.uz npm run build:site
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
| `CNAME` | GitHub Pages uchun domen nomi (`gymbos.uz`) |
