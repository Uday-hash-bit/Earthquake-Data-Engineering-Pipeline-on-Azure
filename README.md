# 🌍 Earthquake Data Engineering Pipeline on Azure

An end-to-end **cloud data engineering project** that ingests real-time earthquake data from the **USGS Earthquake API**, processes it through a **Bronze–Silver–Gold lakehouse architecture**, and serves analytics-ready data using **Azure Databricks, Azure Data Factory, and Azure Synapse Analytics**.  
The pipeline runs both **manually** and via a **fully automated daily trigger**.

---

## 🧠 Project Overview

This project demonstrates how raw, high-frequency API data can be transformed into reliable, analytics-grade datasets using modern Azure-native services.  
The solution emphasizes **data quality, orchestration, automation, and observability**, mirroring real-world data platform design.

**Data Source**  
USGS Earthquake API  
  https://earthquake.usgs.gov/fdsnws/event/1/count

(Parameterized by `starttime` and `endtime`)

---

## 🏗️ Architecture at a Glance

**Ingestion → Transformation → Serving → Visualization**

- **Ingestion:** Azure Data Factory (ADF)
- **Storage:** Azure Data Lake Storage Gen2 (ADLS)
- **Processing:** Azure Databricks (PySpark notebooks)
- **Serving:** Azure Synapse Analytics
- **Visualization:** Power BI / Fabric / Tableau (ready)

The transformation layer follows the **Medallion Architecture**:
- **Bronze:** Raw, immutable ingestion
- **Silver:** Cleaned and standardized data
- **Gold:** Business-ready aggregates

![workflow](https://github.com/dyneth02/Earthquake-Data-Engineering-Pipeline-on-Azure/blob/main/screenshots/workflow.png)

---

## 🔄 End-to-End Pipeline Flow

### 1️⃣ Data Ingestion (ADF → Bronze)

- Azure Data Factory fetches earthquake event counts from the USGS API.
- API parameters are dynamically passed using pipeline expressions.
- Raw JSON responses are written to **ADLS Gen2 (Bronze layer)**.
- Supports **manual execution** and **scheduled automation**.

📘 *Artifacts:*  
- ADF Pipeline  
- Bronze Notebook  
- Data Factory Bronze Notebook  

---

### 2️⃣ Bronze → Silver Transformation (Databricks)

- Bronze data is read from ADLS using PySpark.
- Data is parsed, validated, and normalized.
- Schema enforcement and null handling are applied.
- Cleaned datasets are written to **Silver layer**.

📘 *Artifacts:*  
- Silver Notebook  
- Data Factory Silver Notebook  

---

### 3️⃣ Silver → Gold Transformation (Databricks)

- Silver data is aggregated and enriched.
- Business-level metrics (counts, trends, time windows) are computed.
- Final analytical tables are written to the **Gold layer**.
- Designed for downstream BI and analytics consumption.

📘 *Artifacts:*  
- Gold Notebook  
- Data Factory Gold Notebook  

---

### 4️⃣ Orchestration & Automation (ADF)

- ADF orchestrates the full workflow:
  - Bronze → Silver → Gold notebooks
- Dependencies ensure correct execution order.
- A **daily scheduled trigger** runs the pipeline automatically.
- Time zone configured for Sri Lanka (UTC +5:30).

📊 Pipeline monitoring confirms:
- Successful job execution
- Runtime metrics
- Failure visibility and retry capability

---

![databricks_view](https://github.com/dyneth02/Earthquake-Data-Engineering-Pipeline-on-Azure/blob/main/screenshots/Screenshot%202025-12-22%20193250.png)
![data_factory_pipeline_dubugging](https://github.com/dyneth02/Earthquake-Data-Engineering-Pipeline-on-Azure/blob/main/screenshots/Screenshot%202025-12-22%20181542.png)
![setting_ip_daily_trigger](https://github.com/dyneth02/Earthquake-Data-Engineering-Pipeline-on-Azure/blob/main/screenshots/Screenshot%202025-12-22%20190458.png)
![synapse_analysis_1](https://github.com/dyneth02/Earthquake-Data-Engineering-Pipeline-on-Azure/blob/main/screenshots/Screenshot%202025-12-22%20191609.png)
![synapse_analysis_2](https://github.com/dyneth02/Earthquake-Data-Engineering-Pipeline-on-Azure/blob/main/screenshots/Screenshot%202025-12-22%20192526.png)

---

### 5️⃣ Serving & Analytics (Synapse)

- Gold-layer datasets are made available to **Azure Synapse Analytics**.
- Optimized for SQL-based querying and BI integration.
- Enables seamless connection to Power BI, Fabric, and Tableau.

---

## 🧪 Manual vs Automated Execution

| Mode | Description |
|-----|------------|
| Manual | Direct notebook execution for development & testing |
| Automated | ADF-triggered daily pipeline for production-style runs |

Both paths share the same transformation logic, ensuring **consistency and reliability**.

---

## 🛠️ Technologies Used

- **Azure Data Factory** – Orchestration & scheduling  
- **Azure Databricks** – Distributed data processing (PySpark)  
- **Azure Data Lake Gen2** – Scalable storage  
- **Azure Synapse Analytics** – Data serving layer  
- **USGS API** – Real-world earthquake data source  

---

## 🎯 Key Engineering Highlights

- Real-world API ingestion with parameterized pipelines
- Medallion architecture (Bronze / Silver / Gold)
- Idempotent, replayable data processing
- Automated scheduling with observability
- Separation of concerns across ingestion, transformation, and serving
- Cloud-native, production-aligned design

---

## 🚀 Why This Project Matters

This project mirrors how **modern data platforms** are built in industry:
- API-driven ingestion
- Lakehouse-based transformations
- Orchestrated pipelines
- Analytics-ready outputs

It demonstrates practical data engineering skills beyond theory—covering **design, implementation, automation, and monitoring**.

---

## 👨‍💻 Author

Built and led by **Dineth Hirusha**  
Undergraduate Data Engineering / Analytics Enthusiast  

---

⭐ *If this project resonates with your interests in cloud data engineering or analytics platforms, feel free to explore, fork, or reach out.*
