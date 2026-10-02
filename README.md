# Iran Market Data — دادهٔ رایگان بازار ایران

داده‌های JSON آماده و رایگان برای قیمت دلار، طلا، سکه، ارزهای دیجیتال و تاریخچهٔ بازار ایران.
فایل‌ها هر ۳۰ دقیقه از سرویس **Iran Market API Core** به‌روزرسانی می‌شوند و بدون ثبت‌نام،
توکن یا SDK از طریق GitHub Pages و jsDelivr قابل استفاده‌اند.

## لینک‌های مستقیم

| فایل | کاربرد | GitHub Pages | CDN |
| --- | --- | --- | --- |
| `latest.json` | همهٔ قیمت‌های لحظه‌ای به ریال | [مشاهده](https://iran-market.github.io/data/latest.json) | [jsDelivr](https://cdn.jsdelivr.net/gh/iran-market/iran-market.github.io@main/data/latest.json) |
| `latest-toman.json` | همهٔ قیمت‌های لحظه‌ای به تومان | [مشاهده](https://iran-market.github.io/data/latest-toman.json) | [jsDelivr](https://cdn.jsdelivr.net/gh/iran-market/iran-market.github.io@main/data/latest-toman.json) |
| `popular.json` | دلار، طلا، سکه و تتر | [مشاهده](https://iran-market.github.io/data/popular.json) | [jsDelivr](https://cdn.jsdelivr.net/gh/iran-market/iran-market.github.io@main/data/popular.json) |
| `history/USD_IRR_FREE.json` | تاریخچهٔ روزانه دلار آزاد | [مشاهده](https://iran-market.github.io/data/history/USD_IRR_FREE.json) | [jsDelivr](https://cdn.jsdelivr.net/gh/iran-market/iran-market.github.io@main/data/history/USD_IRR_FREE.json) |
| `history/GOLD_18K_IRR.json` | تاریخچهٔ طلای ۱۸ عیار | [مشاهده](https://iran-market.github.io/data/history/GOLD_18K_IRR.json) | [jsDelivr](https://cdn.jsdelivr.net/gh/iran-market/iran-market.github.io@main/data/history/GOLD_18K_IRR.json) |
| `history/COIN_EMAMI_IRR.json` | تاریخچهٔ سکه امامی | [مشاهده](https://iran-market.github.io/data/history/COIN_EMAMI_IRR.json) | [jsDelivr](https://cdn.jsdelivr.net/gh/iran-market/iran-market.github.io@main/data/history/COIN_EMAMI_IRR.json) |
| `history/USDT_IRR.json` | تاریخچهٔ تتر به ریال | [مشاهده](https://iran-market.github.io/data/history/USDT_IRR.json) | [jsDelivr](https://cdn.jsdelivr.net/gh/iran-market/iran-market.github.io@main/data/history/USDT_IRR.json) |

> برای تازه‌ترین نسخه، GitHub Pages را استفاده کنید. CDN ممکن است چند دقیقه cache داشته باشد.

## نمونهٔ JavaScript

```js
const response = await fetch('https://iran-market.github.io/data/popular.json');
const { data, meta } = await response.json();

const dollar = data.find((item) => item.symbol === 'USD_IRR_FREE');
console.log(`قیمت دلار: ${dollar.price.toLocaleString('fa-IR')} تومان`);
console.log(`آخرین بروزرسانی: ${meta.published_at}`);
```

## نمونهٔ Python

```python
import requests

payload = requests.get(
    "https://iran-market.github.io/data/history/USD_IRR_FREE.json",
    timeout=15,
).json()

for candle in payload["data"][-7:]:
    print(candle["date_jalali"], candle["close"])
```

## ساختار داده

فایل‌های لحظه‌ای شامل `symbol`، نام فارسی و انگلیسی، `price`، تغییر روزانه، بیشترین و کمترین،
زمان UTC و تهران، وضعیت stale و نام منبع هستند. فایل‌های تاریخچه کندل‌های روزانهٔ OHLC را به ترتیب
قدیمی به جدید ارائه می‌کنند. `meta.published_at` زمان انتشار فایل در این مخزن است.

داشبورد، جست‌وجوی نمادها و مثال‌های بیشتر در [iran-market.github.io](https://iran-market.github.io/) در دسترس است.

## پایداری و منبع

- به‌روزرسانی خودکار: هر ۳۰ دقیقه
- فرمت: UTF-8 JSON
- منبع فعلی داده: TGJU
- API مبدا: [imapi.cloudflarezone.net](https://imapi.cloudflarezone.net/docs)
- بدون تضمین برای معاملات مالی؛ قبل از استفادهٔ حساس داده را راستی‌آزمایی کنید.

## License

کد رابط و مثال‌های این مخزن تحت مجوز MIT منتشر می‌شوند. دادهٔ بازار متعلق به تولیدکنندگان اصلی آن است.
