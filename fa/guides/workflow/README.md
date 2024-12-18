# گردش کار

### معرفی اولیه

گردش کارها با تقسیم کارهای پیچیده به مراحل کوچکتر (گره ها)، پیچیدگی سیستم را کاهش می‌دهند، وابستگی به مهندسی سریع و قابلیت‌های استنباط مدل را کاهش می‌دهند و عملکرد برنامه‌های LLM را برای وظایف پیچیده بهبود می‌بخشند. این امر همچنین باعث افزایش تعبیر پذیری، پایداری و تحمل خطای سیستم می‌شود.

گردش کارهای Dify به دو نوع تقسیم می‌شوند:

* **Chatflow**: برای سناریوهای مکالمه ای، از جمله خدمات مشتری، جستجوی معنایی و سایر برنامه‌های مکالمه ای که به منطق چند مرحله ای در ساخت پاسخ نیاز دارند، طراحی شده است.
* **Workflow**: برای سناریوهای اتوماسیون و پردازش دسته ای مناسب است، که برای ترجمه با کیفیت بالا، تجزیه و تحلیل داده ها، تولید محتوا، اتوماسیون ایمیل و موارد دیگر مناسب است.

<figure><img src="../../.gitbook/assets/image (156).png" alt=""><figcaption></figcaption></figure>

Chatflow برای رسیدگی به پیچیدگی شناخت نیت کاربر در ورودی زبان طبیعی، گره های درک پرسش را ارائه می‌دهد. در مقایسه با Workflow، پشتیبانی از ویژگی‌های Chatbot مانند سابقه مکالمه (حافظه)، پاسخ‌های با حاشیه نویسی و گره های پاسخ را اضافه می‌کند.

Workflow برای رسیدگی به منطق پیچیده تجاری در سناریوهای اتوماسیون و پردازش دسته ای، انواع مختلفی از گره های منطقی مانند گره های کد، گره های IF / ELSE، تبدیل الگو، گره های تکرار و موارد دیگر را ارائه می‌دهد. علاوه بر این، قابلیت‌هایی برای اقدامات زمان‌بندی شده و فعال شده توسط رویداد را برای تسهیل ساخت فرآیندهای خودکار ارائه می‌دهد.

### موارد استفاده رایج

* خدمات مشتری

با ادغام LLM در سیستم خدمات مشتری خود، می‌توانید پاسخ‌ها به سؤالات متداول را به طور خودکار انجام دهید و بار کار تیم پشتیبانی خود را کاهش دهید. LLM می‌تواند زمینه و نیت پرسش‌های مشتری را درک کند و پاسخ‌های مفید و دقیق را به موقع تولید کند.

* تولید محتوا

چه نیاز به ایجاد پست‌های وبلاگ، توضیحات محصول یا مواد بازاریابی داشته باشید، LLM می‌تواند با تولید محتوای با کیفیت بالا به شما کمک کند. کافیست یک طرح کلی یا موضوع ارائه دهید و LLM از پایگاه دانش گسترده خود برای تولید محتوای جذاب، آموزنده و ساختار یافته استفاده می‌کند.

* اتوماسیون وظایف

LLM را می‌توان با سیستم‌های مختلف مدیریت وظیفه مانند Trello، Slack و Lark ادغام کرد تا مدیریت پروژه و وظایف را خودکار کند. LLM با استفاده از پردازش زبان طبیعی می‌تواند ورودی کاربر را درک و تفسیر کند، وظایف ایجاد کند، وضعیت‌ها را به روز کند و بدون مداخله دستی اولویت‌ها را اختصاص دهد.

* تجزیه و تحلیل داده ها و گزارش دهی

LLM می‌تواند مجموعه داده‌های بزرگ را تجزیه و تحلیل کند و گزارش‌ها یا خلاصه‌ها تولید کند. LLM با ارائه اطلاعات مربوطه، می‌تواند روندها، الگوها و بینش‌ها را شناسایی کند و داده‌های خام را به اطلاعات قابل عمل تبدیل کند. این برای مشاغلی که به دنبال تصمیم‌گیری مبتنی بر داده هستند، بسیار ارزشمند است.

* اتوماسیون ایمیل

LLM را می‌توان برای نوشتن ایمیل، به‌روزرسانی‌های رسانه‌های اجتماعی و سایر اشکال ارتباطات استفاده کرد. LLM با ارائه یک طرح کلی مختصر یا نکات اصلی می‌تواند پیام‌های ساختار یافته، منسجم و متناسب با زمینه را تولید کند. این امر در زمان قابل توجهی صرفه‌جویی می‌کند و اطمینان می‌دهد که پاسخ‌های شما روشن و حرفه‌ای هستند.

### نحوه شروع

* با ساخت یک گردش کار از ابتدا یا استفاده از الگوهای سیستم برای کمک به شروع کار خود شروع کنید.
* با عملیات اساسی از جمله ایجاد گره‌ها روی بوم، اتصال و پیکربندی گره‌ها، اشکال‌زدایی گردش کار و مشاهده تاریخچه اجرا آشنا شوید.
* یک گردش کار را ذخیره و منتشر کنید.
* برنامه منتشر شده را اجرا کنید یا از طریق API با گردش کار تماس بگیرید.


