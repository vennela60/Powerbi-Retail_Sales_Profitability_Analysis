# DAX Measures

These are the key formulas used in the report. Confirm each against the final `.pbix` before publishing.

```dax
Total Sales = SUM(Sales[SalesAmount])
Total Profit = SUM(Sales[Profit])
Total Cost = SUM(Sales[TotalCost])
Total Orders = DISTINCTCOUNT(Sales[TransactionID])
Total Quantity = SUM(Sales[Quantity])
Profit Margin % = DIVIDE([Total Profit], [Total Sales], 0)

Selected Extra Discount = MAX('Extra Discount'[Extra Discount])

Simulated Sales =
VAR Discount = MAX('Extra Discount'[Extra Discount])
RETURN [Total Sales] * (1 - Discount)

Simulated Profit = [Simulated Sales] - [Total Cost]
Simulated Profit Margin % = DIVIDE([Simulated Profit], [Simulated Sales], 0)
Profit Impact = [Simulated Profit] - [Total Profit]

Discount Scenario Label =
"Extra Discount: " & FORMAT(MAX('Extra Discount'[Extra Discount]), "0%")
```

## What-If logic

The Between slider should have a lower bound of zero. `MAX()` selects its upper bound. The calculations assume no changes in sales quantity or cost.

## Validation

```dax
Profit Reconciliation = [Total Sales] - [Total Cost] - [Total Profit]
```

A zero result is expected only if the source columns use mutually consistent definitions of sales, cost and profit.
