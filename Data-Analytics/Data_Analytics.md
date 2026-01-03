## 📈 Data Analytics (≤400 words)

Analysis was conducted in Tableau Desktop using the cleaned `.hyper` extracts from Tableau Prep to answer three business questions: (1) which products and customers drive revenue, (2) how revenue changes over time, and (3) whether customers can be segmented into actionable groups for retention and targeting. A simple scientific-method structure was used: define hypotheses, operationalise measures, analyse outputs, and evaluate whether results support decisions.

Three hypotheses guided the work: **H1** revenue is concentrated in a small subset of products/customers; **H2** revenue varies over time with identifiable peaks; **H3** behavioural segmentation produces meaningful groups. Revenue was operationalised as `Total Price = Quantity × UnitPrice` using Tableau calculated fields so all charts aggregate a consistent KPI (Tableau, n.d.). H1 was tested using ranked views of product groups, products and customers to identify concentration and prioritisation opportunities. H2 was assessed by aggregating Total Price by month to observe trend and seasonality patterns; this supports planning (campaign timing, stock decisions) while recognising the analysis is observational and does not infer causality.

Customer segmentation used **RFM** because it is widely adopted and interpretable for stakeholder action. Recency was computed as days since the most recent purchase (relative to the dataset maximum date), Frequency as purchase count per customer, and Monetary as total spend per customer. Each dimension was scored 1–5 using explicit bins in Tableau and mapped to segment labels (e.g., Champions, Loyal, Potential, At Risk, Lost), which are visible on the dashboard for immediate action (Cheng and Chen, 2009). Evaluation focused on practical validity: segment distributions were checked for face validity (e.g., higher-value segments exhibit higher Monetary/Frequency) and for stability when adjusting the dashboard date range and filters. Key limitations are sensitivity to scoring thresholds and the absence of causal drivers.

Ethically, CustomerID was treated as pseudonymous and analysis was restricted to the minimum fields required for the stated purpose, aligning with UK GDPR principles including purpose limitation and data minimisation (ICO, 2022; ICO, 2023). Alternative approaches (e.g., k-means clustering on behavioural features, cohort analysis, or customer lifetime value modelling) were considered, but RFM was selected for transparency and ease of adoption in a dashboard context.

---

## References (Harvard)

Cheng, C.-H. and Chen, Y.-S. (2009) ‘Classifying the segmentation of customer value via RFM model and RS theory’, *Expert Systems with Applications*, 36(3, Part 1), pp. 4176–4184. doi:10.1016/j.eswa.2008.04.003.

ICO (2022) *Purpose limitation*. Available at: https://ico.org.uk/for-organisations/uk-gdpr-guidance-and-resources/data-protection-principles/a-guide-to-the-data-protection-principles/purpose-limitation/ (Accessed: 3 January 2026).

ICO (2023) *A guide to the data protection principles*. Available at: https://ico.org.uk/for-organisations/uk-gdpr-guidance-and-resources/data-protection-principles/a-guide-to-the-data-protection-principles/ (Accessed: 3 January 2026).

Tableau (n.d.) *Create a calculated field*. Available at: https://help.tableau.com/current/pro/desktop/en-us/calculations_calculatedfields_formulas.htm (Accessed: 3 January 2026).
