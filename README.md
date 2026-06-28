# swethapriya_2511406_part1_data_cleaning
1. PROBLEM SUMMARY:
As a Business Analyst, the task involved working with order-level sales data of a retail company exported from multiple internal systems. Since data came from multiple sources, it contained quality issues that makes it unsuitable for direct business reporting or analysis.

Problem identified includes:
- Text Formatting
- Missing Values
- Date Problems
- Duplicate Records
- Invalid Discounts
- Empty cells
- Order Status Issues
- Calculations Mismatch

Goal was to clean and validate the data for analysis purpose.

2. 
File Name" `cleaned_orders.xlsx` 
Sheet: `cleaned_data` |
Total Records: 932 rows |
Total Columns: 35 columns |
Date Range: January 2024 — December 2025 |
Source:  Multiple internal retail systems 


Columns Added during cleaning:
`FLAG - ShipDt>OrdDt` - Ship date before order date  `Valid`/`Invalid-Date` 
`FLAG - Negative Discount & Discount above 50%` - Invalid discount range `Valid`/`Invalid-Discount` 
`FLAG-ShipMode_unknown` -  Missing ship mode | `Pass` / `Flagged` 
`FLAG- Region_unknown` -  Missing region | `Pass` / `Flagged`
Calculated columns:
`Calculated_sales1` -  `quantity × unit_price` to get Gross revenue before discount 
`Calculated_sales2` -  `quantity × unit_price × (1 − discount) to calculate Revenue after discount 
`Calculated_Profit`-  Derived from sales and cost Profit verification 
`Profit_margin` -  `profit ÷ sales` Margin per order 
`shipping_delay_days` -  `ship_date − order_date` - to validate Shipping performance 
`order_month` -  Extracted from `order_date` to check Monthly trend analysis 
`order_year` -  Extracted from `order_date`  to check Yearly trend analysis 

Data Quality Report — Sheets:
Summary` | Key metrics and handling logic overview 
`Exact_Duplicates_Removed` -  20 exact duplicate rows removed 
`Conflicting_Duplicates` - 23 rows flagged for review (same order_id, different data) 
`Missing_Region_Flagged` - 26 rows where region was missing → filled as Unknown 
`Missing_ShipMode_Flagged` -  22 rows where ship_mode was missing → filled as Unknown 
`Sales_Profit_Mismatch_Summary` - Summary of sales and profit calculation mismatches 
`Sales_Mismatch_Detail` - 65 rows with sales mismatches 
`Profit_Mismatch_Detail` - 41 rows with profit mismatches 

3.TOOLS USED:
- **Microsoft Excel** — data cleaning, pivot tables, business rules, summary reports
- **Python (pandas)** — data validation and quality checks
- **Markdown** — documentation

4. BUSINESS RULES APPLIED: 
1. Text Standardization
2. Text Formatting
3. Missing Values
4. Date Problems
5. Duplicate Records
6. Invalid Discounts
7. Empty cells
8. Order Status Issues
9. Calculations Mismatch

6. SUMMARY OF DATA QUALITY ISSUES FOUND:
The raw dataset contained multiple quality issues including duplicate records, missing values, inconsistent text formatting, and invalid date entries across 932 rows exported from multiple internal systems. Key issues identified were 40 exact duplicate rows, 48 missing region/ship_mode values, 31 invalid discounts, 149 shipment date errors, and 65 sales calculation mismatches. All issues were documented, flagged, and handled according to defined business rules without silent deletion of any records.

7. SUMMARY OF FINAL PIVOT REPORTS:
The pivot summary report includes a monthly sales trend analysis across 2024 and 2025, a profit margin breakdown by customer segment, and a count of refunded, cancelled, and failed orders by region. These pivots are built on the cleaned dataset and reflect only valid, analysis-ready records. Together they provide a high-level business view of sales performance, profitability, and order quality across the organization.

8. KEY BUSINESS INSIGHTS:
February consistently recorded the highest sales across both 2024 and 2025, while November and December 2025 showed significantly lower figures indicating incomplete data for the period. Small Business and Home Office segments demonstrated the highest profit margins, while the North region had the highest count of cancelled and returned orders requiring attention. A total of ₹9,250,167 in gross sales was recorded, however cancelled, failed, and refunded orders account for a significant portion that must be excluded from final completed sales reporting.

9.ASSUMPTIONS AND LIMITATIONS:
Missing region and ship_mode values were assumed to be data entry omissions and filled as 'Unknown' rather than being removed, and missing discounts were assumed to be zero where all other sales fields were valid. Conflicting duplicate order IDs were flagged for review rather than resolved, as the correct version could not be determined without input from the source systems. The 2025 data appears incomplete beyond October, which limits year-over-year comparisons and may affect trend analysis and business conclusions drawn from the dataset.

10.SCREENSHOTS:

## Cleaned Data Preview
![Cleaned Data Preview](cleaned_data_preview.png)

## Monthly Sales Trend
![Monthly Sales Trend](monthly_sales_trend.png)

## Pivot Summary
![Pivot Summary](pivot_summary.png)