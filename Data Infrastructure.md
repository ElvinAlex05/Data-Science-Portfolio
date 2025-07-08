# 🛠️ Data Infrastructure and Tools

This project was developed using a simple but effective toolchain designed for cleaning, analysing, and visualising retail transaction data. The infrastructure was chosen to prioritise accessibility, speed, and clarity — aligning with common industry practices for business-focused data science.

## 🔧 Tools Used

- **Tableau Prep** 
Used for ETL (Extract, Transform, Load) processes. Enabled the cleaning of over 500,000 transactions, removal of nulls and duplicates, filtering for UK-based customers, and creation of calculated fields (such as `TotalPrice`). Tableau Prep also allowed grouping of inconsistent product descriptions using the "Group and Replace by Spelling" feature.

- **Tableau Desktop** 
Used for data analysis and dashboard creation. Enabled rapid development of interactive visualisations such as revenue trends, top products, and RFM-based customer segments. Calculated fields and filters were used to support segmentation logic and insight delivery.

- **GitHub** 
Used for version control and hosting the portfolio. The final project, including the Tableau Prep flow, dashboard, summary, and supporting documentation, is publicly available and structured for ease of navigation and review.

## 🔁 Data Flow Overview

The data infrastructure followed this sequence:

1. **Ingestion**: Loaded the UK Online Retail dataset (Excel file format)
2. **Transformation (ETL)**: 
- Cleaned and filtered data in Tableau Prep 
- Created new fields (e.g., `TotalPrice`) 
- Grouped product names
3. **Export**: Outputted clean dataset as `.hyper` file
4. **Analysis and Visualisation**: Built dashboards and segmentation logic in Tableau Desktop
5. **Delivery**: Hosted results and documentation in GitHub

This structure ensured the project followed the "3 I’s" of data science — interaction with real-world data, iteration through transformation and insight, and independent execution using modern tools.
