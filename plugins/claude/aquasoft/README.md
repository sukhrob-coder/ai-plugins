# AquaSoft customer reads

Bu plugin ulangan tashkilotingizdagi mijozlarni qidirish, segment va jami soni
(xavf ostida, yo‘qotilgan, qarzdor), detail, manzillar,
buyurtmalar tarixi, to‘lov/qo‘lda yozilgan qarzlar, tashkilot buyurtmalari,
yalpi sotuv va joriy qarzdorlarni o‘qish uchun. Yozish amallari va haydovchilar
statistikasi mavjud emas. Yalpi sotuvdan qaytarish va kredit-notalar ayrilmagan;
uni sof tushum yoki foyda deb qabul qilmang.

Ulanish manzili: `https://api-v2.aquasoft.uz/mcp`.
OAuth login oynasida AquaSoft hisobingiz bilan kiring va faqat kerakli
tashkilotga o‘qish ruxsatini bering. Parol yoki tokenni AI suhbatiga yozmang.
Har bir foydalanuvchi o‘z hisobini ulaydi; paketda umumiy kalit yo‘q.

Claude Code’da paketni ochilgan papkadan `claude --plugin-dir /absolute/path/to/plugin`
orqali sinang; `/mcp` menyusida AquaSoft’ni autentifikatsiya qiling.
OpenAI paketida root `plugin.json` va `mcp.json` bor; uni plugin sinov/ulash
oqimi orqali o‘rnating va AquaSoft OAuth ruxsatini tasdiqlang.
Ilova versiyasi yoki workspace siyosati o‘rnatish usulini cheklashi mumkin.

Ro‘yxat natijalari sahifalangan. Keyingi sahifa mavjud bo‘lsa, javob butun
tarixni ifodalamaydi. Boshqa tashkilot kerak bo‘lsa, ulanish ruxsatini qayta
ko‘rib chiqing; so‘rovga tashkilot ID qo‘shib cheklovni chetlab o‘tib bo‘lmaydi.

Bu dastlabki test paketi. Katalogda nashr qilinganini yoki production OAuth
sinovidan o‘tganini paketning o‘zi tasdiqlamaydi. Logodagi suv belgisi vaqtinchalik
neytral grafika; nashrdan oldin egasi tasdiqlashi kerak.
Paket to‘qqiz vositali yangi release uchun; eski server kamroq vosita qaytarsa,
yetishmayotgan hisobotni avtomatik taxmin qilish o‘rniga serverni yangilash kerak.
