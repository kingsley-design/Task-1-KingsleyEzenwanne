# E-Commerce Order Fulfillment & Sales Analysis: Diagnosing a 41% Revenue Leak
 
**DecodeLabs Industrial Training Kit — Project 2 (Exploratory Data Analysis)**
*By Kingsley Ezenwanne | Batch 2026*
 
## Overview
 
This project is an end-to-end exploratory data analysis of 1,200 e-commerce orders, investigating sales performance, pricing drivers, and — most critically — why over 41% of total potential revenue is being lost to cancelled and returned orders. The dataset was cleaned in a prior phase (Project 1) using Excel Power Query before being loaded here for analysis in Python.
 
## Key Findings
 
- **41.42% of all orders, and 41.09% of total revenue ($519,674), are lost to cancellations and returns.** This rate holds steady across payment methods and product categories, pointing to a systemic issue rather than one tied to a specific channel or product.
- **UnitPrice (r = 0.72) and Quantity (r = 0.62) are the strongest, largely independent drivers of order value** (Quantity–UnitPrice correlation ≈ 0.01). ItemsInCart shows a moderate relationship with Quantity (r = 0.65) but only a weak one with TotalPrice (r = 0.39).
- **High-TotalPrice outliers are signal, not noise.** They consistently involve the maximum quantity (5 units) of high-value products — Laptops, Printers, and Tablets — representing legitimate bulk/high-value purchases rather than data errors.
- **Chair and Printer are effectively tied for top revenue-generating product** ($195,620 vs. $195,612), closely followed by Laptop — too close to call a single "winner."
- **Orders placed without a coupon have a noticeably higher return rate (24.6%)** than coupon-using orders (16–22%), suggesting coupon users may be more committed buyers.
- **Facebook referrals carry the highest average order value (~$1,098)** among all referral sources, while AOV barely varies by payment method.
## Recommendations
 
1. Prioritize root-cause investigation into the 41% unfulfilled order rate — this is the single highest-impact opportunity in the dataset.
2. Expand coupon campaigns, given their association with lower return rates and higher buyer commitment.
3. Shift marketing budget toward higher-AOV channels like Facebook.
4. Build targeted offers around high-quantity, high-value product bundles (Laptops, Printers, Tablets).
5. Set up ongoing monitoring of order status, AOV by segment, and sales trends to catch shifts early.
## Repository Contents
 
| File | Description |
|---|---|
| `DecodeLabs.ipynb` | Full EDA notebook — univariate analysis, outlier detection, correlation analysis, order status investigation, AOV breakdowns, and executive summary |
| `Dataset for Data Analytics Cleaned.csv` | Cleaned dataset (output of Project 1's data cleaning phase) |
 
## Tools & Methods
 
- **Python** — Pandas, NumPy
- **Visualization** — Matplotlib, Seaborn
- **Techniques** — Five-number summaries, mean/median skew comparison, IQR outlier detection, Pearson correlation analysis, categorical cross-tabulation, time-series aggregation
## Data Source
 
1,200-row e-commerce order dataset (`Dataset_for_Data_Analytics.xlsx`), cleaned in Project 1 via Excel Power Query: missing `CouponCode` values imputed, floating-point precision errors in price columns corrected, and duplicate/format integrity verified.
 
---
*Part of the DecodeLabs Data Analytics Internship — Batch 2026*
