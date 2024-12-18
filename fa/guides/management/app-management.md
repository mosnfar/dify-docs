# مدیریت برنامه

### ویرایش اطلاعات برنامه

پس از ایجاد یک برنامه، اگر می خواهید نام یا توضیحات برنامه را تغییر دهید، می توانید در گوشه سمت چپ بالای برنامه، روی "ویرایش اطلاعات" کلیک کنید تا نماد، نام یا توضیحات برنامه را ویرایش کنید.

<figure><img src="../../.gitbook/assets/image (92).png" alt=""><figcaption><p>ویرایش اطلاعات برنامه</p></figcaption></figure>

### کپی کردن برنامه

تمام برنامه ها از کپی کردن پشتیبانی می کنند. در گوشه سمت چپ بالای برنامه روی "کپی" کلیک کنید.

### تغییر به Orchestrate گردش کار

TODO 🚧

### صادر کردن برنامه

برنامه های ایجاد شده در Dify از صادرات به صورت فایل های DSL پشتیبانی می کنند و به شما اجازه می دهند فایل های پیکربندی را به طور آزادانه به تیم های دیگر Dify وارد کنید. می توانید از هر دو روش زیر برای صادرات فایل های DSL استفاده کنید:

* در صفحه "استودیو"، در دکمه منو برنامه روی "صادرات DSL" کلیک کنید
* پس از ورود به صفحه orchestration برنامه، در گوشه سمت چپ بالا روی "صادرات DSL" کلیک کنید

![](../../.gitbook/assets/export-dsl.png)

فایل DSL اطلاعات مجوز را که قبلاً در گره های [ابزار](../workflow/node/tools.md) پر شده است، مانند کلیدهای API برای سرویس های شخص ثالث، شامل نمی شود.

اگر متغیرهای محیطی حاوی متغیرهایی از نوع `Secret` باشند، هنگام صادرات فایل، اعلان ظاهر می شود که از شما می پرسد آیا اجازه صادرات این اطلاعات حساس را می دهید یا خیر.

![](../../.gitbook/assets/export-dsl-secret.png)

{% hint style="info" %}
Dify DSL یک استاندارد فایل مهندسی برنامه AI است که توسط Dify.AI در نسخه 0.6 و بعد از آن تعریف شده است. قالب فایل YML است. این استاندارد توضیحات اساسی برنامه، پارامترهای مدل، پیکربندی orchestration و سایر اطلاعات را پوشش می دهد.
{% endhint %}

### حذف برنامه

اگر می خواهید برنامه ای را حذف کنید، می توانید در گوشه سمت چپ بالای برنامه روی "حذف" کلیک کنید.

{% hint style="info" %}
⚠️ حذف یک برنامه قابل برگشت نیست. تمام کاربران قادر به دسترسی به برنامه شما نخواهند بود و تمام راهنمایی ها، پیکربندی های orchestration و لاگ های موجود در برنامه حذف می شوند.
{% endhint %}


