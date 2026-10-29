# MF.Yuksak Travel — umumiy baza va joylash

## 1. Ilovani joylash
Papkadagi hamma faylni Netlify Drop (app.netlify.com/drop), GitHub Pages yoki Cloudflare Pages'ga joylang. Hosting HTTPS bo‘lishi shart (bularning hammasida shunday).

## 2. Firebase loyihasi (bepul daraja)
1. console.firebase.google.com → "Add project" → nom bering (Google Analytics kerak emas).
2. Build → Authentication → Get started → "Email/Password" ni yoqing.
3. Authentication → Users → "Add user": har bir xodim uchun email va parol yarating.
4. Build → Firestore Database → "Create database" → o‘zingizga yaqin joyni tanlang.
5. Firestore → Rules bo‘limiga quyidagini qo‘yib "Publish" bosing:

```
rules_version = '2';
service cloud.firestore {
  match /databases/{db}/documents {
    match /{document=**} {
      allow read, write: if request.auth != null;
    }
  }
}
```

6. MUHIM: Authentication → Settings → User actions → "Enable create (sign-up)" ni O‘CHIRING. Aks holda begona odam o‘zi hisob ochib, ma’lumotingizni ko‘rishi mumkin.
7. Project settings (tishli g‘ildirak) → General → Your apps → Web (</>) → ilovani ro‘yxatdan o‘tkazing → ko‘rsatilgan `firebaseConfig` blokini nusxalang.
8. Kirishda domen xatosi chiqsa: Authentication → Settings → Authorized domains ga sayt domeningizni qo‘shing.

## 3. Ilovada ulash
Ilovani oching → Qiymat → "Umumiy baza (bulut)" → firebaseConfig'ni joylab "Ulash" → sahifa qayta ochiladi → email va parol bilan kiring.
Birinchi ulanishda qurilmadagi mavjud ma’lumot bulutga yuklanadi (bulut bo‘sh bo‘lsa). Keyingi xodimlar kirganda bulutdagi ma’lumotni oladi.
Har bir xodim ilovani o‘z telefoniga o‘rnatib, shu sozlamani bir marta joylaydi.

## Yangilash
Faylni almashtirsangiz, telefonlar internet borida yangi versiyani o‘zi oladi.
