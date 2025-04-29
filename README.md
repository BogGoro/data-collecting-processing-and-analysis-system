# Modern Data Platform Simulation

This project simulates a modern data architecture using a combination of real-time and batch data processing technologies. It demonstrates how to collect, process, transform, and visualize data from both OLTP (transactional) and data lake systems using open-source tools in a Dockerized environment.

## 🚀 Project Overview

The system consists of:

- **Two pseudo-backend systems**:
  - One mimics a transactional OLTP system using **PostgreSQL**
  - Another mimics a data lake source using **Hadoop HDFS**

- **Change Data Capture (CDC)**:
  - Implemented using **Debezium** and **Kafka** to stream changes from PostgreSQL

- **Data Lake Processing**:
  - Batch processing of data stored in Hadoop using **Apache Spark**

- **Analytical Database**:
  - Processed and streamed data from both pipelines is stored in **ClickHouse** for fast analytical queries

- **Transformation Layer**:
  - **dbt (Data Build Tool)** is used to create modular, incremental data marts in ClickHouse

- **Orchestration**:
  - **Apache Airflow** is used to orchestrate and schedule both dbt models and Spark jobs

- **BI & Visualization**:
  - Data from ClickHouse is visualized using **Power BI** (or any BI tool of choice)

All services are containerized with **Docker Compose** to ensure easy setup and reproducibility.

---

## 🛠️ Tech Stack

| Layer              | Tool/Technology          | Description |
|-------------------|--------------------------|-------------|
| OLTP Database      | PostgreSQL               | Source of transactional data |
| CDC                | Debezium + Kafka         | Captures and streams changes from Postgres |
| Data Lake          | Hadoop HDFS              | Stores batch files (CSV, JSON, etc.) |
| Batch Processing   | Apache Spark             | Reads from HDFS, transforms data |
| Analytical DB      | ClickHouse               | Fast OLAP database for reporting |
| Transformation     | dbt                      | SQL-based transformations and data marts |
| Orchestration      | Apache Airflow           | Schedules and manages dbt + Spark workflows |
| Visualization      | Power BI (or Metabase)   | BI dashboard for business insights |
| Containerization   | Docker + Docker Compose  | Manages all services and dependencies |

---

## 📊 Data Flow Diagram

1. **Postgres ➜ Debezium ➜ Kafka ➜ ClickHouse**  
   Real-time CDC pipeline from transactional DB

2. **Hadoop ➜ Spark ➜ ClickHouse**  
   Batch processing pipeline from the data lake

3. **ClickHouse ➜ dbt ➜ Data Marts ➜ Power BI**  
   Transformation and visualization pipeline

4. **Airflow ➜ Triggers dbt + Spark jobs**

---
