# Milestone 3 – Exploratory Data Analysis (EDA)

**Project:** Netflix Content Trends Dashboard  
**Author:** Fouzia Ashfaq  
**Date:** September 3, 2025  

---

## 📖 Overview
This milestone focused on **exploring the cleaned Netflix dataset** to discover meaningful patterns and relationships that will form the foundation of the final dashboard and data story.

The primary goal was **not to create a polished visualization**, but to **experiment, test ideas, and uncover trends** using Tableau’s features such as filters, hierarchies, and calculated fields.

> *Exploratory analysis is where discovery happens.*

---

## 🎯 Objectives
1. Identify **key metrics** to track as KPIs.
2. Build **multiple worksheets** to experiment with different chart types and views.
3. Use Tableau's interactivity features (filters, parameters, actions) to slice and explore data dynamically.
4. Surface insights that will guide the final dashboard design.

---

## 🗂 Dataset Recap
- Total Records: **6,232 titles**  
- Key Fields Used:
  - `type` (Movie vs TV Show)
  - `date_added` (when title was added to Netflix)
  - `release_year`
  - `rating`
  - `duration_minutes`
  - `duration_seasons`

---

## 📊 KPIs Created
The following **calculated fields** were created in Tableau to track essential metrics:

### 1. **Total Titles**
```tableau
COUNTD([show_id])
Total unique titles in the Netflix catalog.
```
### 2. % Movies
```   
COUNTD(IF [type] = "Movie" THEN [show_id] END) / COUNTD([show_id])


Percentage of catalog that is Movies.
```
### 3. % TV Shows
```
COUNTD(IF [type] = "TV Show" THEN [show_id] END) / COUNTD([show_id])


Percentage of catalog that is TV Shows.
```
### 4. Average Movie Duration (Minutes)
```
AVG(IF [type] = "Movie" THEN [duration_minutes] END)
```
### 5. Average TV Show Length (Seasons)
```
AVG(IF [type] = "TV Show" THEN [duration_seasons] END)
```
## 📈 Key Insights Discovered

| Metric      |	Value	       |Insight |
|-------------|--------------|--------|
|Total Titles	|6,232|	Netflix has a diverse and extensive global catalog.|
|Movies vs TV Shows	|68.4% Movies, 31.6% |TV Shows	Movies dominate the catalog, but TV Shows are a growing focus.|
|Peak Growth Year	|2019 – 2,349 titles added	|The biggest surge of new content occurred in 2019.|
|Top Audience Rating	|TV-MA – 2,026 titles|	Indicates strong focus on mature audiences.|
|Avg Movie Duration|	99 minutes|	Standard feature-length film duration.|
|Avg TV Show Length|	1.8 seasons	|Most shows are limited series or short runs.|

# 🖥 Worksheets Created

### **Movies vs TV Shows (Bar Chart)**
- Simple comparison to show catalog mix.
- Color-coded by type for immediate clarity.

---

### **Titles Added Over Time (Line Chart)**
- Used `date_added` grouped by year.
- Revealed **2019 as the peak year** for new content.

---

### **Ratings Distribution (Horizontal Bar Chart)**
- Sorted descending to show most common audience ratings.
- Highlighted **TV-MA** and **TV-14** as dominant.

---

### **Duration Histograms**
- Separate visualizations for `duration_minutes` and `duration_seasons`.
- Helped validate outlier handling and cleaning steps.

---

# 🖼 Dashboard Prototype
A prototype dashboard was built combining:

- **Top row:** KPI cards (big numbers for Total Titles, % Movies, % TV Shows, Avg Durations).  
- **Middle section:** Growth over time line chart.  
- **Bottom section:** Ratings breakdown and Type comparison.  

> This prototype was primarily for **testing layout and interactivity**, not for the final design.

---

# 🎛 Tableau Features Used
- **Filters:** Type (Movie / TV Show), Year Range.  
- **Parameters:** To dynamically adjust views by date.  
- **Actions:** Clicking on a chart filters related visualizations.  
- **Color Encoding:** Red vs Blue to distinguish Movies and TV Shows.

---



---

# 📝 Reflection
The exploratory analysis was the **most time-intensive phase**, requiring iteration and experimentation:

- Many chart types were tested, with several discarded to avoid clutter.  
- The most surprising finding was how **dominant TV-MA content** is, showing Netflix’s primary audience focus.  
- Separating **Movie and TV Show durations** into two KPIs greatly improved clarity.  

This milestone set the stage for refining these insights into a **polished dashboard for Milestone 5**.

---

# 🔗 Related Resources
- **Previous:** [Milestone 2 – Data Cleaning](../reports/milestone_2_data_cleaning.md)  
- **Next:** [Milestone 4 – KPI Dashboard Development](../reports/milestone_4_kpis.md)  
- **Final Tableau Dashboard:** *(Insert Tableau Public link here)*

