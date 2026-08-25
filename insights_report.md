# Data Cleaning & Visualization Report

**Raw dataset:** 1240 rows x 10 columns

## Issues found in raw data

**Missing values by column:**

- `region`: 38 missing (3.1%)
- `payment_method`: 49 missing (4.0%)
- `unit_price`: 63 missing (5.1%)
- `customer_age`: 99 missing (8.0%)
- `rating`: 124 missing (10.0%)
- `revenue`: 63 missing (5.1%)

**Duplicate rows (excluding order_id):** 34

## Cleaning actions taken

- Standardized text casing in `category`, `region`, `payment_method`
- Removed 40 duplicate orders
- Nulled out 9 impossible ages (e.g. 150, -5) before imputing
- Filled missing categorical values (`region`, `payment_method`) with the mode
- Filled missing `customer_age`/`rating` with the median
- Filled missing `unit_price` with the **category-level** median (more accurate than a global fill)
- Capped 46 `unit_price` outliers to the IQR bounds (₹-499 - ₹2465) instead of dropping rows

**Clean dataset:** 1200 rows x 11 columns, 0 missing values remaining: True

## Key findings

- **Electronics** generated the most total revenue (₹1,143,344)
- **2024-05** was the strongest month (₹473,661 in revenue)
- The highest-revenue combination was **East region paying via UPI** (₹343,060)
- Average customer rating across all categories: 3.00/5
- After cleaning, average order revenue is ₹4,236 (was ₹5,770 in the raw, outlier-skewed data)