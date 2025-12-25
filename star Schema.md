# Star Schema Diagram

```mermaid
flowchart LR
    DIM_DATE[Dim Date<br/>date_key, full_date, month, quarter, year]
    DIM_CUSTOMER[Dim Customer<br/>customer_key, name, segment, region]
    DIM_PRODUCT[Dim Product<br/>product_key, sku, category, brand]
    DIM_CHANNEL[Dim Channel<br/>channel_key, channel_name, type]
    DIM_REGION[Dim Region<br/>region_key, country, state, city]

    FACT_SALES_LINE[Fact Sales Line<br/>date_key, customer_key, product_key, channel_key, region_key<br/>quantity_sold, gross_revenue, discount, margin]

    DIM_DATE --> FACT_SALES_LINE
    DIM_CUSTOMER --> FACT_SALES_LINE
    DIM_PRODUCT --> FACT_SALES_LINE
    DIM_CHANNEL --> FACT_SALES_LINE
    DIM_REGION --> FACT_SALES_LINE
