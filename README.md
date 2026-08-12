#  House Prices - Advanced Regression Techniques

Machine learning project for predicting house prices using the
[Kaggle House Prices: Advanced Regression Techniques](https://www.kaggle.com/competitions/house-prices-advanced-regression-techniques) dataset.

The goal of this project is to build a regression model that accurately predicts the sale price of residential properties based on features such as house quality, living area, neighborhood, garage, basement, and other property characteristics.

##  Project Status

Completed

Currently working on model selection and hyperparameter tuning.

---

## 📊 Dataset

The dataset is provided by the Kaggle House Prices competition.

- Training samples: 1,460
- Features: 79 original features
- Target: SalePrice
- Problem type: Regression

The dataset contains information about residential properties in Ames, Iowa.

---

## 🔍 Exploratory Data Analysis

The project includes:

- Dataset structure and data type inspection
- Missing-value analysis
- Target variable analysis
- SalePrice distribution and skewness analysis
- Correlation analysis
- Identification of important features
- Visualization of relationships between features and SalePrice

### Important features identified

Some of the strongest correlations with `SalePrice` include:

- `OverallQual`
- `GrLivArea`
- `GarageCars`
- `GarageArea`
- `TotalBsmtSF`
- `1stFlrSF`
- `FullBath`
- `TotRmsAbvGrd`
- `YearBuilt`

---

## 🧹 Data Preprocessing

The preprocessing stage includes:

- Handling missing values
- Treating missing categorical values according to their meaning
- Median imputation for numerical variables
- Neighborhood-based imputation for `LotFrontage`
- One-hot encoding of categorical variables
- Standardization of numerical features
- Removing the `Id` column
- Log transformation of `SalePrice` using `log1p()`

A Scikit-learn preprocessing pipeline is used to ensure consistent preprocessing during model training and validation.

---

## 🛠️ Feature Engineering

Additional features were created to provide the models with more meaningful representations of the data:

- `TotalSF` — Total basement + first floor + second floor area
- `TotalBathrooms` — Combined full and half bathrooms
- `TotalPorchSF` — Combined porch and deck area
- `HouseAge` — Age of the house at the time of sale
- `RemodAge` — Years since the house was remodeled
- `TotalSF_per_Room` — Total area relative to number of rooms

---

## 🤖 Models

Several regression models are being compared:

1. Linear Regression
2. Ridge Regression
3. Random Forest Regressor
4. Gradient Boosting Regressor

### Current Cross-Validation Results

| Model | 5-Fold CV RMSE |
|---|---:|
| Ridge Regression | 0.14738 |
| Random Forest | 0.14071 |
| Gradient Boosting| 0.13318 |

Lower RMSE is better.

### Current Best Model

Gradient Boosting Regressor

Current 5-fold cross-validation RMSE:

0.13318

Further hyperparameter tuning will be performed before selecting the final model.

---

## 📈 Evaluation

The primary evaluation metric used during model development is:

Root Mean Squared Error (RMSE) on the log-transformed target.

The target variable is transformed using:

```python
y = np.log1p(train_df["SalePrice"])

## 🏆 Kaggle Result

The final Gradient Boosting model achieved:

Kaggle RMSE: 0.12922

### Final Model

Gradient Boosting Regressor

- `n_estimators`: 1500
- `learning_rate`: 0.02
- `max_depth`: 3
- `min_samples_leaf`: 8
- `loss`: huber

### Validation Performance

5-Fold Cross-Validation RMSE:

0.13059

The final model was trained on the complete training dataset and used to generate predictions for the Kaggle test dataset.
