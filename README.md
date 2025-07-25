# 🏡 Pune House Price Prediction

This project applies machine learning to predict house prices in Pune, India using various features such as area, size, availability, and more. It includes data preprocessing, feature engineering, outlier handling, model building, evaluation, and fine-tuning.

---

## 📊 Dataset

📁 Source: [Kaggle – Pune House Price Data](https://www.kaggle.com/datasets/saipavansaketh/pune-house-data?select=Pune+house+data.csv)  
📄 Shape: 13,320 rows × 9 columns
- 📌 Features: `area_type`, `availability`, `size`, `total_sqft`, `bath`, `balcony`, `site_location`
- 🎯 Target: `price` (in Lakhs)

---

## 🧼 Data Preprocessing

- Dropped high-cardinality `society` column
- Handled missing values with:
  - Median imputation (numerical)
  - Mode imputation (categorical)
- Extracted numerical values from `size` (e.g., "2 BHK" → 2)
- Converted `total_sqft` to float (including ranges and unit conversions)
- Normalized `availability` into two categories:
  - `Ready to Move`
  - `Not Ready to Move`

---

## 📈 Exploratory Data Analysis (EDA)

- **Skewed Columns**: `size`, `bath`, `price` had high skewness
- **Insights**:
  - Increase in `total_sqft`, `size`, and `bathrooms` generally → higher price
  - Most frequent values: `2 BHK`, `2 bath`, `1 balcony`
  - Plot area houses had highest average price
  - Top location: *Gultikde* with highest average pricing

### 📊 Visualizations

- Histograms and boxplots for `size`, `bath`, `balcony`, `price`
- Correlation heatmap
- Average prices by `area_type` and `site_location`

---

## ✂️ Outlier Handling

- Applied `QuantileTransformer` to normalize skewed distributions:
  - `size`, `total_sqft`, and `price`

---
## 🔁 Pipeline Setup

Used `ColumnTransformer` with:
- `Numerical pipeline`: Imputer → QuantileTransformer → StandardScaler
- `Categorical pipeline`: Imputer → OneHotEncoder

---

## 🤖 Models Used

- `Linear Regression`
- `Random Forest`
- `Gradient Boosting`
- `Decision Tree`
- `Support Vector Regressor (SVR)`
- `SGD Regressor`

### 📋 Model Evaluation (Cross-Validation on Training Set)

| Model              | MAE   | MSE   | RMSE  | R² Score |
|-------------------|-------|-------|-------|----------|
| Linear Regression  | 0.45  | 0.35  | 0.59  | 0.655    |
| Random Forest      | 0.40  | 0.30  | 0.54  | 0.704    |
| Gradient Boosting  | 0.41  | 0.28  | 0.53  | 0.716    |
| Decision Tree      | 0.49  | 0.46  | 0.68  | 0.541    |
| SVR                | 0.41  | 0.30  | 0.54  | 0.705    |
| SGD Regressor      | 0.45  | 0.34  | 0.58  | 0.659    |

---

## 🔍 Hyperparameter Tuning

### ✅ Best Model: `RandomForestRegressor`

