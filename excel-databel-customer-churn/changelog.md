# Changelog - Analyzing Databel's Customer Churn in Excel

This changelog documents the steps taken in the Excel-based data analysis project.

## Version 1.0 (2025-02-13) - Initial Analysis

- **Data Source:**
  - File: `databel-customer-data.xlsx`
  - Location: [/excel-databel-customer-churn/databel-customer-churn-data.xlsx](/excel-databel-customer-churn/databel-customer-churn-data.xlsx)
  - Description: Customer, contract, subscription and usage information
  - Metadata: [DataCamp metadata sheet](/excel-databel-customer-churn/databel-customer-churn-metadata-sheet.pdf 'Metadata sheet for customer churn data')

- **Data Cleaning and Preprocessing**
    - Step 1: Create copy of workbook with name `databel-customer-churn-dashboard.xlsx`
    - Step 2: Change worksheet name from `Databel - Aggregate` to `Aggregate`
    - Step 3: On the `Aggregate` worksheet: Insert table named "Aggregate"
    - Step 4: Change worksheet name from `Databel - Customer` to `Customer`
    - Step 5: On the `Customer` worksheet: Insert table named "Customer"
    - Step 6: On the `Customer` worksheet: Remove duplicates on "Customer ID" = No duplicate values found. *Rationale: Ensure data accuracy*
    - Step 7: On the `Customer` worksheet: Replace blank values in "Churn Category" with "Unknown" (4918 replacements). *Rationale: Standardize missing churn category values.*
    - Step 8: On the `Customer` worksheet: Replace blank values in "Churn Reason" with "Unknown" (4918 replacements). *Rationale: Standardize missing churn category values.*
    - Step 9: On the `Customer` worksheet: Add new column "Churned" with formula `=IF([@[Churn Label]]="Yes",1,IF([@[Churn Label]]="No",0,""))`. *Rationale: Convert "Churn Label" to a binomial value*
    