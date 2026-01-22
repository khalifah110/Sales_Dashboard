# Sales_Dashboard

# Dashboard

<img width="1271" height="660" alt="Screenshot 2026-01-22 111913" src="https://github.com/user-attachments/assets/23085974-a67c-4470-9a57-94721c5b29f0" />




# Data Modeling
<img width="1535" height="520" alt="Screenshot 2026-01-22 111617" src="https://github.com/user-attachments/assets/284e72bd-d0ec-4b08-a150-55c4094512bc" />




## 🧮 DAX Measures & Calculations

To drive the visualizations in this dashboard, the following DAX measures were created to aggregate the raw customer data:

| Metric | DAX Formula | Description |
| :--- | :--- | :--- |
| *Total Customers* | Number of customer = COUNT('public customer_data'[customer_id]) | Calculates the total count of unique customer IDs. |
| *Average Purchase* | Average Purchse Amount = AVERAGE('public customer_data'[purchase_amount]) | Calculates the mean value of all transactions. |
| *Average Rating* | Average Review Rating = AVERAGE('public customer_data'[review_rating]) | Calculates the mean satisfaction score across all reviews. |

### Measures Snippet
```dax
// Total Number of Customers
Number of customer = COUNT('public customer_data'[customer_id])

// Average Purchase Value
Average Purchse Amount = AVERAGE('public customer_data'[purchase_amount])

// Average Customer Satisfaction
Average Review Rating = AVERAGE('public customer_data'[review_rating])
