Tagline: 
From grain clarity to conformed dimensions, Section 1.2 gives you the blueprint to architect analytics that scale, govern history, and speak the language of business.

Section 1.2 distills Kimball’s dimensional modeling into a practical playbook for analytics excellence. 
We’ll learn to design star schemas that simplify complexity, choose the right SCD strategy to balance agility with history, define fact table grain for precision, and build conformed dimensions that unify every domain.

This section equips us with clear analogies, step‑by‑step architectures, and interview‑ready summaries, making it both a curriculum artifact and a career accelerator.

Dimensional modeling is more than design—it’s the language of business intelligence. 
Mastering it means turning raw data into trusted dashboards, consistent metrics, and scalable analytics. 
Section 1.2 positions us as a "DATA STORY TELLER", shaping insights that resonate across the enterprise.

flowchart LR
    %% Dimensions
    DIM_DATE[Dim Date<br/>date_key, full_date, month, quarter, year]
    DIM_CUSTOMER[Dim Customer<br/>customer_key, name, segment, region]
    DIM_PRODUCT[Dim Product<br/>product_key, sku, category, brand]
    DIM_CHANNEL[Dim Channel<br/>channel_key, channel_name, type]
    DIM_REGION[Dim Region<br/>region_key, country, state, city]

    %% Fact
    FACT_SALES_LINE[Fact Sales Line<br/>date_key, customer_key, product_key, channel_key, region_key<br/>quantity_sold, gross_revenue, discount, margin]

    %% Relationships
    DIM_DATE --> FACT_SALES_LINE
    DIM_CUSTOMER --> FACT_SALES_LINE
    DIM_PRODUCT --> FACT_SALES_LINE
    DIM_CHANNEL --> FACT_SALES_LINE
    DIM_REGION --> FACT_SALES_LINE


    flowchart LR
    subgraph Sources
      A1[Operational DBs]
      A2[Files (CSV/JSON/Parquet)]
      A3[Streaming (Kafka/Kinesis)]
      A4[SaaS APIs]
    end

    subgraph Ingestion
      B1[Batch ETL/ELT]
      B2[Stream Ingest]
    end

    subgraph Storage
      C1[Raw (Bronze)<br/>as-is, append-only]
      C2[Refined (Silver)<br/>cleaned, standardized]
      C3[Curated (Gold)<br/>business models]
    end

    subgraph Governance
      D1[Catalog/Lineage]
      D2[Access & Policies]
      D3[Quality & SLAs]
    end

    subgraph Compute
      E1[Spark/SQL Engines]
      E2[ML/DS]
      E3[BI/Ad Hoc]
    end

    %% Flows
    A1 --> B1
    A2 --> B1
    A3 --> B2
    A4 --> B1

    B1 --> C1
    B2 --> C1
    C1 --> C2
    C2 --> C3

    D1 --- C1
    D1 --- C2
    D1 --- C3
    D2 --- C1
    D2 --- C2
    D2 --- C3
    D3 --- C2
    D3 --- C3

    C3 --> E3
    C2 --> E1
    C2 --> E2

