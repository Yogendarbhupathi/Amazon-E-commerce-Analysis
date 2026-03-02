🛒 Amazon E-Commerce Sales Analysis (Power BI + SQL Project)

📌 Project Overview

This project analyzes Amazon E-Commerce sales data using Power BI and SQL to uncover business insights, customer behavior patterns, product performance, delivery efficiency, and revenue trends.

The objective was to help stakeholders maintain strong performance while identifying strategic opportunities for growth, customer satisfaction improvement, and revenue optimization.

🎯 Problem Statement
- As a Business Analyst at Amazon, the goal is to:
- Maintain current performance levels
- Identify growth opportunities
- Improve customer experience
- Optimize delivery and product performance
- Provide strategic recommendations based on data

📊 Dataset Information
- Tables Used: Customers, Orders
- Dataset Size: ~1.13 Lakh Rows

Tools Used:
- Power BI (Dashboard & DAX)
- SQL (Advanced Queries & Analysis)
- Power Query (Data Cleaning)

🧹 Data Cleaning & Preparation
- Data was cleaned and prepared using Power Query:
- Removed null values and empty rows
- Deleted unnecessary columns
- Standardized data types (Date, Numeric, Text)
- Replaced missing “Reason” values using DAX
- Created calculated columns (Delivery Days, Customer Category)
- Established relationships between Orders and Customers using CustomerID
- Verified data consistency and formatting
- The dataset was transformed into a structured, analysis-ready format.

📈 Key Business Metrics
💰 Total Revenue
- Total Revenue = SUM(Orders[Sale Price])
- Total Revenue: 107.24M

👥 Unique Customers
- Unique Customers = DISTINCTCOUNT(Orders[CustomerID])

📦 Total Returned Products
- Total Returned Products = CALCULATE(COUNTROWS(Orders), Orders[Status] = "Returned")
- Total Returns: 31K

🚚 Average Delivery Days
```
Delivery Days = DATEDIFF(Orders[OrderDate], Orders[Delivery Date], DAY)

Avg Delivery Days = CALCULATE(
    AVERAGE(Orders[Delivery Days]),
    Orders[Status] = "Delivered"
)
```

- Average Delivery Time: 9.41 Days

📊 Dashboard Highlights
1️⃣ Revenue Trends
- Stable revenue from 2015–2019 (~16–17M)
- Major growth in 2020 (24M)
- January highest monthly revenue (10.1M)
- June lowest revenue month

2️⃣ Product Category Performance
- Phones & Tablets → 39M (Highest)
- Electronics → 33M
- Fashion, Health & Beauty, Home & Office → 12M each

3️⃣ Customer Segmentation (Loyalty Buckets)
```
DAX Customer Category = 
IF(Orders[Sale Price] > 5000, "Platinum",
IF(Orders[Sale Price] > 3000, "Gold",
IF(Orders[Sale Price] > 1000, "Silver", "Bronze")))
```
| Category | Customers | Revenue |
| -------- | --------- | ------- |
| Bronze   | 87K       | 30M     |
| Silver   | 15K       | 26M     |
| Gold     | 7K        | 29M     |
| Platinum | 3K        | 23M     |

Bronze drives revenue through volume of customers.

Gold and Platinum drive revenue through higher spending per customer.

4️⃣ Delivery Performance
| Delivery Type       | Average Delivery Days |
| ------------------- | --------------------- |
| Express             | 3.5 Days              |
| Standard Delivery   | 10 Days               |
| Shipped from Abroad | 15 Days               |

Express delivery ensures fastest fulfillment.

International shipping significantly increases wait time.

5️⃣ Location-Based Revenue

Top Revenue Generating Locations
- Greater Accra
- Ashanti
- Western
- Weija
- Upper West
- Revenue is highly concentrated in these regions, indicating strong geographic demand clusters.

🧠 Advanced SQL Analysis
- Performed advanced SQL analytics including:
- Top 5 Valuable Customers (Composite Score)
- Month-over-Month Growth Rate
- Rolling 3-Month Average Revenue
- Revenue Growth vs Previous Year
- Customers generating 30% above average revenue
- Product Category Sales Increase Analysis
- Consecutive Order Gap Analysis

Example Query:

```sql
SELECT
    CustomerID,
    SUM(SalePrice) AS Total_Revenue,
    COUNT(OrderID) AS Order_Frequency,
    AVG(SalePrice) AS Avg_Order_Value,
    (
        (SUM(SalePrice) * 0.5) +
        (COUNT(OrderID) * 0.3) +
        (AVG(SalePrice) * 0.2)
    ) AS Composite_Score
FROM orders
GROUP BY CustomerID
ORDER BY Composite_Score DESC
LIMIT 5;
```

📌 Key Insights
- Revenue heavily depends on Phones & Electronics categories.
- 2020 saw major customer growth and revenue spike.
- Low ratings (1–3) are significantly higher than 4–5 ratings.
- 31K products returned — quality improvement needed.
- Bronze customers dominate in count but not per-user revenue.
- Delivery time consistency across product categories.

🚀 Strategic Recommendations
- Focus marketing on high-performing categories.
- Improve low-performing product segments via bundles & discounts.
- Promote Express delivery to increase satisfaction.
- Optimize international shipping logistics.
- Convert Bronze customers into Silver via personalized offers.
- Strengthen presence in top-performing regions.
- Reduce low ratings through better product quality and transparency.
- Implement loyalty programs for retention.

📊 Dashboard Pages
- Executive Overview
- Product Category Analysis
- Individual Product Deep Dive

🛠 Skills Demonstrated
- Power BI Dashboard Development
- DAX (CALCULATE, DISTINCTCOUNT, DATEDIFF, SAMEPERIODLASTYEAR)
- Power Query (M Language)
- SQL (CTE, Window Functions, Aggregations)

Data Modeling
- Customer Segmentation
- Business Strategy Development
- Data Cleaning & Transformation

🎯 Conclusion

This project demonstrates end-to-end business analysis — from raw data cleaning to advanced SQL analytics and strategic business recommendations — helping Amazon optimize revenue, improve customer satisfaction, and enhance operational efficiency.
