در این صورت وضعیت خیلی بهتر است. از متن کارفرما این‌طور برداشت می‌شود که:

- Centrifugo را روی سرور نصب کرده.
- دامنه و SSL را تنظیم کرده.
- کانفیگ اولیه را انجام داده.
- دسترسی API را برای تست در اختیار شما گذاشته.
- انتظار دارد شما نحوه استفاده از Centrifugo را یاد بگیرید و روی پروژه پیاده‌سازی کنید.

یعنی الان شما در مرحله **Client Development و Backend Integration** هستید، نه DevOps و نصب سرور.

---

## اولین کاری که باید انجام دهید

قبل از هر چیزی مطمئن شوید که می‌توانید به سرور وصل شوید.

نصب SDK:

```bash
npm install centrifuge
```

سپس:

```javascript
import { Centrifuge } from "centrifuge";

const centrifuge = new Centrifuge("wss://rt.tizpo.ir/connection/websocket");

centrifuge.connect();

centrifuge.on("connected", (ctx) => {
  console.log("Connected", ctx);
});
```

اگر در Console پیام Connected ببینید یعنی اتصال برقرار شده است.

---

## مرحله دوم: Subscribe

طبق کانفیگی که فرستاده:

```json
"allow_subscribe_for_client": true
```

فعلاً می‌توانید روی هر کانالی Subscribe شوید.

مثلاً:

```javascript
const sub = centrifuge.newSubscription("test");

sub.on("publication", (ctx) => {
  console.log(ctx.data);
});

sub.subscribe();
```

---

## مرحله سوم: ارسال پیام تست

کارفرما این مقدار را داده:

```json
"http_api": {
  "key": "813W#SxFJrV@9smE"
}
```

می‌توانید با Postman تست کنید.

POST:

```text
https://rt.tizpo.ir/api/publish
```

Header:

```text
Authorization: apikey 813W#SxFJrV@9smE
Content-Type: application/json
```

Body:

```json
{
  "channel": "test",
  "data": {
    "message": "Hello Centrifugo"
  }
}
```

اگر همه چیز درست باشد، همان لحظه در مرورگر دریافت می‌شود.

---

## چیزی که پیشنهاد می‌کنم برای یادگیری انجام دهید

به ترتیب این مراحل را جلو بروید:

### پروژه 1

کانال عمومی

```text
news
```

هر پیامی منتشر شد در صفحه نمایش داده شود.

---

### پروژه 2

سیستم نوتیفیکیشن

کانال:

```text
notifications_1
```

ارسال:

```json
{
  "title": "سفارش ثبت شد"
}
```

نمایش به صورت Toast.

---

### پروژه 3

تاریخچه نوتیفیکیشن

چون History فعال است:

```json
"history_size":300
```

می‌توانید پیام‌های قبلی را دریافت کنید.

---

### پروژه 4

نمایش کاربران آنلاین

چون Presence فعال است:

```json
"presence":true
```

می‌توانید تعداد کاربران آنلاین را نمایش دهید.

---

## چیزی که باید حتماً یاد بگیرید

برای یک توسعه‌دهنده Frontend یا Full Stack این ۸ مورد تقریباً تمام Centrifugo است:

1. Connection
2. Reconnect
3. Subscription
4. Publication
5. Presence
6. History
7. JWT Authentication
8. Server-side Publish

بعد از یادگیری این‌ها تقریباً ۸۰ تا ۹۰ درصد قابلیت‌های Centrifugo را بلد خواهید بود.

یک نکته مهم: این کانفیگی که کارفرما داده برای **محیط آموزشی و تست** مناسب است. در پروژه واقعی تقریباً حتماً باید JWT و کانال‌های خصوصی را هم یاد بگیرید، چون سیستم نوتیفیکیشن کاربران بدون احراز هویت امن نخواهد بود.
