# 🚀 ការណែនាំការ Deploy

## លំដាប់ការ Deploy

---

## ១. រៀបចំ Google Sheets

1. បើក Google Sheets ថ្មី
2. បង្កើត **Sheet 1** → rename → **Reports**
3. Row 1 (Header) បញ្ចូល columns តាមលំដាប់:
```
timestamp | title | first_name | last_name | phone | room_no | building | sessions | centers | subjects | start_time | end_time | q1 | q2 | q3 | q4 | invig1 | invig2 | total_stu | total_abs | total_female | absent_list | observation_list | other_issues | overall_rating | telegram_id
```

4. បង្កើត **Sheet 2** → rename → **Settings**
5. Row 1 (Header):
```
title1 | title2 | centers | sessions | subjects | telegram_contact | timestamp
```
6. Row 2 (Data):
```
[ចំណងជើងទី១] | [ចំណងជើងទី២] | RULL,IFL | 31 មករា,1 កម្ភៈ ២០២៦ | Maths,Physic,Chemy | @ThavrithKH,+85569515488 | [ទទេ]
```

7. Copy **Sheet ID** ពី URL:
```
https://docs.google.com/spreadsheets/d/[SHEET_ID_នៅទីនេះ]/edit
```

---

## ២. Deploy Google Apps Script

1. បើក [script.google.com](https://script.google.com)
2. **New Project** → copy paste `Code.gs` ទាំងអស់
3. ប្តូរ `SHEET_ID` ដោយ ID ពីខាងលើ
4. **Deploy → New Deployment**
   - Type: **Web App**
   - Execute as: **Me**
   - Who has access: **Anyone**
5. Click **Deploy** → Copy **Web App URL**

---

## ៣. រៀបចំ Telegram Bot

### បង្កើត Bot:
1. Telegram → @BotFather → `/newbot`
2. ដាក់ឈ្មោះ (e.g. `Classroom Exam Report Bot`)
3. Copy **Bot Token**

### បង្កើត Mini App:
1. @BotFather → `/newapp`
2. ជ្រើស bot
3. Upload `index.html` (ឬ host នៅ GitHub Pages/Netlify)
4. Web App URL = hosting URL របស់ `index.html`

---

## ៤. Update index.html

បើក `index.html` ប្តូរ:
```javascript
const GAS_URL = "https://script.google.com/macros/s/[YOUR_ID]/exec";
```

---

## ៥. Host index.html (ជម្រើស)

### Option A — GitHub Pages (ឥតគិតថ្លៃ):
1. Create GitHub repo
2. Upload `index.html`
3. Settings → Pages → Deploy from main branch
4. URL: `https://[username].github.io/[repo]/`

### Option B — Netlify (ឥតគិតថ្លៃ):
1. [netlify.com](https://netlify.com) → Drag & drop `index.html`
2. URL ភ្លាមៗ

---

## ✅ Test Checklist

- [ ] Settings ផ្ទុកច្បាស់ (title, session, center, subject)
- [ ] Submit form → data នៅក្នុង Reports sheet
- [ ] Edit (ក្នុងម៉ោង) → update row
- [ ] Edit (ក្រោយ deadline) → error message
- [ ] Admin login password DEPO@2026
- [ ] Dashboard ឃើញ data real-time
- [ ] Filter by session/center/subject
- [ ] Export CSV
- [ ] Clear → auto backup sheet ត្រូវបង្កើត

---

## ⚠️ Important Notes

- **CORS**: GAS Web App ត្រូវ deploy ជា "Anyone" access
- **Telegram Mini App**: ត្រូវ HTTPS (GitHub Pages/Netlify ផ្តល់ HTTPS ដោយឥតគិតថ្លៃ)
- **Admin Password**: DEPO@2026 (អាចប្តូរក្នុង Code.gs)
- **Buffer Time**: 30 នាទីក្រោយ end_time (អាចប្តូរ `ADDITIONAL_TIME_MINUTES` ក្នុង Code.gs)
