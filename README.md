# EV Charging Operations & Utilization Analytics

An end-to-end analytics project using MySQL and Power BI to analyze 72,856 EV charging sessions, uncover demand patterns, evaluate charger utilization, and identify opportunities for more effective charging infrastructure planning.

## Problem Statement

As electric vehicle adoption grows, charging operators need to understand how charging demand varies across locations, charger types, time periods, and users to make informed infrastructure and operational decisions.

This project investigates where demand is concentrated, when charging activity peaks, which chargers handle the highest demand, and how demand is distributed across users. The objective is to identify utilization patterns and translate them into actionable insights for capacity planning, charger prioritization, and operational efficiency.

## Key Findings and Insights

### **1. Charging Demand Concentration by Charger Type**

Type 0 chargers accounted for approximately **77.7% of total demand**, compared with 22.3% for Type 1 chargers. This substantial difference highlights the importance of evaluating charger deployment against observed usage patterns.

### **2. Evening Peak Demand**

Evening Peak accounted for **41.79% of total demand**, followed closely by Off-Peak at 41.37%. Morning Peak contributed 16.84%. Evening Peak also recorded the highest average demand per session at 19.59, while Off-Peak had the highest session volume, with 31,942 sessions.

### **3. User Demand Concentration**

SQL window functions and demand-decile segmentation revealed that the top 10% of users accounted for approximately **78.64% of total demand**. This concentration highlights the importance of understanding high-demand user segments when assessing charging utilization.

### **4. Location-Level Demand**

Apartments recorded the highest total demand at 263,163.46, while Public Areas recorded the highest session volume at 14,082. These findings show why infrastructure planning should consider both total demand and charging frequency.

### **5. Monthly Charging Trends**

Charging demand peaked in August 2022, reaching 143,041.27 across 8,083 sessions. Monthly trend analysis helps identify periods of higher utilization and supports capacity planning.

## Power BI Dashboard

The interactive dashboard summarizes charging activity through KPI cards and six analytical visuals.

![EV Charging Operations & Utilization Analytics](ev_Dashboard.png)

## Methodology

1. **Data Loading:** Imported the charging transaction dataset into MySQL and reviewed its structure and data types.
2. **Exploratory Data Analysis:** Examined session volumes, demand distributions, charger activity, location categories, and user identifiers.
3. **SQL-Based Risk and Operations Analysis:** Performed eight SQL analyses covering charger performance, location-level demand, user contributions, time-based demand, monthly trends, charger rankings, user activity trends, and demand concentration.
4. **Analytical Segmentation:** Categorized charging periods and segmented users into demand deciles using SQL window functions.
5. **KPI Development:** Created DAX measures and a calculated column to support dashboard metrics and time-period analysis.
6. **Dashboard Development:** Built an interactive Power BI dashboard to present key metrics, comparisons, and trends.

## SQL Analysis

MySQL was used to conduct eight analyses:

- High-demand charger analysis
- Demand share by location
- Top users by demand contribution
- Peak versus off-peak charging demand
- Monthly charging demand trends
- Charger performance ranking within locations
- User activity trends using `LAG()`
- Demand concentration by user decile using `NTILE(10)`

SQL techniques included aggregations, `GROUP BY`, `HAVING`, subqueries, common table expressions (CTEs), window functions, `RANK()`, `LAG()`, `NTILE()`, date and time functions, and percentage calculations.

## Business Implications

- **Infrastructure expansion:** Prioritize locations with consistently high demand and session volumes, particularly apartments and public charging areas.
- **Peak-period capacity planning:** Evaluate capacity during evening peak hours while considering the substantial demand that also occurs outside peak periods.
- **Charger performance monitoring:** Identify heavily utilized chargers for preventive maintenance, reliability monitoring, and capacity assessment.
- **Charger deployment:** Use observed demand differences between charger types to inform future deployment decisions.
- **User segmentation:** Examine high-demand user groups to better understand utilization concentration and potential customer usage patterns.
- **Operational planning:** Combine demand volume, session frequency, and monthly trends rather than relying on a single metric when making infrastructure decisions.

## Limitations

- The dataset covers commercial EV charging sessions in South Korea from September 30, 2021, to September 30, 2022; findings may not generalize to other markets or periods.
- `UserID = 0` represents unsubscribed customers in the original dataset and should not be interpreted as one individual user.
- Charger type and location categories are analyzed as provided in the dataset; their underlying technical specifications are not established by this analysis.
- The analysis is primarily descriptive. Observed patterns identify associations and concentrations but do not establish causation or prove future demand.
- Demand concentration and historical utilization patterns alone are insufficient to determine the optimal location or capacity for new charging infrastructure.

## Conclusion

This project combines MySQL-based operational and behavioral analysis with Power BI visualization to examine EV charging utilization across 72,856 sessions. The findings highlight differences in demand by charger type, location, time period, and user segment. By translating these patterns into actionable metrics and recommendations, the project demonstrates how data analytics can support evidence-based charging infrastructure planning and operational decision-making.

## Tech Stack

MySQL, SQL, Power BI, DAX, GitHub

## Data Source

**Dataset:** A dataset for multi-faceted analysis of electric vehicle charging transactions

**Authors:** Keon Baek, Eunjung Lee, and Jinho Kim

**Publication:** *Scientific Data* (2024)

**Research DOI:** https://doi.org/10.1038/s41597-024-02942-9

**Dataset:** https://figshare.com/articles/dataset/A_dataset_for_multi-faceted_analysis_of_electric_vehicle_charging_transactions/22495141

**License:** CC BY 4.0

The dataset contains 72,856 commercial EV charging sessions collected in South Korea between September 30, 2021, and September 30, 2022. Each row represents an individual charging session and includes user, charger, location, time, duration, and demand information.
