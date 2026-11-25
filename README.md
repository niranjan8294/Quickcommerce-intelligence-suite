# 🟡 Blinkit Quick Commerce Intelligence System

<div align="center">

![Python](https://img.shields.io/badge/Python-3.10%2B-3776AB?logo=python&logoColor=white)
![Streamlit](https://img.shields.io/badge/Streamlit-1.28%2B-FF4B4B?logo=streamlit&logoColor=white)
![Scikit-learn](https://img.shields.io/badge/Scikit--learn-1.3%2B-F7931E?logo=scikit-learn&logoColor=white)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-15-336791?logo=postgresql&logoColor=white)
![FastAPI](https://img.shields.io/badge/FastAPI-0.100%2B-009688?logo=fastapi&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-Ready-2496ED?logo=docker&logoColor=white)
![License](https://img.shields.io/badge/License-MIT-green)

**A production-quality, end-to-end quick-commerce analytics platform**  
**covering descriptive → diagnostic → predictive → prescriptive analytics**

 By [Niranjan Bhagat](https://github.com/NiranjanBhagat)*

</div>

---

> **⚠️ Disclaimer**: This is an **independent portfolio project**. It is **not officially affiliated with, endorsed by, or connected to Blinkit, Zomato, Swiggy Instamart, or JioMart** in any way. All data is a publicly available synthetic/simulated dataset. All ML predictions are illustrative and do not represent real operational forecasts.

---

## 📋 Table of Contents

1. [Project Overview](#project-overview)
2. [Business Problem](#business-problem)
3. [Project Objectives](#project-objectives)
4. [Key Features](#key-features)
5. [Technology Stack](#technology-stack)
6. [System Architecture](#system-architecture)
7. [Dataset Description](#dataset-description)
8. [Installation Guide](#installation-guide)
9. [Dashboard Preview](#dashboard-preview)
10. [SQL Analytics](#sql-analytics)
11. [Machine Learning Methodology](#machine-learning-methodology)
12. [Model Evaluation](#model-evaluation)
13. [Business Recommendations](#business-recommendations)
14. [Future Improvements](#future-improvements)
15. [Original Source & Acknowledgements](#original-source--acknowledgements)
16. [My Contributions](#my-contributions--niranjan-bhagat)
17. [Maintainer](#maintainer)

---

## 🚀 Project Overview

The **Blinkit Quick Commerce Intelligence System (QCI System)** transforms raw quick-commerce transaction data into actionable business intelligence through a complete analytics pipeline — from raw CSV ingestion through advanced ML models to an interactive executive dashboard.

The system analyses **100,000 simulated transactions** across three major Indian quick-commerce platforms (Blinkit, Swiggy Instamart, JioMart) and delivers:

- **Executive KPI dashboards** for C-suite decisions
- **AI-powered demand forecasting** for 7-day horizon planning
- **Delivery delay prediction** to proactively manage SLA breaches
- **Customer RFM segmentation** for targeted retention
- **Stockout risk prediction** for inventory optimisation
- **Revenue and profitability analysis** across platforms and categories

---

## 💼 Business Problem

Quick-commerce (q-commerce) platforms operate in a hyper-competitive market where:

| Challenge | Impact |
|-----------|--------|
| SLA breaches (delivery > promised time) | -1.1 rating points per 10 min delay |
| Evening peak demand (18:00–21:00) | 15% SLA breach rate on Blinkit |
| High churn from price-only customers | 70%+ of JioMart customers at risk |
| Inventory stockouts in top categories | Lost revenue + customer trust damage |
| Lack of real-time analytics | Reactive instead of proactive operations |

**Without a unified intelligence system, platforms cannot:**
- Predict demand spikes before they cause stockouts
- Identify at-risk customers before they churn
- Understand which dark stores underperform
- Take data-driven decisions on SLA targets

---

## 🎯 Project Objectives

1. **Build an end-to-end analytics pipeline** — raw data → processed features → ML models → dashboard
2. **Implement 4-tier analytics** — Descriptive, Diagnostic, Predictive, Prescriptive
3. **Deliver AI-powered predictions** with clear synthetic-data disclaimers
4. **Create an interactive dashboard** with city/store/platform filters
5. **Generate downloadable reports** for stakeholder sharing
6. **Demonstrate portfolio-ready** data engineering and ML engineering skills

---

## ✨ Key Features

### 📊 Analytics Features
- **Executive KPI Cards** — Total revenue, order volume, SLA compliance, NPS, AOV
- **Platform Comparison** — Side-by-side Blinkit vs Swiggy vs JioMart benchmarking
- **Hourly Demand Heatmaps** — Day × Hour demand patterns
- **Category Revenue Treemaps** — Profitability by product category
- **SLA Breach Analysis** — Breach rates by platform, hour, and city

### 🤖 AI/ML Features
- **7-Day Demand Forecast** — Time-series forecasting with confidence intervals
- **Delivery Delay Predictor** — Probability score per order context (Random Forest)
- **Customer Segmentation** — RFM-based KMeans clustering (5 segments)
- **Stockout Risk Scoring** — Category/platform-level risk heatmap
- **Customer LTV Estimation** — Lifetime value modelling per segment
- **Product Recommendations** — Category co-occurrence affinity engine

### 🏙️ City & Store Analytics
- **City-wise Filtering** — Mumbai, Delhi, Bangalore, Hyderabad
- **Dark Store Performance** — Simulated store-level metrics
- **Geographic Order Distribution** — City-level revenue breakdown

### 📁 Export & Reporting
- **Download CSV** — Filtered data export
- **Download Excel Report** — Full analytics export
- **Model Evaluation Card** — Markdown model documentation

---

## 🛠️ Technology Stack

| Layer | Technologies |
|-------|-------------|
| **Data Processing** | Python 3.10+, Pandas, NumPy, SciPy |
| **Machine Learning** | Scikit-learn (RF, KMeans, LogReg), StatsModels |
| **Visualisation** | Plotly, Seaborn, Matplotlib |
| **Dashboard** | Streamlit 1.28+ |
| **API Layer** | FastAPI, Uvicorn |
| **Database** | PostgreSQL 15, SQLAlchemy |
| **SQL Analytics** | Advanced PostgreSQL (CTEs, Window Functions, NTILE) |
| **Containerisation** | Docker, Docker Compose |
| **Testing** | Pytest |
| **Notebook EDA** | Jupyter, Plotly Express |

---

## 🏗️ System Architecture

```
┌─────────────────────────────────────────────────────────────────┐
│                    RAW DATA LAYER                                │
│         dataset/raw_data/ecommerce_delivery_analytics.csv        │
│                      (100K rows, 11 columns)                     │
└───────────────────────┬────────────────────────────────────────┘
                        │
                        ▼
┌─────────────────────────────────────────────────────────────────┐
│                    ETL PIPELINE                                  │
│              src/data/etl_pipeline.py                            │
│   - Data validation & cleaning                                   │
│   - Feature engineering (hour, is_peak, SLA targets, RFM)       │
│   - Synthetic enrichment (city, store_id, lat/long)              │
│   Output: dataset/processed/orders_processed.csv                 │
└───────────────────────┬────────────────────────────────────────┘
                        │
              ┌─────────┴─────────┐
              ▼                   ▼
┌──────────────────┐   ┌──────────────────────────────────────────┐
│  SQL ANALYTICS   │   │           ML/AI ENGINE                   │
│  sql/schema.sql  │   │  src/models/                             │
│  sql/transform.. │   │  ├── demand_forecaster.py                │
│  - Star schema   │   │  ├── delivery_delay_predictor.py         │
│  - RFM queries   │   │  ├── customer_segmentation.py            │
│  - Cohort anal.  │   │  ├── stockout_predictor.py               │
│  - Rolling KPIs  │   │  ├── revenue_analyzer.py                 │
└──────────────────┘   │  └── recommendation_engine.py            │
                        └──────────────────┬──────────────────────┘
                                           │
                                           ▼
┌─────────────────────────────────────────────────────────────────┐
│                   PRESENTATION LAYER                             │
│                                                                  │
│  ┌──────────────────────┐    ┌────────────────────────────────┐ │
│  │  Streamlit Dashboard │    │        FastAPI REST API        │ │
│  │  dashboard/app.py    │    │        api/main.py             │ │
│  │  - 7 page navigation │    │  GET /api/kpis                 │ │
│  │  - Interactive charts│    │  GET /api/forecast             │ │
│  │  - City/platform     │    │  GET /api/platforms            │ │
│  │    filters           │    │  GET /health                   │ │
│  │  - Export buttons    │    └────────────────────────────────┘ │
│  └──────────────────────┘                                        │
└─────────────────────────────────────────────────────────────────┘
                        │
                        ▼
┌─────────────────────────────────────────────────────────────────┐
│               INFRASTRUCTURE LAYER                               │
│         Docker + Docker Compose + PostgreSQL                     │
└─────────────────────────────────────────────────────────────────┘
```

---

## 📂 Repository Structure

```
📦 QuickCommerce-Intelligence-Suite
├── 📂 api/                          # FastAPI REST backend
│   └── main.py
├── 📂 assets/                       # Images, icons
├── 📂 dashboard/                    # Streamlit dashboard
│   ├── app.py                       # Main application entry point
│   └── components/
│       ├── kpi_cards.py             # KPI card renderer
│       ├── charts.py                # Plotly chart builders
│       └── filters.py               # Data filter utilities
├── 📂 dataset/
│   ├── 📂 raw_data/
│   │   └── ecommerce_delivery_analytics.csv  # Original dataset (100K rows)
│   ├── 📂 dimensions/               # Star schema dimension tables
│   ├── 📂 processed/                # Feature-engineered data (generated)
│   └── DATA_DESCRIPTION.md
├── 📂 notebooks/                    # EDA notebooks (original + refactored)
│   ├── Extract.ipynb
│   ├── Load.ipynb
│   └── Analysis.ipynb
├── 📂 reports/                      # Generated reports
│   └── EDA_Quick_Commerce.pptx
├── 📂 sql/
│   ├── schema.sql                   # Star schema DDL
│   └── transformation.sql           # Advanced analytics SQL
├── 📂 src/                          # Modular Python source
│   ├── 📂 analytics/
│   │   └── kpi_engine.py
│   ├── 📂 data/
│   │   ├── etl_pipeline.py          # Main ETL pipeline
│   │   └── data_generator.py        # Synthetic data enrichment
│   ├── 📂 models/
│   │   ├── demand_forecaster.py
│   │   ├── delivery_delay_predictor.py
│   │   ├── customer_segmentation.py
│   │   ├── stockout_predictor.py
│   │   ├── revenue_analyzer.py
│   │   ├── recommendation_engine.py
│   │   └── model_evaluator.py
│   └── 📂 utils/
│       └── helpers.py
├── 📂 tests/
│   └── test_etl.py
├── .env.example
├── .gitignore
├── CONTRIBUTIONS.md
├── docker-compose.yml
├── Dockerfile
├── LICENSE
├── Makefile
├── pyproject.toml
├── README.md                        # This file
└── requirements.txt
```

---

## 📊 Dataset Description

| Field | Type | Description |
|-------|------|-------------|
| `order_id` | String | Unique order identifier (ORD000001…) |
| `customer_id` | String | Unique customer identifier (CUST0001…) |
| `platform_name` | Categorical | Platform: Blinkit / Swiggy Instamart / JioMart |
| `order_datetime` | DateTime | Synthetic timestamp (March–April 2025) ⚠️ |
| `delivery_time_min` | Integer | Actual delivery time in minutes |
| `product_category` | Categorical | Dairy / Grocery / Snacks / Fruits & Veg / Beverages / Personal Care |
| `order_value_inr` | Float | Order amount in Indian Rupees |
| `delivery_delay` | Binary | Whether delivery exceeded SLA (0/1) |
| `refund_requested` | Binary | Whether customer requested refund (0/1) |
| `service_rating` | Integer | Customer rating 1–5 |
| `customer_feedback` | Text | Free-text feedback |

**Synthetic Enrichments** *(added by Niranjan Bhagat for portfolio purposes)*:

| Field | Description |
|-------|-------------|
| `city` | Assigned city (Mumbai/Delhi/Bangalore/Hyderabad) — ⚠️ Simulated |
| `store_id` | Dark store identifier — ⚠️ Simulated |
| `hour_of_day` | Extracted from synthetic timestamp — ⚠️ Simulated |
| `is_peak_hour` | Whether order placed 18:00–21:00 — ⚠️ Simulated |
| `sla_target` | Platform-specific SLA in minutes — Derived |
| `is_sla_breach` | Whether delivery_time > sla_target — Derived |
| `revenue_tier` | Low / Medium / High / Premium — Derived |

> ⚠️ **Data Disclaimer**: The raw dataset is a synthetic simulation of quick-commerce transactions. It is not real operational data from Blinkit, Swiggy, or JioMart.

---

## ⚙️ Installation Guide

### Prerequisites
- Python 3.10+
- pip
- (Optional) PostgreSQL 15+ for SQL features
- (Optional) Docker for containerised deployment

### Quick Start (Dashboard Only)

```bash
# 1. Clone the repository
git clone https://github.com/NiranjanBhagat/QuickCommerce-Intelligence-Suite.git
cd QuickCommerce-Intelligence-Suite

# 2. Create virtual environment
python3 -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate

# 3. Install dependencies
pip install -r requirements.txt

# 4. Run ETL pipeline (generates processed data)
python3 src/data/etl_pipeline.py

# 5. Launch the dashboard
streamlit run dashboard/app.py
```

Open your browser at **http://localhost:8501** 🚀

### Full Installation with PostgreSQL

```bash
# Configure environment
cp .env.example .env
# Edit .env with your PostgreSQL credentials

# Run database setup
psql -U your_user -d your_db -f sql/schema.sql
psql -U your_user -d your_db -f sql/transformation.sql

# Run FastAPI backend
uvicorn api.main:app --reload --port 8000
```

### Docker Deployment

```bash
# Build and run all services
docker-compose up --build

# Dashboard: http://localhost:8501
# API:       http://localhost:8000/docs
# pgAdmin:   http://localhost:5050
```

### Run Tests

```bash
pytest tests/ -v
```

---

## 🖥️ Dashboard Preview

The dashboard features **7 interactive pages**:

| Page | Description |
|------|-------------|
| 📊 Executive Overview | KPI cards, platform comparison, demand trends |
| 🚀 Platform Analytics | SLA analysis, delivery distributions, radar charts |
| 📦 Inventory & Demand | Category heatmaps, stockout risk, demand patterns |
| 🤖 AI Predictions | ⚠️ Demand forecast, delay probability, churn risk |
| 👥 Customer Intelligence | RFM segments, LTV, city-wise breakdown |
| 💰 Revenue Analysis | Revenue trends, treemaps, 30-day projections |
| ⚙️ Settings | About, dataset info, data download |

**Brand Design System:**
- Primary Yellow: `#F8D70B` (Blinkit-inspired)
- Deep Green: `#0C831F`
- Dark Navy: `#0F172A`
- Supports dark and light mode toggle

---

## 🗄️ SQL Analytics

The `sql/` directory contains advanced PostgreSQL analytics covering:

```sql
-- 1. Star Schema (fact_orders + 4 dimensions)
-- 2. RFM Scoring with NTILE(4) ranking
-- 3. Platform Performance Scorecard (SLA %, NPS proxy)
-- 4. Category Revenue Contribution & Growth
-- 5. Hourly Demand Aggregation (Day × Hour matrix)
-- 6. Customer Lifetime Value Estimation
-- 7. Churn Risk Scoring (recency + refund_rate weighted)
-- 8. Weekly Cohort Retention Analysis
-- 9. Rolling 7-Day Revenue Trends (Window Functions)
-- 10. Views: v_platform_summary, v_category_performance, v_customer_rfm
```

Key SQL techniques demonstrated:
- **CTEs** for readable multi-step transformations
- **Window Functions** (LAG, LEAD, NTILE, ROW_NUMBER, RANK)
- **Cohort Analysis** using DATE_TRUNC and self-joins
- **Statistical approximations** (percentile estimation)

---

## 🤖 Machine Learning Methodology

> ⚠️ **Important**: All models are trained on the synthetic dataset described above. Performance metrics reflect model fit on this simulation, not real-world predictive accuracy.

### 1. Demand Forecasting
- **Algorithm**: Linear Regression with polynomial features (degree 2) + time features
- **Features**: Day of week, is_weekend, 7-day rolling avg, week number
- **Output**: 7-day daily demand forecast per platform with confidence interval

### 2. Delivery Delay Prediction
- **Algorithm**: Random Forest Classifier (n_estimators=100, max_depth=8)
- **Features**: Platform, category, order_value, hour_of_day, is_weekend, is_peak_hour
- **Output**: Delay probability score (0–1)

### 3. Customer Segmentation (RFM)
- **Algorithm**: KMeans Clustering (k=5, StandardScaler)
- **Features**: Recency (days since last order), Frequency (order count), Monetary (total spend)
- **Segments**: Champions, Loyal Customers, At Risk, Price Sensitive, Lost

### 4. Stockout Risk
- **Algorithm**: Heuristic scoring + Random Forest on demand velocity
- **Features**: Daily demand trend, category avg demand, platform allocation
- **Output**: Risk score 0–1 per category×platform combination

### 5. Customer LTV
- **Formula**: `LTV = AOV × purchase_frequency × 12`
- **Segmentation**: High/Medium/Low LTV tiers

---

## 📈 Model Evaluation

> ⚠️ All metrics below are from train/test splits on the **synthetic dataset** and should not be interpreted as real-world model performance.

| Model | Metric | Score (Synthetic) |
|-------|--------|-------------------|
| Delivery Delay Predictor | Accuracy | ~72–78% |
| Delivery Delay Predictor | AUC-ROC | ~0.76–0.82 |
| Customer Segmentation | Silhouette Score | ~0.35–0.45 |
| Demand Forecast (7-day) | MAE | ~180–250 orders/day |

*Run `python3 -c "from src.models.model_evaluator import ModelEvaluator; ..."` to generate your own metrics.*

---

## 💡 Business Recommendations

Based on the analysis (derived from synthetic data — patterns may not apply to real operations):

### 🔴 Critical Actions
1. **SLA breach mitigation during 18:00–21:00** — Blinkit shows 15%+ breach rate in this window. Recommendation: pre-position inventory and increase dark store staffing 2 hours before peak
2. **JioMart churn prevention** — 45% customer satisfaction score and 70%+ churn risk. Targeted retention campaigns for price-sensitive segment can recover 15–20% of churning users

### 🟡 High-Priority
3. **Stockout prevention in Dairy & Grocery** — highest demand velocity. Automated reorder triggers when stock velocity exceeds 3-day rolling average
4. **Champion customer rewards** — 15% of customers drive 40% of revenue. Exclusive loyalty benefits to protect this cohort

### 🟢 Growth Opportunities
5. **City expansion analytics** — Delhi shows lower SLA breach rate (better infrastructure fit). Opportunity for Blinkit dark store expansion
6. **Cross-sell within Personal Care** — lowest basket value but highest attach rate. Bundle recommendations can increase AOV by estimated 8–12%

---

## 🔮 Future Improvements

- [ ] Real-time data streaming integration (Apache Kafka)
- [ ] A/B testing framework for SLA strategy experiments
- [ ] NLP sentiment analysis on customer feedback text
- [ ] Graph-based recommendation (Neo4j / BigQuery Graph)
- [ ] Multi-city supply chain optimisation (OR-Tools)
- [ ] Integration with real Blinkit API (if opened)
- [ ] Automated weekly report generation and email dispatch
- [ ] PowerBI embedded dashboard (enterprise version)
- [ ] Kubernetes deployment for production scaling
- [ ] Advanced XGBoost/LightGBM models with hyperparameter tuning

---



All original copyright notices and MIT License requirements have been preserved. See [CONTRIBUTIONS.md](CONTRIBUTIONS.md) for a detailed breakdown.

---

## 🏆 My Contributions — Niranjan Bhagat

The following elements are **original work by Niranjan Bhagat**, built on top of the original foundation:

| Contribution | Description |
|-------------|-------------|
| **Modular Architecture** | Complete restructuring into src/, dashboard/, tests/, api/ |
| **ETL Pipeline** | `src/data/etl_pipeline.py` — rewritten from scratch |
| **ML Engine (6 models)** | Demand forecasting, delay prediction, RFM segmentation, stockout risk, revenue analysis, recommendations |
| **Streamlit Dashboard** | Full 7-page interactive dashboard with Blinkit brand design |
| **Advanced SQL** | 10 analytics queries + star schema + views (sql/schema.sql, sql/transformation.sql) |
| **FastAPI Backend** | REST API layer (api/main.py) |
| **Docker Setup** | Dockerfile + docker-compose.yml |
| **Data Enrichment** | Synthetic city, store_id, peak-hour features added responsibly |
| **Documentation** | README.md, CONTRIBUTIONS.md, DATA_DESCRIPTION.md |
| **Testing** | pytest suite (tests/test_etl.py) |

---

## 👤 Maintainer

<div align="center">

**Niranjan Bhagat**  
Data Analyst | Full-Stack Developer | Data Scientist

🔗 [GitHub](https://github.com/NiranjanBhagat) | [LinkedIn](https://linkedin.com/in/niranjanbhagat)

*"Turning data into decisions that matter"*

</div>

---

<div align="center">

**⚡ Built with passion for data analytics and quick-commerce intelligence**

*Original dataset and notebooks — MIT License*  
*Transformation and extensions by [Niranjan Bhagat](https://github.com/NiranjanBhagat)

</div>
