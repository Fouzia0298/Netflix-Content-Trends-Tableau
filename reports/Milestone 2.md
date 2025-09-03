# Milestone 2 – Data Cleaning and Preparation

**Project:** Netflix Content Trends Dashboard  
**Author:** Fouzia Ashfaq  
**Date:** September 3, 2025  

---

## 📖 Overview
This milestone focused on **importing the Netflix dataset into Tableau** and preparing it for analysis.  
The main goal was to ensure the data was **clean, accurate, and ready for visualization**, following the principle of  
> *"Garbage in, garbage out."*

The dataset used: `netflix_titles.xlsx`  
- Total records: **6,232 titles**  
- Fields included: `show_id`, `title`, `type`, `date_added`, `release_year`, `rating`, `duration_minutes`, `duration_seasons`, `description`

---

## 🛠 Steps Taken

### 1. **Data Import into Tableau**
- Connected Tableau to `netflix_titles.xlsx`.
- Verified that each field had the correct data type:
  - `show_id` → **Number (Whole)**
  - `release_year` → **Number (Whole)**
  - `date_added` → **Date**
  - `duration_minutes` and `duration_seasons` → **Number (Whole)**

---

### 2. **Data Cleaning Actions**
| Issue Found | Action Taken | Reason |
|-------------|--------------|--------|
| Some `release_year` values were incorrect (e.g., 20 instead of 2020). | Created a calculated field `Release Year (Clean)` to replace invalid years with `NULL` and retain valid ones between 1920–2025. | To avoid skewing visualizations with incorrect year data. |
| `duration_minutes` and `duration_seasons` contained many nulls. | Allowed nulls to remain but filtered them during specific visualizations. | Nulls were valid (e.g., TV Shows don’t have minutes). |
| `type` column sometimes inconsistent or missing. | Created `Type (Clean)` calculated field to infer type based on duration. | Ensured accurate movie vs. TV Show classification. |
| `date_added` had mixed formats. | Converted to Tableau Date type using `DATE([date_added])`. | Enabled proper time-series analysis. |
| Potential extreme outliers in duration (e.g., > 400 minutes or > 100 seasons). | Added filter logic in `Record OK` calculated field to remove unrealistic values. | Improve accuracy of average duration metrics. |

---

### 3. **Calculated Fields Created**

#### `Release Year (Clean)`
```tableau
IF ISNULL([release_year]) THEN NULL
ELSEIF [release_year] >= 1920 AND [release_year] <= 2025 THEN INT([release_year])
ELSE NULL
END
```
#### Type (Clean)
```
IF [type] = "Movie" OR [type] = "TV Show" THEN [type]
ELSEIF NOT ISNULL([duration_minutes]) THEN "Movie"
ELSEIF NOT ISNULL([duration_seasons]) THEN "TV Show"
ELSE NULL
END
```
#### Record OK (to filter out bad records)
```
IF ISNULL([title]) THEN FALSE
ELSEIF ISNULL([Type (Clean)]) THEN FALSE
ELSEIF ISNULL([Release Year (Clean)]) OR [Release Year (Clean)] < 1920 OR [Release Year (Clean)] > 2025 THEN FALSE
ELSEIF NOT ISNULL([duration_seasons]) AND [duration_seasons] > 100 THEN FALSE
ELSEIF NOT ISNULL([duration_minutes]) AND [duration_minutes] > 400 THEN FALSE
ELSE TRUE
END
```
### 4. Tableau Data Source Validation

No problematic outliers: Extreme values removed using Record OK.

Few missing values: Nulls only remain where logically valid (e.g., TV Shows don’t have minutes).

Correct data types: Verified for all columns.

Logical patterns: Date and type trends appeared consistent after cleaning.


## 📊 Insights from Cleaning

Of 6,232 titles, most data was high quality, requiring minimal cleaning.

Null values in duration_minutes were expected for TV Shows and do not indicate data issues.

Outlier filtering improved average calculations:

Movies over 400 minutes were removed.

TV Shows over 100 seasons were flagged as invalid.

Corrected release_year values allowed accurate historical analysis.

## 📝 Reflection

The cleaning process reinforced the importance of data preparation before visualization.

Without correcting invalid years and outliers, insights like growth trends over time and average duration KPIs would have been misleading.

Creating calculated fields in Tableau made the workflow flexible and repeatable.

This milestone created a solid foundation for exploratory analysis in Milestone 3.

## 🔗 Related Resources

Dataset: netflix_titles.xlsx (provided via Coursera)

## Next step: Milestone 3 – Exploratory Analysis
