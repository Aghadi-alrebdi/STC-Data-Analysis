# STC Jawwy TV - Recommendation System

## Task 1: User Behavior Analysis

## Project Overview
This task analyzes user behavior on STC TV platform using a dataset containing 1,048,575 rows and 13 columns. The analysis focuses on understanding viewer preferences across different program classes (MOVIE vs SERIES) and video quality preferences (SD vs HD).

---

## Dataset Information
- **File Name:** `stc- Jawwy TV Data Set_T1.xlsb`
- **Sheet Name:** `Final_Dataset`
- **Total Rows:** 1,048,575
- **Total Columns:** 13

### Columns Description
| Column Name | Description |
|-------------|-------------|
| date_ | Date of viewing |
| user_id_maped | Unique user identifier |
| program_name | Name of the program |
| duration_seconds | Watch time in seconds |
| program_class | MOVIE or SERIES/EPISODES |
| season | Season number (0 for movies) |
| episode | Episode number (0 for movies) |
| program_desc | Description of the program |
| program_genre | Genre of the program |
| series_title | Series title (0 for movies) |
| hd | HD flag (1 = HD, 0 = SD) |
| original_name | Original program name |

---

## Data Preprocessing Steps

1. **Dropped unnecessary columns**
   - Removed `Column1` (index column)

2. **Cleaned text data**
   - Trimmed spaces from `program_name`

3. **Converted data types**
   - `date_` → datetime format
   - `duration_seconds`, `season`, `episode`, `series_title`, `hd` → numeric
   - `user_id_maped`, `program_name`, `program_class`, `program_desc`, `program_genre`, `original_name` → string

4. **Checked for null values**
   - No null values found in any column

---

## Descriptive Statistics

### Numeric Columns Summary

| Statistic | duration_seconds | season | episode | series_title | hd |
|-----------|-----------------|--------|---------|--------------|-----|
| Mean | 1,230.96 | 1.34 | 6.16 | 0.01 | 0.39 |
| Std | 6,821.06 | 2.10 | 12.22 | 0.11 | 0.49 |
| Min | 2 | 0 | 0 | 0 | 0 |
| 25% | 52 | 0 | 0 | 0 | 0 |
| 50% | 119 | 1 | 1 | 0 | 0 |
| 75% | 1,328 | 1 | 9 | 0 | 1 |
| Max | 1,461,329 | 23 | 282 | 1 | 1 |

---

## Part 1: Classification by Program Class (MOVIE vs SERIES)

### Results

| Metric | MOVIE | SERIES/EPISODES |
|--------|-------|------------------|
| Unique Users | 11,355 | 3,901 |
| Total Views | 488,401 | 560,174 |
| Average Duration (seconds) | 762.49 | 1,639.40 |
| Average Duration (minutes) | 12.7 | 27.3 |
| Median Duration (seconds) | 77.0 | 1,133.0 |
| HD Ratio | 0.68 (68%) | 0.13 (13%) |
| Total Watch Time (hours) | 103,444.15 | 255,097.79 |

### Key Findings - Task 1

1. **Movies have more unique users** (11,355) compared to series (3,901)

2. **Series have longer average watch time** (27.3 minutes) compared to movies (12.7 minutes)

3. **Series have more total watch time** (255,097 hours) compared to movies (103,444 hours)

4. **Movies have higher HD adoption** (68%) compared to series (13%)

5. **Series have more total views** (560,174) compared to movies (488,401)

---

## Part 2: Viewing Patterns (SD vs HD)

### Results

| Metric | Standard Quality (SD) | High Quality (HD) |
|--------|----------------------|-------------------|
| Unique Users | 6,728 | 11,000 |
| Total Views | 643,539 | 405,036 |
| Average Duration (seconds) | 1,501.25 | 801.51 |
| Average Duration (minutes) | 25.0 | 13.4 |
| Median Duration (seconds) | 625.0 | 85.0 |
| Total Watch Time (hours) | 268,364.37 | 90,177.56 |

### User Distribution by Quality

| User Type | Count | Percentage |
|-----------|-------|------------|
| Watch Both Qualities | 6,150 | 52% |
| HD Only | 4,850 | 41% |
| SD Only | 578 | 5% |

### Key Findings - Part 2

1. **HD has more unique users** (11,000) compared to SD (6,728)

2. **SD has longer average watch time** (25 minutes) compared to HD (13.4 minutes)

3. **SD has more total watch time** (268,364 hours) compared to HD (90,178 hours)

4. **52% of users watch both qualities**

5. **Only 5% of users watch SD only**

6. **SD has more total views** (643,539) compared to HD (405,036)

---

## Task 2: # Viewership Forecasting

##  Project Overview

This project analyzes STC TV viewership data and builds a forecasting model to predict customer watch time for the next 2 months, while identifying peak viewing times to support business decision-making.

---

##  Dataset Information

| Attribute | Description |
|-----------|-------------|
| Source | stc- Jawwy TV Data Set_T2.xlsb |
| Time Period | January 1, 2018 – April 30, 2018 |
| Total Days | 120 days |
| Available Days | 86 days |
| Missing Days | 34 days (28.3%) |
| Features | date_, Total_watch_time_in_houres |

---

##  Project Objectives

1. Build a simple forecasting model to predict customer views for the next 2 months
2. Identify potential peak viewing times
3. Provide actionable recommendations for service improvement

---

##  Technologies Used

| Tool/Library | Purpose |
|--------------|---------|
| Python | Programming language |
| Pandas | Data manipulation and analysis |
| NumPy | Numerical computations |
| Matplotlib / Plotly | Data visualization |
| Statsmodels | Time series forecasting (Holt-Winters) |
| Scikit-learn | Model evaluation metrics |

---

# STC TV Viewership - Methodology, Performance & Results

## 📋 Methodology Steps

- Load data from Excel file (stc- Jawwy TV Data Set_T2.xlsb)
- Parse dates and set as index
- Check for missing values and data types
- Calculate basic statistics (mean, min, max)
- Split data into training (80%) and testing (20%)
- Build Holt-Winters Exponential Smoothing model
- Set seasonal periods = 7 days (weekly seasonality)
- Train model on historical data
- Generate predictions on test set
- Calculate error metrics (MAE, RMSE, MAPE)
- Forecast next 60 days (2 months)
- Group by day of week to identify peak days
- Calculate monthly averages for trend analysis

---

##  Model Performance

- **MAE:** 57.17 hours
- **RMSE:** 66.73 hours
- **MAPE:** 8.60%
- **Accuracy:** 91.4%
- Model is reliable for business decision-making

---

##  Results

### Trend Analysis
- January average: 866.57 hours
- February average: 823.46 hours (-4.9%)
- March average: 754.65 hours (-12.9%)
- Trend slope: -3.18 (negative/declining)
- **Conclusion: Viewership is declining **


### Forecast Results (Next 2 Months)
- Last 30 days actual: 695.72 hours
- Next 30 days forecast: 646.78 hours
- Expected change: -7.0%
- **Conclusion: Decline expected to continue**


---

  
## Task 3: Build a Movie/Program Recommendation Engine

This project implements a **Collaborative Filtering-based Recommendation System** for STC Jawwy TV platform to suggest relevant programs to users based on their viewing history and ratings.

---

##  Overview

The recommendation system analyzes user rating patterns to predict what programs a user might enjoy. Specifically, it identifies **top 5 recommendations for users who watched the movie "Moana"** using cosine similarity on a user-item matrix.

---

##  Dataset

| Attribute | Description |
|-----------|-------------|
| File | `stc-Jawwy TV Data Set_T3.xlsb` |
| Records | 1,048,575 rows |
| Users | ~34,280 unique users |
| Rating Scale | 1 (lowest) to 4 (highest) |

**Columns:**
- `user_id_maped` - Anonymous user identifier
- `program_name` - Name of the movie/TV show
- `rating` - User rating (1-4)
- `date_` - Viewing date
- `program_genre` - Genre of the program

---

##  Technologies Used

- pandas - Data manipulation
- numpy - Numerical computations
- scikit-learn - Cosine similarity
- matplotlib / plotly - Visualization
- pyxlsb - Reading .xlsb files

---

##  Methodology

**Step 1: Data Preparation**
- Load data, remove nulls, keep original ratings (1-4 scale)

**Step 2: Build User-Item Matrix**
- Rows = users, Columns = programs, Values = ratings (0 if not watched)

**Step 3: Calculate Item Similarity**
- Apply Cosine Similarity to measure program relationships
- Range: 0 (no similarity) to 1 (identical patterns)

**Step 4: Generate Recommendations**
- Find similar programs to user's watched content
- Weight by user's original ratings
- Exclude already watched programs
- Return top 5 recommendations
- Aggregate results from all 2,173 Moana viewers
---
## Results

- **#1:** Trolls (0.5724)
- **#2:** Surf's Up : WaveMania (0.5294)
- **#3:** The Mermaid Princess (0.4934)
- **#4:** The Boss Baby (0.4486)
- **#5:** The Jetsons & WWE: Robo-WrestleMania! (0.4389)

-  All 5 recommendations are animated family films
-  Model successfully identified Moana viewer preferences
