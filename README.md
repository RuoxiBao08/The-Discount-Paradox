# The Discount Paradox
 **App Link**: [https://the-discount-paradox-bd94lbeirdn43xzj2tav6e.streamlit.app/]

## Dataset and Decision Maker 

-**Data Source:** Amazon India product snapshot from Kaggle (January 2023). Each row is a single product with price, discount, rating, and category. It contains real scraped data, not transactional sales records.
- **Target Role:** E-commerce category manager.
- **Decision Statement:** If the manager sees deeply discounted products (discount >= 60%) with an average rating below 3.8 and sufficient review evidence, they will investigate the product quality, listing accuracy, and pricing strategies.

## Dashboard Justification 

A dashboard is necessary because the category manager needs to review the same questions weekly. 
Without it, the manager must manually filter thousands of rows in Excel, which is time-consuming and risks missing high-volume, low-rating products that could damage brand reputation. Unlike a static weekly email, this dashboard allows interactive filtering by category and evidence threshold, directly supporting the manager's investigation workflow.

## Design Decisions

- **Headline KPIs:** Products in selection, average current price, and average customer rating.
- **Supporting Charts:** A bubble chart to test if bigger discounts equal happier customers, and a bar chart to identify categories with the most questionable deep deals.
- **Filters and Table:** A category filter and a minimum rating count filter. A product table serves as the investigation queue.
  - **Two Deliberate Omissions:** Revenue/sales KPIs are absent because no sales transactions exist in the data. Time trends are omitted because there are no reliable observation dates.
- **Interpretation Limits:** Advertised discounts rely on listed reference prices, which may not reflect real savings. Rating counts do not equal sales or unique buyers, and a snapshot correlation does not prove that discounts caused customer dissatisfaction.

## Refresh Frequency and Deployment

- **Production Refresh:** The production proposal is to refresh the data nightly from the catalog and reviews system. 
- **Review Frequency:** The category manager reviews the dashboard weekly on Monday. 
- **Action Trigger:** Investigate newly qualifying listings when they exceed the selected evidence minimum. 
- **No Real-time Refresh:** Real-time refresh is unnecessary because pricing and quality reviews are weekly decisions, and it would add significant data pipeline costs without changing any actions. 
- **Data Period:** January 2023 Kaggle snapshot.
