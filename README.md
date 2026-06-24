# E-Commerce Data Cleaning & Preparation (Task-1)

**DecodeLabs Industrial Training Kit — Task-1 (Data Cleaning & Preparation)**
*By Kingsley Ezenwanne | Batch 2026*

## Overview

This project represents the foundation phase of the DecodeLabs Data Analytics Internship. Using Excel Power Query, a raw 1,200-row e-commerce dataset was audited, cleaned, and validated to produce a reliable, analysis-ready source of truth. The focus was not on charts or dashboards — it was on data integrity: identifying and resolving every quality issue before any analysis could begin.

## Objectives

- Identify and handle missing or null values
- Verify and eliminate duplicate records
- Correct data formatting issues across numeric and text columns
- Validate pricing logic across all records
- Document every transformation in a structured Change Log

## Tools Used

- **Microsoft Excel** — Power Query Editor, Custom Column formulas

## Dataset

| Property | Detail |
|---|---|
| File | `Dataset for Data Analytics.xlsx` |
| Records | 1,200 orders |
| Columns | 14 (OrderID, Date, CustomerID, Product, Quantity, UnitPrice, ShippingAddress, PaymentMethod, OrderStatus, TrackingNumber, ItemsInCart, CouponCode, ReferralSource, TotalPrice) |

## Data Quality Issues Found & Resolved

| Change ID | Issue | Action Taken | Impact | Status |
|---|---|---|---|---|
| CR001 | 309 blank CouponCode values | Imputed with `~No Coupon~` label | Preserved all 309 records, avoided data loss | Resolved |
| CR002 | Floating-point precision errors in UnitPrice & TotalPrice | Rounded both columns to 2 decimal places | Fixed 29 affected records | Resolved |
| CR003 | Potential duplicate OrderIDs | Verified via Group By/Count check | Confirmed all 1,200 records are unique | Resolved |
| CR004 | Pricing logic consistency | Validated Quantity × UnitPrice = TotalPrice | Zero mismatches across all 1,200 rows | Resolved |

## Key Steps Performed

**Step 1 — Load into Power Query**
Data was loaded via Data → From Table/Range into the Power Query Editor, enabling a reproducible, step-tracked cleaning workflow.

**Step 2 — Column Quality Audit**
View → Column Quality and Column Profile were enabled to get a per-column breakdown of valid, error, and empty percentages before any changes were made.

**Step 3 — Missing Value Imputation**
CouponCode had 309 blank values. Rather than deleting rows (which would have reduced the dataset by 25.75% and reduced statistical power), blanks were replaced with the label `~No Coupon~` — making the absence of a coupon an explicit, analyzable category.

**Step 4 — Duplicate Verification**
OrderIDs were checked via a duplicate Group By query on a separate query copy. Result: zero duplicates across all 1,200 records.

**Step 5 — Floating-Point Precision Fix**
29 TotalPrice records contained values with 13+ decimal places due to binary floating-point arithmetic (e.g., `769.3799999999999` instead of `769.38`). Both UnitPrice and TotalPrice were rounded to 2 decimal places using Transform → Round.

**Step 6 — Pricing Validation**
A custom column `PriceCheck` was added using the formula:
```
= Number.Round([Quantity] * [UnitPrice], 2) = Number.Round([TotalPrice], 2)
```
All 1,200 rows returned TRUE. The column was removed before the final load.

**Step 7 — Final Load & Change Log**
The cleaned table was loaded into Excel. A separate `Change Log` sheet was built documenting all four changes (CR001–CR004) with Change ID, Description, Impact, and Status columns.

## Repository Contents

| File | Description |
|---|---|
| `Dataset for Data Analytics Cleaned.xlsx` | Final cleaned workbook with cleaned data sheet and Change Log tab |

---
*Part of the DecodeLabs Data Analytics Industrial Training Kit — Batch 2026*
