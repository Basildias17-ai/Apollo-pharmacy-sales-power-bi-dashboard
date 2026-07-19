# Apollo-Style Pharmacy Sales Dashboard | Power BI

An end-to-end pharmacy sales analytics project built in Microsoft Power BI using Power Query, Star Schema modelling, DAX, Pareto Analysis, Heatmap, Decomposition Tree, Month-on-Month analysis and Drill-Through.

> **Disclaimer:** This is an independent portfolio project created for educational purposes using synthetic data. It is not affiliated with, endorsed by, or connected to Apollo Hospitals or Apollo Pharmacy.

---

## Dashboard Preview

### Page 1 — Executive Overview

![Executive Overview](assets/dashboard-page-1.png)

### Page 2 — Advanced Business Analysis

![Advanced Analysis](assets/dashboard-page-2.png)

### Page 3 — Drill-Through Analysis

![Drill-Through Page](assets/dashboard-page-3.png)

---

## Project Overview

The purpose of this project is to analyse pharmacy sales performance and convert raw transaction-level data into actionable business insights.

The dashboard focuses on answering questions related to:

* Revenue and profitability performance
* Month-on-Month business growth
* Product and category contribution
* Store and regional performance
* Discount impact on profitability
* Return-related revenue leakage
* Peak sales days and hours
* Customer and channel performance
* Root causes behind changes in revenue and margin

This project goes beyond basic KPI reporting by including advanced analytical features such as Pareto Analysis, Heatmap, Decomposition Tree and Drill-Through.

---

## Business Problem

A pharmacy business generates large amounts of transaction data across multiple stores, products, customers, sales channels and payment methods.

However, raw sales data alone does not clearly explain:

* Which stores and products are driving revenue?
* Which business areas are affecting gross margin?
* Whether discounts are improving sales or reducing profitability
* Which return reasons are responsible for maximum financial loss
* What time periods generate the highest and lowest sales
* Which factors are causing changes in business performance

This dashboard was designed to answer these questions through an interactive and business-focused Power BI solution.

---

## Dashboard Pages

### Page 1: Executive Overview

The first page provides a high-level summary of overall business performance.

Key features include:

* Realized Revenue
* Gross Margin Percentage
* Gross Margin Amount
* COGS
* Discount Percentage
* Total Transactions
* Average Bill Value
* Month-on-Month comparison with dynamic arrows
* Monthly revenue and performance trends
* Product and store-level performance analysis
* Interactive slicers and cross-filtering

---

### Page 2: Advanced Analysis

The second page focuses on deeper business analysis and identifying the main drivers behind performance.

Key features include:

* Return Reason Pareto Analysis
* Cumulative Return Percentage
* 80/20 contribution analysis
* Day and Hour Sales Heatmap
* Decomposition Tree
* Revenue and margin driver analysis
* Store, category and product-level breakdown
* Operational and return leakage analysis

---

### Page 3: Drill-Through Analysis

The third page provides detailed analysis for a selected business entity.

Users can right-click on a store, category, product or other supported dimension and navigate to the drill-through page.

Key features include:

* Selected entity-level KPI analysis
* Detailed revenue and profitability trends
* Product or store-level performance
* Return and discount analysis
* Dynamic filter context
* Back-navigation button

---

## Key Performance Indicators

The dashboard includes the following KPIs:

| KPI                | Description                                                    |
| ------------------ | -------------------------------------------------------------- |
| Realized Revenue   | Revenue earned after adjusting for discounts and returns       |
| Gross Amount       | Sales value before discount and return adjustments             |
| Gross Margin       | Revenue remaining after deducting cost of goods sold           |
| Gross Margin %     | Gross margin as a percentage of realized revenue               |
| COGS               | Total cost of goods sold                                       |
| Discount %         | Overall discount rate applied to sales                         |
| Transactions       | Number of unique sales transactions                            |
| Average Bill Value | Average revenue generated per transaction                      |
| Return Amount      | Estimated financial value of returned products                 |
| Return Rate        | Percentage of transactions or quantity associated with returns |

---

## Advanced Analytics Used

### Month-on-Month Analysis

Month-on-Month measures compare the current month’s performance with the previous month.

Dynamic arrows are used to indicate whether the KPI has increased, decreased or remained unchanged.

Examples include:

* Realized Revenue MoM %
* Gross Margin MoM %
* COGS MoM %
* Discount MoM %
* Transactions MoM %
* Average Bill Value MoM %

---

### Pareto Analysis

The Pareto Chart helps identify the few return reasons responsible for most of the total return-related financial loss.

The chart uses:

* Return Amount
* Return Reason Rank
* Cumulative Return Amount
* Cumulative Return Percentage

The bars represent the individual Return Amount for each return reason, while the line represents the cumulative percentage of total returns.

This helps the business prioritise the most important causes instead of treating every return reason equally.

---

### Heatmap

The Heatmap is used to analyse sales performance across different days and hours.

It helps identify:

* Peak purchasing periods
* Low-performing time slots
* Customer buying patterns
* Store staffing requirements
* Operational planning opportunities

---

### Decomposition Tree

The Decomposition Tree allows users to interactively investigate the factors driving revenue or profitability.

The analysis can be broken down using dimensions such as:

* Region
* State
* City
* Store
* Sales Channel
* Product Category
* Subcategory
* Product
* Customer Segment

---

### Drill-Through

Drill-Through enables users to move from a summary visual to a detailed analysis page for a selected store, product, category or other business dimension.

This provides detailed analysis without overcrowding the main dashboard pages.

---

## Data Preparation

The dataset was cleaned and transformed using Power Query.

Key transformation steps included:

* Correcting column data types
* Checking null values and data quality
* Creating a staging query
* Disabling load for the staging query
* Creating Fact and Dimension tables using Reference queries
* Removing duplicate values from Dimension tables
* Creating surrogate keys for status dimensions
* Merging keys into the Fact table
* Removing unnecessary descriptive columns from the Fact table

---

## Why Was the Staging Query Load Disabled?

The staging query was used only as a base query for creating the Fact and Dimension tables.

Its load was disabled because it was not required inside the final Power BI data model.

This helped:

* Avoid loading the same transaction data twice
* Reduce unnecessary model size
* Keep the model clean
* Improve maintainability
* Prevent confusion between raw and final analytical tables

The staging query still refreshes whenever the source file is updated, and all dependent Fact and Dimension tables refresh automatically.

---

## Data Model

A Star Schema was created with one central Fact table connected to multiple Dimension tables.

![Data Model](assets/data-model.png)

### Fact Table

`Fact_Sales`

The Fact table contains transaction-level identifiers, foreign keys and measurable numeric values.

Examples:

* Transaction ID
* Line ID
* Transaction Date
* Store ID
* Product ID
* Customer ID
* Unit Price
* Quantity
* Discount Percentage
* COGS
* Return Quantity
* Inventory Status Key
* Prescription Status Key

### Dimension Tables

* `Dim_Date`
* `Dim_Store`
* `Dim_Product`
* `Dim_Customer`
* `Dim_Channel`
* `Dim_Payment`
* `Dim_Campaign`
* `Dim_ReturnReason`
* `Dim_InventoryStatus`
* `Dim_PrescriptionStatus`

The Fact table explains **what happened**, while Dimension tables help analyse **where, when, how and for whom it happened**.

---

## Tools and Technologies

* Microsoft Power BI
* Power Query
* DAX
* Microsoft Excel
* Star Schema Data Modelling
* Data Visualisation
* Business Intelligence
* Business Analysis

---

## Repository Structure

```text
Apollo-pharmacy-sales-power-bi-dashboard/
│
├── README.md
│
├── dashboard/
│   └── Apollo_Pharmacy_Sales_Dashboard.pbix
│
├── dataset/
│   └── Pharmacy_Sales_Dataset.xlsx
│
├── dax/
│   └── DAX_Measures.md
│
├── theme/
│   └── Pharmacy_Dashboard_Theme.json
│
├── assets/
│   ├── dashboard-page-1.png
│   ├── dashboard-page-2.png
│   ├── dashboard-page-3.png
│   └── data-model.png
│
└── docs/
    └── Business_Problem_and_Insights.md
```

---

## How to Use the Project

1. Download or clone this repository.
2. Open the `.pbix` file using Microsoft Power BI Desktop.
3. Update the Excel dataset file path if required.
4. Open Power Query and verify the source file location.
5. Click **Close & Apply**.
6. Refresh the Power BI report.
7. Use the slicers and interactive visuals to explore the dashboard.

---

## Important Notes

* The dataset used in this project is synthetic.
* No confidential company, client or patient data has been used.
* The dashboard is intended for portfolio and educational purposes.
* File paths may need to be updated after downloading the project.
* Power BI Desktop is required to open the `.pbix` file.

---

## Skills Demonstrated

* Data Cleaning
* Power Query Transformation
* Fact and Dimension Table Creation
* Star Schema Modelling
* DAX Measure Development
* Time-Intelligence Analysis
* Month-on-Month Analysis
* Pareto Analysis
* Root-Cause Analysis
* Drill-Through Implementation
* Dashboard UI Design
* Business Storytelling
* Analytical Thinking

---

## Author

**Basil Dias**

Power BI | SQL | Healthcare and Business Analytics

This project was created as part of my data analytics portfolio.
