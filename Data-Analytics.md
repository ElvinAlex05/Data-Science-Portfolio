# 📊 Data Analytics

This section outlines the analysis performed on the cleaned retail dataset, focusing on customer behaviour, revenue trends, and product performance. The insights below were developed in Tableau Desktop using the datasets prepared in Tableau Prep.

---

## 🔹 Key Analytical Objectives

- Identify top-selling products
- Understand monthly revenue trends
- Discover high-value customers
- Segment customers by value and engagement using RFM analysis
- Support business decision-making with clear visual insights

---

## 📈 Charts and Insights Developed

### 🏆 1. Top 10 Selling Products

- Shows the products that generated the highest total revenue
- Based on the `TotalPrice` metric (Quantity × UnitPrice)
- Helps identify customer demand and product performance

**Chart Type:** Bar chart 
**Dataset:** Global

---

### 📅 2. Monthly Revenue Trend

- Displays revenue patterns over time by month
- Useful for identifying peak periods and seasonality

**Chart Type:** Line chart 
**Dataset:** Global

---

### 🛍️ 3. Sales by Product Category

- Products were grouped by description using Tableau Prep (UK only)
- Aggregated revenue by product grouping
- Provides a higher-level overview of sales distribution

**Chart Type:** Bar chart 
**Dataset:** UK only

---

### 👤 4. Top Customers by Revenue

- Lists customers who contributed the most to total revenue
- Useful for prioritising VIP or repeat customers

**Chart Type:** Bar chart (CustomerID vs Revenue) 
**Dataset:** Global

---

### 🧠 5. Customer Segmentation using RFM

Implemented RFM (Recency, Frequency, Monetary) analysis using calculated fields:

- **Recency:** Days since last purchase 
- **Frequency:** Number of purchases 
- **Monetary:** Total amount spent

Customers were scored on each dimension (1–5), and total scores were used to segment them:

| RFM Score Range | Segment |
|-----------------|--------------|
| 13–15 | Champions |
| 10–12 | Loyal |
| 7–9 | Potential |
| 4–6 | At Risk |
| 3 | Lost |

**Chart Type:** Bar chart (Customer Segment vs Count) 
**Dataset:** Global

---
