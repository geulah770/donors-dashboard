# דשבורד תורמי הדינר

דף HTML יחיד (`index.html`) שקורא וכותב לגיליון Google Sheets דרך Sheets API. ההרשאות נקבעות בגוגל: רק חשבון עם הרשאת עריכה בגיליון יכול לטעון ולשנות.

## הגדרה
1. ב-Google Cloud: להפעיל Google Sheets API וליצור OAuth Client מסוג Web application.
2. Authorized JavaScript origins: כתובת האתר (למשל `https://donors-dinner-dashboard.vercel.app`).
3. Authorized redirect URIs: כתובת האתר עם סלאש בסוף.
4. Authorized redirect URIs: `https://<הדומיין>/api/auth/callback`.
5. ב-Vercel, משתני סביבה (ואז Redeploy): `GOOGLE_CLIENT_ID`, `GOOGLE_CLIENT_SECRET`, `SESSION_SECRET` (מחרוזת אקראית ארוכה). אופציונלי: `APP_URL` לכתובת קבועה.
6. כדי שהחיבור יחזיק חודשים: ב-Audience לעבור ל-In production. במצב Testing גוגל מבטלת את ההתחברות אחרי 7 ימים.

## איך ההתחברות עובדת
התחברות בקוד הרשאה בצד שרת (`api/auth/*`). אסימון הרענון נשמר מוצפן בעוגייה HttpOnly ל-60 יום (מתחדש בכל שימוש), והדפדפן מקבל רק אסימון גישה קצר. התנתקות מבטלת את האסימון בגוגל ומוחקת את העוגייה.
7. מסך ההסכמה במצב Testing: להוסיף את חברי הצוות ב-Test users.

`SHEET_ID` ו-`TAB` מוגדרים בראש הסקריפט ב-`index.html`.
