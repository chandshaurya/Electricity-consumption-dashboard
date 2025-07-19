# Electricity-consumption-dashboard
This repository contains the Power BI project file and associated data for an in-depth analysis of electricity consumption patterns across various Indian cities. The interactive dashboard provides insights into billing, usage hours, and the factors influencing them, such as location, month, and power distribution company.

# Table of Contents
1. Project Overview

2. Problem Statement

3. Dataset

4. Tools Used

5. Dashboard Showcase

6. Page 1: Electricity Consumption Overview

7. Page 2: Insights by City and Month

8. Data Transformation (Power Query)

9. DAX Measures

10. Key Insights



# Project Overview
The primary goal of this project is to analyze and visualize electricity consumption data to uncover key trends and metrics. By leveraging Power BI, we transform raw data into a dynamic and insightful report that helps stakeholders understand consumption drivers, compare regional performance, and analyze the impact of different power companies.

# Problem Statement
The project aims to answer the following key business questions:

What are the total electricity bill, average tariff rate, and total consumption hours across all regions?

How does the electricity bill vary across different cities and months? Are there significant seasonal trends?

Which appliances contribute the most to the total monthly usage hours?

Which power distribution companies are associated with the highest electricity bills?

What is the relationship between monthly usage, tariff rates, and the final electricity bill for different cities?

# Dataset
The analysis is based on the electricity.csv dataset. Each row represents a monthly record for a household or entity. Data are taken from the kraggle.

# Columns:

Fan, Refrigerator, AirConditioner, Television, Monitor, MotorPump: Hours of usage for each respective appliance in a day.

 Month: The month of the record (1-12).

City: The city where the consumption was recorded.

Company: The name of the electricity transmission/distribution company.

MonthlyHours: The aggregated total monthly hours of electricity usage from all appliances.

TariffRate: The rate charged per unit of electricity (e.g., ₹ per kWh).

ElectricityBill: The total calculated electricity bill for the month in Rupees (₹). It is derived from the formula:

ElectricityBill=MonthlyHours×TariffRate
# Tools Used
Microsoft Power BI Desktop: For data modeling, transformation, and dashboard creation.

Power Query (M Language): For data cleaning and transformation, especially for unpivoting appliance data.

DAX (Data Analysis Expressions): For creating calculated measures to drive the report visuals.

# Dashboard Showcase
The Power BI report consists of two main pages:

 # Page 1: Electricity Consumption Overview
This page provides a high-level summary of the key performance indicators and overall consumption trends.

<img width="1286" height="722" alt="Screenshot 2025-07-19 192220" src="https://github.com/user-attachments/assets/0117e1ae-d062-45b1-a2a4-79bed197c9a0" />



# Visuals Included:

KPI Cards:

Sum of Electricity Bill: Total revenue generated.

Average of Tariff Rate: The average cost per unit across the dataset.

Sum of Monthly Hours: Total consumption hours.

Count of Company: The number of distinct power companies analyzed.

Doughnut Chart (Electricity Bill by City): Shows the percentage contribution of each city to the total electricity bill.

Clustered Bar Chart (Monthly Hours by City): Compares the total consumption hours for each city.

Line Chart (Electricity Bill by Month): Visualizes the trend of electricity bills over the year, highlighting seasonal peaks.

Table (Company wise Bill): A detailed breakdown of the total bill amount for each power company.

Slicer: Filter the entire report page by City.

# Page 2: Insights by City and Month
This page offers a more granular analysis, focusing on appliance-level usage and detailed monthly breakdowns.

<img width="1286" height="723" alt="Screenshot 2025-07-19 192246" src="https://github.com/user-attachments/assets/1ffd8b5a-2bd5-419a-823b-184a088a5780" />


# Visuals Included:

KPI Cards: Consistent KPIs for a seamless user experience.

Treemap (Electricity Bill by Company): Visualizes the market share of different companies based on the total electricity bill.

Stacked Bar Chart (Usage Hours by Appliance): Breaks down the total consumption hours by individual appliance type, showing which devices are used the most.

Matrix (Electricity Bill by City and Month): A powerful visual providing a detailed cross-tabulation of electricity bills for each city, broken down by month. This is ideal for identifying specific high-consumption periods in each location.

Slicer: Filter the entire report page by Month.

# Data Transformation (Power Query)
To build the Usage Hours by Appliance visual, a critical data transformation step was performed in the Power Query Editor:

Select Appliance Columns: The columns Fan, Refrigerator, AirConditioner, Television, Monitor, and MotorPump were selected.

Unpivot Columns: These selected columns were unpivoted. This action transformed the data from a wide format into a long format, creating two new columns:

Attribute (renamed to Appliance): Contains the name of the appliance.

Value (renamed to Usage Hours): Contains the hours of usage for that appliance.

Data Type Correction: All columns were checked and assigned the correct data types (e.g., Whole Number, Decimal Number, Text).

This transformation is essential for enabling flexible analysis of appliance-specific data.

# DAX Measures
Several key DAX measures were created to power the dashboard's visuals:

Code snippet

-- Total electricity bill across all selected filters
Total Bill = SUM('electricity'[ElectricityBill])

-- Average tariff rate, respecting filters
Average Tariff = AVERAGE('electricity'[TariffRate])

-- Total consumption hours
Total Hours = SUM('electricity'[MonthlyHours])

-- Count of unique companies in the dataset
Distinct Companies = DISTINCTCOUNT('electricity'[Company])

# Key Insights
Geographical Impact: Cities like Mumbai, New Delhi, and Hyderabad are major contributors to the total electricity bill, driven by both high consumption and population density.

Seasonal Peaks: The line chart clearly indicates a peak in electricity consumption and bills during the summer months (approximately May to August), likely due to increased usage of Air Conditioners.

Appliance Usage: The unpivoted data reveals that appliances like Refrigerators and Fans have consistent, high hourly usage, while Air Conditioners are the primary drivers of seasonal peaks in the electricity bill.

Company Performance: The treemap and table visuals show that companies like Tata Power, Adani Power, and Power Grid Corp manage a significant portion of the total electricity billing in the dataset.
