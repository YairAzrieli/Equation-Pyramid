# דרישות RTL למשחק פירמידת המספרים

## תמיכה בעברית ו-RTL
- יש להוסיף תמיכה מלאה בכיוון RTL (ימין לשמאל) לכל הממשק
- כל הטקסט במשחק יהיה בעברית
- יש להשתמש בגופנים התומכים בעברית

## ספריות מומלצות
- **react-i18next**: לתמיכה בתרגום ובינאום
- **styled-components** או **emotion**: לסגנון CSS עם תמיכה ב-RTL
- **rtl-detect**: לזיהוי אוטומטי של כיוון הטקסט

## שינויים נדרשים ב-CSS
- הוספת `direction: rtl` לאלמנט השורש
- הוספת `text-align: right` לאלמנטי טקסט
- היפוך מיקום אלמנטים (למשל, תפריטים בצד ימין במקום בצד שמאל)
- התאמת שוליים ומרווחים לתמיכה ב-RTL

## התאמות נוספות
- היפוך אייקונים שכיווניים (כמו חצים)
- התאמת סדר הטאבים לכיוון RTL
- התאמת אנימציות לכיוון RTL

## דוגמת קוד בסיסי

```css
/* CSS בסיסי לתמיכה ב-RTL */
html, body {
  direction: rtl;
  text-align: right;
}

.pyramid-container {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.pyramid-row {
  display: flex;
  justify-content: center;
}

.number-cell {
  margin: 5px;
  padding: 10px;
  border-radius: 50%;
  cursor: pointer;
}
```

```jsx
// דוגמת קוד React לתמיכה ב-RTL
import { createContext, useContext, useState } from 'react';

// יצירת קונטקסט לשפה וכיוון
const RTLContext = createContext({
  isRTL: true,
  setRTL: () => {},
});

export const RTLProvider = ({ children }) => {
  const [isRTL, setRTL] = useState(true);
  
  return (
    <RTLContext.Provider value={{ isRTL, setRTL }}>
      <div dir={isRTL ? 'rtl' : 'ltr'}>
        {children}
      </div>
    </RTLContext.Provider>
  );
};

export const useRTL = () => useContext(RTLContext);
```
