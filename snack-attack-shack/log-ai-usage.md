# AI Usage Log

This log documents the use of AI tools during the Google Sheets data analysis project. It showcases how AI was leveraged for exploratory analysis, generating insights, and assisting with data transformation and visualization. Each entry includes the date, the prompt used, and the result or outcome.

## 2025-04-16 - Initial Interaction with AI

- **Purpose**: Begin exploratory analysis of the uploaded dataset.
- **AI Tool Used**: Perplexity AI
- **Prompt**: "What are some potential analyses I can perform on the attached dataset containing customers, products, and orders?"
- **Response**:
  - **Customer Analysis**
    - **Customer Segmentation**: Group customers based on their purchasing behavior (e.g., frequency, monetary value, products purchased) using clustering techniques.
    - **Customer Lifetime Value (CLTV) Prediction**: Estimate the future value of each customer based on their past transactions.
    - **Customer Churn Analysis**: Identify factors that contribute to customer churn and predict which customers are likely to churn in the future.
  - **Product Analysis**
    - **Product Recommendation**: Develop a system to recommend products to customers based on their past purchases or browsing history.
    - **Market Basket Analysis**: Discover associations between products that are frequently purchased together.
    - **Sales Forecasting**: Predict future sales of each product based on historical sales data and other factors.
  - **Order Analysis**
    - **Order Clustering**: Identify patterns in order characteristics (e.g., order size, order value, shipping destination) using clustering techniques.
    - **Delivery Time Analysis**: Analyze the factors that affect delivery time and identify ways to improve delivery efficiency.
  - **Time Series Analysis**
    - **Sales Trend Analysis**: Analyze sales trends over time to identify seasonal patterns and other trends.
    - **Demand Forecasting**: Forecast future demand for products based on historical sales data.
  - **Shipping Analysis**
    - **Shipping Cost Optimization**: Identify ways to reduce shipping costs while maintaining delivery service levels.
    - **Shipping Performance Analysis**: Evaluate the performance of different shipping carriers.
- **Outcome**:
  - Determine the 3 additional questions to answer in the analysis report:
    - **Sales Trend Analysis**: How have sales trends evolved over time, and what are the key drivers behind these trends? Are there noticeable seasonal patterns, growth trends, or areas of concern that require strategic attention?
    - **Demand Forecasting**: What is the projected demand for the next quarter/year, and how can inventory be optimized and production plannied to meet this demand effectively? What are the potential risks and opportunities associated with these forecasts?
    - **Shipping Carrier Performance**: Which shipping carrier is the fastest on average? Which is the most cost-effective?

## 2025-04-17 - Brainstorming the Analysis Workflow

- **Purpose**: Collaboratively brainstorm with AI to efficiently structure the analysis and address key project questions.
- **AI Tool Used**: Perplexity AI
- **Approach**: Engaged in a dynamic conversation with AI, exploring various strategies for breaking down the dataset and organizing the analysis.
- **Key Outcomes**:
  - Decided to create three sheets to centralize specific analyses:
    - Revenue Sheet: Focus on sales value, trends, and profitability.
    - Inventory Sheet: Track stock levels and identify risk of stockouts or excess inventory.
    - Shipping Sheet: Analyze delivery costs and performance.
  - Defined preprocessing needs, such as calculating sales value (sale price × quantity) and linking product costs from the products sheet.
  - Identified an efficient workflow to answer key questions comprehensively.

## 2025-04-17 - Company Logo Creation

- **Purpose**: Create a visually appealing company logo for use in project documentation.
- **AI Tool Used**: Canva's AI Image Generator Magic Media
- **Prompt**: "Generate a logo on a white background for 'Snack Attack Shack' using the colors blue, green and red."
- **Outcome**:
  - Chose one of the generated designs and note the color codes used for branding.
  - Incorporated the logo into project documentation for cohesive visual identity.

## 2025-04-18 - Heat Map Visualization

- **Purpose**: Create a visually accessible and appealing heatmap to visualize country performance data in the report.
- **AI Tool Used:** Microsoft Copilot
- **Prompt**: "Recommend a color-blind-friendly gradient using three colors (low, mid, high) for a heatmap."
- **Outcome**:
  - Selected gradient colors: Pale Gold (#FFE699), Orange (#FFA500), and Royal Blue (#002FA7) for low, mid, and high values, respectively.
  - Applied the gradient to the heatmap, ensuring accessibility and professional aesthetics.
  - Incorporated the heatmap into the report for impactful visualization of country performance.

## 2025-04-18 - Brainstorming and Debugging Customer Classification Logic

- **Purpose**: Collaboratively refine customer classification logic with AI to improve accuracy and address edge cases in the dataset.
- **AI Tool Used**: Microsoft Copilot
- **Approach**: Engaged in iterative troubleshooting and brainstorming with AI, testing classification formulas and identifying key refinements to address gaps, frequent orders, and dormant customer detection.
- **Key Outcomes**:
  - Refined the formula for the "sinceLastOrder" column (Step 45) to calculate gaps between orders and enable precise customer analysis.
  - Adjusted the logic for the "customerStatus" column (Step 46), ensuring classifications dynamically capture behavior across "New," "Non-Returning," "Dormant," and "Regular".
    - "Dormant" customers were defined with stricter criteria, requiring both no recent activity within 6 months and a long gap (>365 days) between orders.
    - Reactivated customers (e.g., those with frequent recent orders after a long gap) are now correctly classified as "Regular."
   - Successfully debugged edge cases and misclassifications through detailed formula testing.
