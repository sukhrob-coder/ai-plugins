# AquaSoft plugin marketplace

Bu repo AquaSoft CRM plugini uchun Claude Code va Codex (ChatGPT) marketplace’i.
`0.3.0` versiyasi ulangan tashkilotdagi mijozlar, buyurtmalar, to‘lovlar, moliya,
haydovchi profillari, topshiriqlar va omborni o‘qiydi; alohida OAuth ruxsati bilan
topshiriq yaratadi va owner tasdiqlagan Telegram bot xabarlarini yuboradi.
Fayllar backend reposidagi
`plugins/aquasoft/scripts/build.py` orqali generatsiya qilinadi; bu yerda qo‘lda
tahrir qilmang.

Repo: https://github.com/sukhrob-coder/ai-plugins

Claude Code:

```bash
claude plugin marketplace add sukhrob-coder/ai-plugins
claude plugin install aquasoft@aquasoft
```

Claude Code ichida: `/plugin marketplace add sukhrob-coder/ai-plugins`, so‘ng
`/plugin install aquasoft@aquasoft`. `/mcp` menyusida AquaSoft’ni autentifikatsiya qiling.
Yangilash: `claude plugin marketplace update aquasoft`.

Codex / ChatGPT desktop:

```bash
codex plugin marketplace add sukhrob-coder/ai-plugins
codex plugin add aquasoft@aquasoft
```

O‘rnatishda AquaSoft OAuth oynasi ochiladi. Yangilash:
`codex plugin marketplace upgrade aquasoft`.

Har bir foydalanuvchi o‘z AquaSoft hisobi bilan kiradi. Parol yoki tokenni
suhbatga yozmang; paketda umumiy kalit yo‘q.

## Yangi ruxsatlar va customer bot

Claude paketi `mcp:crm:read mcp:tasks:write mcp:customer-bot:write` scope’larini
so‘raydi. OpenAI portable paket OAuth’ni server discovery va tool metadata orqali
aniqlaydi. Eski read-only ulanishda qo‘shimcha OAuth consent kerak; tokenni refresh
qilishning o‘zi yetarli emas. Klient qo‘shimcha ruxsat oynasini ko‘rsatmasa,
AquaSoft ulanishini qayta autentifikatsiya qiling va kerakli yozish ruxsatlarini
tasdiqlang. Backend ruxsatlari barcha chaqiruvlarda tekshiriladi.

Customer bot boshqaruvi faqat tashkilotning `admin` (owner/director) roli va
`customer_app` tarif ruxsati bilan ishlaydi. Bot havolasi va tayyor taklif matni
qo‘lda ulashiladi. Mijozlarga matn, rasm yoki fayl yuborishda avval draft va aniq
oluvchilar ko‘rsatiladi, keyin foydalanuvchi tasdiqlagan draft yuboriladi.
Media uchun ommaviy HTTPS havola yoki shu botga tegishli Telegram `file_id` kerak.
SMS va lokal fayl yuklash qo‘llanmaydi. `sent` Telegram qabul qilganini bildiradi,
mijoz o‘qiganini emas. `unknown` natijani avtomatik qayta yuborish mumkin emas.

Paketdagi 3 ta skill 28 ta MCP amalini qamraydi: `customer-read`,
`crm-operations`, `customer-bot`. Paket yangilanishi backend deploy yoki haqiqiy
klientda yuborish muvaffaqiyatini anglatmaydi.

```text
.claude-plugin/marketplace.json   Claude Code katalogi
.agents/plugins/marketplace.json  Codex / ChatGPT katalogi
plugins/claude/aquasoft/          Claude plugin paketi
plugins/openai/aquasoft/          OpenAI portable plugin paketi
```
