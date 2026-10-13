# Data Dictionary

## Sales (fact table)

 Column                               Description 

 TransactionID               Transaction/order identifier 
 OrderDate                   Date of transaction 
 CustomerID                  Customer key 
 ProductID                   Product key 
 StoreID                     Store key 
 Quantity                    Units purchased
 UnitPrice                   Recorded unit selling price 
 DiscountPct                 Recorded transaction discount percentage 
 UnitCost                    Recorded unit cost 
 SalesAmount                 Recorded transaction revenue 
 TotalCost                   Recorded transaction cost 
 Profit                      Recorded transaction profit 
 PaymentMethod               Payment method 

## Products

ProductID, ProductName, Category, Subcategory, UnitCost, ListPrice.

## Customers

CustomerID, CustomerSegment, Region, JoinDate.

## Stores

StoreID, StoreName, Region, Channel.

## Date

Date, Year, Quarter, MonthNumber, MonthName, YearMonth, DayOfWeek.

## Extra Discount

Disconnected What-If parameter table containing decimal values from 0 to 0.20 in 0.01 increments.

**Note:** Descriptions reflect the report schema discussed in the project. Verify precise source definitions, currency, date coverage and data quality before publication.
