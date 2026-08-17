# Student Performance & Risk Analysis Dashboard

## Project Overview

This project analyses student assessment data to identify academic performance trends, target achievement, and students requiring intervention.

The dashboard was built using **Power BI** and provides an interactive view of student performance across different subjects, terms, and year groups.

The analysis focuses on helping education stakeholders identify:

- Overall academic performance
- Subjects with the lowest performance
- Students performing below their targets
- High-risk students requiring intervention
- Performance patterns across subjects

## Dashboard Preview

![Student Performance & Risk Analysis Dashboard](INSERT-YOUR-DASHBOARD-IMAGE-LINK-HERE)

## Business Problem

Schools collect large amounts of student performance data, but raw data alone does not always provide clear insight into academic performance and intervention needs.

The objective of this project was to transform student assessment data into an interactive dashboard that answers questions such as:

- What is the overall average student score?
- How many students are meeting or exceeding their targets?
- Which subjects have the lowest performance?
- Which subjects have the highest proportion of students below target?
- How many students require intervention?
- Which subjects contain the highest number of high-risk students?

## Dataset

The dataset contains **500 student assessment records**.

Each record represents an individual student assessment and includes fields such as:

- Student ID
- Student Name
- Subject
- Score
- Target Score
- Attendance Percentage
- Assessment Date
- Term
- Year Group
- Intervention Status

### Data Validation Findings

During the data cleaning process, several quality issues were identified:

- Missing score values
- Scores greater than 100
- Duplicate records
- Inconsistent subject naming
- Invalid assessment dates
- Attendance values stored in inconsistent formats

These issues were addressed using **Power Query** before loading the data into Power BI.

## Data Cleaning and Transformation

The following steps were performed:

- Removed duplicate records
- Standardised subject names
- Identified and handled missing score values
- Removed invalid scores greater than 100
- Corrected inconsistent attendance percentage formats
- Identified invalid assessment dates
- Converted columns to appropriate data types
- Validated the number of records after cleaning

The final dataset contained:

**500 assessment records and 500 distinct Student IDs.**

## Key Performance Indicators

The dashboard includes the following KPIs:

| KPI | Result |
|---|---:|
| Average Score | 73.03 |
| Target Achievement % | 43.06% |
| Average Target Gap | -1.53 percentage points |
| High-Risk Students | 70 |
| Total Assessment Records | 500 |


## DAX Calculations

### Average Target Gap and High Risk Students

```DAX
Average Target Gap =
AVERAGEX(
    FILTER(
        Students_Performance,
        NOT ISBLANK(Students_Performance[Score_Percentage])
    ),
    Students_Performance[Score_Percentage]
        - Students_Performance[Target_Score]
)
High Risk Students =
CALCULATE(
    COUNTROWS(Students_Performance),
    Students_Performance[Risk Level] = "High Risk"
)
