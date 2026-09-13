# 🚀 End-to-End Azure Data Engineering Project

## 📌 Project Overview

This project demonstrates an end-to-end **Azure Data Engineering pipeline** for a retail business using multiple data sources.

The solution implements a modern cloud data platform using **Azure Data Factory (ADF), Azure Data Lake Storage Gen2 (ADLS Gen2), Azure Databricks, Azure SQL Database, and Power BI**.

The pipeline follows the **Medallion Architecture (Bronze → Silver → Gold)** to ingest, process, transform, validate, and serve data for analytics and business intelligence.

---

## 🏢 Business Requirements

The retail business requires an automated data platform capable of:

- Building an end-to-end data pipeline for retail data
- Ingesting data from multiple sources
- Loading raw data into a centralized Azure Data Lake
- Processing and transforming data using Databricks
- Implementing Bronze, Silver, and Gold data layers
- Performing data quality and validation checks
- Creating business-ready datasets
- Loading curated data into Azure SQL Database
- Connecting the final data to Power BI for reporting and analytics

---
DATA FLOW

Multiple Sources
      ↓
Azure Data Factory
      ↓
Azure Data Lake Storage Gen2
      ↓
Azure Databricks
      ↓
Bronze Layer
      ↓
Silver Layer
      ↓
Gold Layer
      ↓
Azure SQL Database
      ↓
Power BI

# 🏗️ Solution Architecture

```text
                    ┌─────────────────────────┐
                    │       DATA SOURCES      │
                    └────────────┬────────────┘
                                 │
             ┌───────────────────┼───────────────────┐
             │                   │                   │
             ▼                   ▼                   ▼
      ┌─────────────┐     ┌─────────────┐     ┌──────────────┐
      │ Azure SQL   │     │ Azure SQL   │     │ API / JSON  │
      │ Transaction │     │ Store       │     │ Customer     │
      └──────┬──────┘     └──────┬──────┘     └──────┬───────┘
             │                   │                   │
             └───────────────────┼───────────────────┘
                                 │
                                 ▼
                    ┌─────────────────────────┐
                    │   Azure Data Factory    │
                    │          (ADF)          │
                    │                         │
                    │  Data Ingestion / ETL   │
                    └────────────┬────────────┘
                                 │
                                 ▼
                    ┌─────────────────────────┐
                    │ Azure Data Lake Storage │
                    │         Gen2            │
                    │                         │
                    │       Raw Data          │
                    └────────────┬────────────┘
                                 │
                                 ▼
              ┌─────────────────────────────────────┐
              │          AZURE DATABRICKS            │
              │                                     │
              │       MEDALLION ARCHITECTURE        │
              │                                     │
              │  ┌─────────┐  ┌─────────┐  ┌──────┐│
              │  │ BRONZE  │→ │ SILVER  │→ │ GOLD ││
              │  │  RAW    │  │ CLEANED │  │BUSINESS│
              │  │  DATA   │  │  DATA   │  │ DATA ││
              │  └─────────┘  └─────────┘  └──────┘│
              └──────────────────┬──────────────────┘
                                 │
                                 ▼
                    ┌─────────────────────────┐
                    │     Azure SQL Database  │
                    │                         │
                    │  Curated / Serving Data │
                    └────────────┬────────────┘
                                 │
                                 ▼
                    ┌─────────────────────────┐
                    │        Power BI         │
                    │                         │
                    │ Dashboards & Analytics  │
                    └─────────────────────────┘
