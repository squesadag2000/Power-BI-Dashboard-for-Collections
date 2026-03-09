# Power-BI-Dashboard-for-Collections

A Power BI dashboard for monitoring and analyzing debt collections operations, including portfolio aging, collections rate, agent performance, contact rate heatmap, and payment method analysis.

---

##  Overview

This project provides a fully functional Power BI dashboard built on simulated collections data. It covers the end-to-end process from raw CSV data to a multi-page interactive report, including data modeling, Power Query transformations, DAX measures, and visualization best practices.

The dashboard is organized into 3 report pages:
- **Executive Summary** — KPIs, aging buckets, recovery trend, product distribution
- **Portfolio Management** — Collections rate by country, payment method, and agent performance
- **Collections Operations** — Contact rate heatmap, collection funnel, promise tracking

---

##  Dataset Structure

The dataset follows a **star schema** with 5 dimension tables and 4 fact tables, all in CSV format.

### Dimension Tables

| File | Rows | Description |
|---|---|---|
| `dim_customers.csv` | 1,000 | Customer info: country, segment, contact |
| `dim_products.csv` | 5 | Product types: Credit Card, Loan, Mortgage, etc. |
| `dim_agents.csv` | 10 | Collection agents across 3 teams |
| `dim_payment_methods.csv` | 6 | Payment methods: ACH, Credit Card, Cash, etc. |
| `dim_date.csv` | 731 | Calendar table 2024–2025 with day, week, month attributes |

### Fact Tables

| File | Rows | Description |
|---|---|---|
| `fact_accounts.csv` | 800 | Delinquent accounts with DPD, overdue balance, aging bucket |
| `fact_payments.csv` | ~918 | Processed payments with method and status |
| `fact_calls.csv` | ~1,934 | Collection calls with hour, day, and result |
| `fact_promises.csv` | ~723 | Payment promises with fulfillment status |

### Relationships

```
dim_customers      ──── fact_accounts ──── dim_products
dim_agents         ────      │
dim_date           ────      │
                        fact_payments ──── dim_payment_methods
                        fact_calls
                        fact_promises
```

---

## Key Metrics

| Metric | Description |
|---|---|
| **Collections Rate** | Amount Collected / Total Overdue Balance |
| **Delinquency Rate** | Overdue Balance / Total Portfolio Balance |
| **Average DPD** | Average Days Past Due across all accounts |
| **Contact Rate** | Contacted Calls / Total Calls |
| **Promise Fulfillment Rate** | Fulfilled Promises / Total Promises |
| **Target Achievement %** | Amount Collected / Collection Target |

---

##  Repository Structure

```
collections-dashboard-powerbi/
│
├── data/
│   ├── dim_customers.csv
│   ├── dim_products.csv
│   ├── dim_agents.csv
│   ├── dim_payment_methods.csv
│   ├── dim_date.csv
│   ├── fact_accounts.csv
│   ├── fact_payments.csv
│   ├── fact_calls.csv
│   └── fact_promises.csv
│
├── collections_dashboard.pbix
└── README.md
```

---


## 👤 Author

**sebastiainq**  
[github.com/sebastiainq](https://github.com/sebastiainq)

---

## 📄 License

This project is open source and available under the [MIT License](LICENSE).
