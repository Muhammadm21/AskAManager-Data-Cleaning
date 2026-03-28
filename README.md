# AskAManager Salary Survey — Data Cleaning Project

## Overview
This project focuses exclusively on **data cleaning** using Microsoft Excel.
The dataset is the AskAManager Salary Survey 2021 — a real-world, genuinely messy dataset
collected via an open Google Form with no validation, no dropdowns, and no rules.
Every response was typed freely by a different person.

This is not a dataset artificially made messy for teaching purposes.
This is what real survey data looks like before anyone has touched it.

---

## Dataset
- **Source:** [Ask A Manager Salary Survey 2021](https://www.askamanager.org/2021/04/how-much-money-do-you-make-4.html)
- **Columns:** 18 raw survey questions, reduced to 15 clean analysis-ready columns
- **Tool used:** Microsoft Excel

---

## Problems Identified in Raw Data

| # | Problem | Column(s) Affected |
|---|---|---|
| 1 | 200+ variations of the same country name due to free-text input | Country |
| 2 | Salary values that were clearly not annual salaries (hourly rates, typos, absurd amounts) | Annual_Salary |
| 3 | Text value "Unknown" stored in numeric salary and compensation columns | Annual_Salary, Additional_Compensation |
| 4 | Blank/missing values across multiple columns with no placeholder | Industry, Gender, Education, City, US_State |
| 5 | Number zero used as a blank replacement causing data type inconsistencies | Industry, US_State |
| 6 | Inconsistent text casing and leading/trailing spaces | Country, Industry |
| 7 | Junk entries — gibberish text, city names, sentences entered in the wrong field | Country |
| 8 | Three columns with 74–93% missing values providing no analytical value | Job context, Currency context, Income context |

---

## Cleaning Steps Performed

### 1. Column Renaming
All 18 column headers were long survey questions written in plain English.
Every column was renamed to a short, clean, analysis-ready name.

For example:
- "How many years of professional work experience do you have overall?" → `Experience_Overall`
- "What is your annual salary?" → `Annual_Salary`
- "Please indicate the currency" → `Currency`

### 2. Removing Irrelevant Columns
Three columns had between 74% and 93% missing values.
These were optional clarification fields that most respondents skipped entirely.
Removing them reduced the dataset from 18 to 15 columns.

### 3. Country Column Standardization
This was the most time-intensive cleaning task in the entire project.
Because the country field was free-text, respondents entered their country however they chose.
The result was over 200 variations of the same country names.

Examples of what was found:
- "United States" appeared as: USA, US, U.S., U.S.A., Usa, usa, america, UNITED STATES, UnitedStates, United states, United States of America, and dozens of typos and misspellings
- "United Kingdom" appeared as: UK, Uk, uk, England, Scotland, Wales, Northern Ireland, Britain, Great Britain, and multiple combinations
- Similar inconsistencies existed for Canada, Netherlands, Germany, New Zealand, and others

Every variation was identified and standardized to a consistent country name.
Rows containing junk entries — gibberish text, city names, sentences, and unidentifiable values — were deleted entirely.

### 4. Salary Cleaning
The Annual_Salary column had three types of problems:

**Invalid text values:**
Rows where salary was entered as "Unknown" were deleted entirely — a salary of Unknown has no analytical value.

**Suspiciously low values:**
Values below 1,000 were identified and deleted. These were clearly hourly rates or random numbers entered by mistake — no annual salary is $40 or $55.

**Absurd outliers:**
Extremely high values in non-JPY currencies were reviewed and deleted. Note: high values in JPY were kept because millions of yen is a normal salary range in Japan.

### 5. Compensation Column Cleaning
The Additional_Compensation column had "Unknown" text values mixed in with numeric data.
All "Unknown" values were replaced with 0 — meaning the respondent has no additional compensation.
This is the correct interpretation since the question asked for bonus/overtime amounts.

### 6. Missing Values Treatment
Blank cells were filled with appropriate placeholders per column:

| Column | Blank Treatment |
|---|---|
| Industry | Filled with "Unknown" |
| Additional_Compensation | Filled with 0 (no bonus = zero) |
| Gender | Filled with "Prefer not to say" |
| Education | Filled with "Not Specified" |
| US_State (non-US rows) | Filled with "N/A" |
| City | Filled with "Not Specified" |

### 7. Zero Value Correction
In some columns, blank cells had been replaced with the number 0 instead of proper text placeholders.
This caused data type inconsistencies where text columns contained numeric values.
All instances were identified and corrected to appropriate text placeholders.

---

## Files

| File | Description |
|---|---|
| `AskAManager_Clean_Final.xlsx` | Final cleaned dataset (Cleaned Data_Final sheet) with full formatting |

The workbook contains two sheets:
- `Form Responses 1` — original raw data, untouched
- `Cleaned Data_Final` — fully cleaned and formatted output

---

## Author
**Muhammad** — Information Systems Student, Ajman University
Specialization: E-Business Management / Business Intelligence
[LinkedIn](https://www.linkedin.com/in/mohammad-mohammad-0547283b1/)
