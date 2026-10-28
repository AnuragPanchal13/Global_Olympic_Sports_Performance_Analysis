# Global Olympic Sports Performance Analysis

**Author:** Anurag Malasa  
**Domain:** Data Analytics & Business Intelligence  
**Tools & Technologies:** Tableau Public, GitHub
**Project Status:** Completed  

---

## 1. Project Overview & Problem Statement
The Olympic Games represent the pinnacle of global athletic competition, generating vast volumes of historical data spanning athlete demographics, historical medal tallies, sporting disciplines, and national participation records. 

However, evaluating true athletic performance requires moving beyond simple aggregate medal counts. Factors such as athlete-to-medal efficiency, geographic dominance, gender representation parity, and seasonal disparities (Summer vs. Winter) need structured multi-dimensional analysis.

This project delivers a comprehensive analytical framework leveraging multi-table relational modeling in Tableau Public to extract strategic insights across Olympic history, culminating in an integrated interactive visual dashboard suite and web deployment.

---

## 2. Dataset Architecture & Data Relationships
The analysis synthesizes four core datasets linked through primary-foreign key relationships:

1. **`alltime_country_rankings.csv`**: Contains country-level aggregate metrics, NOC codes, regional classifications, total medals, gold/silver/bronze splits, and average efficiency percentages.
2. **`athletes.csv`**: Granular athlete-level records including Athlete ID, Name, Gender, Sport, Sport Category, Training Hours, BMI, and peak age.
3. **`games_summary.csv`**: High-level edition statistics per Olympic year, host city, season, and athlete participation counts.
4. **`medal_results.csv`**: Granular event results mapped to athlete IDs, competition years, medal types, and sporting disciplines.

### Data Relationships in Tableau:
* `alltime_country_rankings.csv` $\leftrightarrow$ `games_summary.csv` via `[noc_code]` / `[Country]`
* `games_summary.csv` $\leftrightarrow$ `medal_results.csv` via `[year]`
* `medal_results.csv` $\leftrightarrow$ `athletes.csv` via `[athlete_id]`

---

## 3. Calculated Fields & Metrics Defined
To derive actionable metrics, three advanced calculated fields were engineered in Tableau:

1. **Medal Efficiency Percentage (`Medal Efficiency Pct`):**
   $$\text{Medal Efficiency Pct} = \frac{\sum(\text{Total Medals})}{\sum(\text{Games Entered})} \times 100$$
   *Purpose:* Evaluates national consistency by tracking medal yield per edition entered rather than raw volumetric tallies.

2. **Weighted Medal Points (`Medal Points`):**
   $$\text{Medal Points} = (3 \times \text{Total Gold}) + (2 \times \text{Total Silver}) + (1 \times \text{Total Bronze})$$
   *Purpose:* Standardizes national standing by rewarding medal quality over raw count.

3. **Average Medals per Athlete (`Avg Medals per Athlete`):**
   $$\text{Avg Medals per Athlete} = \frac{\text{COUNT}(\text{Medal Results})}{\text{COUNTD}(\text{Athlete Id})}$$
   *Purpose:* Measures squad productivity and multi-medal impact across different disciplines.

---

## 4. Visualizations & Analytical Worksheets (8 Visuals)

### Visual 1: Medals Performance Over Time (Line Chart)
* **Type:** Continuous Trend Line Chart with Mark Labels.
* **Dimensions & Measures:** Columns: `Year`, Rows: `SUM(Total Medals)`.
* **Insight:** Visualizes multi-decade medal trajectory, highlighting cyclical peaks, game expansions, and historical participation shifts.

### Visual 2: Top 10 Countries by Medals (Horizontal Bar Chart)
* **Type:** Sorted Horizontal Bar Chart with Top 10 Filter.
* **Dimensions & Measures:** Rows: `Country`, Columns: `SUM(Total Medals)`.
* **Insight:** Highlights dominance led by the United States (735) and China (696), reflecting historical athletic infrastructure investments.

### Visual 3: Medal Breakdown by Country (Stacked Bar Chart)
* **Type:** Segmented Stacked Bar Chart.
* **Dimensions & Measures:** Rows: `Country`, Columns: `Measure Values` (`SUM(Total Gold)`, `SUM(Total Silver)`, `SUM(Total Bronze)`), Color: `Measure Names`.
* **Insight:** Deconstructs medal portfolios to reveal which nations convert podium finishes into top-tier gold achievements.

### Visual 4: Medal Performance by Region (Horizontal Bar Chart)
* **Type:** Categorical Bar Chart (Descending Sort).
* **Dimensions & Measures:** Rows: `Region`, Columns: `SUM(Total Medals)`.
* **Insight:** Demonstrates European aggregate dominance (2,622 medals) followed by Asia (1,508) and North America (960).

### Visual 5: Summer vs. Winter Medal Totals (Side-by-Side Bar Chart)
* **Type:** Dual-Category Comparative Bar Chart.
* **Dimensions & Measures:** Columns: `Season`, Rows: `SUM(Total Medals)`, Color: `Season`.
* **Insight:** Quantifies seasonal distribution disparity, with Summer Games capturing 3,029 medals versus 2,596 for Winter Games.

### Visual 6: Top 10 Countries by Medal Efficiency (Horizontal Bar Chart)
* **Type:** Efficiency Metric Bar Chart.
* **Dimensions & Measures:** Rows: `Country`, Columns: `AVG(Avg Efficiency Pct)` (Top 10 Filter).
* **Insight:** Surfaced nations with smaller delegation sizes that maintain exceptional conversion rates (e.g., Latvia, Philippines, Monaco).

### Visual 7: Athlete Gender Distribution (Vertical Bar Chart)
* **Type:** Demographic Composition Bar Chart.
* **Dimensions & Measures:** Columns: `Gender`, Rows: `CNTD(Athlete Id)`.
* **Insight:** Evaluates progress toward gender parity, recording 4,179 male athletes and 3,821 female athletes across analyzed records.

### Visual 8: Athlete Participation by Sport (Horizontal Bar Chart)
* **Type:** Volumetric Distribution Bar Chart.
* **Dimensions & Measures:** Rows: `Sport`, Columns: `CNTD(Athlete Id)`.
* **Insight:** Highlights high-capacity disciplines such as Athletics, Swimming, and Gymnastics compared to specialized niche sports.

---

## 5. Tableau Dashboards & Story Design

### Dashboard 1: Global Performance
* **Components:** Visuals 1, 2, 3, and 4 in a 2x2 responsive tiled grid.
* **Interactivity:** Region-level cross-filtering ("Use as Filter" enabled) allowing global metrics to dynamically calibrate when a specific continent or territory is selected.

### Dashboard 2: Regional Analysis & Participation Metrics
* **Components:** Visuals 5, 6, 7, and 8 in a 2x2 structured layout.
* **Interactivity:** Seasonal toggle cross-filtering (`Summer` vs. `Winter`) instantly recalculating gender representation and discipline volumes.

### Olympic Performance Story (4 Story Points)
1. **Scene 1:** *Top 10 Countries by Medal Achievements* — Global podium dominance breakdown.
2. **Scene 2:** *Medal Performance Over Time* — Historical progression across Olympic eras.
3. **Scene 3:** *Summer vs. Winter Olympics* — Seasonal split and discipline comparative analysis.
4. **Scene 4:** *Regional Medal Performance* — Continental aggregation and geopolitical distribution.

---

## 6. Web Application Integration (Flask Architecture)
The project embeds the Tableau Public visualizations into a responsive web application built with Python Flask:

* **Backend (`app.py`):** Flask routing serving modular templates (`/`, `/dashboard1`, `/dashboard2`, `/story`).
* **Frontend:** Responsive layout rendered with modern CSS grid/flexbox, embedding Tableau JavaScript API and responsive `<object>` embed scripts.
* **Cross-Origin Compatibility:** Tableau Public cloud-hosted workbook seamlessly rendered within secure `iframe` wrappers.

---

## 7. Key Findings & Business Impact
1. **Geographic Concentration:** Over 65% of all historical Olympic podium finishes are concentrated within European and North American national Olympic committees.
2. **Efficiency Disconnect:** Raw medal counts favor large delegations, but per-athlete efficiency highlights compact, high-performing squads that achieve superior conversion.
3. **Gender Convergence:** Longitudinal data indicates a steady convergence toward 50/50 gender representation across modern Summer and Winter disciplines.

---

## 8. Repository Directory Structure
```
Project-1/
├── 1. Ideation Phase/
├── 2. Requirement Analysis/
├── 3. Project Design Phase/
├── 4. Project Planning Phase/
├── 5. Project Development Phase/
├── 6. Performance Testing/
├── 7.Project Documentation/
│   └── project_report.md
├── 8.Project Demonstration/
├── alltime_country_rankings.csv
├── athletes.csv
├── games_summary.csv
├── medal_results.csv
└── README.md
```