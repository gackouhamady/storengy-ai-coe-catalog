# 🚀 Project Objective

Prototype an **“AI Use-Case Catalog”** for Storengy CoE Data & AI, covering:

* **Identification & scoping** of two high-impact use cases (energy transition & CSR)
* **Data Science modeling**:

  1. **Forecasting & anomaly detection** on sensor time series (pressure, temperature)
  2. **Generative Assistant** (GenAI) for technical documentation and internal procedures
* **Adoption demonstrator**: simple local interface (Streamlit) to feed, visualize, and interact
* **Lightweight MLOps pipeline** (MLflow, FastAPI), unit tests, documentation, and “Dataiku/GCP-ready” mode

---

## 📅 Detailed 5-day working plan (+ 2 days buffer)

|    Day    | Key tasks                                                                                                                                                                              |
| :-------: | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Day 1** | - **Init repo & env**: `git init` + Python venv, `requirements.txt` (pandas, numpy, scikit-learn, prophet, torch, transformers, streamlit, mlflow, fastapi, uvicorn…) and `.gitignore` |

* **Synthetic datasets**:
  • Sensor CSV (1,000 records)
  • Procedures corpus (10 Markdown docs) |
  \| **Day 2** | - **Ingestion & EDA** (`src/ingestion.py`): read sensor CSV & Markdown, cleaning, normalization, initial visualizations (matplotlib/Streamlit) |
  \| **Day 3** | - **Forecasting & anomaly detection** (`src/time_series_model.py`):
  • Prophet or univariate LSTM for pressure forecasting
  • Isolation Forest to spot anomalies
  • KPIs: MAE, anomaly recall |
  \| **Day 4** | - **Generative Assistant** (`src/genai_model.py`):
  • Local fine-tuning of DistilGPT-2 on Markdown corpus
  • Q\&A endpoints (FastAPI)
  • Qualitative evaluation (prompt tests) |
  \| **Day 5** | - **Pipeline & demonstrator** (`src/app.py`):
  • Orchestration ingestion → sensor prediction → GenAI Q\&A → Streamlit dashboard
  • MLflow experiments (params & metrics)
  • Sanity check monitoring (> thresholds) |
  \| **Day 6** | - **Documentation & tests**:
  • `README.md` (installation, usage, Dataiku/GCP migration)
  • Flow diagram in `docs/`
  • Pytest tests for each module |
  \| **Day 7** | - **Packaging & delivery**:
  • Generate final `requirements.txt`
  • Dockerfile (`python:3.10`) for FastAPI/Streamlit app
  • Commit & push to GitHub + Cloud Run/Vertex AI deployment plan |

---

## ⚙️ Final Git Structure

```bash
storengy-ai-coe-catalog/
├── data/
│   ├── raw/                   # sensor CSV & Markdown corpus
│   └── processed/             # after cleaning
├── docs/
│   └── flow_diagram.png       # visual pipeline
├── src/
│   ├── ingestion.py           # ingestion & EDA
│   ├── time_series_model.py   # forecasting & anomaly detection
│   ├── genai_model.py         # fine-tuning & GenAI Q&A
│   ├── app.py                 # Streamlit + FastAPI orchestration
│   └── mlflow_setup.py        # MLflow config
├── tests/
│   ├── test_ingestion.py
│   ├── test_time_series.py
│   ├── test_genai.py
│   └── test_app.py
├── Dockerfile
├── README.md
├── requirements.txt
└── .gitignore
```
