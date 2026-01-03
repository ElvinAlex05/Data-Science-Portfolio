## 🧰 Data Infrastructure and Tools (≤300 words)

This project used a lightweight, end-to-end toolchain to move from raw retail transactions to an interactive, assessable analytics artefact: **Excel source → Tableau Prep (ETL) → `.hyper` extract → Tableau Desktop dashboard → GitHub portfolio**. The design choice prioritised fast iteration, transparent transformation steps, and stakeholder-ready delivery.

**Tableau Prep** was used for ETL because its visual, step-based workflow makes cleaning and feature engineering decisions explicit (e.g., filters, calculated fields, grouping), which supports auditability and reviewer comprehension compared with ad-hoc spreadsheet edits (Tableau, n.d.-a). This is advantageous for a portfolio context where evidence of process matters. The main limitations are that complex logic and automated testing are easier in code, and local file paths can reduce portability unless carefully managed.

Cleaned data were exported as **Tableau `.hyper` extracts** to provide stable inputs for dashboarding and improve analytical performance compared with repeatedly querying the raw Excel file (Tableau, n.d.-b; Tableau, n.d.-c). **Tableau Desktop** was then used to build interactive views and segmentation outputs because it supports rapid KPI prototyping, consistent aggregation logic, and controlled interactivity for non-technical users.

**Alternatives considered:** Power BI could deliver a similar pipeline using **Power Query** for ETL, which is often beneficial in Microsoft-first environments due to tight integration across the stack (Microsoft, 2025a; Microsoft, 2025b). A code-first approach using Python (e.g., pandas) would increase reproducibility, testing, and automation potential, but adds environment overhead and can be less accessible to non-technical reviewers (pandas, 2025a).

**GitHub** was selected instead of a personal website because it provides version control, traceability, and structured review workflows via pull requests, improving quality control over time (GitHub, n.d.-a; GitHub, n.d.-b). If a web-style presentation is needed, the same repository can be published using **GitHub Pages**, avoiding separate hosting and deployment complexity (GitHub, n.d.-c).

---

## References (Harvard)

GitHub (n.d.-a) *About Git*. Available at: https://docs.github.com/en/get-started/using-git/about-git (Accessed: 3 January 2026).

GitHub (n.d.-b) *About pull requests*. Available at: https://docs.github.com/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/about-pull-requests (Accessed: 3 January 2026).

GitHub (n.d.-c) *What is GitHub Pages?* Available at: https://docs.github.com/en/pages/getting-started-with-github-pages/what-is-github-pages (Accessed: 3 January 2026).

Microsoft (2025a) *What is Power Query?* Available at: https://learn.microsoft.com/en-us/power-query/power-query-what-is-power-query (Accessed: 3 January 2026).

Microsoft (2025b) *Query overview in Power BI Desktop*. Available at: https://learn.microsoft.com/en-us/power-bi/transform-model/desktop-query-overview (Accessed: 3 January 2026).

pandas (2025a) *User guide: Missing data*. Available at: https://pandas.pydata.org/docs/user_guide/missing_data.html (Accessed: 3 January 2026).

Tableau (n.d.-a) *Clean and Shape Data in Tableau Prep*. Available at: https://help.tableau.com/current/prep/en-us/prep_clean.htm (Accessed: 3 January 2026).

Tableau (n.d.-b) *Extract Your Data*. Available at: https://help.tableau.com/current/pro/desktop/en-us/extracting_data.htm (Accessed: 3 January 2026).

Tableau (n.d.-c) *Tableau Server Data Engine (Hyper)*. Available at: https://help.tableau.com/current/server/en-us/data_engine2_intro.htm (Accessed: 3 January 2026).
