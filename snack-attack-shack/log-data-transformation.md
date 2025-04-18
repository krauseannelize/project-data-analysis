# Data Transformation Log

This log documents the steps taken in the Google Sheets data analysis project.

## 2025-04-16 - Initial Analysis

- **Data Source:**
  - Location: [data-snack-attack-shack-challenge](https://docs.google.com/spreadsheets/d/17sne5-vAbKo69kr0YPQMmApfRUFgpff48aJP6NSLnRY/edit?usp=drive_link)
  - Description: Customers, products and orders information
  - Sheets:
    - 1 orders
    - 2 products
    - 3 customers

- **Data Processing:**
    - Step 1: Create a copy of the workbook with name `analysis-snack-attack-shack-challenge`.
    - Step 2: Uploaded the workbook to AI for initial exploration and querying. *For details on AI interactions, refer to the* [AI Usage Log](/snack-attack-shack/log-ai-usage.md).

## 2025-04-17 - Continued Data Processing

  - Step 3: Create a copy of the "1 orders" worksheet and rename the copy to "analysis-revenue".
  - Step 4: Change the named table name to "revenue".
  - Step 5: Delete columns "requiredDate", "shippedDate", "arrivedDate", "freightCost" and "shipVia".
  - Step 6: Insert column "customerName" and use VLOOKUP to pull in the customer name from the "3 customers" worksheet.
  - Step 7: Insert column "customerCity" and use VLOOKUP to pull in the customer city from the "3 customers" worksheet.
  - Step 8: Decide to omit customer region from the analysis. *Rationale: 60 of the 91 customers have NULL in this field*
  - Step 9: Insert column "customerCountry" and use VLOOKUP to pull in the customer country from the "3 customers" worksheet.
  - Step 10: Insert column "productName" and use VLOOKUP to pull in the product name from the "2 products" worksheet.
  - Step 11: Insert column "productCategory" and use VLOOKUP to pull in the category name from the "2 products" worksheet.
  - Step 12: Insert column "productCost" and use a combination of VLOOKUP and YEAR to pull in product price from the "purchasePrice_2022", "purchasePrice_2023" and "purchasePrice_2024" columns in the "2 products" worksheet, respectively.
  - Step 13: Insert column "productMarkup" to calculate the percentage markup from productCost to orderPrice.
  - Step 14: Insert column "orderTotal" to calculate total of order multiplying order price and quantity before discount.
  - Step 15: Insert column "revenue" to calculate the amount paid by the customer by deducting any discounts from the order total.
  - Step 16: Insert column "profit" to calculate the profit by deducting total product cost (multiply product cost and quantity) from revenue.
  - Step 17: Insert column "profitMargin" to calculate the percentage profit over revenue.
  - Step 18: Apply a filter to "orderDate" to only show transactions before 2024-05-01. *Rationale: Only partial records for May 2024 transactions exist, which will skew results.*
  - Step 19: Create a new worksheet named "summary".
  - Step 20: Extracted a list of all customers and their associated revenue using the formula: `=QUERY(revenue,"SELECT C, SUM(P) WHERE C IS NOT NULL GROUP BY C ORDER BY SUM(P) DESC LABEL C 'Customer', SUM(P) 'Revenue'", 1)`.
  - Step 21: Inserted a column "% of Total" to calculate each customer's percentage of the total revenue.
  - Step 22: Inserted a column "Cumulative" to calculate a running balance of the "% of Total," providing insight into cumulative revenue distribution.
