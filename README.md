# 🍪 Cookies Sales Analysis — Power BI Dashboard
 
<div align="center">
<img src="https://img.shields.io/badge/Power%20BI-F2C811?style=for-the-badge&logo=powerbi&logoColor=black" alt="Power BI"/>
<img src="https://img.shields.io/badge/DAX-Measures-6366F1?style=for-the-badge" alt="DAX"/>
<img src="https://img.shields.io/badge/Dashboard%20Pages-2-D97706?style=for-the-badge" alt="Pages"/>
<img src="https://img.shields.io/badge/Schema-Star%20Schema-0EA5E9?style=for-the-badge" alt="Schema"/>
<img src="https://img.shields.io/badge/Status-Completed-16a34a?style=for-the-badge" alt="Status"/>
<br/><br/>
 
<strong>An interactive 2-page Power BI dashboard analyzing cookie sales performance across customers, products, states, and time — covering 700 orders, 5 major retail customers, and 6 cookie product types.</strong>
 
</div>
---
 
## 🗂️ Table of Contents
 
- [Project Overview](#-project-overview)
- [Dashboard Pages](#-dashboard-pages)
- [Data Model](#-data-model)
- [DAX Measures](#-dax-measures)
- [Key KPIs at a Glance](#-key-kpis-at-a-glance)
- [Tools & Technologies](#-tools--technologies)
- [Project Structure](#-project-structure)
- [How to Use](#-how-to-use)
---
 
## 🎯 Project Overview
 
This project analyzes **cookie sales data** for a retail bakery business to help management understand:
 
- 🏪 **Which customers** generate the most orders and revenue
- 🍪 **Which products** are the best and worst performers
- 📅 **Which time periods** drive the highest sales
- 📍 **Which states and cities** have the highest demand
| Feature | Details |
|---|---|
| 📁 Power BI File | `cookies.pbix` |
| 📄 Dashboard Pages | 2 Interactive Pages |
| 🗃️ Schema | Star Schema |
| 🏪 Total Customers | 5 Retail Customers |
| 🍪 Cookie Products | 6 Product Types |
| 📦 Total Orders | 700 Orders |
 
---
 
## 📑 Dashboard Pages
 
### 1️⃣ Customers
> *Customer-level performance: orders, sales, and product breakdown*
 
| KPI | Value |
|---|---|
| 📦 Total Orders | **700** |
| 💰 Total Sales | **4.69M** |
| 📊 Average Sales | **6.70K** |
| 🏪 Total Customers | **5** |
| 📫 Total Quantity | **1.13M** |
 
**Visuals:**
- 🍩 **Donut Chart** — Total Orders by Customer (ACME Bites leads at 29.43%)
- 📊 **Clustered Bar Chart** — Avg Sales vs Avg Profit by Customer (side-by-side comparison)
- 📊 **Stacked Bar Chart** — Total Quantity by Customer and Product (6 cookie types per customer)
**Slicers:** Customer · State · Product
 
**Top Customer by Orders:** ACME Bites (206 orders — 29.43%)
 
---
 
### 2️⃣ Orders & Products
> *Product-level analysis: quantity, sales, profit, and seasonal trends*
 
| KPI | Value |
|---|---|
| 📦 Total Orders | **700** |
| 💰 Total Sales | **4.69M** |
| 📊 Average Sales | **6.70K** |
| 💵 Total Profit | **2.72M** |
| 📫 Total Quantity | **1.13M** |
| 🍪 Count of Products | **6** |
 
**Visuals:**
- 🎯 **Gauge Chart** — Total Sales vs Min/Max target (4.69M out of 8.00M)
- 📊 **Bar Chart** — Total Quantity by Product (Chocolate Chip leads at 0.34M)
- 📈 **Line Chart** — Average Quantity by Month (seasonality trend across 12 months)
- 🍩 **Donut Chart** — Total Sales by Product breakdown
- 📊 **Combo Chart** — Total Sales & Total Profit by Quarter (Q1–Q4 trend)
- 📋 **Table** — Product detail: Total Profit · Total Cost · Total Sales per product
**Slicers:** City · Product · Year / Quarter / Month
 
**Top Product by Sales:** Chocolate Chip (1.69M sales)  
**Best Quarter:** Q4 (1.96M sales)
 
---
 
## 🗃️ Data Model
 
The project uses a **Star Schema** with one central fact table and two dimension tables.
 
```
┌──────────────────┐              ┌─────────────────────┐
│    Customers     │              │    Cookies Type     │
│                  │              │                     │
│  Address         │              │  Cost               │
│  City            │  1        1  │  Product            │
│  Country         ├──────────────┤  Profit             │
│  Customer        │              │  Revenue            │
│  Customer ID     │   *      *   │                     │
│  Phone           │    ┌──────┐  └─────────────────────┘
│  State           └────┤Orders├──┘
│  Zip                  │      │
└──────────────────┘    │Orders│
                        │      │
                   ┌────┴──────┴────┐
                   │    Orders      │
                   │                │
                   │  Customer ID   │
                   │  Date          │
                   │  Day Name      │
                   │  Month Name    │
                   │  Order ID      │
                   │  Product       │
                   │  Quantity      │
                   │  Year          │
                   └────────────────┘
```
 
### Tables Summary
 
| Table | Type | Description |
|---|---|---|
| `Orders` | ⭐ Fact | All transactions: orders, dates, quantities |
| `Customers` | 👥 Dimension | Customer info: name, city, state, address |
| `Cookies Type` | 🍪 Dimension | Product details: cost, profit, revenue per unit |
| `_measures` | 📐 Measures | All DAX KPI measures (no rows) |
 
---
 
## 📐 DAX Measures
 
All measures are stored in the dedicated **`_measures`** table:
 
```
📁 _measures
├── 💰 Total_Sales
├── 💵 Total_Profit
├── 🏭 Total_Cost
├── 📦 Total_Orders
├── 📫 Total_Quantity
├── 👥 Total_Customers
├── 📊 Average_Sales
└── 📈 Average_Profit
```
 
---
 
## 📊 Key KPIs at a Glance
 
```
┌──────────────────────────────────────────────────────────┐
│                  BUSINESS SUMMARY                        │
├──────────────────────┬───────────────────────────────────┤
│  📦 Total Orders     │  700 orders                       │
│  💰 Total Sales      │  $4.69M                           │
│  💵 Total Profit     │  $2.72M                           │
│  📊 Avg Sales        │  $6.70K per order                 │
│  📫 Total Quantity   │  1.13M units                      │
│  🍪 Products         │  6 cookie types                   │
│  🏪 Customers        │  5 retail accounts                │
├──────────────────────┼───────────────────────────────────┤
│  🏆 Top Customer     │  ACME Bites (206 orders — 29.43%) │
│  🏆 Top Product      │  Chocolate Chip ($1.69M sales)    │
│  🏆 Best Quarter     │  Q4 ($1.96M sales)                │
│  🏆 Highest Profit   │  White Chocolate Macadamia Nut    │
└──────────────────────┴───────────────────────────────────┘
```
 
### 🍪 Product Breakdown
 
| Product | Total Sales | Total Profit | Total Cost |
|---|---|---|---|
| 🥇 Chocolate Chip | $1,691,190 | $1,014,718 | $676,479 |
| 🥈 White Choco. Macadamia Nut | $974,540 | $527,879 | $446,667 |
| 🥉 Oatmeal Raisin | $776,570 | $434,882 | $341,693 |
| Snickerdoodle | $587,380 | $367,115 | $220,269 |
| Sugar | $506,340 | $295,370 | $210,978 |
| Fortune Cookie | $154,190 | $77,099 | $77,099 |
 
---
 
## 🛠️ Tools & Technologies
 
| Tool | Usage |
|---|---|
| ![Power BI](https://img.shields.io/badge/-Power%20BI-F2C811?logo=powerbi&logoColor=black&style=flat-square) | Dashboard design & interactive visuals |
| ![DAX](https://img.shields.io/badge/-DAX-6366F1?style=flat-square) | KPI calculations & aggregations |
| ![Power Query](https://img.shields.io/badge/-Power%20Query-0EA5E9?style=flat-square) | Data loading & transformation |
| ![Star Schema](https://img.shields.io/badge/-Star%20Schema-D97706?style=flat-square) | Relational data modeling |
 
---
 
## 📁 Project Structure
 
```
📦 Cookies-Sales-Analysis/
├── 📊 cookies.pbix                 ← Power BI dashboard file
├── 📸 screenshots/
│   ├── 01_Customers_Page.png
│   ├── 02_Orders_Products_Page.png
│   └── 03_Data_Model.png
└── 📄 README.md
```
 
---
 
## 🚀 How to Use
 
1. Download `cookies.pbix`
2. Open in **Power BI Desktop** (2023 or later recommended)
3. Navigate between the 2 pages using the **bottom tabs**: `Customers_` and `Orders & Products`
4. Use the **slicers** on each page to filter by Customer, State, Product, City, or Time Period
5. Hover over any visual to see **detailed tooltips**
---
 
## 👤 About the Author
 
**Abd Elfatah Gaber Ebrahim**  
Data Analysis Student · ITI (Information Technology Institute) · Egypt 🇪🇬
 
<div align="center">
<a href="https://www.linkedin.com/in/abd-elfatah-gaber-ebrahim/"><img src="https://img.shields.io/badge/LinkedIn-Abd%20Elfatah%20Gaber-0A66C2?style=for-the-badge&logo=linkedin" alt="LinkedIn"/></a>
<a href="https://github.com/abd-elfatah-gaber"><img src="https://img.shields.io/badge/GitHub-abd--elfatah--gaber-181717?style=for-the-badge&logo=github" alt="GitHub"/></a>
<a href="https://mostaql.com/u/Abdelfatah26"><img src="https://img.shields.io/badge/Mostaql-Abdelfatah26-1abc9c?style=for-the-badge" alt="Mostaql"/></a>
<a href="https://khamsat.com/user/abd_elfatah_gaber26"><img src="https://img.shields.io/badge/Khamsat-abd__elfatah__gaber26-e67e22?style=for-the-badge" alt="Khamsat"/></a>
 
</div>
---
 
<div align="center">
⭐ <strong>If you found this project useful, please consider giving it a star!</strong> ⭐
 
<em>Built with ❤️ using Power BI</em>
 
</div>
 
