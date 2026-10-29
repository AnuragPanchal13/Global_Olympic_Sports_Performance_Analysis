# Global Olympic Sports Performance Analysis

An end-to-end interactive sports analytics project analyzing historical Olympic Games data. This project explores country-level medal dominance, seasonal trends (Summer vs. Winter), regional athletic performance, and athlete demographics using Tableau visualizations and an interactive web portal.

---

## 📌 Project Links

* **Live Tableau Public Dashboard**: [View on Tableau Public](https://public.tableau.com/views/GlobalOlympicSportsPerformanceAnalysis_17930317215980/Dashboard1GlobalPerformance?:language=en-US&:sid=&:redirect=auth&:display_count=n&:origin=viz_share_link)
*  **Live Tableau Public Dashboard**: [View on Tableau Public](https://public.tableau.com/views/GlobalOlympicSportsPerformanceAnalysis_17930317215980/Dashboard1GlobalPerformance?:language=en-US&:sid=&:redirect=auth&:display_count=n&:origin=viz_share_link)
- **Author**: Anurag Malasa
* **Author**: Anurag Malasa

---

## 📊 Project Overview & Key Deliverables

This project processes Olympic datasets to deliver:
* **8 Analytical Worksheets** across historical trends, country totals, efficiency metrics, and athlete participation.
* **2 Interactive Dashboards** with cross-filtering capabilities.
* **1 4-Point Interactive Story** narrating the Olympic performance journey.
* **A Responsive Web Portal (`index.html`)** embedding the live dashboards and providing an interactive country rankings explorer.

---

## 📁 Datasets & Relationships

The project connects four relational datasets via `noc_code` and `year`:

1. **`alltime_country_rankings.csv`**: Country-level historical aggregates (Total Medals, Gold/Silver/Bronze split, efficiency rates, region).
2. **`athletes.csv`**: Individual athlete profiles (Athlete ID, Name, Gender, Sport, Age at Peak, Training Hours).
3. **`games_summary.csv`**: Olympic editions breakdown (Year, Season, Host City, Total Events, Participating Nations).
4. **`medal_results.csv`**: Event-level medal logs mapping athletes to medal outcomes.

---

### 🧮 Calculated Fields

Custom metrics created in Tableau:

| Metric Name | Formula |
| :--- | :--- |
| **Medal Efficiency Pct** | `(Total Medals / Athletes Count) * 100` |
| **Medal Points** | `(Gold * 3) + (Silver * 2) + (Bronze * 1)` |
| **Avg Medals per Athlete** | `SUM(Total Medals) / COUNTD(Athlete Id)` |
---

## 📈 Visualizations & Dashboards

### Visualizations (8 Sheets)
1. **Medals Performance Over Time**: Line chart showing total medals awarded across Olympic editions (1992–2026).
2. **Top 10 Countries by Medals**: Horizontal bar chart highlighting top-ranking nations (USA: 735, China: 696, Russia: 429).
3. **Medal Breakdown by Country**: Stacked bar chart showing Gold, Silver, and Bronze distributions for top nations.
4. **Medal Performance by Region**: Bar chart comparing aggregate medals across continental regions (Europe: 2,622; Asia: 1,508).
5. **Summer vs. Winter Medal Totals**: Side-by-side comparison showing seasonal medal distribution.
6. **Top 10 Countries by Medal Efficiency**: Bar chart showcasing nations with the highest conversion of athletes to medals.
7. **Athlete Gender Distribution**: Comparative bar chart of male vs. female participation (3,821 Female vs. 4,179 Male).
8. **Athlete Participation by Sport**: Horizontal bar chart mapping athlete count across sports disciplines.

### Dashboards (2 Interactive Views)
* **Dashboard 1 — Global Performance**: Combines Sheets 1, 2, 3, and 4 into a 2x2 grid with regional interactive filtering.
* **Dashboard 2 — Regional Analysis & Participation**: Combines Sheets 5, 6, 7, and 8 with seasonal interactive filtering.

### Story Points (Olympic Performance Story)
1. *Top 10 Countries by Medal Achievements*
2. *Medal Performance Over Time*
3. *Summer vs. Winter Olympics*
4. *Regional Medal Performance*

---

## 📂 Repository Structure

```text
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
├── index.html
└── README.md
