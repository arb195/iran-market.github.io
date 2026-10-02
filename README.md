<h1 dir="rtl" align="right">دادهٔ رایگان بازار ایران</h1>

<p dir="rtl" align="right">
فایل‌های JSON آماده برای قیمت دلار، طلا، سکه، ارز، رمزارز و تاریخچهٔ بازار ایران. داده‌ها هر ۳۰ دقیقه به‌روزرسانی می‌شوند و بدون ثبت‌نام، توکن یا SDK از طریق GitHub Pages و jsDelivr قابل دریافت‌اند.
</p>

<h2 dir="rtl" align="right">لینک‌های مستقیم</h2>

<table dir="rtl" align="right">
  <thead>
    <tr>
      <th align="right">فایل</th>
      <th align="right">کاربرد</th>
      <th align="right">GitHub Pages</th>
      <th align="right">CDN</th>
    </tr>
  </thead>
  <tbody>
    <tr><td><code>latest.json</code></td><td>همهٔ قیمت‌های فعلی به ریال</td><td><a href="https://iran-market.github.io/data/latest.json">مشاهده</a></td><td><a href="https://cdn.jsdelivr.net/gh/iran-market/iran-market.github.io@main/data/latest.json">jsDelivr</a></td></tr>
    <tr><td><code>latest-toman.json</code></td><td>همهٔ قیمت‌های فعلی به تومان</td><td><a href="https://iran-market.github.io/data/latest-toman.json">مشاهده</a></td><td><a href="https://cdn.jsdelivr.net/gh/iran-market/iran-market.github.io@main/data/latest-toman.json">jsDelivr</a></td></tr>
    <tr><td><code>popular.json</code></td><td>دلار، یورو، پوند، طلا، سکه و تتر</td><td><a href="https://iran-market.github.io/data/popular.json">مشاهده</a></td><td><a href="https://cdn.jsdelivr.net/gh/iran-market/iran-market.github.io@main/data/popular.json">jsDelivr</a></td></tr>
    <tr><td><code>symbols.json</code></td><td>فهرست کامل شناسه‌ها، نام‌ها و دسته‌بندی‌ها</td><td><a href="https://iran-market.github.io/data/symbols.json">مشاهده</a></td><td><a href="https://cdn.jsdelivr.net/gh/iran-market/iran-market.github.io@main/data/symbols.json">jsDelivr</a></td></tr>
    <tr><td><code>history/USD_IRR_FREE.json</code></td><td>تاریخچهٔ روزانه دلار آزاد</td><td><a href="https://iran-market.github.io/data/history/USD_IRR_FREE.json">مشاهده</a></td><td><a href="https://cdn.jsdelivr.net/gh/iran-market/iran-market.github.io@main/data/history/USD_IRR_FREE.json">jsDelivr</a></td></tr>
    <tr><td><code>history/GOLD_18K_IRR.json</code></td><td>تاریخچهٔ روزانه طلای ۱۸ عیار</td><td><a href="https://iran-market.github.io/data/history/GOLD_18K_IRR.json">مشاهده</a></td><td><a href="https://cdn.jsdelivr.net/gh/iran-market/iran-market.github.io@main/data/history/GOLD_18K_IRR.json">jsDelivr</a></td></tr>
    <tr><td><code>history/COIN_EMAMI_IRR.json</code></td><td>تاریخچهٔ روزانه سکه امامی</td><td><a href="https://iran-market.github.io/data/history/COIN_EMAMI_IRR.json">مشاهده</a></td><td><a href="https://cdn.jsdelivr.net/gh/iran-market/iran-market.github.io@main/data/history/COIN_EMAMI_IRR.json">jsDelivr</a></td></tr>
    <tr><td><code>history/USDT_IRR.json</code></td><td>تاریخچهٔ روزانه تتر</td><td><a href="https://iran-market.github.io/data/history/USDT_IRR.json">مشاهده</a></td><td><a href="https://cdn.jsdelivr.net/gh/iran-market/iran-market.github.io@main/data/history/USDT_IRR.json">jsDelivr</a></td></tr>
  </tbody>
</table>

<br clear="all">

<p dir="rtl" align="right">برای تازه‌ترین نسخه از GitHub Pages استفاده کنید؛ CDN ممکن است چند دقیقه cache داشته باشد.</p>

<h2 dir="rtl" align="right">راهنمای شناسه‌ها</h2>

<p dir="rtl" align="right">
شناسه‌های این مجموعه پایدار و مستقل از نام داخلی منبع هستند؛ برای نمونه <code>USD_IRR_FREE</code> شناسهٔ دلار بازار آزاد است. نام فارسی یا انگلیسی حدس زده نمی‌شود: هر جا نام معتبر در دادهٔ مرجع موجود نباشد مقدار نام در <code>symbols.json</code> برابر <code>null</code> است. فهرست کامل و توضیح قواعد را در <a href="SYMBOLS.md">راهنمای نمادها</a> ببینید.
</p>

<h2 dir="rtl" align="right">نمونهٔ JavaScript</h2>

```js
const response = await fetch('https://iran-market.github.io/data/popular.json');
const { data, meta } = await response.json();

const dollar = data.find((item) => item.symbol === 'USD_IRR_FREE');
console.log(`قیمت دلار: ${dollar.price.toLocaleString('fa-IR')} تومان`);
console.log(`آخرین به‌روزرسانی: ${meta.published_at}`);
```

<h2 dir="rtl" align="right">نمونهٔ Python</h2>

```python
import requests

payload = requests.get(
    "https://iran-market.github.io/data/history/USD_IRR_FREE.json",
    timeout=15,
).json()

for candle in payload["data"][-7:]:
    print(candle["date_jalali"], candle["close"])
```

<h2 dir="rtl" align="right">ساختار داده</h2>

<p dir="rtl" align="right">
فایل‌های قیمت شامل <code>symbol</code>، نام فارسی و انگلیسی، <code>price</code>، تغییر روزانه، بیشترین و کمترین، زمان UTC و تهران، وضعیت کهنگی داده و نام منبع هستند. فایل‌های تاریخچه کندل‌های روزانهٔ OHLC را از قدیمی به جدید ارائه می‌کنند. <code>meta.published_at</code> زمان انتشار فایل در این مخزن است.
</p>

<p dir="rtl" align="right">داشبورد، جست‌وجوی قیمت‌ها، راهنمای قابل جست‌وجوی شناسه‌ها و مثال‌های بیشتر در <a href="https://iran-market.github.io/">وب‌سایت پروژه</a> در دسترس است.</p>

<h2 dir="rtl" align="right">پایداری و منبع داده</h2>

<ul dir="rtl" align="right">
  <li>به‌روزرسانی خودکار: هر ۳۰ دقیقه</li>
  <li>فرمت: UTF-8 JSON</li>
  <li>منبع فعلی داده: TGJU</li>
  <li>قیمت‌ها صرفاً جهت اطلاع‌رسانی‌اند؛ پیش از استفادهٔ حساس یا مالی آن‌ها را راستی‌آزمایی کنید.</li>
</ul>

<h2 dir="rtl" align="right">مجوز</h2>

<p dir="rtl" align="right">کد رابط و مثال‌های این مخزن تحت مجوز MIT منتشر می‌شوند. دادهٔ بازار متعلق به تولیدکنندگان اصلی آن است.</p>
