# اضافه کردن یک ارائه دهنده جدید

### روش‌های پیکربندی ارائه دهنده

ارائه دهندگان از سه مدل پیکربندی پشتیبانی می‌کنند:

**مدل از پیش تعریف شده**

این نشان می‌دهد که کاربران فقط نیاز به پیکربندی اعتبارنامه‌های ارائه دهنده یکپارچه برای استفاده از مدل‌های از پیش تعریف شده در ارائه دهنده دارند.

**مدل قابل تنظیم**

کاربران باید برای هر مدل، پیکربندی اعتبارنامه‌ها را اضافه کنند. برای مثال، Xinference هم از LLM و هم از Text Embedding پشتیبانی می‌کند، اما هر مدل یک **model_uid** منحصر به فرد دارد. اگر می‌خواهید به هر دو متصل شوید، باید برای هر مدل یک **model_uid** پیکربندی کنید.

**دریافت از راه دور**

مشابه روش پیکربندی `predefined-model`، کاربران فقط نیاز به پیکربندی اعتبارنامه‌های ارائه دهنده یکپارچه دارند، و مدل‌ها با استفاده از اطلاعات اعتبارنامه از ارائه دهنده دریافت می‌شوند.

به عنوان مثال، با OpenAI، می‌توانیم چندین مدل را بر اساس gpt-turbo-3.5 تنظیم دقیق کنیم، همه در زیر یک **api_key** یکسان. هنگامی که به عنوان `fetch-from-remote` پیکربندی می‌شود، توسعه دهندگان فقط نیاز به پیکربندی یک **api_key** یکپارچه دارند تا به Dify Runtime اجازه دهند تا همه مدل‌های تنظیم دقیق شده توسعه دهنده را دریافت کند و به Dify متصل شود.

این سه روش پیکربندی می‌توانند **همزمان وجود داشته باشند**، به این معنی که یک ارائه دهنده می‌تواند از `predefined-model` + `customizable-model` یا `predefined-model` + `fetch-from-remote` و غیره پشتیبانی کند. این امر امکان استفاده از مدل‌های از پیش تعریف شده و مدل‌های دریافت شده از راه دور با اعتبارنامه‌های ارائه دهنده یکپارچه را فراهم می‌کند، و مدل‌های سفارشی اضافی در صورت اضافه شدن قابل استفاده هستند.

### دستورالعمل‌های پیکربندی

**اصطلاحات**

* `module`: یک `module` یک بسته Python است، یا به طور عامیانه‌تر، یک پوشه حاوی یک فایل `__init__.py` و فایل‌های `.py` دیگر.

**مراحل**

افزودن یک ارائه دهنده جدید عمدتاً شامل چندین مرحله است. در اینجا یک طرح مختصر برای ارائه درک کلی ارائه شده است. مراحل دقیق در زیر ارائه شده است.

* یک فایل YAML ارائه دهنده ایجاد کنید و آن را مطابق با [طرح ارائه دهنده](https://github.com/langgenius/dify/blob/main/api/core/model_runtime/docs/en_US/schema.md) بنویسید.
* کد ارائه دهنده را ایجاد کنید و یک `class` پیاده سازی کنید.
* `modules` نوع مدل مربوطه را در `module` ارائه دهنده ایجاد کنید، مانند `llm` یا `text_embedding`.
* فایل‌های کد با نام مشابه را در `module` مدل مربوطه ایجاد کنید، مانند `llm.py`، و یک `class` پیاده سازی کنید.
* اگر مدل‌های از پیش تعریف شده وجود دارد، فایل‌های YAML با نام مشابه را در `module` مدل ایجاد کنید، مانند `claude-2.1.yaml`، و آنها را مطابق با [نهاد مدل AI](https://github.com/langgenius/dify/blob/main/api/core/model_runtime/docs/en_US/schema.md#aimodelentity) بنویسید.
* کد تست را برای اطمینان از در دسترس بودن قابلیت‌های آن بنویسید.

#### بیایید شروع کنیم

برای افزودن یک ارائه دهنده جدید، ابتدا شناسه انگلیسی ارائه دهنده را مشخص کنید، مانند `anthropic`، و یک `module` با نام آن در `model_providers` ایجاد کنید.

در این `module`، باید پیکربندی YAML ارائه دهنده را ابتدا آماده کنیم.

**آماده سازی YAML ارائه دهنده**

با استفاده از `Anthropic` به عنوان مثال، اطلاعات اولیه ارائه دهنده، انواع مدل‌های پشتیبانی شده، روش‌های پیکربندی و قوانین اعتبارنامه را از پیش تنظیم کنید.

```YAML
provider: anthropic  # شناسه ارائه دهنده
label:  # نام نمایش ارائه دهنده، می تواند در انگلیسی en_US و چینی zh_Hans تنظیم شود. اگر zh_Hans تنظیم نشده باشد، به طور پیش فرض en_US استفاده می شود.
  en_US: Anthropic
icon_small:  # نماد کوچک ارائه دهنده، در دایرکتوری _assets در زیر دایرکتوری پیاده سازی ارائه دهنده مربوطه ذخیره می شود، همان استراتژی زبان به عنوان label
  en_US: icon_s_en.png
icon_large:  # نماد بزرگ ارائه دهنده، در دایرکتوری _assets در زیر دایرکتوری پیاده سازی ارائه دهنده مربوطه ذخیره می شود، همان استراتژی زبان به عنوان label
  en_US: icon_l_en.png
supported_model_types:  # انواع مدل‌های پشتیبانی شده، Anthropic فقط از LLM پشتیبانی می‌کند
- llm
configurate_methods:  # روش‌های پیکربندی پشتیبانی شده، Anthropic فقط از مدل‌های از پیش تعریف شده پشتیبانی می‌کند
- predefined-model
provider_credential_schema:  # قوانین اعتبارنامه ارائه دهنده، از آنجایی که Anthropic فقط از مدل‌های از پیش تعریف شده پشتیبانی می‌کند، باید قوانین اعتبارنامه یکپارچه ارائه دهنده را تعریف کرد
  credential_form_schemas:  # لیست آیتم‌های فرم اعتبارنامه
  - variable: anthropic_api_key  # نام متغیر پارامتر اعتبارنامه
    label:  # نام نمایش
      en_US: API Key
    type: secret-input  # نوع فرم، secret-input در اینجا نشان دهنده یک کادر ورودی اطلاعات رمزگذاری شده است، فقط اطلاعات ماسک شده را هنگام ویرایش نمایش می‌دهد.
    required: true  # آیا الزامی است
    placeholder:  # اطلاعات PlaceHolder
      zh_Hans: در اینجا API Key خود را وارد کنید
      en_US: Enter your API Key
  - variable: anthropic_api_url
    label:
      en_US: API URL
    type: text-input  # نوع فرم، text-input در اینجا نشان دهنده یک کادر ورودی متن است
    required: false
    placeholder:
      zh_Hans: در اینجا API URL خود را وارد کنید
      en_US: Enter your API URL
```

اگر ارائه دهنده متصل شده مدل‌های قابل تنظیم را ارائه می‌دهد، مانند `OpenAI` که مدل‌های تنظیم دقیق شده را ارائه می‌دهد، باید [`model_credential_schema`](https://github.com/langgenius/dify/blob/main/api/core/model_runtime/docs/en_US/schema.md) را اضافه کنیم. با استفاده از `OpenAI` به عنوان مثال:

```yaml
model_credential_schema:
  model: # نام مدل تنظیم دقیق شده
    label:
      en_US: Model Name
      zh_Hans: نام مدل
    placeholder:
      en_US: Enter your model name
      zh_Hans: نام مدل را وارد کنید
  credential_form_schemas:
  - variable: openai_api_key
    label:
      en_US: API Key
    type: secret-input
    required: true
    placeholder:
      zh_Hans: در اینجا API Key خود را وارد کنید
      en_US: Enter your API Key
  - variable: openai_organization
    label:
        zh_Hans: شناسه سازمان
        en_US: Organization
    type: text-input
    required: false
    placeholder:
      zh_Hans: در اینجا شناسه سازمان خود را وارد کنید
      en_US: Enter your Organization ID
  - variable: openai_api_base
    label:
      zh_Hans: پایه API
      en_US: API Base
    type: text-input
    required: false
    placeholder:
      zh_Hans: در اینجا پایه API خود را وارد کنید
      en_US: Enter your API Base
```

همچنین می توانید به [اطلاعات پیکربندی YAML](https://github.com/langgenius/dify/blob/main/api/core/model_runtime/docs/en_US/schema.md) در دایرکتوری‌های ارائه دهنده‌های دیگر در زیر دایرکتوری `model_providers` مراجعه کنید.

**پیاده سازی کد ارائه دهنده**

باید یک فایل Python با همان نام در زیر `model_providers` ایجاد کنیم، مانند `anthropic.py`، و یک `class` را پیاده سازی کنیم که از کلاس پایه `__base.provider.Provider` ارث بری می‌کند، مانند `AnthropicProvider`.

**ارائه دهندگان مدل سفارشی**

برای ارائه دهندگانی مانند Xinference که مدل‌های سفارشی را ارائه می‌دهند، این مرحله را می‌توان حذف کرد. فقط یک کلاس `XinferenceProvider` خالی ایجاد کنید و یک روش `validate_provider_credentials` خالی را پیاده سازی کنید. این روش در واقع استفاده نخواهد شد و فقط برای جلوگیری از خطاهای نمونه سازی کلاس انتزاعی است.

```python
class XinferenceProvider(Provider):
    def validate_provider_credentials(self, credentials: dict) -> None:
        pass
```

**ارائه دهندگان مدل از پیش تعریف شده**

ارائه دهندگان باید از کلاس پایه `__base.model_provider.ModelProvider` ارث بری کنند و روش `validate_provider_credentials` را برای اعتبارسنجی اعتبارنامه‌های یکپارچه ارائه دهنده پیاده سازی کنند. می‌توانید به [AnthropicProvider](https://github.com/langgenius/dify/blob/main/api/core/model_runtime/model_providers/anthropic/anthropic.py) مراجعه کنید.

```python
def validate_provider_credentials(self, credentials: dict) -> None:
    """
    اعتبارسنجی اعتبارنامه‌های ارائه دهنده
    می توانید از هر روش validate_credentials از نوع مدل یا روش validate را به صورت خودتان پیاده سازی کنید،
    مانند: گرفتن لیست مدل api

    اگر اعتبارسنجی ناموفق بود، یک استثنا را مطرح کنید

    :param credentials: اعتبارنامه‌های ارائه دهنده، فرم اعتبارنامه تعریف شده در `provider_credential_schema`.
    """
```

همچنین می توانید پیاده سازی `validate_provider_credentials` را ابتدا رزرو کنید و پس از پیاده سازی روش اعتبارسنجی اعتبارنامه مدل، از آن به طور مستقیم استفاده مجدد کنید.

**افزودن مدل‌ها**

[**افزودن مدل‌های از پیش تعریف شده**](https://docs.dify.ai/v/zh-hans/guides/model-configuration/predefined-model)**👈🏻**

برای مدل‌های از پیش تعریف شده، می توانیم با تعریف ساده یک فایل YAML و پیاده سازی کد تماس، آنها را متصل کنیم.

[**افزودن مدل‌های سفارشی**](https://docs.dify.ai/v/zh-hans/guides/model-configuration/customizable-model) **👈🏻**

برای مدل‌های سفارشی، فقط باید کد تماس را برای اتصال آنها پیاده سازی کنیم، اما پارامترهایی که آنها را اداره می‌کنند ممکن است پیچیده‌تر باشند.

***

#### تست کردن

برای اطمینان از در دسترس بودن ارائه دهنده/مدل متصل شده، هر روش نوشته شده باید کد تست ادغام مربوطه را در دایرکتوری `tests` داشته باشد.

با استفاده از `Anthropic` به عنوان مثال.

قبل از نوشتن کد تست، باید متغیرهای محیطی اعتبارنامه مورد نیاز برای تست ارائه دهنده را در `.env.example` اضافه کنید، مانند: `ANTHROPIC_API_KEY`.

قبل از اجرا، `.env.example` را در `.env` کپی کنید و سپس اجرا کنید.

**نوشتن کد تست**

یک `module` با همان نام ارائه دهنده در زیر دایرکتوری `tests` ایجاد کنید: `anthropic`، و همچنان `test_provider.py` و فایل‌های تست نوع مدل مربوطه را در این ماژول ایجاد کنید، مانند زیر:

```shell
.
├── __init__.py
├── anthropic
│   ├── __init__.py
│   ├── test_llm.py       # تست LLM
│   └── test_provider.py  # تست ارائه دهنده
```

کد تست را برای موقعیت‌های مختلف کد پیاده سازی شده در بالا بنویسید، و پس از قبولی در تست‌ها، کد را ارسال کنید.


