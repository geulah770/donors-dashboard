# דשבורד תורמי הדינר

דף HTML יחיד (`index.html`) שקורא וכותב לגיליון Google Sheets דרך Sheets API. ההרשאות נקבעות בגוגל: רק חשבון עם הרשאת עריכה בגיליון יכול לטעון ולשנות.

## הגדרה
1. ב-Google Cloud: להפעיל Google Sheets API וליצור OAuth Client מסוג Web application.
2. Authorized JavaScript origins: כתובת האתר (למשל `https://donors-dinner-dashboard.vercel.app`).
3. Authorized redirect URIs: כתובת האתר עם סלאש בסוף.
4. ב-Vercel: משתנה סביבה `GOOGLE_CLIENT_ID` עם ה-Client ID, ואז Redeploy.
5. מסך ההסכמה במצב Testing: להוסיף את חברי הצוות ב-Test users.

`SHEET_ID` ו-`TAB` מוגדרים בראש הסקריפט ב-`index.html`.
