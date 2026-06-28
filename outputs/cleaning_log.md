
2. Missing Values:

**Missing region**
Records found: 26
Action taken: Filled missing region column cells with 'Unknown' and flagged them in Yellow.
Column Created : Created new column (AA) labelled "FLAG-Region_unknown" and captured missing region values as 'Flagged'.

**Missing ship_mode**
Records found: 22
Action: Filled missing ship_mode column cells with "Unknown" and flagged them in Yellow.
Column Created :Craeted new column (Z) labelled "FLAG-ShipMode_unknown" and captured missing ship_mode values as 'Flagged'.

**Missing Discount**
Records found: Multiple Records found without discount values flagged them in Yellow.
Action: Filled missing discount column cells with 0.00.


3. Date Cleaning:
Dates in order_date and ship_date columns were displayed in multiple forms. Some of them were in text format. Used "Text to Columns' option on Data pane to convert some text formatted dates to date format.
Both the columns are now displaying dates in mm/dd/yy format. As per requirement, created two new columns order_month and order_year that will display order month and order year captured from order_date column.

3.1 Date format Standardization:
Both order_date and ship_date columns are standardized to MM/DD/YY format.

3.2 Invalid date - shipped before order_date:
Records found: 149
Created two columns "shipping_delay_dates" and "FLAG-ShipDt>OrderDt".
shipping_delay_dates : This created column displays the diffirence between order_date and ship_date. Expected only positive values nut its displaying both positive and negective values. Same day delivery is displaying as '0'. Negative values corresponds to flagged records.
FLAG-ShipDt>OrderDt: This created column displays Valid and Invalid values. This column displays 'Valid' for positive numbers and same day delivery records and 'Invalid-Date' for negative numbers.

3.3 Shipping_delay_dates:
Excel formula used : ship_dated - order_date
shipping_delay_dates : This created column displays the diffirence between order_date and ship_date. Expected only positive values nut its displaying both positive and negective values. Same day delivery is displaying as '0'. Negative values corresponds to flagged records.

4. Discount Cleaning:
4.1 Negative Discount:
Identified all empty cells in discount column and replaced them with '0.00'. Used Find and Replace to find empty cells and replaced them with "0.00". Used conditional formatting(Equal to '0') to flag values "0.00" and highlighted them in Yellow. Also, used conditional formatting(Less than ' 0') to flag negative values and highlighted them in Red.

4.2 Discount range allowed : Less than 50%
Discount allowed is less than 50% . Records with discount percantage above 50% are considered as Invalid-Discount so flagged them in green color in dicsounts column. New column is also created(Column "Y") to captures both negative and discount above 50% flagged them as "Invalid-Discount" 

5. Duplicates:
Total rows involved in duplicate order_ids : 63
Total number of Duplicates found: 40(20 pairs)
Number of records removed(Exact Duplicates kept one for each pair):	20
Number of duplicate order_Id's found with conflicting data(rows):	23
Unique order_ids duplicated	31
order_id's that appears exactly 2 time:	30
order_id's that appears exactly 3 times: 1
Number of rows flagged for review : 23

6. Business Rules applied:
6.1. Created new excel sheet sales_summary to capture sales summary.
1. Calculated_sales1 captures (quantity * unit_price).
2. Calculated_sales2 displays sales amount after applying discount.

6.22:Order and Payment status(without removing duplicates):

Order Status:
Completed orders : 622
Returned orders: 164
Cancelled orders: 146 

Payment Status : 704
Paid :87
Pending Refunded : 72
Failed : 69

7. Calculated Columns:
1. Calculated_sales1 (quantity*unit_price) : quantity × unit_price
2. Calculated_sales2 (after applying discount) : quantity × unit_price × (1 − discount)
3. Calculated_Profit : Derived from sales and cost
4. Profit_margin : profit / sales
5. shipping_delay_days : ship_date − order_date
6. order_month : Extracted from order_date
7. order_year : Extracted from order_date

8. Flag Columns Summary:
FLAG - ShipDt>OrdDt : captures Ship date before order date
FLAG - Negative Discount & Discount above 50% : Captures invalid Negative discount and invalid Discount above 50%
FLAG-ShipMode_unknown : Missing ship mode filled as Unknown
FLAG- Region_unknown : Missing region filled as Unknown


9. Quality Report
All flagged records are documented in data_quality_report.xlsx 