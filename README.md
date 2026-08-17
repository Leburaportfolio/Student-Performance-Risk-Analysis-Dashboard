# Student Performance & Risk Analysis Dashboard

## Table of Contents

- [Project Overview](#project-overview)
- [Dashboard Preview](#dashboard-preview)
- [Business Problem](#business-problem)
- [Dataset](#dataset)
- [Data Cleaning and Transformation](#data-cleaning-and-transformation)
- [Key Performance Indicators](#key-performance-indicators)
- [DAX Calculations](#dax-calculations)
- [Risk Classification](#risk-classification)
- [Key Insights](#key-insights)
  - [Science Requires Broad Intervention](#science-requires-broad-intervention)
  - [English and Geography Have the Highest High-Risk Students](#english-and-geography-have-the-highest-high-risk-students)
  - [More Than Half of Students Are Below Target](#more-than-half-of-students-are-below-target)
- [Dashboard Features](#dashboard-features)
- [Tools and Technologies](#tools-and-technologies)
- [Key Skills Demonstrated](#key-skills-demonstrated)
- [Conclusion](#conclusion)
- [Author](#author)
  
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
```

## Risk Classification
A custom risk classification was developed based on student performance relative to their target score.
| Performance                                    | Risk Level        |
| ---------------------------------------------- | ----------------- |
| No valid score                                 | Insufficient Data |
| 10 or more percentage points below target      | High Risk         |
| Below target by less than 10 percentage points | Moderate Risk     |
| Meets or exceeds target                        | Low Risk          |
The classification was created using a calculated column in Power BI.

## Key Insights
### Science Requires Broad Intervention
Science recorded:

- The lowest average score at 70.44%
- The highest percentage of students below target at 63.9%

This suggests that Science represents the broadest area of academic concern.

### English and Geography Have the Highest High-Risk Students
| Subject     | High-Risk Students |
| ----------- | -----------------: |
| English     |                 16 |
| Geography   |                 16 |
| Science     |                 14 |
| Mathematics |                 13 |
| History     |                 11 |
Although Science had the broadest performance challenge, English and Geography contained the highest number of students performing significantly below their individual targets.

### More Than Half of Students Are Below Target

Out of 500 student assessment records:

283 were below target
109 were on track
105 were exceeding target
3 had no score

This means:

**56.6% of students were performing below their individual targets.**

## Dashboard Features

The dashboard includes:

- Interactive slicers for Subject, Term and Year Group
- KPI cards
- Average performance by subject
- Student risk distribution
- Risk distribution across subjects
- Conditional formatting
- Interactive subject comparison table
- Reset Filters button using Power BI Bookmarks

## Tools and Technologies
- Microsoft Power BI
- Power Query
- DAX
- Data Modelling
- Data Visualisation
- Data Cleaning and Transformation

## Key Skills Demonstrated
- Exploratory Data Analysis
- Data Cleaning
- Data Validation
- Power Query
- DAX
- Calculated Columns
- Measures
- KPI Development
- Conditional Formatting
- Data Storytelling
- Dashboard Design
- Risk Classification

## Conclusion

This project demonstrates how student assessment data can be transformed into actionable insights for education stakeholders.

The dashboard helps identify:

- Overall academic performance
- Students at risk of underperformance
- Subjects requiring intervention
- Gaps between student performance and targets

The analysis provides a data-driven foundation for prioritising academic interventions and supporting improved student outcomes.

## Author

### Lebura Olawale

Data Analyst | Education Consultant | Mathematics Educator

Connect with me on LinkedIn.
