# Task 5 – Financial KPI Scorecard using Power BI

## Project Overview

This project is a Financial KPI Scorecard developed using Microsoft Power BI. The dashboard analyzes financial performance by comparing actual sales with budget values and provides key financial KPIs, monthly trends, variance analysis, and profit margin insights.

The project uses the Microsoft Power BI Financial Sample dataset.

## Dataset

Source:

https://learn.microsoft.com/en-us/power-bi/create-reports/sample-financial-download

The Financial Sample contains financial information including:

- Segment
- Country
- Product
- Discount Band
- Units Sold
- Manufacturing Price
- Sale Price
- Gross Sales
- Discounts
- Sales
- COGS
- Profit
- Date

The dataset covers financial transactions across different products, countries, and segments.

## Objectives

The main objectives of this project are:

1. Import financial data into Power BI.
2. Clean and transform the finance data.
3. Create Actual Sales and Budget measures.
4. Calculate financial variance.
5. Calculate profit margin.
6. Analyze monthly financial trends.
7. Compare Budget vs Actual performance.
8. Create KPI cards.
9. Apply conditional formatting.
10. Add Year filters.
11. Publish the completed dashboard.

## Data Preparation

The financial data was imported into Power BI and cleaned using Power Query.

Data preparation activities included:

- Checking column data types.
- Converting Date columns to Date format.
- Converting financial columns to numeric/decimal format.
- Removing unnecessary columns.
- Checking for blank and invalid values.
- Creating month and year fields.
- Creating a Date Table for time-based analysis.

## Date Table

A Date Table was created to support monthly and yearly analysis.

Example DAX:

```DAX
DateTable =
ADDCOLUMNS(
    CALENDAR(
        MIN(Financials[Date]),
        MAX(Financials[Date])
    ),
    "Year", YEAR([Date]),
    "Month Number", MONTH([Date]),
    "Month", FORMAT([Date], "MMM"),
    "Month Year", FORMAT([Date], "MMM YYYY"),
    "Month Year Sort", YEAR([Date]) * 100 + MONTH([Date])
)

The Month Year column was sorted using Month Year Sort to ensure that months appear in chronological order.

Measures
Total Sales
Total Sales =
SUM(Financials[Sales])
Total Profit
Total Profit =
SUM(Financials[Profit])
Total Budget

The Budget measure was created from the Budget table.

Total Budget =
SUM(Budget[Budget])

Note: The column name should be changed to match the actual budget amount column in the Budget table.

Variance

Variance measures the difference between Actual Sales and Budget.

Variance =
[Total Sales] - [Total Budget]
Profit Margin
Profit Margin =
DIVIDE(
    [Total Profit],
    [Total Sales],
    0
)

The Profit Margin measure was formatted as a percentage.

Monthly Trend

A line chart was created to show monthly sales performance.

Chart configuration
Visual: Line Chart
X-axis: Month Year
Y-axis: Total Sales
Filter: Year

The monthly trend helps identify increases and decreases in financial performance over time.

Budget vs Actual

A Line and Clustered Column Chart was created to compare Actual Sales with Budget.

Chart configuration
Visual: Line and Clustered Column Chart
X-axis: Month Year
Column Y-axis: Total Sales
Line Y-axis: Total Budget

The chart allows users to identify months where actual sales were above or below the budget.

KPI Cards

The dashboard contains KPI cards for important financial metrics.

KPI 1 – Total Sales

Displays the total actual sales amount.

KPI 2 – Total Budget

Displays the planned budget amount.

KPI 3 – Variance

Displays the difference between actual sales and budget.

KPI 4 – Profit

Displays total profit.

KPI 5 – Profit Margin

Displays the percentage of sales retained as profit.

Conditional Formatting

Conditional formatting was applied to the Variance values.

Positive variance → Green
Negative variance → Red
Zero or neutral variance → Neutral color

This makes it easier to identify positive and negative financial performance.

Year Filter

A Year slicer was added to allow users to filter the dashboard by year.

Users can select a specific year and view:

Sales
Budget
Variance
Profit
Profit Margin
Monthly trends

for the selected period.

Dashboard Components

The final Financial KPI Scorecard contains:

Total Sales KPI Card
Total Budget KPI Card
Variance KPI Card
Total Profit KPI Card
Profit Margin KPI Card
Monthly Sales Trend
Budget vs Actual Chart
Year Slicer
Conditional Formatting
Dashboard Insights

The dashboard can be used to identify:

Monthly sales trends.
Budget performance.
Positive and negative variances.
Profitability.
Profit margin.
Year-over-year financial performance.
Financial performance across different segments and products.
Tools Used
Microsoft Power BI Desktop
Power Query
DAX
Microsoft Excel
GitHub
Project Structure
Task-5-Financial-KPI-Scorecard/
│
├── README.md
├── Financial Sample.xlsx
├── Financial KPI Scorecard.pbix
└── Dashboard.png
Dashboard Preview

Add your dashboard screenshot to the repository and name it:

Dashboard.png

Then add the following to this README:

## Dashboard Preview

![Financial KPI Scorecard](Dashboard.png)
How to Use
Download the .pbix Power BI file.
Open the file using Power BI Desktop.
Refresh the dataset if required.
Use the Year slicer to filter the report.
Review KPI cards.
Analyze the Monthly Trend.
Compare Budget vs Actual.
Review Variance and Profit Margin.
Conclusion

The Financial KPI Scorecard provides a simple and interactive view of financial performance. It combines actual sales, budget, variance, profit, and profit margin into a single Power BI dashboard.

The dashboard helps users quickly understand whether financial performance is above or below budget and identify monthly trends that can support business decision-making.

Data Source

Microsoft Power BI Financial Sample:

https://learn.microsoft.com/en-us/power-bi/create-reports/sample-financial-download
