# artavilcrown.com

یک صفحه ساده که روی Cloudflare Workers اجرا می‌شود و یک عکس نشان می‌دهد.

## ساختار

```
public/
  index.html        صفحه اصلی
  404.html          صفحه «پیدا نشد»
  images/desktop.png  عکس دسکتاپ (افقی، پیشنهاد 1920x1080)
  images/mobile.png   عکس موبایل (عمودی، پیشنهاد 1080x1920)
wrangler.jsonc      تنظیمات Worker و دامنه
```

## عوض کردن عکس‌ها

سایت دو عکس دارد:

| فایل | کجا نمایش داده می‌شود | اندازه پیشنهادی |
|---|---|---|
| `public/images/desktop.png` | دسکتاپ و صفحه‌های افقی | 1920 × 1080 |
| `public/images/mobile.png` | موبایل و صفحه‌های عمودی | 1080 × 1920 |

1. عکس‌های خودتان را دقیقاً با همین اسم‌ها (حروف کوچک، پسوند `.png`) جایگزین این دو فایل کنید.
2. `npm run deploy` بزنید.

اگر عکس‌هایتان `jpg` هستند، یا به png تبدیلشان کنید یا در `public/index.html` اسم‌ها را عوض کنید.
عکس کل صفحه را پر می‌کند؛ اگر نسبتش با صفحه فرق کند لبه‌ها کمی بریده می‌شود.

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
