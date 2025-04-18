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
  - Step 19: Create a new worksheet named "summary" to consolidate key metrics and streamline analysis.
  - Step 20: Extracted a list of all customers and their associated revenue using the formula: `=QUERY(revenue,"SELECT C, SUM(P) WHERE C IS NOT NULL GROUP BY C ORDER BY SUM(P) DESC LABEL C 'Customer', SUM(P) 'Revenue'", 1)`.
  - Step 21: Inserted a column "% of Total" to calculate each customer's percentage of the total revenue.
  - Step 22: Inserted a column "Cumulative" to calculate a running balance of the "% of Total," providing insight into cumulative revenue distribution per customer.

## 2025-04-18 - Continued Data Processing

  - Step 23: Create a new worksheet named "visualizations" to centralize charts and graphs for analysis.
  - Step 24: Created a combination chart titled "Pareto Chart: Revenue by Customers" with:
    - Columns: Representing customer revenue.
    - Line: Representing cumulative % of total revenue.
  - Step 25: Extracted a list of all products and their associated revenue in the "summary" worksheet by using the formula: `=QUERY(revenue,"SELECT H, SUM(P) WHERE H IS NOT NULL GROUP BY H ORDER BY SUM(P) DESC LABEL H 'Product', SUM(P) 'Revenue'", 1)`.
  - Step 26: Inserted a column "% of Total" to calculate each products's percentage of the total revenue.
  - Step 27: Inserted a column "Cumulative" to calculate a running balance of the "% of Total," providing insight into cumulative revenue distribution per product.
  - Step 28: Created a combination chart in "visualizations" titled "Pareto Chart: Revenue by Products" with:
    - Columns: Representing product revenue.
    - Line: Representing cumulative % of total revenue.
  - Step 29: Extracted a list of all categories and their associated revenue in the "summary" worksheet by using the formula: `=QUERY(revenue,"SELECT I, SUM(P) WHERE I IS NOT NULL GROUP BY I ORDER BY SUM(P) DESC LABEL I 'Category', SUM(P) 'Revenue'", 1)`.
  - Step 30: Inserted a column "% of Total" to calculate each category's percentage of the total revenue.
  - Step 31: Inserted a column "Cumulative" to calculate a running balance of the "% of Total," providing insight into cumulative revenue distribution per category.
  - Step 32: Created a combination chart in "visualizations" titled "Pareto Chart: Revenue by Category" with:
    - Columns: Representing category revenue.
    - Line: Representing cumulative % of total revenue.
  - Step 33: Added comments to cells containing the QUERY function to warn users: *"The QUERY function references specific columns. If columns in the source data are added, removed, or reordered, this formula may break or return incorrect results. Update the QUERY parameters as needed."*
  - Step 34: Delete rows for orders placed in May 2024 and updated values accordingly in report. *Rationale: Noticed the filter applied in the "analysis-revenue" worksheet didn't exclude the transactions from initial analyses. As May 2024 only has partial records, it is excluded for ensure consistency and reliability.*
  - Step 35: Extracted a list of all countries and their associated revenue in the "summary" worksheet by using the formula: `=QUERY(revenue,"SELECT E, SUM(P) WHERE E IS NOT NULL GROUP BY E ORDER BY SUM(P) DESC LABEL E 'Country', SUM(P) 'Revenue'", 1)`. Included comments with warning - see Step 33.
  - Step 36: Inserted a column "% of Total" to calculate each country's percentage of the total revenue.
  - Step 37: Inserted a column "Cumulative" to calculate a running balance of the "% of Total," providing insight into cumulative revenue distribution per country.
  - Step 38: Created a combination chart in "visualizations" titled "Pareto Chart: Revenue by Country" with:
    - Columns: Representing country revenue.
    - Line: Representing cumulative % of total revenue.
  - Step 39: Created a heat map visualization representing country revenue on a world map in "visualizations". Use AI to choose an accessible color scheme. Incorporate gradient colors: Pale Gold (#FFE699), Orange (#FFA500), and Royal Blue (#002FA7) for low, mid, and high values, respectively.
  - Step 40: Inserted a pivot table in "summary" referencing the "analysis-revenue" worksheet with the following configuration:
    - Rows:
      - customerCountry (sorted descending by sum of revenue)
      - customerCity (sorted descending by sum of revenue).
    - Values:
      - Revenue: Sum (default).
      - Revenue: Sum as % of grand total.
    - Filter: Applied filter on customerCountry to analyze city-level contributions per selected country.
  - Step 41: Create a copy of the "analysis-revenue" worksheet and rename the copy to "analysis-dynamic".
  - Step 42: Change the named table name to "dynamic".
  - Step 43: Delete "customerCity" and "customerCountry" columns.
  - Step 44: Added a new column titled "orderCount" to track the cumulative count of unique orders per customer using the formula `=COUNTUNIQUEIFS($A$2:$A2, $B$2:$B2, B2)`. This calculates a running balance of distinct orders per customer, ensuring line items for the same order are counted only once.
  - Step 45: Added a new column titled "sinceLastOrder" to calculate the days since the customer's last order using the formula `=IF(E2=1, 0, D2 - INDEX($D$2:$D2,MATCH(1, ($B$2:$B2=B2)*($E$2:$E2=E2-1), 0)))`. This will help to identify gaps in customer order history for classification purposes.
  - Step 46: Added a new column titled "customerStatus" to classify customers as New, Non-Returning, Dormant, or Regular based on their order history and purchasing patterns. The classification criteria is:
    - New: Customer placed exactly 1 order within the 180 days preceding 2024-04-30, the last day of our range.
    - Non-Returning: Customer has placed exactly 1 order and the gap between their order date and 2024-04-30 exceeds 180 days.
    - Dormant: Customer has placed multiple orders, but has not made a purchase within the last 180 days and at least one gap between orders exceed 365 days.
    - Regular: Customer has placed multiple orders, all gaps between orders are less than or equal to 365 days, with at least one purchase within the 180 days preceding 2024-04-30.
    The classification was done using this formula: `=IF(MAXIFS(dynamic[orderCount], dynamic[customerID], B2)=1, 
     IF((DATE(2024,4,30) - MAXIFS(dynamic[orderDate], dynamic[customerID], B2)) > 180, "Non-Returning", "New"), 
     IF(AND(MAX(dynamic[sinceLastOrder]) > 365, (DATE(2024,4,30) - MAXIFS(dynamic[orderDate], dynamic[customerID], B2)) > 180), "Dormant", "Regular"))`

- **Data Correction:**
  - Corrected customer "Que Delícia" city from " 12Rio de Janeiro" to "Rio de Janeiro" in the original "3 customers" worksheet to ensure data accuracy.

