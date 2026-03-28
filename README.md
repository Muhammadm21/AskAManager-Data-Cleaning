# 🧹 AskAManager Salary Survey — Data Cleaning Project

## Project Overview
This project focuses exclusively on **data cleaning** using Microsoft Excel.
The dataset is the AskAManager Salary Survey 2021 — a real-world, 
messy dataset collected via Google Forms with 28,000+ free-text responses.

## Dataset
- **Source:** [Ask A Manager Salary Survey 2021](https://www.askamanager.org/2021/04/how-much-money-do-you-make-4.html)
- **Raw rows:** 28,211
- **Columns:** 18 (renamed to 15 after removing irrelevant columns)
- **Tools used:** Microsoft Excel

## Problems Found in Raw Data

| # | Issue | Column(s) Affected |
|---|---|---|
| 1 | 200+ variations of the same country name | Country |
| 2 | Blank/missing values across multiple columns | Industry, City, Gender, Education |
| 3 | Salary outliers (entries like $0, $33, $6 billion) | Annual_Salary |
| 4 | Inconsistent text casing and spacing | Country, Industry |
| 5 | Junk/nonsense entries (e.g. "dbfemf", "ss", "Remote") | Country |
| 6 | Placeholder zeros used instead of proper null values | Industry, US_State |
| 7 | Duplicate column semantics (3 columns rarely filled) | Job context, Currency context, Income context |

## Cleaning Steps Performed

### 1. Column Renaming
Renamed all 18 long survey question headers to short, clean column names
(e.g. "How old are you?" → `Age_Group`)

### 2. Removed Unnecessary Columns
Deleted 3 columns with 74–93% missing values that added no analytical value:
- Job title context
- Currency (Other) context  
- Income context

### 3. Country Standardization *(Biggest task)*
The Country column had 200+ variations of the same countries due to free-text input.
- Standardized all USA/US/U.S./Usa/america variations → `United States`
- Standardized UK/England/Scotland/Wales/Northern Ireland → `United Kingdom`
- Fixed casing inconsistencies across all countries
- Deleted 30 rows with junk/unidentifiable country entries

### 4. Missing Values
Filled blank cells with appropriate placeholders:
- `Industry` blanks → `Unknown`
- `Additional_Compensation` blanks → `0` (no bonus = zero)
- `Gender` blanks → `Prefer not to say`
- `US_State` for non-US rows → `N/A`

### 5. Salary Outlier Flagging & Removal
- Added a helper column `Annual_Salary(Ok/flag)` to flag suspicious values
- Flagged and deleted 132 rows where salary < 1,000 (likely hourly rates or typos)
- Deleted 1 row with $0 salary (no valid data)

## Results

| Metric | Before | After |
|---|---|---|
| Total rows | 28,211 | 28,053 |
| Rows removed | — | 158 |
| Country unique values | 200+ | 98 |
| Columns | 18 | 15 |

## Files
| File | Description |
|---|---|
| `AskAManager_Cleaned_Final.xlsx` | Final cleaned dataset (Cleaned Data_Final sheet) |

## Author
**Muhammad** — Information Systems Student, Ajman University  
Specialization: E-Business Management / Business Intelligence  
[LinkedIn Profile] : https://www.linkedin.com/in/mohammad-mohammad-0547283b1/
