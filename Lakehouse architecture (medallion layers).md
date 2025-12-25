# Modern Data Architecture Pipeline

This diagram shows sources, ingestion, storage layers, governance, and compute engines.

```mermaid
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
