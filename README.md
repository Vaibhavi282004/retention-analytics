# Customer Retention & Repeat-Order Analytics

**Business question:** Which customers and products drive repeat orders, where do we lose customers, and which segment should the business focus on first?

**Data:** Instacart Online Grocery Shopping Dataset (Kaggle), about 3.4M orders and 32M order-product rows across 6 tables. Check the Kaggle usage terms; this is a portfolio project only.
Put the CSVs in `data/`: orders, order_products__prior, order_products__train, products, aisles, departments.

## Run order
1. `python python/01_load_validate.py`  loads CSVs into SQLite and runs validation checks
2. `sqlite3 retention.db < sql/02_analysis.sql`  or run each query in DB Browser for SQLite and export results
3. `python python/03_segments.py`  builds customer segments, writes `outputs/segment_summary.csv` and a `customer_segments` table in the database
4. `sqlite3 retention.db < sql/03_advanced.sql`  window-function queries (NTILE, ROW_NUMBER, share per segment); needs step 3 first
5. `python python/04_build_dashboard.py`  writes `outputs/dashboard.html`. Double-click it to open the dashboard in a browser. On the full data this takes a few minutes.
6. Open Excel, import `vba/WeeklySummary.bas`, run `BuildSegmentSummary`
7. Optional: rebuild the same pages in Power BI or Tableau Public from `outputs/*.csv` (layout below)

Install once: `pip install pandas numpy`. The dashboard itself needs nothing but a browser (fonts load from Google Fonts when online).

## Definitions (write your own numbers next to each)
- **Reorder rate:** items with reordered = 1 divided by all items, on prior orders.
- **Days between orders:** days_since_prior_order. A value of 30 means 30 or more (the data is capped).
- **Light customer:** 5 orders or fewer. (Every user in this dataset has at least 3 prior orders, so true one-time customers do not exist here.)
- **Segments (rules in order):** Champions = 30+ orders and average gap of 10 days or less; At-risk = average gap of 20 days or more; Light = 5 orders or fewer; Loyal = 15+ orders; Regular = everyone else.

## Dashboard (outputs/dashboard.html)
Six tabs, one file, no server:
- **Overview:** KPI strip, customers still ordering by order number (grouped by usual gap), days-between-orders distribution, reorder rate by department
- **Segments:** summary table with a suggested action per segment, customer share, orders per customer
- **Products:** products with the highest reorder rate (filterable by department), basket size by order number
- **Timing:** orders by weekday and hour heatmap
- **What-if:** move a share of customers from one segment to another and see the estimated change in orders, with the assumptions shown
- **Data and method:** definitions, limits and the data checks
Filters at the top: customer segment and department. Every chart has a "Show table" button.
The dashboard shows a yellow warning when it was built from the fake test data.

Why the retention chart is grouped by gap and not by segment: Light, Regular and so on are defined by how many orders a customer has, so a curve per segment would fall to zero by construction. Gap bands do not have that problem.

## Dashboard layout for Power BI / Tableau (optional rebuild)
- Filter: segment, department
- KPI cards: reorder rate, average days between orders, orders per customer, % light customers
- Charts: reorder rate by department, customers still ordering by order number, days-between-orders distribution, customers by segment
- Table: segment summary with suggested action

## Assumptions and limits
- No calendar dates in the data, so recency is approximated by the gap between orders.
- Segment cut-offs are rules I chose; I tested alternatives by changing them and checking the shares.
- Findings are correlations, not proof that an action will lift orders.

## Findings (fill in after running)
1. ...
2. ...
3. ...
Recommendation memo: `outputs/memo.md` (3 findings, 3 recommendations, one what-if estimate)

## Testing the pipeline before you download the real data
`python python/00_make_test_data.py` creates a small fake dataset in the same file format.
Steps 1, 3, 4 and 5 were run on it: the 5 validation checks ran, the 4 advanced queries returned rows, the segment script wrote its CSVs and the dashboard built and rendered with no script errors.
Delete the fake CSVs in `data/` and `retention.db` before loading the real Instacart files.
Numbers from the fake data are meaningless and must not appear on your resume.
