# Samsung-Supply-Chain-Logistic-Dashboard
<img width="1305" height="731" alt="image" src="https://github.com/user-attachments/assets/9b4aa3a0-9fd3-4120-a790-7e015d56168e" />

# 1. Project Overview

The **Samsung Supply Chain & Logistics Dashboard** is an interactive Power BI business intelligence solution designed to analyze and monitor the performance of a supply chain across multiple business functions.

The dashboard brings together information related to:

* Sales
* Procurement
* Production
* Inventory
* Shipments
* Customers
* Suppliers
* Facilities
* Products
* Delivery performance
* Revenue and profitability

The primary objective is to convert raw operational data into **actionable business insights** that can help management understand:

* How much revenue is being generated
* How profitable the business is
* How efficiently orders are being fulfilled
* Where shipment delays are occurring
* How much inventory is available
* Which products hold the most inventory
* Which suppliers have higher lead times
* How sales and profit are changing over time
* Whether customer orders are being fulfilled successfully
* How supply-chain performance varies across countries

The dashboard is designed as an **executive-level overview**, while still providing product, supplier, geographical and time-based analysis.

The dashboard interface contains KPI cards, country filters, product filters, supplier analysis, inventory analysis, time-series analysis and achievement visualization. 

---

# 2. Business Problem

Large supply chains generate huge amounts of transactional data across different stages:

**Supplier → Procurement → Production → Inventory → Shipment → Customer**

When these processes are analyzed separately, management may struggle to identify the relationship between:

* Procurement lead time
* Inventory levels
* Production
* Sales
* Shipping
* Delivery
* Revenue
* Profitability

For example, a company may have strong sales but still face:

* High inventory holding
* Delayed shipments
* High transportation costs
* Long supplier lead times
* Poor order fulfillment
* Low perfect-order performance

Therefore, the business needs a centralized analytical solution that provides a **360-degree view of supply-chain performance**.

---

# 3. Project Objective

The major objectives of the dashboard are:

### Financial Analysis

* Analyze total revenue
* Analyze sales cost
* Calculate profit
* Monitor profit margin
* Analyze revenue and profit trends

### Supply Chain Analysis

* Monitor inventory levels
* Analyze shipment quantities
* Track delivered quantities
* Analyze delayed orders
* Evaluate perfect-order performance

### Supplier Analysis

* Compare suppliers based on lead time
* Identify suppliers with relatively higher lead times
* Understand supplier performance

### Product Analysis

* Analyze inventory by product
* Identify products holding high inventory
* Compare product-level supply-chain performance

### Logistics Analysis

* Track total shipments
* Analyze shipping cost
* Identify delivery performance issues

### Geographic Analysis

* Compare business performance across:

  * USA
  * Poland
  * India

---

# 4. Technology Stack

## Primary Tool

**Microsoft Power BI**

Used for:

* Data modeling
* Data transformation
* DAX calculations
* Interactive visualization
* KPI creation
* Dashboard design
* Business analysis

## Data Modeling

The dashboard uses a **star-schema-style model** containing multiple dimension and fact tables.

The visible model contains:

### Dimension Tables

* `dim_customer`
* `dim_date`
* `dim_facility`
* `dim_product`
* `dim_supplier`

### Fact Tables

* `fact_inventory`
* `fact_procurement`
* `fact_production`
* `fact_sales`
* `fact_shipment`

This structure is visible in the Power BI model screenshot. 

---

# 5. Data Model Architecture

The overall analytical architecture can be understood as:

```text
                     dim_date
                        |
                        |
dim_customer ---- fact_sales ---- dim_product
                        |
                        |
                   dim_facility
                        |
                        |
                   Supply Chain
                        |
        ---------------------------------
        |               |               |
 fact_procurement  fact_production  fact_inventory
        |               |               |
        |               |               |
        -------- dim_supplier ----------
                        |
                  fact_shipment
```

The exact relationship paths should be validated against the actual Power BI model, but conceptually the model follows a **central fact + shared dimensions** approach.

---

# 6. Dimension Tables

## 6.1 dim_customer

This dimension contains customer-related information.

Potential analytical attributes include:

* Customer ID
* Customer Name
* Customer location
* Customer category
* Geographic information

### Business purpose

It allows the dashboard to analyze sales and order behavior from the customer perspective.

Possible analysis:

* Revenue by customer
* Orders by customer
* Customer-level shipment performance
* Customer demand

---

# 7. dim_date

The date dimension is essential for time-based analysis.

It enables:

* Year analysis
* Month analysis
* Quarterly analysis
* Year-over-year analysis
* Monthly trends
* Daily analysis

The dashboard's **Total Sales & Profit By Time** visual uses a time dimension to analyze changes over the displayed period. 

### Recommended date columns

A professional date table would typically contain:

```text
Date
Year
Month
Month Number
Quarter
Quarter Number
Year-Month
Day
Week
```

---

# 8. dim_facility

This dimension represents facilities involved in the supply chain.

Examples could include:

* Manufacturing facilities
* Warehouses
* Distribution centers
* Production locations

### Business purpose

Facility-level analysis can help determine:

* Inventory concentration
* Production activity
* Shipment activity
* Facility performance

---

# 9. dim_product

This dimension contains product-related information.

The dashboard prominently uses **Product Name** as a filter and analytical dimension. The visible product list includes products such as:

* Smart Front Load Washer
* OLED 65" 4K
* Neo QLED 85" 4K
* Galaxy Z Fold5
* Galaxy Z Flip5
* Galaxy Watch6 Classic
* Galaxy Tab S9 Ultra
* Galaxy Tab S9

These products appear in the dashboard's product selector and inventory analysis. 

### Business purpose

Product analysis allows management to understand:

* Which products have high inventory
* Which products drive sales
* Which products require greater supply
* Which products may be overstocked

---

# 10. dim_supplier

This dimension contains supplier information.

The dashboard uses **Supplier Name** for lead-time analysis.

The supplier chart compares average lead time across suppliers, with displayed values ranging approximately from 3.0K to 3.9K in the current formatting. 

### Business purpose

Supplier analysis helps identify:

* Suppliers with longer lead times
* Potential procurement bottlenecks
* Supplier performance differences
* Opportunities for supplier optimization

---

# 11. Fact Tables

The model contains five major transactional fact tables. 

---

## 11.1 fact_sales

This is the primary sales transaction table.

It is likely responsible for metrics such as:

* Sales quantity
* Revenue
* Sales cost
* Profit
* Profit margin

### Business questions

* How much did we sell?
* How much revenue did we generate?
* What was the sales cost?
* How profitable were sales?
* How are sales changing over time?

---

# 12. fact_procurement

This table represents procurement activity.

It is relevant to:

* Supplier performance
* Procurement quantity
* Lead time
* Procurement cost
* Supplier-related analysis

The dashboard's **Average Lead Time by Supplier Name** is conceptually linked to procurement/supplier activity.

---

# 13. fact_production

This fact table represents manufacturing/production activity.

It can be used to understand:

* Production quantity
* Manufacturing activity
* Facility utilization
* Product production
* Supply availability

This becomes particularly useful when combined with inventory and sales information.

---

# 14. fact_inventory

This table represents inventory information.

The dashboard uses it to calculate/display:

* Inventory Stock
* Safety Stock
* Inventory by Product

The inventory chart shows products ranked by inventory stock, with the highest visible product around **25K units**, followed by approximately **22K, 20K, 15K, 14K**, etc. 

---

# 15. fact_shipment

This table represents logistics and shipment activity.

It supports metrics such as:

* Total Shipment
* Total Shipment Quantity
* Delivered Quantity
* Delayed Orders
* Shipping Cost
* Perfect Order

This table is central to evaluating logistics efficiency.

---

# 16. Data Model Approach

The model follows a **multi-fact star-schema approach**.

Instead of putting everything into one huge table, the project separates:

```text
Sales
Procurement
Production
Inventory
Shipment
```

and connects them to common dimensions such as:

```text
Date
Product
Supplier
Customer
Facility
```

### Why this is useful

This architecture improves:

* Data organization
* DAX calculation reliability
* Performance
* Filtering
* Scalability
* Maintainability

It also allows the same product/date/supplier filters to affect multiple business processes.

---

# 17. DAX Measures

The dashboard contains a dedicated `Dax_Measures` table containing measures for financial, inventory, sales and logistics analysis. 

The visible measures include:

1. Average Lead Time
2. Defective Unit
3. Inventory Stock
4. Order Quantity
5. Perfect Order
6. Profit
7. Profit Margin
8. Safety Stock
9. Total Delayed Order
10. Total Delivered Quantity
11. Total Revenue
12. Total Sales Cost
13. Total Sales Quantity
14. Total Shipment
15. Total Shipment Quantity
16. Total Shipping Cost

---

# 18. KPI Documentation

## 18.1 Total Revenue

### Definition

Total revenue represents the total monetary value generated from sales.

Conceptually:

```DAX
Total Revenue =
SUM(Sales[Revenue])
```

### Business question

> How much revenue has the business generated?

The dashboard displays approximately **$176.95M** in the achievement visualization/current overall context. 

---

# 19. Total Sales Cost

### Definition

Total Sales Cost represents the total cost associated with sold products.

Conceptually:

```DAX
Total Sales Cost =
SUM(Sales[Sales Cost])
```

The dashboard displays approximately **78.13M** for Total Sales Cost. 

---

# 20. Profit

Profit measures the amount remaining after relevant sales costs.

Conceptually:

```DAX
Profit =
[Total Revenue] - [Total Sales Cost]
```

Based on the displayed revenue, sales cost and profit-margin context, the dashboard appears to be operating with profit in the tens of millions rather than hundreds of millions; the KPI card itself is visually truncated. 

---

# 21. Profit Margin

Profit margin represents profitability relative to revenue.

Formula:

```DAX
Profit Margin =
DIVIDE(
    [Profit],
    [Total Revenue],
    0
)
```

The dashboard shows approximately:

**27.44%**

This means that roughly ₹/$0.274 of profit is generated for every ₹/$1 of revenue, depending on the dataset's currency convention. 

---

# 22. Total Shipment

Total Shipment measures the number of shipment transactions.

Conceptually:

```DAX
Total Shipment =
COUNTROWS(fact_shipment)
```

or potentially:

```DAX
DISTINCTCOUNT(fact_shipment[ShipmentID])
```

depending on the dataset design.

The dashboard shows approximately:

**8K shipments**. 

---

# 23. Total Shipment Quantity

This represents the total number of units included in shipments.

Conceptually:

```DAX
Total Shipment Quantity =
SUM(fact_shipment[ShipmentQuantity])
```

The dashboard displays approximately:

**3M**. 

---

# 24. Total Delivered Quantity

This measures the quantity successfully delivered to customers.

Conceptually:

```DAX
Total Delivered Quantity =
SUM(fact_shipment[DeliveredQuantity])
```

The dashboard shows approximately:

**187K** in the displayed context. 

### Important validation point

Because **Total Shipment Quantity (~3M)** and **Total Delivered Quantity (~187K)** appear to use different scales, the business definition and filter context should be validated.

Possible explanations include:

* Different units
* Different date filters
* Different fact-table grain
* Delivered quantity being recorded differently
* Data-quality issue

This is something worth checking before presenting the metric as an operational KPI.

---

# 25. Total Delayed Order

This measures orders that were delivered later than the expected delivery date.

Conceptually:

```DAX
Total Delayed Order =
CALCULATE(
    [Order Quantity],
    Shipment[DeliveryStatus] = "Delayed"
)
```

The dashboard displays approximately:

**573 delayed orders**. 

---

# 26. Perfect Order

Perfect Order is a key supply-chain performance KPI.

It generally evaluates whether an order was fulfilled correctly across multiple dimensions such as:

* On-time delivery
* Complete delivery
* Damage-free delivery
* Accurate fulfillment

A simplified calculation could be:

```DAX
Perfect Order % =
DIVIDE(
    Perfect Orders,
    Total Orders,
    0
)
```

The dashboard shows:

**75.29%**

This indicates that approximately three-quarters of orders meet the project's definition of a perfect order. 

### Business interpretation

A 75.29% perfect-order rate indicates there is considerable room to improve fulfillment reliability.

---

# 27. Inventory Stock

Inventory Stock represents the quantity currently held in inventory.

Conceptually:

```DAX
Inventory Stock =
SUM(fact_inventory[InventoryQuantity])
```

The dashboard shows approximately:

**160K units**. 

---

# 28. Safety Stock

Safety stock represents inventory maintained to protect against:

* Demand variability
* Supplier delays
* Production variability
* Transportation delays

A useful analysis is:

```text
Inventory Stock
vs
Safety Stock
```

If inventory is consistently far above safety-stock requirements, the organization may be carrying excess inventory.

If inventory falls below safety stock, stockout risk increases.

---

# 29. Order Quantity

Order Quantity represents the number of units/orders placed within the selected context.

The dashboard displays approximately:

**129K**. 

---

# 30. Average Lead Time

Average Lead Time measures the typical time required for procurement/supply activity.

Conceptually:

```DAX
Average Lead Time =
AVERAGE(fact_procurement[LeadTime])
```

The dashboard compares suppliers based on this metric.

### Critical dashboard observation

The chart labels show values such as:

* 3.9K
* 3.8K
* 3.1K
* 3.0K

If these values represent **days**, they are clearly unrealistic for normal supply-chain lead times.

Therefore, one of the following is likely true:

1. Lead time is measured in another unit.
2. The visual formatting is incorrect.
3. The measure is aggregating a value before averaging.
4. The underlying field contains unusually large values.
5. The measure is calculating duration in a base unit such as minutes/hours.

This should definitely be validated in the model.

For a portfolio project, I'd recommend displaying:

```text
Average Lead Time (Days)
```

rather than simply:

```text
Average Lead Time
```

if the actual unit is days.

---

# 31. Defective Unit

Defective Unit measures products/units identified as defective during production or quality inspection.

Conceptually:

```DAX
Defective Unit =
SUM(fact_production[DefectiveUnits])
```

This KPI can be used to evaluate:

* Manufacturing quality
* Product quality
* Production efficiency
* Waste

A useful future KPI would be:

```text
Defect Rate =
Defective Units / Total Production Units
```

---

# 32. Dashboard Layout

The dashboard follows a structured executive-dashboard design.

The main page is titled:

**Samsung — Overview**

with the subtitle:

**Supply Chain & Logistic Dashboard**. 

The dashboard can be divided into approximately **six analytical zones**.

---

# 33. Zone 1 — Executive KPI Section

The left-hand section contains important business KPIs.

Visible metrics include:

* Total Revenue
* Profit
* Profit Margin
* Total Shipment
* Total Delayed Order
* Total Sales Cost
* Perfect Order
* Total Shipping Cost

These KPIs give management an immediate snapshot of financial and operational performance. 

### Why this design works

A manager should be able to answer within a few seconds:

> How much are we earning?

> How profitable are we?

> How many shipments are happening?

> How many are delayed?

> How much are we spending on logistics?

> How efficiently are orders being fulfilled?

---

# 34. Zone 2 — Geographic Filters

The dashboard provides country-level filtering:

* USA
* Poland
* India

Selecting one of these locations should filter the relevant dashboard visuals based on the model relationships. 

This allows comparative analysis such as:

```text
USA
vs
Poland
vs
India
```

Potential metrics to compare:

* Revenue
* Profit
* Inventory
* Shipment
* Delivery
* Shipping cost
* Perfect order

---

# 35. Zone 3 — Supply Chain Navigation

The top-right section contains four navigation elements:

### Manufacturer

Represents the manufacturing/production side.

### Shipment

Represents logistics and transportation.

### Customers

Represents customer/order activity.

### Supplier

Represents supplier/procurement activity.

These elements create a **supply-chain journey**:

```text
Supplier
    ↓
Manufacturer
    ↓
Shipment
    ↓
Customer
```

That's actually a nice storytelling device because it helps users understand the flow of the supply chain rather than seeing isolated metrics.

---

# 36. Zone 4 — Operational KPI Cards

The dashboard includes cards for:

### Inventory Stock

Approximately:

**160K**

### Total Shipment Quantity

Approximately:

**3M**

### Total Delivered Quantity

Approximately:

**187K**

### Order Quantity

Approximately:

**129K**

These provide a quick operational snapshot. 

---

# 37. Zone 5 — Supplier Analysis

### Visual:

**Avg Lead Time By Supplier Name**

This is a vertical bar chart.

The purpose is to compare supplier lead times.

The visible chart shows suppliers with lead-time values approximately between 3.0K and 3.9K under the current formatting. 

### Business questions answered

* Which suppliers have the longest lead time?
* Which suppliers have the shortest lead time?
* Are supplier lead times relatively consistent?
* Which suppliers should procurement investigate?

### Business action

If a supplier consistently has significantly higher lead times:

* Renegotiate SLA
* Review supplier capacity
* Investigate transportation
* Consider alternative suppliers
* Increase safety stock where appropriate

---

# 38. Zone 6 — Inventory by Product

### Visual:

**Inventory Stock By Product Name**

This horizontal bar chart ranks products according to inventory stock.

Visible examples include:

| Product               | Approx. Inventory |
| --------------------- | ----------------: |
| Galaxy S24 Ultra      |               25K |
| Galaxy Buds2 Pro      |               22K |
| Galaxy Watch6 Classic |               20K |
| Galaxy S23            |               15K |
| Galaxy Z Flip5        |               14K |
| Galaxy S24            |               13K |
| Galaxy Z Fold5        |               13K |
| Galaxy Tab A9         |                8K |
| Galaxy Tab S9         |                7K |
| Galaxy Tab S9 Ultra   |                7K |

The screenshot shows the product ranking and approximate values. 

### Business interpretation

The chart immediately identifies products with the highest inventory exposure.

For example, **Galaxy S24 Ultra** appears to have the highest inventory among the displayed products.

High inventory may indicate:

* Strong expected demand
* Overstocking
* Slow-moving inventory
* Production exceeding current sales
* Safety-stock requirements

Inventory should therefore be analyzed together with sales velocity.

---

# 39. Zone 7 — Sales & Profit Trend

### Visual:

**Total Sales & Profit By Time**

This is one of the most important analytical visuals in the dashboard.

It tracks:

* Net revenue
* Profit
* Time

The chart covers a period beginning around **January 2023** and extending into **2024**, based on the visible x-axis. 

---

# 40. Sales Trend Analysis

The chart shows revenue fluctuating over time.

There are visible periods of:

* Gradual growth
* Decline
* Recovery
* Significant spikes

A particularly strong spike appears around **October 2023**, with revenue reaching roughly the 10M+ range in the visual.

Another major spike appears around **October 2024**. 

### Business interpretation

This suggests the business may experience:

* Seasonal demand
* Product launches
* Promotional campaigns
* Holiday-driven sales
* Periodic demand spikes

The exact reason cannot be established from the screenshot alone and should be investigated using product, customer and date-level data.

---

# 41. January 2024 Dip

The trend appears to show a noticeable decline around **January 2024**.

This could potentially indicate:

* Post-holiday demand normalization
* Seasonal demand decline
* Inventory constraints
* Reduced promotional activity

Again, this is a hypothesis rather than a proven cause.

A good analyst should investigate rather than immediately claim causation.

---

# 42. Revenue vs Profit Analysis

The dashboard simultaneously compares:

```text
Revenue
vs
Profit
```

This is useful because revenue growth does not automatically mean profitability growth.

For example:

```text
Revenue ↑
Profit ↑
→ Healthy growth

Revenue ↑
Profit ↓
→ Cost/margin problem

Revenue ↓
Profit ↑
→ Potential cost optimization

Revenue ↓
Profit ↓
→ Business performance concern
```

This is one of the most valuable analytical concepts demonstrated by the dashboard.

---

# 43. Achievement Gauge

The dashboard includes an **Achievement** gauge displaying approximately:

**176.95M**

This appears to represent a revenue achievement/target-oriented metric. 

A gauge like this is useful for answering:

> How close are we to the business target?

For an even stronger implementation, the gauge should clearly show:

```text
Actual
Target
Achievement %
Variance
```

For example:

```text
Actual Revenue       $176.95M
Target Revenue       $200M
Achievement          88.48%
Remaining            $23.05M
```

---

# 44. Product Selection

The left-side product selector provides interactive product filtering.

Users can select individual products such as:

* Smart Front Load Washer
* OLED 65" 4K
* Neo QLED 85" 4K
* Galaxy Z Fold5
* Galaxy Z Flip5
* Galaxy Watch6 Classic
* Galaxy Tab S9 Ultra
* Galaxy Tab S9

The selected product can then be used to analyze the dashboard from a product-specific perspective. 

---

# 45. End-to-End Business Flow

The dashboard can be explained using this supply-chain lifecycle:

```text
SUPPLIER
   ↓
PROCUREMENT
   ↓
MANUFACTURING
   ↓
INVENTORY
   ↓
SALES / ORDER
   ↓
SHIPMENT
   ↓
DELIVERY
   ↓
CUSTOMER
```

Each stage produces analytical questions.

### Supplier

How long does procurement take?

↓

### Procurement

How much are we purchasing?

↓

### Manufacturing

How much are we producing?

↓

### Inventory

How much stock do we have?

↓

### Sales

How much are we selling?

↓

### Shipment

How efficiently are products shipped?

↓

### Delivery

How many orders are delayed?

↓

### Customer

Are customers receiving complete and timely orders?

This is the core story behind the dashboard.

---

# 46. Key Business Insights From the Current Dashboard

Based strictly on what is visible in the dashboard:

### Insight 1 — Strong Revenue Scale

The dashboard indicates approximately **176.95M** in revenue/achievement context. 

This suggests the business is operating at a significant sales scale.

---

### Insight 2 — Profitability Is Positive

The dashboard reports a **27.44% profit margin**. 

This indicates a meaningful portion of revenue is retained as profit under the dashboard's definition.

---

### Insight 3 — Perfect Order Performance Needs Improvement

The Perfect Order KPI is approximately:

**75.29%**



That means around one-quarter of orders are not meeting the project's perfect-order criteria.

This is an important operational improvement opportunity.

---

### Insight 4 — Delayed Orders Are Significant

Approximately:

**573 delayed orders**

are displayed. 

This should be investigated alongside:

* Supplier lead time
* Inventory availability
* Shipment performance
* Facility
* Product
* Customer location

---

### Insight 5 — Inventory Is Concentrated in Specific Products

Galaxy S24 Ultra appears to have the highest displayed inventory, followed by Galaxy Buds2 Pro and Galaxy Watch6 Classic. 

These products should be analyzed against sales velocity to determine whether inventory is healthy or excessive.

---

### Insight 6 — Supplier Lead Times Are Relatively Close

The supplier chart shows displayed values clustered roughly around 3.0K–3.9K. 

This indicates relatively limited variation between the displayed suppliers, although the unit/measure calculation needs validation.

---

### Insight 7 — Sales Are Highly Variable Over Time

The time-series chart contains substantial peaks and troughs, including strong spikes around October periods and a visible decline around January 2024. 

This suggests potential seasonality or event-driven demand.

---

### Insight 8 — Shipping Cost Is an Important Cost Driver

The dashboard reports approximately:

**19.42M Total Shipping Cost**



This is significant enough to justify deeper logistics-cost analysis.

A useful next metric would be:

```text
Shipping Cost % of Revenue
```

---

# 47. Important KPI Relationships

The real power of the dashboard comes from connecting the KPIs.

## Revenue vs Profit

```text
Revenue
   ↓
Sales Cost
   ↓
Profit
   ↓
Profit Margin
```

---

## Inventory vs Sales

```text
Inventory Stock
       ↓
Sales Quantity
       ↓
Inventory Turnover
```

This determines whether inventory is efficiently utilized.

---

## Lead Time vs Inventory

```text
Supplier Lead Time ↑
        ↓
Safety Stock Requirement ↑
        ↓
Inventory ↑
```

Longer lead times can force companies to maintain more safety stock.

---

## Shipment vs Delivery

```text
Shipment Quantity
       ↓
Delivered Quantity
       ↓
Delayed Orders
       ↓
Perfect Order %
```

This creates the logistics performance chain.

---

# 48. Recommended Advanced KPIs

To make this dashboard even stronger from a data-analyst portfolio perspective, I would add the following.

## 48.1 Inventory Turnover

```text
Inventory Turnover =
Cost of Goods Sold / Average Inventory
```

Useful for identifying slow-moving inventory.

---

## 48.2 Inventory Days

```text
Inventory Days =
Average Inventory / COGS × 365
```

Answers:

> How many days of inventory are we carrying?

---

# 49. 48.3 On-Time Delivery %

```text
On-Time Delivery % =
On-Time Orders / Total Orders
```

This should be displayed next to Perfect Order.

---

# 50. 48.4 Delay Rate

```text
Delay Rate =
Delayed Orders / Total Orders
```

This gives management a normalized view of delays.

---

# 51. 48.5 Defect Rate

```text
Defect Rate =
Defective Units / Production Units
```

This connects manufacturing quality to supply-chain performance.

---

# 52. 48.6 Shipping Cost per Unit

```text
Shipping Cost per Unit =
Total Shipping Cost / Total Shipment Quantity
```

This is especially useful for logistics cost optimization.

---

# 53. 48.7 Revenue per Unit

```text
Revenue per Unit =
Total Revenue / Total Sales Quantity
```

This can identify changes in product mix and average selling price.

---

# 54. 48.8 Profit per Unit

```text
Profit per Unit =
Profit / Total Sales Quantity
```

Useful for product profitability analysis.

---

# 55. 48.9 Inventory Coverage

```text
Inventory Coverage =
Current Inventory / Average Daily Sales
```

This helps determine how long current inventory can support demand.

---

# 56. Recommended Dashboard Improvements

The current dashboard is visually strong, but there are several analytical improvements I would recommend.

## Improvement 1 — Fix KPI formatting

Some KPI values are truncated:

```text
$176946...
$485595...
```

For executive dashboards, use:

```text
$176.95M
$48.56M
```

instead.

---

# 57. Improvement 2 — Show Units

Instead of:

```text
Average Lead Time
```

use:

```text
Average Lead Time (Days)
```

or:

```text
Average Lead Time (Hours)
```

depending on the actual data.

Similarly:

```text
Inventory Stock (Units)
Shipment Quantity (Units)
Shipping Cost ($)
```

Clear units make the dashboard much more professional.

---

# 58. Improvement 3 — Validate Average Lead Time

This is probably the **most important technical validation** I would perform.

Values such as:

```text
3.9K
3.8K
3.1K
3.0K
```

need to be checked.

If the underlying value is, for example:

```text
3,900 minutes
```

then convert it into:

```text
65 hours
```

or:

```text
2.7 days
```

depending on business meaning.

An interviewer may immediately ask:

> "Why is supplier lead time 3,900?"

So definitely validate this before publishing the project.

---

# 59. Improvement 4 — Add Target vs Actual

Instead of only showing Achievement, create:

```text
Actual Revenue
Revenue Target
Achievement %
Variance
```

This makes the gauge much more useful.

---

# 60. Improvement 5 — Add Conditional Formatting

Use business logic:

### Green

Good performance

### Yellow

Needs attention

### Red

Poor performance

For example:

```text
Perfect Order > 95%      → Good
90–95%                    → Warning
<90%                      → Critical
```

The actual thresholds should be based on the business requirement rather than arbitrary values.

---

# 61. Improvement 6 — Add Drill-through

Create drill-through pages for:

### Product

Product → Sales → Inventory → Profit

### Supplier

Supplier → Lead Time → Procurement → Delays

### Customer

Customer → Orders → Revenue → Delivery

### Facility

Facility → Production → Inventory → Shipment

This would turn the dashboard from a static overview into a more complete analytical application.

---

# 62. Improvement 7 — Add Tooltip Pages

Create custom tooltip pages for:

### Product

```text
Revenue
Profit
Margin
Inventory
Sales Quantity
Shipment Quantity
```

### Supplier

```text
Lead Time
Procurement Quantity
Shipment Delay
Supplier Performance
```

This allows users to get more information without overcrowding the main page.

---

# 63. Improvement 8 — Add a Supply Chain Funnel

A powerful additional visual could show:

```text
Order Quantity
       ↓
Shipment Quantity
       ↓
Delivered Quantity
       ↓
Perfect Orders
```

This would make the supply-chain conversion process much easier to understand.

---

# 64. Suggested Additional Dashboard Pages

If you want to turn this into a complete professional Power BI project, I would structure it into **5 pages**.

## Page 1 — Executive Overview

Already largely implemented.

KPIs:

* Revenue
* Profit
* Profit Margin
* Orders
* Shipments
* Delayed Orders
* Perfect Order
* Inventory

---

# 65. Page 2 — Sales & Profit Analysis

Visuals:

* Revenue by month
* Profit by month
* Profit margin trend
* Revenue by product
* Profit by product
* Revenue by country
* Top 10 products
* Bottom 10 products

---

# 66. Page 3 — Inventory & Production

Visuals:

* Inventory stock
* Safety stock
* Inventory by product
* Inventory by facility
* Production quantity
* Defective units
* Defect rate
* Inventory turnover

---

# 67. Page 4 — Supplier & Procurement

Visuals:

* Average lead time by supplier
* Procurement quantity
* Procurement cost
* Supplier ranking
* Lead-time distribution
* Supplier performance matrix

---

# 68. Page 5 — Shipment & Logistics

Visuals:

* Total shipments
* Shipment quantity
* Delivered quantity
* Delayed orders
* Perfect order %
* Shipping cost
* Shipping cost per unit
* On-time delivery %

This would create a complete **end-to-end supply-chain analytics solution**.

---

# 69. Analytical Questions This Dashboard Can Answer

This is a very important section for interviews.

The project can answer questions such as:

### Financial

1. What is total revenue?
2. What is total profit?
3. What is the profit margin?
4. How does profit change over time?
5. Which products generate the most revenue?
6. Which products are most profitable?

### Inventory

7. How much inventory is currently available?
8. Which products have the highest inventory?
9. Are inventory levels above safety stock?
10. Which products may be overstocked?

### Supplier

11. Which suppliers have the longest lead time?
12. Which suppliers perform best?
13. Where are procurement bottlenecks occurring?

### Logistics

14. How many shipments are being processed?
15. How many orders are delayed?
16. How much quantity has been delivered?
17. How much is being spent on shipping?
18. What percentage of orders are perfect orders?

### Geographic

19. How does the USA perform compared with Poland and India?
20. Which region generates the most revenue?
21. Which region has the highest shipment cost?
22. Which region has the highest delay rate?

---

# 70. Example Business Scenario

Suppose management sees:

```text
Inventory        = 160K
Delayed Orders   = 573
Perfect Order    = 75.29%
Shipping Cost    = 19.42M
Profit Margin    = 27.44%
```

The analyst should not simply report the numbers.

The next question should be:

> **Why are perfect orders only 75.29%?**

Then investigate:

```text
Delayed Orders
      ↓
Shipment
      ↓
Inventory Availability
      ↓
Supplier Lead Time
      ↓
Facility
      ↓
Product
```

This is the difference between **reporting** and **analytics**.

---

# 71. Analytical Story of the Dashboard

The dashboard tells the following story:

### Step 1 — Financial Health

The company is generating substantial revenue and maintaining a positive profit margin.

↓

### Step 2 — Operational Scale

The company is handling thousands of shipments and large quantities of products.

↓

### Step 3 — Inventory

A significant amount of stock is held across products.

↓

### Step 4 — Supplier Performance

Supplier lead time varies across suppliers and needs monitoring.

↓

### Step 5 — Logistics

Hundreds of delayed orders indicate fulfillment challenges.

↓

### Step 6 — Customer Experience

The perfect-order percentage of 75.29% suggests opportunities to improve order fulfillment.

↓

### Step 7 — Optimization

The company should optimize:

* Inventory
* Supplier lead time
* Shipping cost
* Delivery reliability
* Order fulfillment

---

# 72. Data Analyst Approach Used in the Project

A strong interview explanation would be:

> "I approached the project from an end-to-end supply-chain perspective. I structured the data into dimension and fact tables, created reusable DAX measures for financial, inventory, procurement and shipment KPIs, and then designed an executive overview dashboard. I focused on connecting revenue and profitability with operational KPIs such as inventory, supplier lead time, delayed orders and perfect-order performance."

That's a much stronger explanation than simply saying:

> "I created a Power BI dashboard."

---

# 73. Project Workflow

The end-to-end development process can be documented as:

```text
Raw Data
   ↓
Data Understanding
   ↓
Data Cleaning
   ↓
Data Transformation
   ↓
Data Modeling
   ↓
Relationship Creation
   ↓
DAX Measures
   ↓
KPI Development
   ↓
Visual Design
   ↓
Interactive Filters
   ↓
Business Analysis
   ↓
Dashboard Validation
   ↓
Final Insights
```

---

# 74. Data Cleaning & Transformation

Before creating the dashboard, typical data-quality checks should include:

### Missing values

Identify:

* Missing product
* Missing supplier
* Missing customer
* Missing dates
* Missing quantities

### Duplicate records

Check transaction IDs for duplicates.

### Data types

Ensure:

```text
Date → Date
Quantity → Whole Number
Revenue → Decimal/Currency
Cost → Decimal/Currency
Lead Time → Numeric
Rating → Decimal
```

### Outliers

Investigate:

* Extremely high shipment quantity
* Negative revenue
* Negative inventory
* Abnormally large lead time
* Extremely high shipping cost

---

# 75. Data Validation

Before publishing, validate:

### Revenue

```text
Power BI Revenue
=
Source Revenue
```

### Shipment

```text
Power BI Shipment Count
=
Source Shipment Count
```

### Inventory

```text
Power BI Inventory
=
Source Inventory
```

### Profit

```text
Revenue - Cost
=
Profit
```

### Profit Margin

```text
Profit / Revenue
=
Profit Margin
```

This is extremely important for a professional analytics project.

---

# 76. Dashboard Design Principles

The dashboard uses several good visualization practices:

### KPI cards

Used for high-level metrics.

### Bar chart

Used for supplier and product comparison.

### Line/area chart

Used for time-series analysis.

### Gauge

Used for achievement/target tracking.

### Slicers

Used for product and geographic filtering.

### Navigation cards

Used to visually communicate the supply-chain journey.

The dashboard therefore combines **descriptive analytics + interactive exploration**.

---

# 77. Descriptive Analytics

The current dashboard is primarily a **descriptive analytics** solution.

It answers:

> What happened?

Examples:

* Revenue was X.
* Profit margin was 27.44%.
* There were 573 delayed orders.
* Inventory was around 160K.
* Perfect-order performance was 75.29%.

---

# 78. Diagnostic Analytics — Next Level

The next analytical layer should answer:

> Why did it happen?

For example:

```text
Why did delayed orders increase?

→ Which supplier?
→ Which product?
→ Which facility?
→ Which country?
→ Which month?
→ Was inventory below safety stock?
```

This is where the project can become significantly stronger.

---

# 79. Predictive Analytics — Future Enhancement

A future version could answer:

> What is likely to happen?

Examples:

* Forecast monthly demand
* Predict inventory shortages
* Forecast shipment volume
* Predict delayed orders
* Forecast revenue
* Identify products at stockout risk

Power BI could be combined with Python or machine-learning workflows for this.

---

# 80. Prescriptive Analytics — Advanced Enhancement

The final level would answer:

> What should the business do?

For example:

```text
Supplier A has high lead time
+
Product X has high demand
+
Inventory is below safety stock

→ Increase safety stock
→ Expedite procurement
→ Evaluate alternative supplier
```

This turns the dashboard into a decision-support system.

---

# 81. Potential Data Quality Issues to Validate

From the screenshots alone, I would specifically check these areas before final submission:

### 1. Lead Time

The **3K–4K** displayed values need unit validation. 

### 2. Delivered Quantity

The displayed **187K** should be reconciled against shipment quantity of approximately **3M**. 

### 3. Revenue/Profit Formatting

Some KPI cards are truncated and should be formatted in M/K notation.

### 4. Achievement

Clearly define whether **176.95M** is:

* Actual revenue
* Target
* Achievement
* Revenue in selected context

### 5. Perfect Order Definition

Document exactly what qualifies as a perfect order.

---

# 82. Recommended Final KPI Panel

For a polished final version, I'd use:

| KPI                  | Purpose                     |
| -------------------- | --------------------------- |
| Total Revenue        | Financial performance       |
| Total Profit         | Absolute profitability      |
| Profit Margin        | Relative profitability      |
| Sales Quantity       | Demand volume               |
| Inventory            | Stock availability          |
| Safety Stock         | Risk buffer                 |
| Total Shipments      | Logistics activity          |
| On-Time Delivery %   | Delivery reliability        |
| Delayed Orders       | Logistics problems          |
| Perfect Order %      | Overall fulfillment quality |
| Shipping Cost        | Logistics expense           |
| Shipping Cost / Unit | Logistics efficiency        |
| Defect Rate          | Manufacturing quality       |

---

# 83. Recommended Color/UX Logic

The current design uses a Samsung-inspired visual identity with dark/neutral elements and blue accents. 

For consistency:

```text
Blue       → Primary metrics
Green      → Positive performance
Red        → Problems/delays
Orange     → Warning
Grey       → Supporting information
```

Keep the dashboard relatively clean and avoid too many colors.

---

# 84. Project Outcome

The dashboard transforms multiple supply-chain datasets into a centralized business intelligence solution.

It enables stakeholders to monitor:

```text
Financial Performance
        +
Sales
        +
Inventory
        +
Procurement
        +
Production
        +
Shipment
        +
Delivery
        +
Supplier Performance
        +
Customer Fulfillment
```

The result is a **single analytical view of the complete supply-chain ecosystem**.

---

# 85. Resume Project Description

You can describe the project on your resume like this:

> **Samsung Supply Chain & Logistics Analytics Dashboard | Power BI**
> Developed an interactive Power BI dashboard to analyze end-to-end supply-chain performance across sales, procurement, production, inventory and shipment operations. Built a multi-fact data model with customer, date, facility, product and supplier dimensions and created DAX measures for revenue, profit, profit margin, inventory, shipment, delayed orders, delivered quantity, shipping cost, lead time and perfect-order performance. Implemented interactive product and country-level analysis and time-series visualizations to identify inventory concentration, supplier lead-time variation, logistics delays and profitability trends.

---

# 86. Interview Explanation — 60 Seconds

If an interviewer asks:

### "Tell me about your project."

You can say:

> "I created a Samsung Supply Chain and Logistics Analytics Dashboard in Power BI. The objective was to provide an end-to-end view of the supply chain, from suppliers and procurement to production, inventory, sales, shipment and customer delivery. I worked with multiple fact tables such as sales, procurement, production, inventory and shipment, supported by dimensions including product, supplier, customer, facility and date. I created DAX measures for revenue, profit, profit margin, inventory stock, shipment quantity, delayed orders, shipping cost, lead time and perfect-order performance. The dashboard allows users to analyze performance by product, country, supplier and time. Some of the key findings were a 27.44% profit margin, around 573 delayed orders and a 75.29% perfect-order rate, highlighting opportunities in logistics and fulfillment optimization."

That is a **very interview-friendly explanation**.

---

# 87. Strong Interview Questions You Should Prepare

Because this project uses Power BI + DAX + data modeling, prepare for:

### Power BI

* Why did you use Power BI?
* How did you design the data model?
* Why use fact and dimension tables?
* What is a star schema?
* What relationships did you create?
* What is filter propagation?
* Why did you create a separate DAX measure table?

### DAX

* Difference between measure and calculated column?
* How did you calculate Profit?
* How did you calculate Profit Margin?
* Why use `DIVIDE()`?
* How did you calculate delayed orders?
* How did you calculate Perfect Order?
* What is filter context?
* What is row context?
* How would country selection affect the measures?

### Data Analysis

* Why is inventory important?
* What does perfect order mean?
* How can you reduce delayed orders?
* How can you optimize supplier lead time?
* How would you identify slow-moving products?
* How would you investigate high shipping costs?

---

# 88. Most Important Business Recommendations

Based on the current dashboard, the strongest recommendations would be:

### 1. Improve Perfect Order Performance

Current displayed performance:

**75.29%**

Investigate the causes of imperfect orders and separate them into:

* Late
* Incomplete
* Damaged
* Incorrect

---

### 2. Investigate Delayed Orders

There are approximately:

**573 delayed orders**

Break these down by:

```text
Supplier
Product
Facility
Country
Month
Customer
```

---

### 3. Optimize High-Inventory Products

Products such as Galaxy S24 Ultra and Galaxy Buds2 Pro show relatively high inventory in the displayed ranking. 

Compare their:

```text
Inventory
vs
Sales Velocity
```

before increasing production.

---

### 4. Investigate Shipping Costs

With approximately **19.42M** in total shipping cost, calculate:

```text
Shipping Cost / Shipment
Shipping Cost / Unit
Shipping Cost / Revenue
```

Then identify high-cost routes/facilities/products.

---

### 5. Investigate Supplier Lead Time

Rank suppliers by:

```text
Lead Time
+
Procurement Volume
+
Delay Rate
```

A supplier with both **high volume + high lead time** should receive priority attention.

---

# 89. Final Project Architecture

Your complete project can be represented as:

```text
                  SAMSUNG SUPPLY CHAIN
                         │
        ┌────────────────┼────────────────┐
        │                │                │
     SUPPLIER        MANUFACTURER      CUSTOMER
        │                │                │
   Procurement       Production          Sales
        │                │                │
        └──────────── Inventory ──────────┘
                         │
                      Shipment
                         │
                      Delivery
                         │
                  Business KPIs
                         │
        ┌────────────────┼────────────────┐
        │                │                │
     Financial       Operations       Logistics
        │                │                │
 Revenue/Profit     Inventory        Shipment
 Profit Margin      Lead Time        Delivery
 Sales Cost         Safety Stock     Delays
                    Defects          Shipping Cost
                    Products         Perfect Order
```

---

# 90. Final Summary

This Power BI project demonstrates an **end-to-end supply-chain analytics approach**, rather than just a collection of charts.

The dashboard connects:

**Supplier → Procurement → Production → Inventory → Sales → Shipment → Delivery → Customer**

and converts these processes into measurable KPIs.

The most important performance indicators currently highlighted are approximately:

* **Revenue:** 176.95M context
* **Profit Margin:** 27.44%
* **Total Sales Cost:** 78.13M
* **Inventory Stock:** 160K
* **Shipment Quantity:** 3M
* **Delivered Quantity:** 187K
* **Order Quantity:** 129K
* **Delayed Orders:** 573
* **Perfect Order:** 75.29%
* **Shipping Cost:** 19.42M

These figures and dashboard elements are visible in the supplied dashboard screenshot. 

The project demonstrates skills in:

**Power BI + Data Modeling + DAX + KPI Design + Supply Chain Analytics + Business Intelligence + Data Visualization + Interactive Dashboard Development.**
