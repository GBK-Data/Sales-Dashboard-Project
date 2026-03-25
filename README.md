# Sales-Dashboard-Project

# Project Title
This project analyzes sales data to uncover trends, KPI performance, and business insights using **Excel (Power Query, Pivot Tables)** and **Power BI**.  
It demonstrates data cleaning, transformation, visualization, and reporting skills relevant for business and analytical roles.

## 🛠️ Tools & Technologies

**Microsoft Excel**
- Power Query
- Pivot Tables
- Charts & Visualization

**Power BI**
- Sales Dashboard
- Interactive Analysis
- Filters & Slicers
- KPI Cards

**SQL (Structured Query Language)**
- GROUP BY, SUM, AVG, COUNT, HAVING, LIMIT
- Extract, Sort, Filter

**Data Visualization & Dashboard Design**
- Designed dashboards for insights
- Interactive and user‑friendly visuals

# Dashboards preview
## Excel Dashboard
[Sales Dashboard/ https://1drv.ms/x/c/683fb194621b57d6/IQBqnRs9HBY4T6GTvhT2MzPoAZ8Pew2Mhqjn2-PJ5SUUeWw]

<img width="1833" height="592" alt="image" src="https://github.com/user-attachments/assets/e86dccab-a1af-4597-9111-9931b795e202" />

  ## Power BI Dashboard
<img width="1262" height="710" alt="image" src="https://github.com/user-attachments/assets/f386f245-48c2-4c75-b403-159b3e9c6810" />

## The dashboard provides insights into:
- Which region and country generates the most revenue
- Which products contribute the most to total sales
- Which categories have the highest sales volume
- How revenue changes over time
## Key Insights:
- Germany generated the most revenue among all countries, showing it's our strongest market
- The East generated the highest revenue, indicating focus on regional performance
- Laptop is the bestselling product, suggesting a focus for marketing and inventory planning.
- Hardware slightly outsells other accessories, indicating higher demand for hardware products
- December had the highest revenue, while October recorded the lowest
- October generated the lowest revenue, which might need attention for sales strategy
- Revenue trends reflect seasonal peaks and troughs, helping to plan inventory and marketing strategies

# SQL Queries
## 1. Total Revenue by Region and Country
This query calculates total revenue by region and country.
Also highlights underperforming regions and countries that may require improvement.
Insight: Germany and the East region generate the highest revenue, making them the strongest performers.
```sql
SELECT Sales.Region, Sales.Country, SUM(Sales.Revenue) AS TotalRevenue
FROM Sales
GROUP BY Sales.Region, Sales.Country
ORDER BY TotalRevenue DESC;
```

## 2. Average Unit Price per Product
Shows average unit price, total Units sold, and revenue per product.
Helps identify best-selling products and their contribution to overall revenue.
Insight: Laptop has the highest average unit price and generates the most revenue among all products.
```sql
SELECT Product, AVG(UnitPrice) AS AverageUnitPrice,
SUM(Units) AS TotalUnitsSold,
SUM(Revenue) AS TotalRevenue
FROM Sales
GROUP BY Product
ORDER BY AverageUnitPrice DESC;
```
## 3. Number of Unique Orders per Region
Counts unique orders and sums revenue and units per region. 
This helps to understand sales distribution and order volume by region.
Insight: The East region has the highest number of orders, indicating strong sales activity.
```sql
SELECT Region, COUNT(DISTINCT OrderID) AS UniqueOrders,
SUM(Revenue) AS TotalRevenue,
SUM(Units) AS TotalUnits
FROM Sales
GROUP BY Region
ORDER BY UniqueOrders DESC;
```

## 4. Top Performing Sales Representatives (Revenue > $10,000).
Shows total revenue per sales representatives for those who exceeded $10,000 revenue, sorted highest first.
Insight: Anna generates the highest revenue, making her the top-performing sales representative.
```sql
SELECT SalesRep, SUM(Revenue) AS TotalRevenue,
COUNT(DISTINCT OrderID) AS OrdersHandled
FROM Sales
GROUP BY SalesRep
HAVING SUM(Revenue) > 10000
ORDER BY TotalRevenue DESC;
```

## 5. Total Revenue per Product
Calculates total revenue and units sold per product.
Helps identify which products contribute the most to overall sales.
Insight: Laptop generates the highest total revenue, making it the key product for the business.
```sql
SELECT Product, SUM(Revenue) AS TotalRevenue,
SUM(Units) AS TotalUnits
FROM Sales
GROUP BY Product
ORDER BY TotalRevenue DESC;
```
## 6. Monthly Revenue by Regions
This query analyzes total revenue by regions over time, helping identify trends, seasonality, and performance differences across regions.
Insight: December shows the highest revenue, while October records the lowest, indicating seasonality in sales.
```sql
SELECT Region, MONTH(Date) AS Month, SUM(Revenue) AS TotalRevenue
FROM Sales
GROUP BY Region, MONTH(Date)
ORDER BY Region, Month;
```
## 7. Which Product sold the most Units
This query calculates total units sold per product, helping identify which product is the most popular.
Insight: Laptop has the highest number of units sold, confirming its popularity among customers.
```sql
SELECT Product, SUM(Units) AS TotalUnits
FROM Sales
GROUP BY Product
ORDER BY TotalUnits DESC;
```

**Total rows:** [1000]  
**Columns:**
- `OrderID` — unique identifier for each order
- `Date` — date of the transaction
- `Product` — product name
- `Category` — product category
- `Region` — sales region
- `Country` — country of sale
- `SalesRep` — sales representative
- `Units` — number of units sold
- `UnitPrice` — price per unit
- `Revenue` — total revenue per order
- `CheckRevenue` — verification column for revenue
- `DateMonths` — month extracted from Date
- `DateDays` — day extracted from Date

## Future Improvements:
- Add more complex SQL queries (JOINs, CTEs)
- Perform customer segmentation
- Expand dashboard with predictive metrics

## Notes:  
- Dataset cleaned and transformed using Power Query.
- Missing values handled / duplicates removed.  
