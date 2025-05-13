# 🚀 Objectif du projet
Prototyper un **“AI Use-Case Catalog”** pour Storengy CoE Data & IA, couvrant :

- **Identification & cadrage** de deux cas d’usage à fort enjeu (transition énergétique & RSE)  
- **Modélisation Data Science** :
  1. **Forecasting & détection d’anomalies** sur séries temporelles de capteurs (pression, température)  
  2. **Assistant Génératif** (GenAI) pour la documentation technique et les procédures internes  
- **Démonstrateur d’adoption** : interface locale simple (Streamlit) pour alimenter, visualiser et interagir  
- **Pipeline MLOps léger** (MLflow, FastAPI), tests unitaires, documentation et mode « prêt Dataiku/GCP »

---

## 📅 Planning détaillé sur 5 jours ouvrés (+ 2 jours de buffer)

| Jour   | Tâches clés                                                                                                                                                                                                                     |
|:------:|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Jour 1 | - **Init repo & env** : `git init` + venv Python, `requirements.txt` (pandas, numpy, scikit-learn, prophet, torch, transformers, streamlit, mlflow, fastapi, uvicorn…) et `.gitignore`<br> - **Datasets synthétiques** :  <br>  • CSV capteurs (1 000 enregistrements)  <br>  • Corpus “procédures” (10 docs Markdown) |
| Jour 2 | - **Ingestion & EDA** (`src/ingestion.py`) : lecture CSV capteurs & Markdown, nettoyage, normalisation, premières visualisations (matplotlib/Streamlit)                                                                       |
| Jour 3 | - **Forecasting & détection d’anomalies** (`src/time_series_model.py`) :  <br>  • Prophet ou LSTM univarié pour prévoir la pression<br>  • Isolation Forest pour repérer anomalies<br>  • KPIs : MAE, recall anomalies    |
| Jour 4 | - **Assistant Génératif** (`src/genai_model.py`) :  <br>  • Fine-tuning local de DistilGPT-2 sur le corpus Markdown<br>  • Endpoints Q&A (FastAPI)<br>  • Évaluation qualitative (prompt tests)                               |
| Jour 5 | - **Pipeline & démonstrateur** (`src/app.py`) :  <br>  • Orchestration ingestion → prédiction capteurs → GenAI Q&A → dashboard Streamlit<br>  • Expériences MLflow (params & metrics)<br>  • Monitor sanity checks (> seuils) |
| Jour 6 | - **Documentation & tests** :  <br>  • `README.md` (installation, usage, migration Dataiku/GCP)  <br>  • Diagramme du flow dans `docs/`  <br>  • Tests pytest pour chaque module                                            |
| Jour 7 | - **Packaging & livraison** :  <br>  • Générer `requirements.txt` final  <br>  • Dockerfile (`python:3.10`) pour app FastAPI/Streamlit  <br>  • Commit, push sur GitHub + plan de déploiement Cloud Run/Vertex AI                  |

---

## ⚙️ Structure Git finale

```bash
storengy-ai-coe-catalog/
├── data/
│   ├── raw/                   # CSV capteurs & corpus Markdown
│   └── processed/             # after cleaning
├── docs/
│   └── flow_diagram.png       # pipeline visuel
├── src/
│   ├── ingestion.py           # ingestion & EDA
│   ├── time_series_model.py   # forecasting & anomaly detection
│   ├── genai_model.py         # fine-tuning & Q&A GenAI
│   ├── app.py                 # Streamlit + orchestration FastAPI
│   └── mlflow_setup.py        # config MLflow
├── tests/
│   ├── test_ingestion.py
│   ├── test_time_series.py
│   ├── test_genai.py
│   └── test_app.py
├── Dockerfile
├── README.md
├── requirements.txt
└── .gitignore
