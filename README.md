# Retail Sales Performance & Profitability Analysis | Power BI

**End-to-end retail business intelligence portfolio project** featuring approximately **1 million sales transactions**, interactive reporting, DAX, a star-schema data model, and discount scenario analysis.

> **Project status:** Portfolio documentation available. Dashboard screenshots and the `.pbix` report must be added from the finished Power BI Desktop project. Figures below are approximate and should be checked against the final report before publication.

## Project overview
This project explores retail revenue, profitability, product performance, regional trends and customer behaviour using Microsoft Power BI. It is designed to help stakeholders monitor key performance indicators, identify business opportunities and explore the financial implications of additional discounts.

### Reported headline metrics (verify before publishing)

    Metric                 Approximate value

 Total Sales                 £989.58M 
 Total Profit                £425.33M
 Profit Margin                42.98% 

## Business questions
- How are revenue and profit performing over time?
- Which products and categories contribute most to sales and profit?
- How does performance differ by region and sales channel?
- Which customer segments contribute most to revenue?
- How would an additional discount affect sales, profit and profit margin, assuming constant volume and costs?

## Tools and techniques
- **Power BI Desktop** — data modelling, reporting and visualisation
- **Power Query** — data preparation and type validation
- **DAX** — KPI measures, time intelligence and scenario calculations
- **Star schema** — Sales fact table with Products, Customers, Stores and Date dimensions
- **Interactivity** — drill-through, report-page tooltips, bookmarks and field parameters
- **Performance Analyzer** — inspection of visual execution timings

## Data model

 Table            Role                                Example fields 
Sales            Fact                           TransactionID, OrderDate, CustomerID, ProductID, StoreID, SalesAmount, TotalCost, Profit 
Products         Dimension                      ProductID, ProductName, Category, Subcategory 
Customers        Dimension                      CustomerID, CustomerSegment, Region 
Stores           Dimension                      StoreID, StoreName, Region, Channel 
Date             Dimension                      Date, Year, Quarter, YearMonth 
Extra Discount   Disconnected parameter         Extra Discount 

The four dimensions have one-to-many relationships to Sales. The What-If parameter table is intentionally disconnected.

## Dashboard pages

 Page                                    Purpose

Executive Overview                Revenue, profit, margin and high-level sales trends 
Product Analysis                  Product/category contributions and comparisons 
Regional Performance              Regional and channel performance 
Customer Insights                 Customer segments and purchasing activity
Dynamic Performance               Switch measures dynamically using field parameters
Discount Simulator                Evaluate 0–20% additional-discount scenarios 

Supporting pages: **Product Drillthrough**, **Category Tooltip** and **Validation** (kept out of main navigation).


## Selected DAX calculations
```dax
Total Sales = SUM(Sales[SalesAmount])
Total Profit = SUM(Sales[Profit])
Total Cost = SUM(Sales[TotalCost])
Profit Margin % = DIVIDE([Total Profit], [Total Sales], 0)

Simulated Sales =
VAR Discount = MAX('Extra Discount'[Extra Discount])
RETURN [Total Sales] * (1 - Discount)

Simulated Profit = [Simulated Sales] - [Total Cost]
Simulated Profit Margin % = DIVIDE([Simulated Profit], [Simulated Sales], 0)
Profit Impact = [Simulated Profit] - [Total Profit]
```

## Discount Simulator assumptions
The parameter ranges from 0% to 20%. For the **Between** slicer, the lower bound is kept at 0%, and `MAX()` reads the upper bound. The model reduces realised revenue while holding units sold and total cost constant. It is a **scenario analysis**, not a forecast of how customer demand will change.

## Validation and performance
The report includes a dedicated validation page and uses Performance Analyzer to review visual loading times. In a sample recording, observed visual durations were approximately 134–468 ms; these are environment-specific observations, not universal performance benchmarks.

## Business applications
- Compare sales growth with profit margin to avoid focusing on revenue alone.
- Investigate product categories and regions with weaker profitability.
- Examine customer-segment contribution.
- Evaluate the potential financial effect of proposed discounts.

## Repository contents
- dashboard — place your completed Power BI `.pbix` report here
- screenshots  — export six screenshots from Power BI
- documentation — portfolio PDF, DAX measures and data dictionary
- data — data availability and privacy notes; no private raw data is included

## How to open the report
1. Install Microsoft Power BI Desktop.
2. Download the `.pbix` file from `dashboard/` once it has been added.
3. Open it in Power BI Desktop.
4. Explore the six report pages and interact with the slicers, bookmarks, field parameters and discount simulator.


