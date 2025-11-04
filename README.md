# 📈 Real-Time Stock Market Data Pipeline (Modern Data Stack)

This project showcases a complete **end-to-end real-time data pipeline** built using the **Modern Data Stack**.  
It captures **live stock market data** from an external API, streams it in real time, performs automated transformations, and delivers **analytics-ready insights** — all orchestrated in a single unified workflow.

---

## 🏗️ Architecture Overview

### ⚡ Tech Stack

| Component | Purpose |
|------------|----------|
| **Snowflake** | Cloud Data Warehouse for scalable storage and analytics |
| **DBT** | SQL-based data transformation and modeling |
| **Apache Airflow** | Workflow orchestration and task scheduling |
| **Apache Kafka** | Real-time data streaming backbone |
| **Python** | API integration and data ingestion |
| **Docker** | Containerized infrastructure setup |
| **Power BI** | Real-time data visualization and dashboards |

---

## ✅ Core Highlights

- Fetches **live (non-simulated)** stock market data directly from the Finnhub API  
- **Real-time streaming** with Apache Kafka  
- Automated **ETL orchestration** using Airflow  
- **DBT transformations** within Snowflake (Bronze → Silver → Gold layers)  
- **Cloud-native scalability** with Snowflake  
- **Interactive Power BI dashboards** for live insights  

---


## 🚀 Getting Started

1. **Clone the repository** and configure your environment variables.  
2. **Spin up the services** using Docker Compose (Kafka, Airflow, MinIO, etc.).  
3. **Run the producer script** to start fetching live market data.  
4. Data flows seamlessly into **Snowflake** through **Airflow DAGs**.  
5. **DBT** runs transformations from raw → cleaned → analytical layers.  
6. Visualize live metrics in **Power BI** dashboards.

---

## ⚙️ Implementation Steps

### 1. Kafka Configuration
- Set up **Apache Kafka** locally using Docker.  
- Created a topic `stocks-topic` for real-time event streaming.  
- Defined **producer** (API data ingestion) and **consumer** (pipeline ingestion) services.

### 2. Live Market Data Producer
- Built `stock_producer.py` using Python to fetch **real-time stock data** from the **Finnhub API**.  
- Streams JSON payloads into Kafka topics continuously.  
- Includes API key authentication and retry logic.

### 3. Kafka Consumer → MinIO Sink
- Developed `stock_consumer.py` to consume live data from Kafka.  
- Saves the streaming data into **MinIO (S3-compatible storage)**.  
- Organizes data into **raw/bronze layer directories** for staging ingestion.

### 4. Airflow Orchestration
- Initialized **Apache Airflow** (Dockerized environment).  
- Designed the DAG `stock_pipeline_dag.py` to:  
  - Extract data from MinIO  
  - Load it into **Snowflake staging tables**  
  - Schedule automated runs every **1 minute**.

### 5. Snowflake Setup
- Configured **Snowflake database**, schema, and compute warehouse.  
- Created structured layers for **Bronze → Silver → Gold** pipelines.  
- SQL scripts available within `/dbt_stocks/models/`.

### 6. DBT Transformations
- Connected **DBT** with Snowflake.  
- Defined models for each layer:  
  - **Bronze** → raw, structured ingestion  
  - **Silver** → cleaned, validated datasets  
  - **Gold** → final analytics views (Candlestick, KPI, Tree Map)

### 7. Power BI Dashboard
- Linked **Power BI** directly to the **Snowflake Gold layer** using Direct Query.  
- Built dynamic visualizations including:  
  - **Candlestick Chart** → Stock performance trends  
  - **Tree Map** → Price and volume breakdown  
  - **Gauge Charts** → Volume and sales metrics  
  - **KPIs** → Real-time performance indicators  

---

## 📊 Final Deliverables

- Fully automated **real-time data pipeline**
- **Snowflake** datasets across Bronze, Silver, and Gold layers
- **DBT models** for clean, reusable transformations
- **Airflow DAGs** for seamless orchestration
- **Power BI dashboard** with actionable insights

---

## 🧩 Summary

This project integrates **real-time data streaming, orchestration, transformation, and analytics** into one cohesive system.  
It demonstrates how modern cloud-native tools can power **live analytics** pipelines — scalable, modular, and production-ready.

---



