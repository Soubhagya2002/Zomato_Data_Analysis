# Zomato Restaurant Data Analysis

An end-to-end data analytics project exploring restaurant listings, ratings, cuisines, pricing, location, and service availability across countries and cities. The project uses **Excel, SQL, Tableau, and Power BI** to prepare data, answer business questions, and present findings through dashboards.

---

## Table of Contents

- [About This Project](#about-this-project)
- [Problem Statement](#problem-statement)
- [Project Objectives](#project-objectives)
- [Dataset Overview](#dataset-overview)
- [Technology Stack](#technology-stack)
- [Project Workflow](#project-workflow)
- [Data Preparation](#data-preparation)
- [SQL Analysis](#sql-analysis)
- [Dashboard and Visualization](#dashboard-and-visualization)
- [Key Observations](#key-observations)
- [Repository Structure](#repository-structure)
- [How to Use This Project](#how-to-use-this-project)
- [Limitations](#limitations)
- [Future Improvements](#future-improvements)
- [Author](#author)

## About This Project

This project analyzes restaurant data associated with Zomato to understand how restaurants are distributed across locations and how they differ in terms of customer ratings, cuisine, average cost, table booking, and online delivery.

The analysis combines data preparation in Microsoft Excel, SQL queries for aggregation and business-focused questions, and interactive dashboards created in Tableau and Power BI. The Excel workbook also contains supporting tables and analysis sheets used to explore the dataset.

The project demonstrates a practical analytics workflow: preparing a dataset, organizing it for analysis, querying it to answer specific questions, and communicating the results through visual dashboards.

## Problem Statement

Restaurant platforms operate across different cities and countries, with restaurants offering different cuisines, price ranges, ratings, and services. Understanding these patterns can help stakeholders explore market distribution, customer preferences, restaurant performance, and service availability.

This project focuses on questions such as:

1. How are restaurants distributed across countries and cities?
2. How many restaurants fall into each rating category?
3. How does restaurant availability change over time?
4. Which price ranges are most common?
5. What proportion of restaurants offer table booking and online delivery?
6. Which cuisines and cities have a notable restaurant presence?

## Project Objectives

- Explore restaurant distribution by country and city.
- Analyze restaurant ratings and rating categories.
- Examine restaurant openings by year, quarter, and month.
- Group restaurants by average-cost ranges.
- Compare table-booking and online-delivery availability.
- Explore cuisine distribution and city-level patterns.
- Build dashboards that make the results easier to understand.
- Practice using Excel, SQL, Tableau, and Power BI together in one analytics project.

## Dataset Overview

The supplied Excel workbook contains a **Cleaned Data** sheet with **9,552 records and 27 columns**. The fields cover restaurant identity, location, cuisine, pricing, ratings, votes, services, and opening dates.

| Data area | Example fields | Purpose |
|---|---|---|
| Restaurant details | `RestaurantID`, `ResturantName` | Identify each restaurant |
| Location | `CountryCode`, `Country`, `City`, `Address`, `Locality`, `Latitude`, `Longitude` | Geographic analysis |
| Food and cuisine | `Cuisines` | Explore cuisine categories |
| Services | `Has_Table_booking`, `Has_Online_delivery`, `Is_delivering_now` | Compare service availability |
| Pricing | `Average_Cost_for_two`, `Currency`, `Price_range`, `Price in USD` | Analyze restaurant costs |
| Customer feedback | `Rating`, `Rating_Bucket`, `Votes` | Explore customer ratings and engagement |
| Time | `Datekey_Opening`, `WeekDayName` | Analyze restaurant openings over time |
| Derived fields | `COST_FLAG`, `echange rates`, `price bucket` | Support preparation and categorization |

The workbook also includes a country mapping sheet and a calendar table. The SQL script expects the restaurant and country lookup tables to be available as `Zomato_Data` and `Zomato_DataC` in MySQL.

## Technology Stack

| Tool | Role in the project |
|---|---|
| Microsoft Excel | Data preparation, supporting tables, summaries, and dashboard |
| MySQL | Relational queries, joins, grouping, date calculations, and aggregations |
| Tableau | Interactive visual exploration and dashboarding |
| Microsoft Power BI | Interactive reports and visual analysis |
| Git & GitHub | Version control and project sharing |

## Project Workflow

```text
Restaurant Dataset
       |
       v
Data Preparation in Excel
       |
       +-------------------------+
       |                         |
       v                         v
SQL Analysis in MySQL      Excel Analysis
       |                         |
       v                         v
Business Queries           Excel Dashboard
       |                         |
       +------------+------------+
                    |
                    v
          Tableau and Power BI
                    |
                    v
        Insights and Interpretation
```

## Data Preparation

The Excel workbook contains a `Cleaned Data` sheet and supporting sheets used in the analysis. The prepared data includes fields for country, currency conversion, cost in USD, rating categories, price buckets, and weekday names.

Supporting workbook sheets include:

- `CountryMap` – country, currency, country code, and exchange-rate reference.
- `Calender Table` – calendar attributes such as year, month, quarter, weekday, and financial period.
- Additional sheets containing summaries for city/country, opening trends, ratings, price buckets, table booking, online delivery, and cuisines.

The README describes the workbook as supplied; it does not assume that every transformation was performed by a particular tool or that every source-data issue has been eliminated.

## SQL Analysis

The `zomato-SQL.sql` script contains queries for the following tasks:

1. **Country mapping:** Join restaurant records with the country lookup table to retrieve country names.
2. **Calendar table creation:** Derive year, month, month name, quarter, year-month, weekday, financial month, and financial quarter from the opening date.
3. **Restaurant distribution:** Count restaurants by country and city.
4. **Opening trends:** Count restaurant openings by year, quarter, and month.
5. **Rating distribution:** Count restaurants by rating.
6. **Price segmentation:** Categorize restaurants into average-cost buckets (0–500, 501–1,000, 1,001–2,000, and above 2,000).
7. **Table booking:** Calculate the count and percentage of restaurants with table booking.
8. **Online delivery:** Calculate the count and percentage of restaurants offering online delivery.
9. **Cuisine and rating preparation:** Aggregate restaurant counts by city, cuisine, and rating.

The script uses SQL operations including `CREATE DATABASE`, `CREATE TABLE AS SELECT`, `LEFT JOIN`, `GROUP BY`, `ORDER BY`, date functions, `CASE` expressions, and aggregate functions.

### Running the SQL Script

1. Install and open MySQL Server and MySQL Workbench.
2. Import the restaurant dataset and country lookup data into your MySQL schema.
3. Ensure the imported tables are named `Zomato_Data` and `Zomato_DataC`, or update the script to match your table names.
4. Open `zomato-SQL.sql` in MySQL Workbench.
5. Execute the script. It creates and uses the `zomato_db` database and creates the calendar table from `Zomato_Data`.

> **Note:** The SQL file assumes that `Zomato_Data` and `Zomato_DataC` have already been imported. The Excel workbook is provided, but the SQL script does not include the table-import or table-creation steps for those two source tables.

## Dashboard and Visualization

The project includes three dashboard/report files:

### Microsoft Excel

`DASHBOARD-Excel.xlsx` contains the cleaned dataset, country mapping, calendar table, supporting analysis sheets, and a dashboard sheet (`Dashboard2`).

### Tableau

`Zomato -Tableau.twbx` is a packaged Tableau workbook. It includes views covering topics such as average rating by city, restaurant counts by city and country, restaurant openings over time, ratings, price buckets, table booking, online delivery, cuisine patterns, and a dashboard.

Open the `.twbx` file using Tableau Desktop or Tableau Public (where supported).

### Power BI

`Zomato PowerBI.pbix.zip` is the supplied compressed Power BI project file. Extract the ZIP archive first, then open the contained `.pbix` file in Power BI Desktop.

## Key Observations

The following figures are calculated from the `Cleaned Data` sheet in the supplied Excel workbook:

| Metric | Observation |
|---|---:|
| Restaurant records | 9,552 |
| Countries represented | 15 |
| Cities represented | 141 |
| Distinct cuisine entries | 1,826 |
| Restaurants with table booking marked Yes | 1,158 (about 12.1%) |
| Restaurants with online delivery marked Yes | 2,451 (about 25.7%) |
| Most represented country | India (8,652 records) |
| Most represented city | New Delhi (5,473 records) |

These are descriptive counts from the workbook, not conclusions about the entire Zomato business or current restaurant market. The dataset's coverage and collection period should be considered when interpreting them.

## Repository Structure

```text
Zomato_project/
├── README.md                       # Project documentation
├── DASHBOARD-Excel.xlsx             # Excel workbook, cleaned data and dashboard
├── Zomato -Tableau.twbx             # Packaged Tableau workbook
├── Zomato PowerBI.pbix.zip          # Compressed Power BI report
└── zomato-SQL.sql                   # MySQL analysis queries
```

## How to Use This Project

1. **Download or clone** this repository.
2. Open `DASHBOARD-Excel.xlsx` to review the cleaned data, supporting sheets, and Excel dashboard.
3. Import the required restaurant and country tables into MySQL, then run `zomato-SQL.sql`.
4. Open `Zomato -Tableau.twbx` in Tableau to explore the visualizations.
5. Extract `Zomato PowerBI.pbix.zip` and open the `.pbix` file in Power BI Desktop.

## Limitations

- The repository contains analysis workbooks and a SQL script; it does not include a separate documented data-ingestion pipeline.
- The SQL script relies on pre-existing MySQL tables named `Zomato_Data` and `Zomato_DataC`.
- Restaurant listings and ratings represent the supplied dataset and should not be treated as live Zomato information.
- Currency conversions and derived categories depend on the values and assumptions stored in the workbook.
- Some records have missing values in individual fields; check the relevant columns before reproducing calculations.
- The project is descriptive and does not establish causal relationships between restaurant characteristics and ratings.

## Future Improvements

- Add a dedicated data-cleaning script or documented Power Query workflow.
- Document the dataset's original source, license, and collection date.
- Add validation checks for missing values, duplicates, inconsistent categories, and outliers.
- Standardize currency conversion and cost-bucket definitions across Excel, SQL, Tableau, and Power BI.
- Add dashboard screenshots and a short explanation of the main visual findings.
- Add reproducible database import instructions or SQL table-definition scripts.

## Author

**Soubhagya Kumar Routray**

- GitHub: [@Soubhagya2002](https://github.com/Soubhagya2002)

---

If you find this project useful, feel free to star the repository.
