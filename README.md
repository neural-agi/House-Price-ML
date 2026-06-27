<div align="center">

# 🏠 House Price Predictor ML

### End-to-end machine learning pipeline to predict residential house prices — clean, reproducible, and explainable.

[![Python](https://img.shields.io/badge/Python-3.8%2B-3776AB?style=for-the-badge&logo=python&logoColor=white)](https://python.org)
[![Scikit-Learn](https://img.shields.io/badge/Scikit--Learn-1.x-F7931E?style=for-the-badge&logo=scikit-learn&logoColor=white)](https://scikit-learn.org)
[![Pandas](https://img.shields.io/badge/Pandas-2.x-150458?style=for-the-badge&logo=pandas&logoColor=white)](https://pandas.pydata.org)
[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg?style=for-the-badge)](LICENSE)
[![Status](https://img.shields.io/badge/Status-Active-brightgreen?style=for-the-badge)]()

<br/>

> **Predicts residential sale prices** with a Random Forest pipeline, complete with preprocessing, hyperparameter tuning, overfitting analysis, and model explainability using feature & permutation importance.

</div>

---

## 🎯 What This Project Does

Given a house's physical attributes — size, quality, basement, garage — this model predicts its **final sale price** in dollars.

This is a real-world regression problem built end-to-end:
- Raw data → preprocessing → model training → evaluation → explainability
- No data leakage (thanks to proper sklearn `Pipeline` usage)
- Validated against overfitting with train vs validation MAE comparison

---

## 📊 Results at a Glance

| Model | Train MAE | Validation MAE |
|---|---|---|
| Linear Regression (Baseline) | — | ~$22,000+ |
| Random Forest (Default) | — | **~$17,500** |
| Random Forest (Tuned) | ~$7,200 | ~$17,500 |

> ⚠️ The tuned model's train-vs-val gap (~$10K) reveals classic overfitting — a great teaching moment on the bias-variance tradeoff.

---

## 🏗️ Project Structure

```
house-price-ml/
│
├── notebooks/
│   └── 01_house_price_prediction.ipynb   # Full ML pipeline notebook
│
├── data/
│   ├── train.csv                          # Ames Housing dataset
│   └── data_description.txt              # Feature documentation
│
├── requirements.txt                       # Python dependencies
└── README.md
```

---

## ⚙️ ML Pipeline Overview

```
Raw Data (Ames Housing)
        │
        ▼
┌──────────────────────────────┐
│       Data Preprocessing     │
│  ┌──────────┐ ┌───────────┐  │
│  │ Numerical│ │Categorical│  │
│  │  Impute  │ │  Impute + │  │
│  │ (Median) │ │  OneHot   │  │
│  └──────────┘ └───────────┘  │
│      ColumnTransformer       │
└──────────────┬───────────────┘
               │
               ▼
    ┌─────────────────────┐
    │   sklearn Pipeline  │
    │ (No data leakage ✅) │
    └──────────┬──────────┘
               │
     ┌─────────┴──────────┐
     ▼                    ▼
Linear Regression    Random Forest
  (Baseline)       (Tuned w/ GridSearch)
     │                    │
     └────────┬───────────┘
              ▼
     MAE Evaluation + Overfitting Analysis
              │
              ▼
     Feature Importance + Permutation Importance
```

---

## 🔍 Model Explainability

Both **feature importance** and **permutation importance** were used to understand what the model actually learned.

### Top Predictive Features

| Feature | Interpretation |
|---|---|
| `OverallQual` | Build quality rating |
| `GrLivArea` | Above-ground living area (sq ft) |
| `TotalBsmtSF` | Total basement area |
| `BsmtFinSF1` | Finished basement area |
| `1stFlrSF` | First floor area |
| `GarageArea` / `GarageCars` | Garage size and capacity |

> 💡 These align with real-world intuition — bigger, higher-quality homes with more usable space cost more. The model learned something meaningful, not noise.

---

## 🚀 Getting Started

### Prerequisites
- Python 3.8+
- pip

### Installation

```bash
# 1. Clone the repo
git clone https://github.com/neural-agi/house-price-ml.git
cd house-price-ml

# 2. Install dependencies
pip install -r requirements.txt

# 3. Launch the notebook
jupyter notebook notebooks/01_house_price_prediction.ipynb
```

---

## 📦 Tech Stack

| Tool | Purpose |
|---|---|
| **Python** | Core language |
| **Pandas / NumPy** | Data wrangling |
| **Scikit-learn** | Pipelines, models, evaluation |
| **Matplotlib / Seaborn** | Visualization |

---

## 🧠 Key Learnings & Insights

- ✅ Proper use of `Pipeline` + `ColumnTransformer` prevents data leakage
- ✅ `MAE` chosen over `RMSE` for interpretability in dollar terms
- ✅ Hyperparameter tuning ≠ better generalization — overfitting is real
- ✅ Permutation importance cross-validates feature importance (no contradictions found)
- ✅ Model behavior is grounded in domain-relevant features, not spurious correlations

---

## 🔮 Roadmap / Future Improvements

- [ ] Advanced feature engineering (interaction terms, log-transforms)
- [ ] Gradient Boosting experiments (XGBoost, LightGBM, CatBoost)
- [ ] SHAP values for deeper explainability
- [ ] Streamlit or FastAPI deployment
- [ ] Kaggle submission + leaderboard benchmarking

---

## 🤝 Contributing

Pull requests are welcome! For major changes, please open an issue first to discuss what you'd like to change.

1. Fork the repo
2. Create your feature branch (`git checkout -b feature/your-feature`)
3. Commit your changes (`git commit -m 'Add some feature'`)
4. Push to the branch (`git push origin feature/your-feature`)
5. Open a Pull Request

---

## 📄 License

This project is licensed under the [MIT License](LICENSE).

---

## 👤 Author

**Paranjay Das**
BTech CSE (AI/ML) | Aspiring Machine Learning Engineer

[![GitHub](https://img.shields.io/badge/GitHub-Follow-181717?style=flat-square&logo=github)](https://github.com/neural-agi)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-Connect-0A66C2?style=flat-square&logo=linkedin)](www.linkedin.com/in/paranjay-das-10b167384)

---

<div align="center">

⭐ **If this project helped you, drop a star — it actually means a lot!** ⭐

</div>
