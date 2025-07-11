# 🧹 Data Engineering

This project used Tableau Prep to clean, transform, and prepare the UK Online Retail dataset for analysis. The raw dataset contained over 500,000 transactions, which required several data quality steps before insights could be drawn. The key data engineering actions were:

- **Removed invalid entries** including:
- Rows with missing `CustomerID` values
- Transactions with negative quantities or prices
- Cancelled transactions identified by an "InvoiceNo" starting with "C"

- **Created a new field: `TotalPrice`** 
This was calculated as `Quantity × UnitPrice`, to represent the revenue per line item.

- **Filtered for UK-only transactions** 
This narrowed the scope to a single market for cleaner, more consistent insights and avoided distortion from low-volume international data.

- **Grouped product descriptions using spelling similarity** 
Tableau Prep’s “Group and Replace by Spelling” feature was used to consolidate near-duplicate product names caused by typos or inconsistent formatting. This helped prevent fragmentation in product-level analysis.

- **Exported cleaned dataset** 
The final data was exported as a `.hyper` file for use in Tableau Desktop for dashboarding and segmentation.

Tableau Prep’s visual ETL environment made it easy to document each cleaning decision and ensured a reproducible transformation pipeline. These steps were critical for enabling accurate customer segmentation and product performance analysis in the later stages of the project.
