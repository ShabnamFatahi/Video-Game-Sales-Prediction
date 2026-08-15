# Video Game Sales Prediction Using Machine Learning

## Overview

This project focuses on predicting video game sales using machine learning regression models.

The project follows a complete machine learning workflow, including data cleaning, exploratory data analysis, feature engineering, categorical encoding, model training, hyperparameter tuning, model evaluation, and model interpretation.

The final model was selected by comparing multiple regression algorithms based on MAE, RMSE, and R².

---

## Objective

The main objective of this project is to predict video game sales based on information available about each game.

The features used for modeling include:

- Console / Platform
- Genre
- Publisher
- Developer
- Release Year

The target variable is total game sales, which was log-transformed to reduce the effect of extreme values and the strong right-skewness of the original sales distribution.

---

## Dataset

The dataset contains information about video games, including their platform, genre, publisher, developer, release date, and sales.

The target variable used in this project is:

total_sales

A logarithmic transformation was applied:

log_total_sales = log1p(total_sales)

Rows with missing target values were removed before modeling.

---

## Data Preprocessing

The following preprocessing steps were performed:

- Removed observations with missing target values
- Selected relevant features for modeling
- Converted release dates into release_year
- Removed observations with missing release years
- Analyzed missing values
- Handled remaining missing categorical values
- Removed extremely rare genre categories
- Applied logarithmic transformation to total sales
- Encoded categorical variables for machine learning

### Encoding

Frequency Encoding was applied to:

- Publisher
- Developer

One-Hot Encoding was applied to:

- Console / Platform
- Genre

---

## Exploratory Data Analysis

Exploratory analysis was performed to investigate:

- The distribution of video game sales
- Sales across different genres
- The presence of rare categories
- The effect of the log transformation
- Feature relationships and distributions

The analysis showed that total sales were highly right-skewed, which motivated the use of a logarithmic transformation.

---

## Machine Learning Models

Five regression models were trained and evaluated:

1. Linear Regression
2. Decision Tree Regressor
3. Random Forest Regressor
4. XGBoost Regressor
5. Tuned XGBoost Regressor

The models were evaluated on a held-out test set.

---

## Model Evaluation

The following metrics were used:

- MAE (Mean Absolute Error): measures the average absolute difference between actual and predicted values.
- RMSE (Root Mean Squared Error): gives greater weight to larger prediction errors.
- R² (R-squared): measures the proportion of variance in the target explained by the model.

### Results

| Model | MAE | RMSE | R² |
|---|---:|---:|---:|
| Linear Regression | 0.1905 | 0.2943 | 0.1487 |
| Decision Tree | 0.1927 | 0.3402 | -0.1376 |
| Random Forest | 0.1560 | 0.2586 | 0.3426 |
| XGBoost | 0.1600 | 0.2595 | 0.3380 |
| Tuned XGBoost | 0.1533 | 0.2495 | 0.3881 |

### Best Model

Tuned XGBoost achieved the best overall performance.

It obtained:

- MAE: 0.1533
- RMSE: 0.2495
- R²: 0.3881

Based on these evaluation metrics, Tuned XGBoost was selected as the final model.

---

## Model Interpretation

Feature importance and SHAP analysis were used to interpret the final Tuned XGBoost model.

### Top Features

The most important features included:

| Feature | Importance |
|---|---:|
| console_PS4 | 0.0854 |
| console_XOne | 0.0670 |
| console_PC | 0.0620 |
| console_PS2 | 0.0443 |
| console_PS3 | 0.0429 |
| console_X360 | 0.0425 |
| console_PS | 0.0392 |
| genre_Shooter | 0.0343 |
| publisher_freq | 0.0315 |
| genre_Adventure | 0.0310 |

SHAP analysis was also used to examine how individual features contributed to model predictions.

---

## Final Model Evaluation

The final Tuned XGBoost model was further evaluated using:

- Actual vs. Predicted plots
- Residual distribution
- Feature importance
- SHAP summary analysis

The actual-versus-predicted plot shows that the model captures general patterns in the target variable, although prediction errors increase for some high-sales observations.

The residual distribution is concentrated around zero, while showing some asymmetry and a positive tail.

---

## Limitations

Several limitations should be considered:

- The dataset contains missing values in several variables.
- Video game sales are strongly skewed, requiring a logarithmic transformation.
- The final model explains approximately 38.8% of the variance in the transformed target.
- The dataset does not include potentially important commercial variables such as marketing expenditure, advertising budget, game price, or review scores.
- Frequency encoding represents publisher and developer frequency rather than their individual identities or characteristics.
- The model's performance is limited by the information available in the dataset.

---

## Technologies

- Python
- Pandas
- NumPy
- Matplotlib
- Seaborn
- Scikit-learn
- XGBoost
- SHAP
- Jupyter Notebook

---

## Project Structure

Video-Game-Sales-Prediction/

- VideoGameSales.ipynb
- README.md
- data/
  - vgchartz-2024.csv

## Conclusion

This project demonstrates a complete machine learning workflow for predicting video game sales.

Among the evaluated models, Tuned XGBoost achieved the best performance, outperforming the baseline regression and tree-based models according to MAE, RMSE, and R².

The results also demonstrate the usefulness of model interpretation techniques such as feature importance and SHAP for understanding the factors contributing to machine learning predictions.