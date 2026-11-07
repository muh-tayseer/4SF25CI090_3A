# E-Commerce Orders Analysis using Pandas

**Name:** Muhammad Tayseer
**USN:** 4SF25CI090

## Overview

This project analyses an e-commerce orders dataset of 80,000 orders (Jan 2025 to Oct 2026) from Indian cities, using Python, Pandas, Matplotlib and Seaborn. It covers the full workflow: reading the data, understanding it, cleaning and transforming it, handling null values with mean imputation, generating insights, and visualizing them.

## Dataset

- **File:** `ecommerce_orders.csv`
- **Rows / columns:** 80,600 rows (including 600 duplicate rows) and 26 columns
- **Source:** Synthetic dataset generated for learning and practice. It is not real customer data.
- **Contents:** order details, customer details (age, gender, city, state), product details (name, brand, category, price), discount and coupon, payment method, order status, delivery date, rating and review.
- **Data quality issues included on purpose:** null values, placeholder text such as `N/A`, `null` and `?`, invalid ages (e.g. -1, 999), quantity outliers, duplicate rows and inconsistent text case.

## Tasks Performed

1. **Dataset reading:** loaded the CSV with `pd.read_csv`, converting placeholder strings such as `N/A`, `null` and `?` to real nulls.
2. **Data understanding:**
   - checked shape, data types and summary statistics
   - counted nulls per column
   - checked unique values for gender, city, product category and state
   - found duplicate rows
   - checked the ranges of age, order date and quantity
3. **Data transformation:**
   - converted order and delivery dates to datetime
   - replaced placeholder phone and pincode values with real nulls
   - removed 600 duplicate rows
   - fixed inconsistent text case in city and product category
   - converted low-cardinality text columns to the `category` dtype
   - treated invalid ages and quantity outliers as null
   - added new columns: `year_month` and `delivery_days`
   - dropped unnecessary columns (phone, email, pincode, customer name, review text)
4. **Null handling:**
   - built a null report with a bar chart
   - mean imputation for numeric columns (`age`, `unit_price`, `quantity`, `discount_pct`, `shipping_fee`, `total_amount`)
   - rounded `age` and `quantity` to whole numbers
   - added a mean-filled `rating_filled` column
   - filled categorical columns (`gender`, `city`, `state`, `payment_method`, `brand`) with `Unknown`
   - left nulls that carry meaning (`coupon_code`, `rating`, `delivery_date`, `delivery_days`) as they are
5. **Insights and visualization:** revenue is calculated on valid orders only (cancelled and returned orders are excluded).
   - monthly revenue trend
   - state-wise and city-wise revenue
   - revenue by product category
   - top 10 products by revenue
   - order status distribution
   - payment method share

## Key Insights

- 67,311 of the 80,000 orders are valid sales, giving a total revenue of about Rs 279 million and an average order value of about Rs 4,151.
- Monthly revenue is about Rs 10 to 14 million but roughly doubles in October of both years (about Rs 23 million), which is the festive sale season.
- Karnataka, Maharashtra and Delhi are the top states, and Bengaluru is the top city.
- Electronics gives about 58% of revenue, and the top products are laptops, cameras and phones.
- About 83% of orders are delivered, 9% are returned and 7% are cancelled.
- UPI is the most used payment method, at about 46% of orders.

## Files in this Repository

| File | Description |
|---|---|
| `cie1.ipynb` | Notebook with the code, outputs and charts |
| `ecommerce_orders.csv` | Dataset used for the analysis |
| `README.md` | Project overview |

## Tools Used

Python, Pandas, NumPy, Matplotlib, Seaborn, Jupyter Notebook
