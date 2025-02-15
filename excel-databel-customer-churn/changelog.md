# Changelog - Analyzing Databel's Customer Churn in Excel

This changelog documents the steps taken in the Excel-based data analysis project.

## Version 1.0 (2025-02-13) - Initial Analysis

- **Data Source:**
  - File: `databel-customer-data.xlsx`
  - Location: [/excel-databel-customer-churn/databel-customer-churn-data.xlsx](/excel-databel-customer-churn/databel-customer-churn-data.xlsx)
  - Description: Customer, contract, subscription and usage information
  - Metadata: [DataCamp metadata sheet](/excel-databel-customer-churn/databel-customer-churn-metadata-sheet.pdf 'Metadata sheet for customer churn data')

- **Data Cleaning and Preprocessing:**
    - Step 1: Create copy of workbook with name `databel-customer-churn-dashboard.xlsx`
    - Step 2: Change worksheet name from "Databel - Aggregate" to "Aggregate"
    - Step 3: On the "Aggregate" worksheet: Insert table named "Aggregate"
    - Step 4: Change worksheet name from "Databel - Customer" to "Customer"
    - Step 5: On the "Customer" worksheet: Insert table named "Customer"
    - Step 6: On the "Customer" worksheet: Remove duplicates on "Customer ID" = No duplicate values found. *Rationale: Ensure data accuracy.*
    - Step 7: On the "Customer" worksheet: Replace blank values in "Churn Category" with "Unknown" (4918 replacements). *Rationale: Standardize missing churn category values.*
    - Step 8: On the "Customer" worksheet: Replace blank values in "Churn Reason" with "Unknown" (4918 replacements). *Rationale: Standardize missing churn category values.*
    - Step 9: On the "Customer" worksheet: Changed "Churn Category" to "Unknown" where "Churn Reason" is "Don't know" (123 replacements). *Rationale: To standardize the representation of unknown churn reasons across categories.*
    - Step 10: On the "Customer" worksheet: Add new column "Churned" with formula `=IF([@[Churn Label]]="Yes",1,IF([@[Churn Label]]="No",0,""))`. *Rationale: Convert "Churn Label" to a binomial value.*
    - Step 11: On the "Aggregate" worksheet: Add new column "Age Demographics" with formula `=IF([@Senior]="Yes","Senior",IF([@[Under 30]]="Yes","Under 30","Other"))`. *Rationale: Segment customers by age demographics to identify trends and patterns within specific customer segments.*
    - Step 12: On the "Aggregate" worksheet: Add new column "Age Group" with formula `=IFS([@Age]<=28,"19-28",[@Age]<=38,"29-38",[@Age]<=48,"39-48",[@Age]<=58,"49-58",[@Age]<=68,"59-68",[@Age]<=78,"69-78",[@Age]<=88,"79-88",TRUE,"Other")`. *Rationale: Segment customers by age groups to identify trends and patterns within specific customer segments.*
    - Step 13: On the "Aggregate" worksheet: Add new column "Data Usage" with formula `=IFS([@[Avg Monthly GB Download]]>10,"10 or more GB",[@[Avg Monthly GB Download]]<5,"Less than 5 GB",AND([@[Avg Monthly GB Download]]>=5,[@[Avg Monthly GB Download]]<=10),"Between 5 and 10 GB")`. *Rationale: Segment customers based on their average monthly gigabytes downloaded to analyze how data usage levels correlate with other customer attributes.*

- **Data Analysis:**
  - Step 1: Created a new "Analysis" worksheet to calculate key metrics and KPIs.
  - Step 2: Calculated the following metrics on the "Analysis" worksheet:
    - Total Customers (using `COUNTA` function)
    - Churned Customers (using `SUM` function)
    - Churn Rate (calculated as Churned Customers / Total Customers)
  - Step 3: Created a pivot table on the "Analysis" worksheet using the "Customer" table data to analyze churn reason by category. *Rationale: To identify the leading categories contributing to customer churn.*
  - Step 4: Created a pie chart visualizing churn reason by category from the pivot table and placed it on a new "Dashboard" worksheet.
  - Step 5: Created a dynamic, interactive churn analysis section on the "Analysis" worksheet. This section allows users to filter churn reasons by category.
    - Added a form control combo box linked to cell B16, listing the churn categories from the pivot table.
    - Created a dynamic chart title in cell B17, updating based on the combo box selection (e.g., "Price Churn Analysis").
    - Implemented a dynamic filtering mechanism in cell A20 using the `LET`, `SWITCH`, `FILTER` and `PIVOTBY` functions. This formula filters the 'Churn Reason' and 'Churned' columns based on the selected category in the combo box and generates a new pivot table.
    - Created dynamic named ranges referencing the output of the filtering formula in A20.
    - Inserted a donut chart visualizing the filtered churn reasons, with its title linked to the dynamic title in cell B17.  This chart updates dynamically as the combo box selection changes.
    * Rationale: To enable interactive exploration of churn reasons by category, allowing users to drill down into specific areas of interest and gain deeper insights into the drivers of churn.

## Version 1.1 (2025-02-15) - Continued Analysis

  - Step 6: Grouped the churn reason donut chart and its associated combo box and moved them to the "Dashboard" worksheet.
  - Step 7: On the "Analysis" worksheet, created a pivot table using the "Aggregate" table data to analyze the number of customers and churn rate per age group.
  - Step 8: Created a combination chart on the "Analysis" worksheet, visualizing the number of customers per age group as a column chart and the corresponding churn rate as a line graph. *Rationale: To visualize and analyze customer distribution and churn rate trends across different age groups, providing insights into age-related churn patterns.*
  - Step 9: Moved the age group analysis combination chart to the "Dashboard" worksheet.
  - Step 10: On the "Analysis" worksheet, extracted a list of unique state codes from the "Customer" table using the `UNIQUE` and `SORT` functions, ensuring the list is sorted alphabetically.
  - Step 11: On the "Analysis" worksheet, calculated the following metrics for each state:
    - Total Customers (using `SUMIFS`)
    - Churned Customers (using `SUMIFS`)
    - Churn Rate (calculated as Churned Customers / Total Customers, using `IFERROR` to handle potential division by zero errors)
  - Step 12: Created a map visualization on the "Dashboard" worksheet using the calculated state-level churn rate data. *Rationale: To visualize geographic patterns in churn rates and identify states with high or low churn, enabling targeted interventions and resource allocation.*
