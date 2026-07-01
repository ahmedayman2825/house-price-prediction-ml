<div align="center">

<h1>🏡 HomeValue-ML</h1>
<h3>House Price Prediction using Machine Learning</h3>

<p>
  Multiple regression models trained and compared to predict house prices from a real estate dataset — from a single-feature baseline to a tuned Random Forest ensemble.
</p>

<p>
  <img src="https://img.shields.io/badge/Python-3.8+-3776AB?style=for-the-badge&logo=python&logoColor=white" />
  <img src="https://img.shields.io/badge/Jupyter-Notebook-F37626?style=for-the-badge&logo=jupyter&logoColor=white" />
  <img src="https://img.shields.io/badge/scikit--learn-ML-F7931E?style=for-the-badge&logo=scikitlearn&logoColor=white" />
  <img src="https://img.shields.io/badge/License-MIT-green?style=for-the-badge" />
</p>

<p>
  <a href="#-overview">Overview</a> •
  <a href="#-features">Features</a> •
  <a href="#-tech-stack">Tech Stack</a> •
  <a href="#-installation">Installation</a> •
  <a href="#-usage">Usage</a> •
  <a href="#-results">Results</a> •
  <a href="#-project-structure">Structure</a> •
  <a href="#-future-improvements">Roadmap</a> •
  <a href="#-contributors">Contributors</a>
</p>

</div>

---

## 📌 Overview

**HomeValue-ML** predicts residential house prices from a 14,619-row Indian real estate dataset using a progression of regression techniques — from a single-feature baseline up to a hyperparameter-tuned ensemble model.

The workflow covers exploratory data analysis, missing-value and correlation checks, an 80/20 train/test split, and four progressively more powerful regressors: Simple Linear Regression, Multiple Linear Regression, Polynomial Regression (degree-tuned via `GridSearchCV`), Decision Tree, and Random Forest (both hyperparameter-tuned via `GridSearchCV`). Each model is evaluated with MAE, MSE, RMSE, and R², visualized with actual-vs-predicted and residual plots, and compared head-to-head.

**Best result:** The tuned **Random Forest Regressor** achieved an **R² of 0.883** and an **MAE of ~69,636**, outperforming every other model and cutting MAE nearly in half compared to Multiple Linear Regression.

---

## ✨ Features

- 📊 **Exploratory Data Analysis** — dataset structure, summary statistics, missing-value check, price distribution, and full feature correlation heatmap
- 🔎 **Correlation-driven feature selection** — identifies `living area` as the single strongest predictor of price for the baseline model
- 🧹 **Clean preprocessing** — drops the non-predictive `id` column and normalizes column names
- 🤖 **Five regression models compared**:
  - Simple Linear Regression (single best-correlated feature)
  - Multiple Linear Regression (all features)
  - Polynomial Regression (degree tuned via `GridSearchCV`)
  - Decision Tree Regressor (tuned via `GridSearchCV`)
  - Random Forest Regressor (tuned via `GridSearchCV`)
- 📈 **Full evaluation suite** — MAE, MSE, RMSE, and R² for every model, plus actual-vs-predicted and residual plots
- 🌳 **Feature importance analysis** — top 10 most influential features from the Random Forest model
- 🏆 **Model comparison table & chart** ranking all five models by performance
- 💾 **Model persistence** — best-performing model saved with `joblib` for reuse

---

## 🛠️ Tech Stack

| Layer | Technology |
|---|---|
| Language | Python 3.8+ |
| Data Handling | `pandas`, `NumPy` |
| Visualization | `matplotlib`, `seaborn` |
| Machine Learning | `scikit-learn` (`Pipeline`, `GridSearchCV`, `StandardScaler`, `PolynomialFeatures`, `LinearRegression`, `DecisionTreeRegressor`, `RandomForestRegressor`) |
| Model Persistence | `joblib` |
| Environment | Jupyter Notebook |

---

## ⚙️ Installation

**1. Clone the repository**

```bash
git clone https://github.com/ahmedayman2825/house-price-prediction-ml.git
cd house-price-prediction-ml
```

**2. Create a virtual environment (recommended)**

```bash
python -m venv venv
source venv/bin/activate        # Linux / macOS
venv\Scripts\activate           # Windows
```

**3. Install dependencies**

```bash
pip install numpy pandas matplotlib seaborn scikit-learn joblib notebook
```

---

## 🚀 Usage

Launch the notebook:

```bash
jupyter notebook project.ipynb
```

Then run all cells top to bottom. The notebook will:

1. Load `House Price India.csv` and run exploratory data analysis
2. Preprocess features and split the data (80% train / 20% test)
3. Train a Simple Linear Regression baseline on the most correlated feature
4. Train and evaluate Multiple Linear Regression, Polynomial Regression, Decision Tree, and Random Forest
5. Tune Polynomial degree, Decision Tree, and Random Forest hyperparameters via `GridSearchCV`
6. Plot actual-vs-predicted and residual plots for every model
7. Compare all models in a summary table and bar chart
8. Save the best-performing model to `house_price_model.pkl`

**Dataset:** 14,619 property records with 21 input features (bedrooms, bathrooms, living area, lot area, floors, waterfront, condition, grade, year built/renovated, location, nearby schools, distance from airport, etc.) and `Price` as the target.

---

## 📊 Results

Evaluated on the 20% held-out test set (2,924 samples):

| Model | MAE | RMSE | R² Score |
|---|---|---|---|
| **Random Forest** | **69,636.33** | **131,817.78** | **0.8826** |
| Decision Tree | 89,297.02 | 163,312.15 | 0.8198 |
| Polynomial Regression (degree 2) | 101,360.98 | 163,968.16 | 0.8183 |
| Multiple Linear Regression | 125,366.18 | 210,018.91 | 0.7020 |
| Simple Linear Regression (baseline) | 169,625.25 | 263,098.62 | 0.5323 |

`living area`, `grade of the house`, and `Area of the house (excluding basement)` emerged as the features most correlated with — and most important for predicting — price.

---

## 📁 Project Structure

```
house-price-prediction-ml/
│
├── project.ipynb                # Main notebook — EDA, preprocessing, training, evaluation
├── House Price India.csv        # Real estate dataset (14,619 records, 23 columns)
├── house_price_model.pkl        # Saved best-performing model (Random Forest, generated on run)
├── .gitignore
└── README.md
```

---

## 🔭 Future Improvements

- [ ] Add gradient boosting models (XGBoost, LightGBM, CatBoost) to the comparison
- [ ] Engineer date-based features (listing age, renovation recency) from `Date`, `Built Year`, and `Renovation Year`
- [ ] Apply log-transformation to `Price` to address right-skew and potentially improve linear model performance
- [ ] Add k-fold cross-validation scores for all models, not just the tuned ones
- [ ] Wrap the saved model in a simple prediction script or Flask/FastAPI endpoint
- [ ] Explore geospatial features using `Lattitude`/`Longitude` (e.g. distance to city center, clustering by neighborhood)

---

## 👤 Contributors

 **Ahmed Ayman**

[![LinkedIn](https://img.shields.io/badge/LinkedIn-0077B5?style=flat-square&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/eng-ahmed-ayman/)
[![GitHub](https://img.shields.io/badge/GitHub-181717?style=flat-square&logo=github&logoColor=white)](https://github.com/ahmedayman2825)

**Ahmed Tawfik**

[![LinkedIn](https://img.shields.io/badge/LinkedIn-0077B5?style=flat-square&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/ah-mo-tawfik/)
[![GitHub](https://img.shields.io/badge/GitHub-181717?style=flat-square&logo=github&logoColor=white)](https://github.com/tAwFiK2005)

**Ashraf Khamis**

[![LinkedIn](https://img.shields.io/badge/LinkedIn-0077B5?style=flat-square&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/ashraf-k-eesa-b8b8802b4)
[![GitHub](https://img.shields.io/badge/GitHub-181717?style=flat-square&logo=github&logoColor=white)](https://github.com/ashrafeesa)

**Ahmed Abdelwahab**

[![LinkedIn](https://img.shields.io/badge/LinkedIn-0077B5?style=flat-square&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/ahmed-abdalwahab/)
[![GitHub](https://img.shields.io/badge/GitHub-181717?style=flat-square&logo=github&logoColor=white)](https://github.com/ahmedabdalwahab)

**Ahmed Emad**

[![LinkedIn](https://img.shields.io/badge/LinkedIn-0077B5?style=flat-square&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/ahmed-zamel09/)
[![GitHub](https://img.shields.io/badge/GitHub-181717?style=flat-square&logo=github&logoColor=white)](https://github.com/AhmedZamel09)

---

<div align="center">
  <sub>Built with ❤️ by Ahmed Ayman · Alexandria University, Computer Science — AI Track</sub>
</div>
