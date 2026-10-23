# AquaSoft CRM va customer bot

Bu plugin ulangan tashkilotingizdagi mijozlarni qidirish, segment va jami soni
(xavf ostida, yo‘qotilgan, qarzdor), detail, manzillar,
buyurtmalar tarixi, to‘lov/qo‘lda yozilgan qarzlar, tashkilot buyurtmalari,
yalpi sotuv va joriy qarzdorlarni o‘qish uchun. `0.3.0` versiyasi moliya,
haydovchilarning joriy profillari, topshiriqlar va omborni o‘qish, ruxsatli
topshiriq yaratish va owner sifatida customer botni boshqarishni ham qamraydi.
Yalpi sotuvdan qaytarish va kredit-notalar ayrilmagan; uni sof tushum yoki foyda
deb qabul qilmang. Haydovchi performance/oylik statistikasi mavjud emas.

Ulanish manzili: `https://api-v2.aquasoft.uz/mcp`.
OAuth login oynasida AquaSoft hisobingiz bilan kirib, kerakli tashkilotga ruxsat
bering. Parol, access/refresh token yoki bot tokenini AI suhbatiga yozmang.
Har bir foydalanuvchi o‘z hisobini ulaydi; paketda umumiy kalit yo‘q.

| Ruxsat | Imkoniyat |
| --- | --- |
| `mcp:crm:read` | Mavjud CRM ruxsatlari bilan o‘qish |
| `mcp:tasks:write` | Topshiriq yaratish va xodimga bildirishnoma |
| `mcp:customer-bot:write` | Owner sifatida bot xabarini tayyorlash va tasdiqlab yuborish |

Claude konfiguratsiyasi uchala scope’ni so‘raydi va yangi consent oynasida ular
ko‘rsatiladi. OpenAI portable paket OAuth’ni server metadata va tool ruxsatlari
orqali aniqlaydi. Eski read-only ulanishga qo‘shimcha consent kerak; oddiy token
refresh yozish ruxsatini qo‘shmaydi. Klient qo‘shimcha ruxsat oynasini ochmasa,
ulanishni qayta autentifikatsiya qiling va kerakli scope’ni tasdiqlang. Server
ruxsatni bermagan bo‘lsa, plugin uning o‘rniga muvaffaqiyat da’vo qilmaydi.

Customer bot amallari faqat tashkilotning mavjud `admin` roli va `customer_app`
tarif ruxsati bilan ishlaydi. Bot havolasi va taklif matni qo‘lda ulashish uchun;
SMS yuborilmaydi. Tanlangan 1–1000 mijozga matn, rasm yoki fayl uchun avval
draft tayyorlanadi. Aniq matn/media, oluvchilar va soni ko‘rsatilgach, foydalanuvchi
alohida tasdiqlaydi; shundan keyin aynan o‘sha draft yuboriladi.

Rasm/fayl uchun ommaviy HTTPS havola yoki shu botning Telegram `file_id`si kerak;
lokal fayl yuklash mavjud emas. Botga ulanmagan mijozlar `skipped` bo‘ladi.
`queued` — navbatga qo‘yilgan, `sent` — Telegram qabul qilgan, `unknown` — natija
noaniq. O‘qilganlik haqida dalil yo‘q; noaniq xabar avtomatik qayta yuborilmaydi.

O‘rnatish (Claude Code): `/plugin marketplace add sukhrob-coder/ai-plugins`, so‘ng
`/plugin install aquasoft@aquasoft`.
Codex: `codex plugin marketplace add sukhrob-coder/ai-plugins`, so‘ng
`codex plugin add aquasoft@aquasoft`.

Claude Code’da paketni ochilgan papkadan `claude --plugin-dir /absolute/path/to/plugin`
orqali sinang; `/mcp` menyusida AquaSoft’ni autentifikatsiya qiling.
OpenAI paketida root `plugin.json` va `mcp.json` bor; uni plugin sinov/ulash
oqimi orqali o‘rnating va AquaSoft OAuth ruxsatini tasdiqlang.
Ilova versiyasi yoki workspace siyosati o‘rnatish usulini cheklashi mumkin.

Ro‘yxat natijalari sahifalangan. Keyingi sahifa mavjud bo‘lsa, javob butun
tarixni ifodalamaydi. Boshqa tashkilot kerak bo‘lsa, ulanish ruxsatini qayta
ko‘rib chiqing; so‘rovga tashkilot ID qo‘shib cheklovni chetlab o‘tib bo‘lmaydi.

Paket 28 ta amaliyotga mo‘ljallangan: `skills/customer-read` (9),
`skills/crm-operations` (13), `skills/customer-bot` (6). Eski server kamroq tool
qaytarsa, mavjud bo‘lmagan amalni simulyatsiya qilmang. Pluginni yangilash backendni
deploy qilmaydi va mavjud ulanishga yozish huquqini yashirincha bermaydi.
