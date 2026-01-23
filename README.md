# Sales_Dashboard

# Dashboard

<img width="1271" height="660" alt="Screenshot 2026-01-22 111913" src="https://github.com/user-attachments/assets/23085974-a67c-4470-9a57-94721c5b29f0" />




# Data Modeling
<img width="1535" height="520" alt="Screenshot 2026-01-22 111617" src="https://github.com/user-attachments/assets/284e72bd-d0ec-4b08-a150-55c4094512bc" />



# 🧮 DAX Measures & Calculations

The following DAX measures were created to analyze returns, sales, profit, and year-over-year (YoY) performance (*Time Interlligence Calculation*):

| Measure Name | DAX Formula | Description |
|-------------|------------|-------------|
| **% Returned Orders** | `DIVIDE(DISTINCTCOUNT('Return'[Order ID]), DISTINCTCOUNT(Orders[Order ID]))` | Calculates the percentage of total orders that were returned. |
| **Total Profit** | `SUM(Orders[Profit])` | Calculates total profit across all orders. |
| **Total Sales** | `SUM(Orders[Sales])` | Calculates total sales revenue. |
| **% Returned Orders PY** | `CALCULATE([% Returned Orders], SAMEPERIODLASTYEAR('Data Table'[Date]))` | Computes the percentage of returned orders in the previous year. |
| **Profit PY** | `CALCULATE([Total Profit], SAMEPERIODLASTYEAR('Data Table'[Date]))` | Calculates total profit for the previous year. |
| **Sales PY** | `CALCULATE([Total Sales], SAMEPERIODLASTYEAR('Data Table'[Date]))` | Calculates total sales for the previous year. |
| **YoY Change – Returned Orders %** | `[% Returned Orders] - [% Returned Orders PY]` | Measures year-over-year change in the return rate. |
| **YoY Change – Profit %** | `DIVIDE([Total Profit] - [Profit PY], [Profit PY])` | Calculates year-over-year profit growth rate. |
| **YoY Change – Sales %** | `DIVIDE([Total Sales] - [Sales PY], [Sales PY])` | Calculates year-over-year sales growth rate. |

### Measures Snippet
```dax
// Percentage of Returned Orders
% Returned Orders =
VAR _total_orders = DISTINCTCOUNT(Orders[Order ID])
VAR _returned_orders = DISTINCTCOUNT('Return'[Order ID])
RETURN
DIVIDE(_returned_orders, _total_orders)

// Total Profit
Total Profit =
SUM(Orders[Profit])

// Total Sales
Total Sales =
SUM(Orders[Sales])

// Previous Year Returned Orders %
% Returned Orders PY =
CALCULATE(
    [% Returned Orders],
    SAMEPERIODLASTYEAR('Data Table'[Date])
)

// Previous Year Profit
Profit PY =
CALCULATE(
    [Total Profit],
    SAMEPERIODLASTYEAR('Data Table'[Date])
)

// Previous Year Sales
Sales PY =
CALCULATE(
    [Total Sales],
    SAMEPERIODLASTYEAR('Data Table'[Date])
)

// YoY Change in Returned Orders %
YoY Change – Returned Orders % =
[% Returned Orders] - [% Returned Orders PY]

// YoY Profit Growth
YoY Change – Profit % =
DIVIDE(
    [Total Profit] - [Profit PY],
    [Profit PY]
)

// YoY Sales Growth
YoY Change – Sales % =
DIVIDE(
    [Total Sales] - [Sales PY],
    [Sales PY]
)
```
