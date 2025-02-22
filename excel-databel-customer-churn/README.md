# Databel Customer Churn Dashboard

- [Raw Data](/excel-databel-customer-churn/databel-customer-data.xlsx)
- [Excel Dashboard](/excel-databel-customer-churn/databel-customer-churn-dashboard.xlsx)
- Video Walkthrough

This interactive Excel dashboard analyzes customer churn for the fictional telecoms company, Databel. Developed as part of DataCamp's Fundamental Skill track, specifically the "Analyzing Customer Churn in Excel" case study, this project significantly enhances the suggested solution by focusing on business-relevant metrics and advanced visualizations.

The dashboard provides a comprehensive view of customer churn through:

- **Key Metrics Widgets:**
  - Total customers: 6,687
  - Churned customers: 1,796
  - Churn rate: 26.86%
- **Churn Reason Analysis:** A bar chart illustrating that "Competitor" is the leading churn reason (44.82%), followed by "Attitude" (15.98%).
- **Dynamic Churn Reason Breakdown:** A dynamic bar chart that allows filtering by churn category (eg. "Competitor," "Dissatisfaction") to reveal specific sub-reasons. For example, filtering by "Competitor" shows "Competitor made better offer" and "Competitor had better devices" as primary drivers.
- **Age Group Analysis:** A combined column and line chart showing customer distribution by age group and the corresponding churn rate. Churn rate drastically increases for customers aged 68 and above, reaching over 40% in the 79-88 age group.
- **Churn Rate by Account Age and Demographics:** A heatmap and bar chart visualization showing churn rate by account age and demographic (Under 30, Senior, Other). This reveals that senior customers and customers with shorter account tenure (1-12 months) exhibit the highest churn rates.
- **Dynamic State-Level Churn Analysis:** An interactive map visualization that allows toggling between total customers, churned customers, and churn rate by state. Notably, California shows a significantly higher churn rate (63.24%) compared to other states.

This project showcases proficiency in advanced Excel data analysis, including complex formula construction (eg., using LET, SWITCH, FILTER, and PIVOTBY) to enable dynamic and interactive analysis of churn reasons. The heatmap visualization, created with linked image references and conditional formatting, provides an intuitive way to understand churn rate by account age and demographics. The dashboard provides actionable insights for Databel to identify and address key churn drivers.

![Final Dashboard](/excel-databel-customer-churn/databel-dashboard.png 'Final Dashboard')
