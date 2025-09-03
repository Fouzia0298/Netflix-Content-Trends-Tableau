# Milestone 4 – KPI Dashboard Development

**Project:** Netflix Content Trends Dashboard  
**Author:** Fouzia Ashfaq  
**Date:** September 3, 2025  

---

## 📖 Overview
This milestone focused on **identifying key metrics (KPIs)** and designing an initial **KPI dashboard** to track Netflix’s catalog performance.  
The purpose of this dashboard is to:
- Provide a **clear, high-level view** of important trends.
- Enable **interactive exploration** through filters and parameters.
- Serve as the foundation for the final deliverable in Milestone 5.

> *KPIs transform raw data into actionable insights by answering specific business questions.*

---

## 🎯 Objectives
1. Select the **most relevant KPIs** for Netflix content analysis.
2. Build **calculated fields** to accurately measure these KPIs.
3. Create **visual hierarchy** for KPI presentation.
4. Add **interactive elements** such as filters and parameters.
5. Prepare a prototype dashboard layout for peer feedback.

---

## 📊 Selected KPIs
| **KPI**                | **Purpose** |
|-------------------------|-------------|
| **Total Titles**        | Show the overall size of Netflix's catalog. |
| **% Movies**            | Measure catalog share of movies. |
| **% TV Shows**          | Measure catalog share of TV shows. |
| **Average Movie Duration** | Understand typical feature length for movies. |
| **Average TV Show Length** | Show average number of seasons per TV show. |
| **Most Common Rating**  | Identify Netflix's main target audience. |
| **Titles Added Per Year** | Track growth trends and peak years. |

---

## 🧮 KPI Calculated Fields

### 1. **Total Titles**
```tableau
COUNTD([show_id])
```
### 3. % TV Shows
```
COUNTD(IF [type] = "TV Show" THEN [show_id] END) / COUNTD([show_id])

```
Format as Percentage.

### 4. Average Movie Duration (Minutes)
```
AVG(IF [type] = "Movie" THEN [duration_minutes] END)
```
### 5. Average TV Show Length (Seasons)
```
AVG(IF [type] = "TV Show" THEN [duration_seasons] END)
```
### 6. Most Common Rating
INDEX()


Used in combination with a sorted ratings chart to highlight the top rating.
# 🗂 KPI Values (From Dataset)

| Metric                | Value                       |
|-----------------------|----------------------------|
| **Total Titles**      | 6,232                      |
| **% Movies**          | 68.4%                      |
| **% TV Shows**        | 31.6%                      |
| **Avg Movie Duration**| 99 minutes                 |
| **Avg TV Show Length**| 1.8 seasons                |
| **Top Rating**        | TV-MA (2,026 titles)       |
| **Peak Growth Year**  | 2019 – 2,349 titles added  |

---

# 🖼 Dashboard Layout Prototype

**Layout Structure:**
```
+------------------------------------------------------+
|                    KPI Row (Top)                     |
|  [Total Titles]   [ % Movies ]   [ % TV Shows ]      |
|  [Avg Movie Duration]   [Avg TV Show Seasons]        |
+------------------------------------------------------+
|  Line Chart: Titles Added Over Time                  |
+------------------------------------------------------+
|  Bar Chart: Movies vs TV Shows Split                 |
+------------------------------------------------------+
|  Ratings Breakdown (Sorted Horizontal Bar Chart)     |
+------------------------------------------------------+
|  Filters: Type | Release Year Range                  |
+------------------------------------------------------+
```

---

# 🎛 Interactive Elements Added

**Filters:**
- Type (Movie vs TV Show)
- Year Range slider using `date_added`

**Parameters:**
- Dynamic selection for viewing specific content segments.

**Actions:**
- Clicking a bar dynamically filters other charts for deeper exploration.

---

# 🖥 Tableau Worksheets

**KPI Worksheet (Measure Names & Values)**
- Displays all KPIs as large numbers in one worksheet.
- Simplifies design and allows easy placement at the top of the dashboard.

**Growth Over Time Line Chart**
- Uses: `YEAR([date_added])` vs `COUNTD([show_id])`
- Clearly highlights 2019 as the peak year for content growth.

**Ratings Breakdown Bar Chart**
- Sorted descending to emphasize TV-MA dominance.

---

# 📸 Screenshot

*(Insert screenshot here of KPI dashboard prototype in Tableau.)*

---

# 📝 Reflection

This milestone clarified the core metrics that matter most to the audience:
- Overall size of Netflix's catalog
- Content type mix (Movies vs TV Shows)
- Growth trend over time
- Audience segmentation by rating

Creating calculated fields directly in Tableau improved flexibility and eliminated the need for heavy preprocessing in external tools.

Peer feedback also highlighted the importance of keeping KPIs at the very top of the dashboard so viewers can quickly understand the big picture before exploring detailed visualizations.

---

# 🔗 Related Resources

- **Previous:** Milestone 3 – Exploratory Analysis
- **Next:** Milestone 5 – Final Reflection
