## 🧹 Data Engineering (Tableau Prep)

The Online Retail dataset was prepared in **Tableau Prep** to create clean, consistent, and analysis-ready extracts for **Tableau Desktop dashboarding** and **RFM-based customer segmentation**. The workflow follows a maintainable ETL pattern: core transformations are applied once in an upstream cleaning stage, after which the pipeline branches into a **UK-only dataset** (used directly in the dashboard) and a **globally cleaned dataset** (retained for reuse and potential future extension).  
**Evidence:** Figures **DE1–DE6**.

---

### 1.0 Input (dataset ingestion and schema)

#### 1.1 Dataset ingestion
The workflow begins by ingesting the raw Online Retail transactions into Tableau Prep from the Excel source. Establishing a stable input step creates a consistent entry point so the same transformations can be rerun when the source data is refreshed.  
**Evidence:** Figure **DE1**.

#### 1.2 Schema confirmation and field selection
The input schema retains the business fields required for analysis—`InvoiceNo`, `StockCode`, `Description`, `Quantity`, `InvoiceDate`, `UnitPrice`, `CustomerID`, and `Country`—and excludes non-analytical technical fields (e.g., “Source Row Number”). This keeps the dataset focused on attributes that directly support revenue calculation, customer aggregation, product reporting, and time-series analysis.  
**Evidence:** Figure **DE1** (fields included/excluded).

---

### 2.0 Core cleaning & feature engineering (upstream shared transformations)

#### 2.1 Customer identifier quality control (exclude null `CustomerID`)
Records with missing `CustomerID` values are excluded to ensure every transaction can be attributed to an identifiable customer. This is essential for RFM segmentation and prevents anonymous rows from distorting frequency, recency, and monetary calculations.  
**Evidence:** Figure **DE2** (CustomerID null excluded).

#### 2.2 Quantity validity control (constrain `Quantity` to a valid range)
Quantity values are constrained using a range filter that enforces a non-negative lower bound (`Quantity >= 0`) and, as configured in the flow, an upper bound to reduce the influence of extreme outliers. This stabilises revenue KPIs and prevents anomalous records from disproportionately affecting trend analysis and “top customer/product” rankings.  
**Evidence:** Figure **DE2** (Quantity range filter).

#### 2.3 Revenue feature engineering (`Total Price`)
A derived line-item revenue metric `Total Price` is created using `Total Price = Quantity * UnitPrice`. The raw dataset contains quantities and unit prices but does not supply revenue per transaction line; this engineered feature underpins monthly revenue trends, customer monetary value calculations, and product/product-group revenue reporting in Tableau Desktop.  
**Evidence:** Figure **DE2** (calculated field creation).

#### 2.4 Description standardisation (uppercase)
Product descriptions are standardised by converting `Description` to uppercase. Normalising casing reduces false duplication caused by inconsistent formatting and improves the reliability of downstream grouping operations and the usability of dashboard filters.  
**Evidence:** Figure **DE2** (uppercase transformation).

#### 2.5 Description standardisation (remove extra spaces)
Extra spaces are removed from `Description` to reduce formatting noise. Whitespace normalisation further reduces false duplicates, improves grouping accuracy, and provides a cleaner filtering experience in Tableau Desktop.  
**Evidence:** Figure **DE2** (remove extra spaces).

---

### 3.0 UK ONLY branch (scoping and product description consolidation)

#### 3.1 Market scoping (filter `Country = "United Kingdom"`)
Following upstream cleaning, the workflow branches to create a UK-scoped dataset aligned to the dashboard’s intended analytical scope. A country filter retains only records where `Country = "United Kingdom"`, ensuring that KPIs, trends, and segmentation results reflect a single market and are not distorted by low-volume international transactions.  
**Evidence:** Figure **DE3** (UK filter applied).

#### 3.2 Product description consolidation (Group Values / spelling similarity)
Within the UK branch, Tableau Prep’s **Group Values** functionality is applied to `Description` using spelling similarity, consolidating near-duplicate product names caused by typos or inconsistent naming. This step materially reduces fragmentation in product reporting, evidenced by the reduction from **1,093** description values to **608** grouped values, strengthening the interpretability and accuracy of product rankings and product-group revenue analysis presented in the dashboard.  
**Evidence:** Figure **DE3** (grouping result showing 1093 → 608).

---

### 4.0 All Countries branch (global cleaned dataset)

#### 4.1 Global branch design (no additional transforms at node)
In parallel, the workflow retains an “All Countries” branch to output a globally cleaned dataset. No additional transformations are applied at the branch node (“Changes: 0”) because the baseline cleaning and feature engineering are performed upstream. This design avoids duplicating ETL logic and preserves a reusable cleaned dataset for future extensions such as international comparison, additional dashboards, or alternative analytical approaches.  
**Evidence:** Figure **DE4** (All Countries branch showing no additional changes).

---

### 5.0 Outputs (extract generation for Tableau Desktop)

#### 5.1 Output 1: UK cleaned extract (`Output.hyper`)
The UK-only branch is exported as a **Tableau Data Extract (`.hyper`)** to serve as the primary dataset for dashboarding and segmentation. The output step is configured to **save to file** and write a full extract named `Output.hyper`. The output preview confirms the extract contains the expected schema and includes the engineered field `Total Price`, enabling downstream analysis without repeatedly processing the raw Excel source.  
**Evidence:** Figure **DE5** (UK output configuration and preview).

#### 5.2 Output 2: Global cleaned extract (`Output 2.hyper`)
The all-countries branch is exported as a second **`.hyper` extract** (`Output 2.hyper`) using the same output-to-file configuration. This creates a reusable globally cleaned dataset with a consistent schema (including `Total Price`) to support future scope expansion, comparisons, or alternative dashboards while keeping the core transformation logic centralised in the upstream cleaning step.  
**Evidence:** Figure **DE6** (Global output configuration and preview).

#### 5.3 Reproducibility note (portability)
Both outputs are currently written to a machine-specific local path, as shown in the output configuration. The workflow remains reproducible because the transformation logic is fully captured in the `.tfl` flow; however, when the flow is executed on a different machine, the output location must be updated before running.  
**Evidence:** Figures **DE5–DE6** (output paths shown).

---

## ✅ Validation (ETL quality checks)
A set of sanity checks was used to confirm the ETL produced analysis-ready extracts. Output previews confirm both extracts contain the expected schema and include the engineered `Total Price` measure, and that the pipeline successfully writes `.hyper` outputs for Tableau Desktop consumption (Figures **DE5–DE6**). The cleaning step evidence confirms that null `CustomerID` records are excluded and that `Quantity` is constrained to a valid range, reducing the likelihood of invalid transactions biasing revenue KPIs (Figure **DE2**). UK scoping is validated by the country filter applied in the UK branch, and the effectiveness of product description consolidation is evidenced by the documented reduction in distinct description values from **1,093** to **608** (Figure **DE3**). Together, these checks provide confidence that the outputs are consistent, interpretable, and fit for customer segmentation and product performance reporting.
