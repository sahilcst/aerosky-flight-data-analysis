# AeroSky Flight Data Analysis & Data Quality Investigation

## Project Overview

This project was completed as part of a Data Analyst assessment focused on analyzing real-world-style flight-tracking data using Python and Pandas.

The objective was to understand the dataset, identify data-quality issues, clean and transform the data, perform exploratory analysis, and extract meaningful insights related to flight activity, airlines, aircraft, and routes.

The project demonstrates practical data analysis skills, including data profiling, data cleaning, exploratory data analysis (EDA), time-series analysis, data aggregation, and analytical reporting.

## Objectives

- Understand and profile a large flight-tracking dataset.
- Identify missing values, duplicate records, and inconsistent data.
- Clean and transform raw data into an analytical dataset.
- Perform time-based analysis of flight observations.
- Analyze flight-level, airline-level, and route-level activity.
- Investigate invalid geographical coordinates and unusual telemetry values.
- Communicate findings through analytical reports and recommendations.

## Tools & Technologies

- **Python** – Primary programming language
- **Pandas** – Data manipulation, cleaning, and analysis
- **NumPy** – Numerical operations
- **Matplotlib** – Data visualization
- **Jupyter Notebook** – Interactive analysis and documentation

## Dataset Overview

The project uses a flight-tracking snapshot dataset containing approximately 48 hours of observations.

The raw dataset includes fields such as:

- Timestamp
- Flight number
- Aircraft registration and type
- Airline
- Origin and destination airports
- Latitude and longitude
- Altitude
- Ground speed
- Vertical speed
- Heading
- Squawk
- On-ground status
- Flight status

After cleaning, the analytical dataset contained **60,000 observations**, covering 10 August 2026 to 11 August 2026.

## Data Cleaning & Preparation

The raw dataset was inspected before performing transformations.

The following data-quality checks and cleaning steps were carried out:

### 1. Missing Value Analysis
- Identified missing values across important columns.
- Examined missing information in aircraft, airline, airport, and telemetry fields.
- Avoided blindly replacing missing values with zero.
- Retained missing values where reliable replacements were unavailable.

### 2. Duplicate Detection
- Identified duplicate observations.
- Removed repeated records during data cleaning.

### 3. Standardization
- Investigated inconsistent airline names.
- Standardized airline naming variations to improve grouping and reporting.

### 4. Datetime Conversion
- Converted timestamp values into an appropriate datetime format.
- Extracted date, hour, and day-of-week information for time-series analysis.

### 5. Geographical Validation
- Checked latitude and longitude against valid geographical ranges.
- Latitude: -90 to +90
- Longitude: -180 to +180
- Identified invalid coordinates and handled them during cleaning.

### 6. Numeric Data Investigation
- Examined altitude, ground speed, and vertical speed using descriptive statistics.
- Investigated unusual values instead of automatically removing every extreme observation.

## Exploratory Data Analysis & Analysis Performed

### 1. Time-Series Analysis
- Analyzed flight observations by hour.
- Calculated hourly observation counts and unique observed flight numbers.
- Identified peak and low observation periods.

### 2. Flight-Level Analysis
- Grouped records using the supplied flight number field.
- Generated a flight-level summary.
- Examined flight observation counts and available flight information.

**Output:** `flight_summary.csv`

### 3. Airline Analysis
- Analyzed flight activity across airlines.
- Compared airline presence using unique observed flight numbers.
- Examined airline-level patterns in the dataset.

**Output:** `airline_summary.csv`

### 4. Route Analysis
- Combined origin and destination airport codes to create route identifiers.
- Analyzed frequently observed routes using the available records.

### 5. Basic Telemetry & Data Quality Investigation
- Identified latitude and longitude values outside valid geographical ranges.
- Investigated unusual altitude, ground speed, and vertical speed values.
- Considered the potential impact of missing and suspicious telemetry on analysis.

## Key Findings

Some of the important findings from the analysis include:

| Metric | Finding |
|---|---:|
| Observations after cleaning | 60,000 |
| Unique flight numbers | 39,352 |
| Highest hourly observation count | 2,596 |
| Lowest hourly observation count | 2,406 |
| Highest airline flight-number count (IndiGo) | 7,988 |
| Most frequently observed aircraft type (A320neo) | 12,990 observations |
| Missing latitude values after cleaning | 269 |
| Missing longitude values after cleaning | 269 |

- The highest observation volume occurred around 01:00, while the lowest occurred around 03:00.

- IndiGo had the highest observed flight-number count in the dataset, and the A320neo was the most frequently observed aircraft type.

These findings represent the supplied tracking observations and should not be interpreted as complete airline market-share or scheduled-flight statistics.

## Business Recommendations

Based on the data-quality investigation, the following recommendations were identified:

1. **Geographical Validation:** Implement automated latitude and longitude validation before using flight data in maps and reports.
2. **Missing Data Monitoring:** Display missing-value indicators in reports to make data limitations visible.
3. **Standardized Airline Records:** Maintain consistent airline naming at the data-source level.
4. **Telemetry Validation:** Introduce validation checks for unusual altitude, speed, and vertical-speed values.
5. **Further Analysis:** Extend the analysis with tracking-continuity and airport-level reporting for a more complete view of flight activity.

## Project Limitations & Future Scope

The project covers the analysis completed within the assessment.

The following areas could be explored further:

- Tracking continuity analysis using consecutive aircraft observations.
- Airport-level departure and arrival summaries.
- More detailed aircraft-level performance analysis.
- Advanced telemetry anomaly detection.
- Interactive dashboards for exploring flight activity.

A full tracking-continuity analysis and an airport summary dataset were not completed as part of this submission.

## Project Structure

```text
aerosky-flight-data-analysis/
│
├── AeroSky_Data_Analysis.ipynb
├── aerosky_flight_snapshots_cleaned.csv
├── flight_summary.csv
├── airline_summary.csv
├── AeroSky_Data_Quality_Report.md
├── AeroSky_Executive_Summary.pdf
└── README.md
```




## Conclusion

This project provided practical experience in working with a large structured dataset, identifying data-quality issues, applying data-cleaning techniques, performing exploratory analysis, and communicating data-driven findings.

It demonstrates the use of Python and Pandas to transform raw flight-tracking observations into structured analytical outputs and actionable recommendations.

---

**Project Type:** Data Analyst Assessment  
**Domain:** Aviation / Flight Tracking  
**Primary Focus:** Python, Pandas, Data Cleaning, EDA & Data Quality Investigation
