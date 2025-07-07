# -Merchandise-Sales-Analytics-Dashboard
This project involves end-to-end analysis of merchandise sales data from various locations and demographics. The goal was to extract insights on sales performance, customer satisfaction, product performance, and revenue by demographic to inform data-driven business decisions.
  #  1. Data Collection
  ## The data was collected from the company’s sales database and exported in .CSV format for cleaning and processing.

Sources:

- Order ID, Type (Domestic/International), Order Date

- Location

- Quantity

- Total Sales ($)

- Shipping Charge ($)

- Customer Satisfaction
  # 2. Data Cleaning (SQL & Excel)
   ```sql
 -- Standardize Date Format
UPDATE `sales`
SET `order_date` = CAST(`order_date` AS DATE);

-- Remove Nulls or Irregular Entries
DELETE FROM `sales`
WHERE `order_id` IS NULL OR `total_sales` IS NULL;

-- Create Cleaned Table
CREATE TABLE `clean_sales` AS
SELECT 
    `order_id`,
    `type`,
    `order_date`,
    `location`,
    `quantity`,
    `total_sales`,
    `shipping_charge`,
    `satisfaction`
FROM `raw_sales`
WHERE `total_sales` > 0; ```

# 3.  Excel Data Cleaning Tasks   
 ## Removed Duplicates
 
Used Excel's built-in Remove Duplicates tool:

- Go to Data tab → Click Remove Duplicates

- Selected columns like Order ID, Order Date, Total Sales to check for duplicate rows.

## Fixed Date Formatting Inconsistencies
 - Selected the entire Order Date column.

 - Applied standard date format:

- Home tab → Number Format → select Short Date or Custom: yyyy-mm-dd.

  ```=TEXT(A2, "yyyy-mm-dd") ```
  ## Converted Numeric Columns from Text to Number
   ### For columns like Total Sales, Quantity, Shipping Charge:

- Selected column → Data tab → Text to Columns → Click Finish

- Alternatively, used formula to force conversion:
    ## Used Data Validation for Satisfaction Status
 ### To ensure consistent entries like Satisfied, Neutral, Unsatisfied:

- Selected Satisfaction column → Data tab → Data Validation

- Settings:

- Allow: List

- Source:

- excel
- Copy
- Edit
  # 3. Data Visualization (Tableau)
 ## Tool: Tableau Desktop

Steps:

- Imported cleaned Excel/SQL data

- Created Calculated Fields:

- Revenue = Total Sales + Shipping

- Revenue per Unit = Revenue / Quantity

- Net Satisfaction Score

- Created Parameters:

- Filter by Date Range

- Filter by Product Type

- Filter by Location

# 📈 Dashboards Created:


## Transaction Records View

### Tabular overview of every order

### Conditional formatting for satisfaction (Red = Dissatisfied, Yellow = Neutral, Green = Satisfied)

- Deep Sales Exploration

- KPIs: Total Revenue, Top Categories

- Weekly revenue trend line

- Pareto chart for Top Products

- Gender & Age Group Revenue Split

- Sales Overview Dashboard

- Revenue comparison across months

- Customer rating distribution

- Revenue by location (Map view)

# Top performing products

## 📌 4. Key Insights & Recommendations
### 💡 Insights:
- Clothing generates over 80% of total revenue.

- San Antonio, New York, and Austin are high-revenue locations.

- Most dissatisfied customers are from international orders with shipping charges.

- Revenue dips drastically in early July, suggesting a seasonal or operational issue.

# ✅ Recommendations:
- Focus on Clothing category for future campaigns and upsell strategies.

- Optimize shipping for international customers to reduce dissatisfaction.

- Investigate revenue drop in July and prepare a recovery strategy.

Explore personalized offers for high-spending age groups (26–30 Males and 30–32 Females).

- Introduce loyalty programs for locations like San Antonio and New York.

## 🧰 Tech Stack
- Tool	Purpose
- Excel	Initial data cleaning
- SQL	Data transformation & QC
- Tableau	Visualization & dashboards
- GitHub	Documentation & versioning

# 📁 Repository Structure
- pgsql
- Copy
- Edit
## 📦merchandise-sales-analytics
 ┣ 📂data
 ┃ ┣ raw_sales_data.csv
 ┃ ┣ cleaned_sales_data.sql
 ┃ ┗ cleaned_sales_data.xlsx
 ┣ 📂sql
 ┃ ┗ cleaning_queries.sql
 ┣ 📂tableau
 ┃ ┣ sales_dashboard.twb
 ┣ 📂images
 ┃ ┣ transaction_records.png
 ┃ ┣ deep_exploration.png
 ┃ ┗ sales_overview.png





