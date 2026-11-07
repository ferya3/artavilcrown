# artavilcrown.com

یک صفحه ساده که روی Cloudflare Workers اجرا می‌شود و یک عکس نشان می‌دهد.

## ساختار

```
public/
  index.html        صفحه اصلی
  404.html          صفحه «پیدا نشد»
  images/photo.jpg  عکس صفحه (این را با عکس خودتان جایگزین کنید)
wrangler.jsonc      تنظیمات Worker و دامنه
```

## عوض کردن عکس

عکس خودتان را با همین نام در `public/images/photo.jpg` بگذارید.
اگر نام یا پسوند دیگری دارد (مثلاً `my.png`)، در `public/index.html` مقدار `src` تگ `<img>` را هم عوض کنید.

## اجرا روی کامپیوتر خودتان

```bash
npm install
npm run dev
```

بعد آدرس http://localhost:8787 را باز کنید.

## انتشار روی Cloudflare

پیش‌نیاز: دامنه `artavilcrown.com` باید در حساب Cloudflare شما اضافه شده باشد
(nameserverهای دامنه روی Cloudflare تنظیم شده باشند).

### روش ۱: از کامپیوتر خودتان

```bash
npx wrangler login
npm run deploy
```

### روش ۲: اتصال مستقیم گیت‌هاب در داشبورد Cloudflare

در داشبورد Cloudflare به **Workers & Pages → Create → Import a repository** بروید،
این مخزن را انتخاب کنید و دستور Deploy را `npx wrangler deploy` بگذارید.
از این به بعد هر push روی شاخه اصلی، سایت را خودکار به‌روز می‌کند.

با `deploy`، دامنه‌های `artavilcrown.com` و `www.artavilcrown.com` به‌صورت Custom Domain
به Worker وصل می‌شوند و Cloudflare رکورد DNS و گواهی SSL را خودش می‌سازد.
اگر از قبل برای این دامنه‌ها رکورد DNS (مثلاً A یا CNAME) دارید، اول آن‌ها را پاک کنید.
