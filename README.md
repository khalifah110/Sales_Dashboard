# Sales_Dashboard

## Business Problem
Sales Performance, Profitability & Returns Analysis
The leadership team requires a comprehensive performance analysis to evaluate the company’s commercial health and identify opportunities to improve profitability and operational efficiency. While overall sales volume has grown, concerns remain around profit volatility, product-level losses, and increasing order returns.
To support strategic planning and executive decision-making, the following key business questions must be addressed:

1. Metrics-Sales, Profit, % of Returned Orders. Show % change vs PY.


2. Compare Sales performance versus previous year over time.


3. Determine the most profitable product and the most loss making product.


4. Find out the place where most of the profit is happening.


5. Sales by Segment.

---------------------------------------------------------------------------------------------------------------------------------------------------------------------------

Once the business challenges were clearly defined, the data was prepared and analyzed in Power BI to support informed, data-driven decision-making.




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

# Dashboard

<img width="1271" height="660" alt="Screenshot 2026-01-22 111913" src="https://github.com/user-attachments/assets/23085974-a67c-4470-9a57-94721c5b29f0" />

## We finaaly Automated the dashboard.


## 🔍 Key Business Insight

Based on the analysis, the following insights were identified:

1.Total sales amount to $2.33M, while total profit stands at $292.3K, indicating a healthy overall margin.

2.Copiers are the most profitable product category, contributing the highest share of total profit.

3.Tables represent the most loss-making product category, negatively impacting overall profitability.

4.California is the most profitable state, generating the highest level of profit across all regions.

5.The Consumer segment leads in sales, generating $1,170,659.79, which accounts for 50.32% of total sales.

## 📊 Strategic Business Recommendations

### 1️⃣ Optimize Product Portfolio

Expand investment in high-margin products such as Copiers through targeted promotions and inventory prioritization.

Review pricing, discounting, and cost structures for Tables to address consistent losses. Consider redesign, renegotiating supplier costs, or discontinuation if profitability cannot be improved.

### 2️⃣ Strengthen Geographic Focus

Maintain and grow market presence in California, leveraging it as a profit stronghold.

Analyze underperforming regions to identify opportunities for operational improvement or targeted marketing.

### 3️⃣ Segment-Driven Strategy

Continue to prioritize the Consumer segment, as it drives over half of total sales.

Explore upselling and cross-selling strategies within this segment to increase average order value and profitability.

### 4️⃣ Monitor Returns & Profit Trends

Track returned orders year-over-year to identify their impact on profit margins.

Use YoY performance metrics as early indicators for corrective action in declining categories or regions.








