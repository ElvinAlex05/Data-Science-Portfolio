## 📊 Dashboard & Visualisation 

The **UK Online Retail Performance Dashboard** was built in Tableau Desktop to communicate sales performance and customer value to non-technical stakeholders who need quick, defensible answers in meetings. 
<img width="1500" height="1000" alt="Retail Dashboard Screenshot" src="https://github.com/user-attachments/assets/4cc76330-70c4-4e25-8843-e43b3ea1253f" />


The layout follows a simple top-to-bottom reading order: product performance and revenue context first, then customer value and segmentation. 
<img width="1588" height="655" alt="image" src="https://github.com/user-attachments/assets/3b64ffa1-144c-4f3b-8839-a911a5b2fd1d" />

Ranked **horizontal bar charts** are used for Top Products/Customers and Sales by Product Group because length-based comparisons support fast, accurate ranking and reduce cognitive load when scanning for “top drivers” (Few, 2013).
<img width="1636" height="455" alt="image" src="https://github.com/user-attachments/assets/816f7c81-e170-420d-9377-f29a522d502d" />

A **line chart** is used for Monthly Revenue because it communicates change over time effectively and supports identification of peaks and dips (Munzner, 2014).

Interactivity is deliberately constrained to business questions via filters (e.g., Product Name, Month, Customer ID and segment filters), enabling drill-down without overwhelming users—consistent with dashboard design guidance (Tableau, n.d.). 

<img width="1623" height="1065" alt="image" src="https://github.com/user-attachments/assets/b2fc463f-3b54-4ed0-a6b8-753ebd06b26e" />
Two segmentation views (spend tiers and RFM segments) translate analysis into action by making retention/targeting groups visible at a glance (Cheng and Chen, 2009). Alternative visuals such as treemaps/packed bubbles were avoided because they weaken precise comparison for ranking tasks compared with bars (Few, 2013). Consistent titles, labels and aligned axes connect the visuals to the written narrative and reduce misinterpretation risk.




---

## References (Harvard)

Cheng, C.-H. and Chen, Y.-S. (2009) ‘Classifying the segmentation of customer value via RFM model and RS theory’, *Expert Systems with Applications*, 36(3, Part 1), pp. 4176–4184. doi:10.1016/j.eswa.2008.04.003.

Few, S. (2013) *Information Dashboard Design: Displaying Data for At-a-Glance Monitoring*. 2nd edn. Berkeley, CA: Analytics Press.

Munzner, T. (2014) *Visualization Analysis and Design*. Boca Raton, FL: CRC Press.

Tableau (n.d.) *Best Practices for Effective Dashboards*. Available at: https://help.tableau.com/current/pro/desktop/en-us/dashboards_best_practices.htm (Accessed: 3 January 2026).
