
# 🚗 Car Price Prediction Model

A machine learning regression project built with Python and `scikit-learn` to predict used and new car prices based on key vehicle specifications. The complete preprocessing pipeline and trained model are serialized using `joblib` for seamless reuse and deployment.

---

## 📌 Project Overview
* **Goal:** Predict accurate vehicle market prices (`Price`) using historical car attributes.
* **Dataset:** `car_price_prediction_dataset_2500_improved.csv` (`2,500` records).
* **Model Type:** Supervised Regression (`LinearRegression` inside a `scikit-learn` `Pipeline`).

---

## 📊 Dataset Features
| Column | Type | Description |
| :--- | :--- | :--- |
| `Brand` | Categorical | Vehicle manufacturer (e.g., Honda, Toyota, BMW, Maruti) |
| `Model` | Categorical | Specific car model (e.g., City, Camry, Swift, Baleno) |
| `Year` | Numerical | Manufacturing year of the vehicle |
| `Engine Size` | Numerical | Engine displacement in liters (`0.0` for Electric) |
| `Fuel Type` | Categorical | Petrol, Diesel, or Electric |
| `Transmission` | Categorical | Manual or Automatic |
| `Condition` | Categorical | New, Like New, or Used |
| `Price` *(Target)* | Numerical | Market price of the vehicle |

> **Note:** `Car ID` serves strictly as a row identifier and is excluded from model features.

---

## 🛠️ Tech Stack
* **Language:** Python 3.x
* **Data Handling:** `pandas`, `numpy`
* **Machine Learning:** `scikit-learn` (`OneHotEncoder`, `ColumnTransformer`, `Pipeline`, `LinearRegression`)
* **Model Evaluation:** `r2_score`, `mean_absolute_error`, `mean_squared_error`
* **Serialization:** `joblib`

---

## ⚙️ Model Architecture
To prevent data leakage and streamline inference, all transformations are bundled into a single `Pipeline`:
1. **Preprocessing (`ColumnTransformer`):** Applies `OneHotEncoder` to categorical columns (`Brand`, `Fuel Type`, `Transmission`, `Condition`, `Model`) while passing numerical features through cleanly.
2. **Estimator (`LinearRegression`):** Learns linear relationships between encoded features and vehicle `Price`.
3. **Export (`joblib`):** Saves the end-to-end pipeline as `car_price_prediction_model.pkl`.

---

## 📈 Evaluation Metrics
Performance evaluated on the held-out test split:

| Metric | Score | Interpretation |
| :--- | :--- | :--- |
| **🎯 R² Score** | `0.9957` (`99.57%`) | Explains ~99.57% of variance in car prices |
| **📉 MAE** | `606.39` | Average absolute prediction error |
| **📐 MSE** | `491,334.69` | Mean squared prediction error |
| **📏 RMSE** | `700.95` | Root mean squared error in price units |

---

## 📁 Repository Structure
```text
Car_price_prediction/
├── Car price prediction.ipynb        # Data exploration, training & evaluation notebook
├── car_price_prediction_model.pkl    # Serialized scikit-learn pipeline
└── README.md                         # Project documentation
