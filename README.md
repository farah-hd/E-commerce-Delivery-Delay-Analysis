# E-commerce Delivery Delay Analysis & Performance Optimization

## Project Overview
A Business Intelligence project analyzing delivery delays for a medium-to-large e-commerce company.
The project identifies root causes of late deliveries, measures their financial impact, and provides
data-driven recommendations to optimize logistics and improve customer satisfaction.

**Key finding: 58% of all orders are delivered late.**

---

## Business Problem
The company lacks visibility into why 58% of orders arrive late and which factors contribute most
to delivery delays. This project answers 11 analytical questions spanning regions, shipping modes,
product categories, customer segments, and financial impact.

---

## Analytical Questions
1. What percentage of orders are delayed, on-time, or early?
2. Which regions experience the highest delivery delay rates?
3. Which shipping modes result in the most delays?
4. Are certain product categories more prone to delivery delays?
5. Do high-value orders experience more delays than low-value orders?
6. How does delivery delay impact profit per order?
7. Which customer segments are most affected by late deliveries?
8. Is there a relationship between payment type and delivery delay?
9. How do delays vary over time (by month or season)?
10. What is the average shipping time for delayed vs on-time orders?
11. Which cities or states generate the highest number of delayed orders?

---

## Key KPIs
| KPI | Value |
|-----|-------|
| Delivery Delay Rate | 58% |
| On-Time Delivery Rate | 19% |
| Early Delivery Rate | 23% |
| Average Shipping Time | 63.3 days |
| Delayed Orders | 8,000+ |
| Profit Impact Score | 0.56 |
| Highest Delay Mode | Standard Class (41.2%) |

---

## Key Findings
- **58% of orders are delayed**, only 19% arrive on time
- Delays are concentrated in **Santo Domingo, Tegucigalpa, Managua, New York City, and Manila**
- **Standard Class** generates the most delayed orders by volume; First and Second Class show high
  delay rates relative to their volume, meaning premium options are not performing as expected
- **Lower-value orders** have delay rates close to 60%; higher-value orders closer to 45–50%
- Delayed orders have a **profit impact score of 0.56**, confirming a strong negative financial effect
- **Consumer segment** accounts for the highest volume of delayed orders (4K), followed by Corporate (2K)
- Delayed orders take **over 70 days on average** to ship vs 55 days for early deliveries
- Delays peak between **June and August**, mid-year demand overwhelms fulfillment capacity

---

## Data Pipeline (ETL)
Tool: Python (pandas).See `etl/ETL_Ecommerce_Cleaning.ipynb`

Steps performed:
1. Load raw CSV (incom2024_delay_example_dataset.csv)
2. Remove duplicate rows
3. Standardise column names (lowercase + underscore)
4. Convert date columns to datetime
5. Convert numeric columns with coerce on errors
6. Impute missing values: median for numeric, mode for categorical
7. Standardise categorical values (payment_type, shipping_mode, customer_segment, market)
8. Standardise country name variants (ee. uu. → united_states)
9. Validate label column (-1 = Early, 0 = On-time, 1 = Delayed)
10. Create derived columns: delivery_status, order_year, order_month, is_delayed
11. Export cleaned dataset to data_cleaned/

---

## Data Model
Star schema with one fact table and three dimension tables.
See `model/diagram model.png` for the full schema.

| Table | Description |
|-------|-------------|
| Fact_table.csv | Order-level transactions with delivery metrics |
| dim_customer.csv | Customer demographics and location |
| dim_order.csv | Order details and status |
| dim_product.csv | Product categories and pricing |

---

## Dashboard
Built in Power BI Desktop. See `dashboard/dashboard.pbix`.
A PDF export is available at `dashboard/dashboard_PDF.pdf`.
All DAX measures are documented in `dashboard/Delivery_KPI_DAX_Measures.docx`.

Dashboards included:
- Executive Overview (delay rate, revenue, profit KPIs)
- Regional Analysis (delay map by city and country)
- Shipping Mode Performance
- Product Category Analysis
- Customer Segment Analysis
- Time Trend Analysis

---

## Business Recommendations
1. **Redesign delivery promises**, align estimated delivery dates with actual shipping performance
2. **Target high-delay cities**, prioritize Santo Domingo, Tegucigalpa, Managua, NYC, Manila
3. **Reassess premium shipping modes**, First and Second Class are not meeting expectations
4. **Category-specific logistics**, develop fulfillment strategies for bulky and high-risk products
5. **Balance order prioritization**, improve service levels for low-value orders to prevent churn
6. **Proactive customer communication**, notify customers of delays before they escalate
7. **Increase capacity before peak months**, pre-plan for June–August demand surge

---

## Limitations
- Analysis is based on historical data and may not reflect recent operational changes
- External factors (weather, strikes, fuel costs) are not included
- The dataset classifies delays but does not always identify the exact root cause
- Customer satisfaction metrics (reviews, complaints) are not integrated

---

## Future Improvements
- Integrate real-time tracking data for proactive delay detection
- Add external data sources (weather, traffic)
- Link delivery delays to customer satisfaction and churn data
- Apply machine learning to predict delays before they occur
- Expand analysis to supplier and warehouse performance

---

## Tools Used
| Tool | Purpose |
|------|---------|
| Python (pandas, numpy) | Data cleaning and ETL |
| Power BI Desktop | Dashboard and data model |
| DAX | KPI measures and calculated columns |
| SQL | Data querying |
| PDF / PowerPoint | Reporting and presentation |

---
