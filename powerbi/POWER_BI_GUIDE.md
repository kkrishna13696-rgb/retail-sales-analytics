# Power BI Dashboard: Build Guide (about 30 minutes)

## 1. Load
Home > Get Data > Text/CSV > `data/superstore_clean.csv` > Transform Data. Check `Order Date` and `Ship Date` are Date type, `Postal Code` is Text. Close & Apply.

## 2. DAX measures
Right-click the table > New measure:
```
Total Sales = SUM(superstore_clean[Sales])
Total Profit = SUM(superstore_clean[Profit])
Profit Margin % = DIVIDE([Total Profit], [Total Sales])
Total Orders = DISTINCTCOUNT(superstore_clean[Order ID])
Avg Discount % = AVERAGE(superstore_clean[Discount])
Loss-Making Lines = CALCULATE(COUNTROWS(superstore_clean), superstore_clean[Profit] < 0)
```
Format Profit Margin % and Avg Discount % as percentage.

## 3. Layout (one page, title: "Retail Sales Performance Dashboard")
| Zone | Visual |
|---|---|
| Top row | 4 KPI cards: Total Sales, Total Profit, Profit Margin %, Total Orders |
| Left, row 2 | Line chart: Axis = Order Date (Year, Month), Values = Total Sales, Total Profit |
| Middle, row 2 | Clustered bar: Category vs Total Sales and Total Profit |
| Right, row 2 | Donut: Segment by Total Sales |
| Left, row 3 | Bar: Sub-Category by Total Profit (conditional colour: negative = red) |
| Middle, row 3 | Filled map or bar: State by Total Profit |
| Right, row 3 | Scatter: X = Avg Discount %, Y = Profit Margin %, Details = Sub-Category |
| Left column or top | Slicers: Year, Region, Category, Segment |

## 4. Finish
Same colour theme throughout, align visuals to a grid, add text boxes for 2-3 key takeaways, then take a full-page screenshot into `powerbi/dashboard.png` and save `powerbi/retail_dashboard.pbix`.
