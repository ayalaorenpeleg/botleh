# בוטל'ה - אתר דף אחד

## איך לפרסם ב-GitHub Pages

1. היכנסי ל-GitHub וצרי repository חדש (למשל בשם `botleh`), Public.
2. העלי את הקובץ `index.html` לתוך ה-repository (Add file → Upload files).
3. בתפריט ה-repository: **Settings → Pages**.
4. תחת "Build and deployment", בחרי Source: **Deploy from a branch**, Branch: **main** (או master), תיקייה: **/ (root)**.
5. שמרי (Save). תוך דקה-שתיים יופיע קישור בפורמט:
   `https://<שם-המשתמש-שלך>.github.io/botleh/`

## עדכון כתובת ה-Webhook

בתוך `index.html`, קרוב לסוף הקובץ, יש שורה:

```js
const WEBHOOK_URL = "https://YOUR-N8N-INSTANCE/webhook/botleh-chat";
```

יש להחליף אותה בכתובת ה-Production Webhook האמיתית מ-n8n (מופיעה ב-workflow, ב-node ה-Webhook, אחרי שה-workflow מוגדר כ-Active). לאחר העדכון - שמרי, והעלי שוב את הקובץ ל-GitHub (או ערכי ישירות בממשק העריכה של GitHub).

## מה בקובץ

- HTML + CSS + JS מלאים בקובץ אחד, בלי תלות בשירות חיצוני מלבד Google Fonts ו-n8n.
- שולח POST עם השדות: `eventType`, `recipientName`, `relationship`, `personalDetail`, `senderName`, `userId`, `chatId`.
- מצפה לתשובה בפורמט: `{ "greeting": "...", "imageUrl": "..." }` (imageUrl אופציונלי).
- `userId` ו-`chatId` נשמרים ב-localStorage של הדפדפן, כך שאותו משתמש יזוהה בפניות חוזרות (למנגנון מניעת חזרה על ברכות).
