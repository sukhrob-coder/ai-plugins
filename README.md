# Aquasoft plugin marketplace

Bu repo Aquasoft CRM plugini uchun Claude Code va Codex (ChatGPT) marketplace’i.
Plugin ulangan tashkilotdagi mijozlar, manzillar, buyurtmalar, to‘lovlar, yalpi
sotuv va joriy qarzdorlarni faqat o‘qiydi. Fayllar backend reposidagi
`plugins/aquasoft/scripts/build.py` orqali generatsiya qilinadi; bu yerda qo‘lda
tahrir qilmang.

Repo: https://github.com/sukhrob-coder/ai-plugins

Claude Code:

```bash
claude plugin marketplace add sukhrob-coder/ai-plugins
claude plugin install aquasoft@aquasoft
```

Claude Code ichida: `/plugin marketplace add sukhrob-coder/ai-plugins`, so‘ng
`/plugin install aquasoft@aquasoft`. `/mcp` menyusida Aquasoft’ni autentifikatsiya qiling.
Yangilash: `claude plugin marketplace update aquasoft`.

Codex / ChatGPT desktop:

```bash
codex plugin marketplace add sukhrob-coder/ai-plugins
codex plugin add aquasoft@aquasoft
```

O‘rnatishda Aquasoft OAuth oynasi ochiladi. Yangilash:
`codex plugin marketplace upgrade aquasoft`.

Har bir foydalanuvchi o‘z Aquasoft hisobi bilan kiradi. Parol yoki tokenni
suhbatga yozmang; paketda umumiy kalit yo‘q.

```text
.claude-plugin/marketplace.json   Claude Code katalogi
.agents/plugins/marketplace.json  Codex / ChatGPT katalogi
plugins/claude/aquasoft/          Claude plugin paketi
plugins/openai/aquasoft/          OpenAI portable plugin paketi
```
