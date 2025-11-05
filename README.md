
English & Persian Summary

This project builds a machine learning pipeline for taxi fare prediction
using a large real-world dataset (~1,000,000 raw rows).
After strict quality control and cleaning, ~13,000 rows remained for
training and ~15,000 for testing.

Raw Data (~1M rows before cleaning)

-   pickup/dropoff timestamps
-   GPS coordinates
-   trip duration
-   passenger count
-   store_and_fwd flag
-   total price (target)

Removed During Cleaning

-   corrupted or broken rows
-   impossible trips (duration ≤ 0, passengers ≤ 0, duration > 4 hours)
-   zero-distance with long duration
-   invalid coordinates
-   extreme outliers
-   duplicates

Engineered Features

Time-based: hour, day-of-week, month, weekend, rush-hour, sin/cos
encodings
Geographic: haversine distance, manhattan distance, bearing, short/long
trip
Passenger logic: passenger_ge3, passenger_ge5, binary store_and_fwd_flag

Modeling

-   ElasticNet (log-target baseline)
-   CatBoost (plain + log-target)
-   Time-based split: 80% train, 20% future validation

Final Performance (on unseen future data)

Best model: CatBoost log-target
- MAE ≈ 1.27
- R² ≈ 0.97

------------------------------------------------------------------------

خلاصه فارسی

این پروژه یک پایپ‌لاین ML برای پیش‌بینی کرایه تاکسی روی یک دیتاست بزرگ
واقعی با حدود یک میلیون ردیف است.
بعد از پاک‌سازی دقیق، حدود ۱۳ هزار ردیف برای آموزش و ۱۵ هزار برای تست
باقی ماند.

داده خام (~1M ردیف)

-   زمان شروع/پایان
-   مختصات GPS
-   تعداد مسافر
-   مدت سفر
-   store_and_fwd
-   قیمت سفر

موارد حذف‌شده

-   ردیف‌های خراب
-   سفرهای غیرممکن (مدت ≤۰، مسافر ≤۰، مدت >۴ ساعت)
-   فاصله صفر با زمان زیاد
-   مختصات نامعتبر
-   outlier شدید
-   داده‌های تکراری

فیچرهای ساخته‌شده

زمانی: ساعت، روز هفته، ماه، آخر هفته، ساعت شلوغی، سینوسی/کسینوسی
جغرافیایی: فاصله هاورساین، منهتن، زاویه حرکت، سفر کوتاه/بلند
منطقی: passenger_ge3 / ge5، نسخه باینری store_and_fwd

مدل‌ها

-   ElasticNet baseline
-   CatBoost (plain + log)
-   اسپلیت زمانی ۸۰٪ → ۲۰٪ انتهایی

نتیجه نهایی

بهترین مدل: CatBoost-log
- MAE ≈ 1.27
- R² ≈ 0.97
(روی دادهٔ آیندهٔ ندیده)
