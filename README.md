# Trendify Nexus V2

**A simple installer for Trendify Nexus V2**

Trendify Nexus V2 provides an installation workflow for setting up the required project components. Use the online installer below and follow the setup instructions in your preferred language.

<p align="center">
  <a href="https://trendv2.pages.dev/">
    <img src="https://img.shields.io/badge/🚀_OPEN_INSTALLER-Launch%20Installer-635BFF?style=for-the-badge" alt="Open Trendify Nexus Installer">
  </a>
</p>

<p align="center">
  <strong>Choose your language / انتخاب زبان</strong>
</p>

<p align="center">
  <a href="#english-guide">🇬🇧 English</a> ·
  <a href="#راهنمای-فارسی">🇮🇷 فارسی</a>
</p>

---

# English Guide

## 1. Open the Installer

Click the button below to open the online installer:

**[🚀 Launch Trendify Nexus Installer](https://trendv2.pages.dev/)**

The installer runs in your browser. Follow the on-screen instructions.

## 2. Requirements

Prepare the following before starting:

- A GitHub account and a GitHub Personal Access Token with the repository permissions required by the installer.
- A Cloudflare account and an API token with the permissions required to create and deploy Workers.
- Your Cloudflare Account ID.
- A Railway account for hosting the backend and TCP relay components.
- A PostgreSQL database for the backend.

Use tokens with only the permissions needed for installation. Never publish your tokens or commit them to a Git repository.

## 3. Run the Installer

1. Open the installer.
2. Enter your GitHub token.
3. Enter your Cloudflare API token.
4. Enter your Cloudflare Account ID.
5. Start the installation.
6. Wait for the installer to return its result.
7. Save the generated repository and deployment details.

Do not share installation results that contain private secrets.

## 4. Configure PostgreSQL

Create a PostgreSQL database using your database provider.

Copy the database connection URL and configure the backend's `DATABASE_URL` environment variable in Railway.

Use the connection URL supplied by your provider. Do not commit it to your repository or expose it publicly.

## 5. Configure Railway

Deploy the backend and relay components to Railway using the repositories and instructions provided by your project setup.

Configure the required environment variables according to the actual source code. These may include:

- `DATABASE_URL`
- `CF_TOKEN`
- `CF_ACCOUNT_ID`
- `PUBLIC_URL`
- `NEXUS_GATEWAY_SECRET`
- `RELAY_SECRET`
- `PORT`

The backend, relay, and gateway may require different variables. Do not assume that every variable belongs in every service.

Generate strong, private secrets. The backend gateway authentication secret and the relay authentication secret are separate values unless your implementation explicitly specifies otherwise.

## 6. Configure the Railway TCP Proxy

If the relay uses a Railway TCP Proxy:

1. Enable or create the TCP Proxy for the relay service.
2. Copy the public proxy hostname and port assigned by Railway.
3. Configure the gateway with the corresponding relay host and port variables required by your gateway source code.
4. Ensure the relay listener port matches the Railway service configuration.
5. Keep the relay secret consistent between the gateway and relay.

Use the actual hostname and port displayed by Railway. Do not use example values as production settings.

## 7. Verify the Deployment

After configuration:

- Confirm that the backend starts without errors.
- Confirm that PostgreSQL is reachable.
- Confirm that the relay starts and accepts authenticated connections.
- Confirm that the Cloudflare Worker is deployed and configured with the correct environment variables.
- Test the complete gateway-to-relay connection.
- Check Railway and Cloudflare logs if a service fails.

A successful installation response does not necessarily mean every manually configured service is fully operational.

## Security Notes

- Never publish GitHub or Cloudflare tokens.
- Never publish `DATABASE_URL` or authentication secrets.
- Do not commit `.env` files containing credentials.
- Review GitHub repository visibility before storing project source code.
- Rotate any credential that has been exposed.

---

# راهنمای فارسی

## ۱. ورود به Installer

برای باز کردن نصب‌کننده آنلاین روی دکمه زیر کلیک کن:

**[🚀 اجرای Installer ترندیفای نکسوس](https://trendv2.pages.dev/)**

نصب‌کننده داخل مرورگر اجرا می‌شود. مراحل نمایش‌داده‌شده را دنبال کن.

## ۲. موارد موردنیاز

قبل از شروع، این موارد را آماده کن:

- حساب GitHub و یک GitHub Personal Access Token با مجوزهای موردنیاز نصب‌کننده.
- حساب Cloudflare و یک API Token با مجوزهای لازم برای ساخت و انتشار Workerها.
- مقدار Cloudflare Account ID.
- حساب Railway برای میزبانی Backend و Relay.
- دیتابیس PostgreSQL برای Backend.

توکن‌ها را فقط با مجوزهای لازم بساز. هرگز آن‌ها را عمومی نکن یا داخل مخزن Git قرار نده.

## ۳. اجرای نصب‌کننده

۱. وارد Installer شو.

۲. توکن GitHub را وارد کن.

۳. توکن API کلادفلر را وارد کن.

۴. مقدار Cloudflare Account ID را وارد کن.

۵. روی دکمه شروع نصب بزن.

۶. منتظر بمان تا نتیجه نصب نمایش داده شود.

۷. اطلاعات مخزن ساخته‌شده و جزئیات استقرار را ذخیره کن.

اگر نتیجه نصب شامل Secret یا اطلاعات محرمانه است، آن را برای دیگران ارسال نکن.

## ۴. تنظیم PostgreSQL

از طریق سرویس‌دهنده دیتابیس خود یک دیتابیس PostgreSQL بساز.

آدرس اتصال دیتابیس را دریافت کن و آن را در متغیر محیطی `DATABASE_URL` سرویس Backend در Railway قرار بده.

از آدرس اتصال واقعی سرویس‌دهنده استفاده کن. این آدرس نباید در مخزن Git قرار بگیرد یا به‌صورت عمومی منتشر شود.

## ۵. تنظیم Railway

سرویس‌های Backend و Relay را با استفاده از مخازن و دستورالعمل‌های پروژه در Railway مستقر کن.

متغیرهای محیطی لازم را مطابق کد واقعی هر سرویس تنظیم کن. این متغیرها ممکن است شامل موارد زیر باشند:

- `DATABASE_URL`
- `CF_TOKEN`
- `CF_ACCOUNT_ID`
- `PUBLIC_URL`
- `NEXUS_GATEWAY_SECRET`
- `RELAY_SECRET`
- `PORT`

تمام این متغیرها لزوماً برای هر سرویس موردنیاز نیستند. تنظیمات Backend، Relay و Gateway را با یکدیگر اشتباه نگیر.

Secretهای قوی و محرمانه بساز. Secret احراز هویت Gateway در Backend و Secret ارتباط Relay دو مقدار مجزا هستند؛ مگر اینکه پیاده‌سازی پروژه صراحتاً روش دیگری را تعیین کرده باشد.

## ۶. تنظیم Railway TCP Proxy

اگر Relay از Railway TCP Proxy استفاده می‌کند:

۱. برای سرویس Relay یک TCP Proxy ایجاد یا فعال کن.

۲. آدرس عمومی Host و شماره Port اختصاص‌یافته توسط Railway را کپی کن.

۳. مقادیر Host و Port مربوط به Relay را در متغیرهای موردنیاز Gateway قرار بده.

۴. مطمئن شو پورت شنونده Relay با تنظیمات سرویس Railway مطابقت دارد.

۵. مقدار `RELAY_SECRET` در Gateway و Relay باید یکسان باشد.

از Host و Port واقعی نمایش‌داده‌شده در Railway استفاده کن؛ مقادیر نمونه برای استقرار واقعی مناسب نیستند.

## ۷. بررسی نهایی

پس از تنظیمات:

- مطمئن شو Backend بدون خطا اجرا می‌شود.
- اتصال Backend به PostgreSQL را بررسی کن.
- مطمئن شو Relay اجرا شده و اتصال احراز هویت‌شده را می‌پذیرد.
- انتشار Cloudflare Worker و متغیرهای محیطی آن را بررسی کن.
- ارتباط کامل Gateway با Relay را آزمایش کن.
- در صورت بروز خطا، لاگ‌های Railway و Cloudflare را بررسی کن.

نمایش موفقیت در Installer به‌تنهایی تضمین نمی‌کند که تمام سرویس‌هایی که نیاز به تنظیم دستی دارند، آماده کار هستند.

## نکات امنیتی

- توکن GitHub و Cloudflare را منتشر نکن.
- `DATABASE_URL` و Secretهای احراز هویت را محرمانه نگه دار.
- فایل `.env` حاوی اطلاعات ورود را در Git کامیت نکن.
- قبل از ذخیره کد، عمومی یا خصوصی بودن مخزن GitHub را بررسی کن.
- اگر اطلاعات محرمانه افشا شد، آن‌ها را تغییر بده.

---

## Support

If you encounter a problem, include the relevant error message and service logs when requesting help. Remove all tokens, passwords, database URLs, and private secrets first.

اگر با خطا مواجه شدی، هنگام درخواست راهنمایی متن خطا و لاگ مرتبط را ارسال کن؛ اما قبل از ارسال، تمام توکن‌ها، رمزها، آدرس دیتابیس و Secretهای محرمانه را حذف کن.
