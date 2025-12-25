# Modern Data Architecture Pipeline

```mermaid
flowchart LR
    subgraph Sources
      A1[Operational DBs]
      A2[Files<br/>CSV<br/>JSON<br/>Parquet]
      A3[Streaming<br/>Kafka<br/>Kinesis]
      A4[SaaS APIs]
    end

    subgraph Ingestion
      B1[Batch ETL and ELT]
      B2[Stream Ingest]
    end

    subgraph Storage
      C1[Raw Bronze<br/>as-is<br/>append-only]
      C2[Refined Silver<br/>cleaned<br/>standardized]
      C3[Curated Gold<br/>business models]
    end

    subgraph Governance
      D1[Catalog and Lineage]
      D2[Access and Policies]
      D3[Quality and SLAs]
    end

    subgraph Compute
      E1[Spark and SQL Engines]
      E2[Machine Learning and Data Science]
      E3[BI and Ad Hoc]
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
