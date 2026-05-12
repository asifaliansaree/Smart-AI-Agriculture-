🌾 Pakistan Crop Intelligence System
An interactive, AI-powered agricultural decision-support platform built with Streamlit and scikit-learn. This project was developed as part of the 4th Semester Data Science coursework and covers three core machine learning tasks: crop disease classification, yield regression forecasting, and temporal zone clustering — all accessible through a polished web dashboard.

📌 Project Overview
TaskDatasetAlgorithm(s)Wheat Disease ClassificationCustom wheat disease dataset (43 samples, SMOTE applied)Decision Tree, KNN, Random ForestRaisin ClassificationRaisin Dataset (900 samples, 7 features)Logistic Regression, SVM, Random ForestCrop Yield RegressionFAOSTAT data (Wheat, Rice, Maize)Linear Regression, Ridge, Random Forest, XGBoostYield Zone ClusteringYield time-series dataK-Means (with Elbow & Silhouette analysis)

🖥️ Application Pages
The Streamlit app has six interactive pages accessible via the sidebar:

🏠 Home — Project overview, system metrics, and dataset summaries
📊 Model Performance Dashboard — Confusion matrices, ROC curves, and comparison tables for all trained models
🔬 Disease Risk Checker — Input crop symptoms and get a live disease prediction
📈 Yield Predictor — Select a crop and year range to generate a yield forecast
🗺️ Crop Zone Insights — K-Means clustering results visualized over time and across PCA space
🔍 Comparative Analysis — Side-by-side model evaluation across all pipelines


📁 Project Structure
ML_Project_Ansaree/
│
├── app.py                          # Main Streamlit application
├── run_app.py                      # Launcher script
│
├── classification_models.py        # Disease & raisin classification pipelines
├── regression_models.py            # Crop yield regression pipeline
├── clusturing.py                   # K-Means clustering pipeline
├── data_preprocessing.py           # Data cleaning & feature engineering
├── eda.py                          # Exploratory data analysis & plot generation
│
├── Dataset.xlsx                    # Wheat yield dataset
├── Raisin_Dataset.xlsx             # Raisin classification dataset
├── FAOSTAT_data_en_4-5-2026.csv    # FAO crop yield data
│
├── cleaned_disease.csv             # Preprocessed disease data
├── cleaned_raisin.csv              # Preprocessed raisin data
├── cleaned_yield.csv               # Preprocessed yield data
├── clustered_yield.csv             # Yield data with cluster labels
│
├── best_disease_model.pkl          # Saved best disease classifier
├── best_raisin_model.pkl           # Saved best raisin classifier
├── best_yield_model.pkl            # Saved best yield regressor
├── crop_models.pkl                 # Per-crop regression models
├── disease_encoders.pkl            # Label encoders for disease features
├── raisin_encoder.pkl              # Label encoder for raisin classes
├── raisin_scaler.pkl               # StandardScaler for raisin features
│
├── disease_classification_results.csv
├── raisin_classification_results.csv
├── regression_results.csv
│
├── eda_plots/                      # All generated EDA and evaluation plots
│   ├── confusion matrices (cm_*.png)
│   ├── ROC curves (roc_*.png)
│   ├── regression plots (regression_*.png)
│   ├── clustering visuals (clusters_*.png, elbow_curve.png, ...)
│   └── feature importance, correlation heatmaps, etc.
│
└── Report/
    └── ML_Project_Report.docx      # Full project report

🚀 Getting Started
Prerequisites
Python 3.8 or higher is required. All dependencies are auto-installed when you run the app for the first time.
Installation & Run
bash# 1. Clone the repository
git clone https://github.com/your-username/ML_Project_Ansaree.git
cd ML_Project_Ansaree

# 2. (Optional) Create a virtual environment
python -m venv venv
source venv/bin/activate      # Windows: venv\Scripts\activate

# 3. Run the app
python run_app.py
The app will open in your browser at http://localhost:8501.

Note: You can also launch directly with streamlit run app.py

Dependencies
The following packages are used (auto-installed on first run):
pandas, numpy, scikit-learn, matplotlib, seaborn,
plotly, openpyxl, joblib, streamlit, xgboost, imbalanced-learn

🧪 Running Individual Pipelines
To retrain models or regenerate EDA plots independently:
bashpython data_preprocessing.py    # Clean and preprocess all datasets
python eda.py                   # Generate EDA plots
python classification_models.py # Train disease & raisin classifiers
python regression_models.py     # Train crop yield regressors
python clusturing.py            # Run K-Means clustering

📊 Key Results
Model TaskBest ModelMetricWheat Disease ClassificationRandom ForestBest F1-Score (cross-validated)Raisin ClassificationSVM / Random Forest~95%+ AccuracyCrop Yield RegressionXGBoost / Random ForestBest R² per cropClusteringK-Means (optimal k)Silhouette Score evaluated

⚠️ The wheat disease dataset contains only 43 samples across 9+ classes. SMOTE was applied to handle class imbalance, and cross-validation was used instead of a fixed train-test split.


📝 Notes

All trained models are saved as .pkl files and loaded at runtime by the Streamlit app — no retraining is needed to use the dashboard.
The eda_plots/ folder contains all evaluation plots (confusion matrices, ROC curves, feature importance charts, clustering visualizations) pre-generated for the dashboard.
GridSearchCV was used to tune hyperparameters for Random Forest, SVM, Ridge, and KNN models.
