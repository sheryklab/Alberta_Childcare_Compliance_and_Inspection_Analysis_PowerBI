# Alberta Childcare Compliance and Inspection Analysis Power BI Dashboard

Provincial childcare oversight analysis using open data to explore compliance, inspections, enforcement, and program distribution in Alberta.

---

## Executive Summary

This project analyzes eighteen months of childcare inspection records from the Government of Alberta. I transformed one large dataset into a structured Power BI dashboard that highlights trends, patterns, and quality concerns across the province. My goal is to make oversight transparent and give both government staff and the public a clear view of how childcare programs are performing in real time.

---

## Business Problem

Childcare quality affects children, families, and communities. Oversight data exists, but the raw structure makes it difficult to understand which programs comply with regulations, which areas require more attention, and where enforcement is increasing.  
Government teams need a clear view of compliance activity, city-level differences, inspection reasons, and enforcement outcomes. Parents also benefit from accessible information.

This dashboard organizes complex licensing and inspection data into a set of pages that answer direct questions about sector performance across Alberta.

---

## Dataset and Source

**Source:** Government of Alberta Open Data Portal  
**Dataset:** Child Care Information (June 2025 snapshot)  
**Time Range:** January 2024 to June 2025  

Dataset link:  
https://open.alberta.ca/opendata/childcareinformation/resource/db56e8fd-8c00-4a40-b190-e00109af8970

The dataset includes program information, inspection events, inspection reasons, non-compliance outcomes, enforcement actions, and program type classifications.

**Limitations:** Some records contain blanks or partial enforcement details. The dataset is a point-in-time extract. Even with these limitations, it provides a reliable view of provincial oversight activity.

---

## Methodology

I cleaned and reshaped the original dataset in Power Query and separated it into multiple tables to build a stable star schema model in Power BI.  
The full cleaning workflow is documented here:

➡️ **[Data Cleaning Notes](docs/data_cleaning_notes.md)**

---

## Data Model

The dashboard uses a star schema with **Inspections** as the fact table and six dimension tables, consistent with the model diagram included in this repository.  
Complete table definitions and relationship logic are available here:

➡️ **[Data Model Details](docs/model_details.md)**

---

## Analytical Logic

The dashboard uses DAX measures to calculate inspection totals, compliance rates, non-compliance volumes, enforcement activity, and program capacity metrics.

A list of core measures and example DAX is included here:

➡️ **[DAX Measures List](docs/dax_measures_list.md)**

---

## Visualization Strategy

The dashboard follows a clean, government-style reporting layout with accessible visuals.

Included visuals:
- Metric cards for key indicators  
- Dual line chart for inspection and compliance trends  
- Bar charts comparing cities by capacity and compliance  
- Filled map highlighting enforcement hotspots  
- Donut and bar charts for inspection reasons and enforcement actions  
- Program type and capacity distribution charts  
- Interactive filters for year, month, city, and program type  
- A detailed table for record-level analysis

---

## Dashboard Overview

### Provincial Summary and Trends
Shows:
- Total programs  
- Total inspections  
- Total capacity  
- Compliance and enforcement rates  
- Monthly inspection and compliance trends  

### Geographic and City Insights
Shows:
- Top cities by total capacity  
- Lowest compliance cities  
- Enforcement hotspots across Alberta  

### Quality and Enforcement
Shows:
- Inspection reasons  
- Enforcement actions  
- Comparison of compliance and enforcement trends  

### Program Type and Capacity Distribution
Shows:
- Total capacity by program type  
- Average capacity by program type  
- Program count distribution  
- Program distribution across city categories  

### Childcare Overview Table
Record-level details:
- Program name  
- City  
- Capacity  
- Inspection dates  
- Compliance results  
- Enforcement actions  

---

## Key Insights

- Provincial compliance stays mostly between 65 and 70 percent.  
- Routine inspections are the most common, but complaint-related inspections trigger more enforcement.  
- Orders to Remedy are the most frequent enforcement outcome.  
- Calgary and Edmonton hold most capacity but do not always lead in compliance.  
- Smaller towns show more consistent performance.  
- Facility-based programs hold most provincial childcare spaces.  
- Family day homes and group family programs are smaller but stable.

---

## Business Recommendations

- Support cities that show repeated low compliance.  
- Expand early interventions where complaint-driven inspections are increasing.  
- Use smaller municipalities as examples of consistent oversight performance.  
- Strengthen capacity planning for family day homes.  
- Monitor enforcement spikes to identify systemic issues.

---

## Technical Skills Used

- Power BI  
- Power Query  
- DAX  
- Data modeling  
- Data cleaning  
- Open data analysis  
- Visual analytics  
- Trend and comparative analysis  

---

## Limitations and Next Steps

Limitations: 
- Dataset is a single time-point extract.  

Next steps:
- Build multi-year comparisons.  
- Analyze program openings and closures.  
- Segment programs by size categories. Program size often influences workload, staffing, risk level, and quality indicators. 
- Add demographics or regional context if future public datasets support it.

---

## Live Dashboard Link

🔗 https://www.sheryk.com/ABchildcare-Data 

---

## Repository Structure

- `README.md`  
- `LICENSE`  
- `assets/` — screenshots  
- `docs/` — cleaning notes, model details, and DAX summary  
- `reports/` — full project Dashboard  

---

## License and Attribution

Data provided by the Government of Alberta under the Alberta Open Data License.

This project is licensed under the **Creative Commons Attribution–NonCommercial–NoDerivatives (CC BY-NC-ND)** license.  
Users may view and share this work with credit. No modifications or commercial use are allowed.

---

## About the Author

I am a data analyst who understands both the technical side and the childcare domain. I built this project to turn raw inspection records into something practical and readable. My work focuses on clarity, accuracy, and meaningful questions. 
You can connect with me on LinkedIn or explore more of my work through my portfolio.

