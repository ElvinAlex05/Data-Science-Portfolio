## 🧹 Data Engineering (ETL in Tableau Prep) (≤300 words)

The Online Retail dataset was prepared in Tableau Prep using a repeatable ETL flow so the dashboard and customer segmentation are built on consistent, analysis-ready data. The ETL was planned around three requirements: transactions must be attributable to customers, revenue must be computed consistently at line level, and product labels must be standardised to avoid fragmented reporting.

**Extract:** The raw Excel transaction table was ingested into Tableau Prep and limited to the business fields required for analysis (InvoiceNo, StockCode, Description, Quantity, InvoiceDate, UnitPrice, CustomerID, Country), excluding non-analytical technical fields to keep the dataset focused and reduce noise in downstream calculations.

**Transform:** Core transformations were applied once upstream so both outputs inherit the same baseline. Rows with null CustomerID were removed using a filter because customer-level aggregation (e.g., recency, frequency and monetary summaries) requires every transaction to be linkable to an identifiable customer. Quantity was constrained with a range filter (including a non-negative lower bound) to remove invalid values and limit anomalies that can bias revenue KPIs, reflecting established data-cleaning practice where erroneous records can propagate into analytics if not controlled (Rahm and Do, 2000). A calculated field, Total Price = Quantity × UnitPrice, was created to provide a consistent revenue metric for product ranking, time-series revenue, and customer value calculations. Description was standardised (Make Uppercase; Remove Extra Spaces) to reduce false duplicates from inconsistent text formatting and improve grouping/filter consistency (Tableau, n.d.-a).

Task-specific preprocessing was implemented via branching. The UK branch filtered Country = “United Kingdom” to align scope with the dashboard and applied Group Values (spelling similarity) to consolidate near-duplicate descriptions (e.g., 1,093 → 608). A parallel All Countries branch applied no additional transformations at the branch node, preserving a reusable globally cleaned dataset.

**Load + validation:** Both branches were exported as `.hyper` extracts for Tableau consumption (Tableau, n.d.-b; Tableau, n.d.-c). Validation checked expected schema (including Total Price), correct UK-only scoping/grouping, and successful extract generation.

---

## References (Harvard)

Rahm, E. and Do, H.H. (2000) ‘Data Cleaning: Problems and Current Approaches’, *IEEE Data Engineering Bulletin*, 23(4), pp. 3–13. Available at: https://dbs.uni-leipzig.de/files/research/publications/2000-1/pdf/TBDE2000.pdf (Accessed: 3 January 2026).

Tableau (n.d.-a) *Clean and Shape Data in Tableau Prep*. Available at: https://help.tableau.com/current/prep/en-us/prep_clean.htm (Accessed: 3 January 2026).

Tableau (n.d.-b) *Extract Your Data*. Available at: https://help.tableau.com/current/pro/desktop/en-us/extracting_data.htm (Accessed: 3 January 2026).

Tableau (n.d.-c) *Tableau Server Data Engine (Hyper)*. Available at: https://help.tableau.com/current/server/en-us/data_engine2_intro.htm (Accessed: 3 January 2026).
