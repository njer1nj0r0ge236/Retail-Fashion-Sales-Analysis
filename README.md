# 🛍️ Retail Fashion Sales Analysis & BI Dashboard
<p align="center"> <img src="https://img.shields.io/badge/SQL-Analysis-blue?style=for-the-badge&logo=microsoftsqlserver"/> <img src="https://img.shields.io/badge/PowerBI-Dashboard-yellow?style=for-the-badge&logo=powerbi"/> <img src="https://img.shields.io/badge/Data-Cleaning-green?style=for-the-badge"/> <img src="https://img.shields.io/badge/Status-Completed-success?style=for-the-badge"/> </p>
## 📌 Overview

This project analyzes retail fashion sales data to uncover insights into revenue performance, customer behavior, product profitability, and seasonal trends.

The goal was to transform raw, messy data into a business-ready dataset and deliver actionable insights through SQL and Power BI.

## 🎯 Objectives

✔️ Understand overall business performance
✔️ Identify top-performing products, regions, and customers
✔️ Analyze profitability vs revenue
✔️ Investigate return patterns and risks
✔️ Detect seasonal trends for forecasting

## 🛠️ Tools & Technologies
Tool	Purpose
🗄️ SQL Server (SSMS)	Data cleaning & analysis
📊 Power BI	Dashboard & visualization
📑 Excel	Initial preprocessing
🗂️ Dataset & Data Model

### This project uses a relational database structure:

👤 Customers → demographics
🛍️ Products → pricing & attributes
💳 Sales → transactions
🏬 Stores → location data

🔗 Connected using Primary & Foreign Keys

## 🧠 Feature Engineering

💰 Revenue Calculation

```bash
Revenue = Quantity * ListPrice * (1 - Discount)
```

👉 Converts raw transactional data into business value (money)

## 🧹 Data Cleaning
### ✔️ Key Steps
Replaced missing values (Discount → 0, Email → "Unknown")
Standardized categories (??? → Unknown)
Ensured correct data types (IDs, prices, dates)
Maintained referential integrity (added "Unknown" customer)
Verified no duplicates in primary keys
Performed outlier detection → no unrealistic values found

💡 Result: Clean, analysis-ready dataset

### 🧩 SQL View (Master Dataset)
```bash
CREATE VIEW Sales_Analysis AS
SELECT 
    s.TransactionID,
    s.Date,
    s.CustomerID,
    s.ProductID,
    s.StoreID,
    s.Quantity,
    s.Discount,
    s.Returned,

    c.Age,
    c.Gender,
    c.City,

    p.Category,
    p.Color,
    p.Size,
    p.Season,
    p.Supplier,
    p.CostPrice,
    p.ListPrice,

    st.StoreName,
    st.Region,
    st.StoreSize_m2,

    (s.Quantity * p.ListPrice * (1 - s.Discount)) AS Revenue

FROM Sales s
JOIN Customers c ON s.CustomerID = c.CustomerID
JOIN Products p ON s.ProductID = p.ProductID
JOIN Stores st ON s.StoreID = st.StoreID;
```

💥 One clean dataset → ready for analysis & Power BI

## 📊 Analysis Performed

🔹 Revenue (total, category, region, yearly)
🔹 Customer insights (top customers, behavior)
🔹 Product profitability (revenue vs cost)
🔹 Returns analysis (risk & patterns)
🔹 Channel performance (online vs physical)
🔹 Seasonal trends & forecasting

## 🔍 Key Insights

📈 Revenue is stable (~12.3M) with peak seasons (May–July)
👜 Accessories generate the most revenue but also highest returns (~10%)
🏬 Physical stores outperform online channels
👥 High-value customers show repeat purchase behavior
🌍 Revenue is evenly distributed across regions
🔁 Return rate (~10%) indicates revenue leakage

## 🚀 Business Recommendations

✔️ Align inventory & marketing with peak months
✔️ Improve product quality & descriptions
✔️ Optimize online shopping experience
✔️ Introduce loyalty programs for top customers
✔️ Reduce returns in high-risk categories

## 📊 Dashboard Preview
<p align="center"> <img src="images/dashboard.png" width="85%"/> </p>
💥 Key Takeaways

✔️ Built a relational data model
✔️ Performed end-to-end data cleaning
✔️ Engineered business KPIs
✔️ Delivered actionable insights
✔️ Designed a decision-driven dashboard

## 📁 Project Structure
```bash
Retail-Fashion-Analysis/
│
├── data/
├── sql/
│   ├── table_creation.sql
│   ├── data_cleaning.sql
│   ├── analysis_queries.sql
│   └── view_creation.sql
│
├── powerbi/
│   └── dashboard.pbix
│
├── images/
│   └── dashboard.png
│
└── README.md
```

## 🧠 Final Note

This project demonstrates how raw data can be transformed into meaningful business insights through data modeling, SQL analysis, and visualization — enabling better decision-making.

⭐ If you found this useful

Give it a ⭐ on GitHub or connect with me!

## 👩‍💻 Author  
Developed by [Marydiana Njoroge](https://marydiananjorogeportfolio.vercel.app/)  
💼 [LinkedIn](https://www.linkedin.com/in/marydiana-njoroge-41b236244/)  
🐙 [GitHub](https://github.com/njer1nj0r0ge236)  
✍️ [Medium](https://medium.com/@njorogediana236)  


## 📌 License
This project is licensed under the [MIT License](./LICENSE) – see the LICENSE
 file for details.
