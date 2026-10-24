# עדכונים לאפליקציית "מסלול הטיפולים"

האפליקציה בודקת בכל פתיחה את הקובץ `version.json` שבמאגר הזה.
אם המספר `versionCode` כאן **גבוה** מהגרסה שמותקנת בטלפון, תופיע הודעת עדכון.

## איך מוציאים גרסה חדשה

1. **ב-Android Studio**, בקובץ `app/build.gradle.kts`, הגדל את המספרים:
   ```kotlin
   versionCode = 2          // היה 1
   versionName = "1.0.1"    // היה "1.0.0"
   ```
2. **בנה APK חתום:** Build ← Generate Signed App Bundle / APK ← APK ← release.
   - בפעם הראשונה: Create new... ליצירת מפתח חתימה. **שמור את קובץ המפתח והסיסמה!**
     בלי אותו מפתח בדיוק, לא תוכל לעדכן את האפליקציה בהמשך.
   - הקובץ ייווצר ב: `app/release/app-release.apk`
3. **כאן ב-GitHub:** Releases ← Draft a new release
   - Tag: `v1.0.1` (תואם ל-versionName)
   - גרור את `app-release.apk` לאזור הקבצים ← Publish release
4. **ערוך את `version.json`** (לחיצה על הקובץ ← סמל העיפרון):
   ```json
   "versionCode": 2,
   "versionName": "1.0.1",
   "apkUrl": "https://github.com/festarik-netizen/maslul-updates/releases/download/v1.0.1/app-release.apk",
   "releaseNotes": "מה השתנה"
   ```
   ← Commit changes

בפתיחה הבאה של האפליקציה תופיע הודעת העדכון.

## חשוב
- בפעם הראשונה צריך להתקין בטלפון את גרסת ה-**release** (מאותו מפתח חתימה), לא את גרסת ה-debug
  שנוצרת מכפתור ▶️. לגרסת debug יש שם חבילה אחר (`com.maslul.app.debug`), ועדכון release לא יחליף אותה.
- המאגר ציבורי. אל תעלה לכאן מידע על מטופלים.
