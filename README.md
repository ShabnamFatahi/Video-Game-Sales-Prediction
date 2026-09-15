# Video Game Sales Prediction Using Machine Learning

## Overview

The project involves the use of machine learning regression models to predict video game sales.

The complete machine learning workflow is followed, comprising data cleaning, exploratory data analysis, feature engineering, categorical encoding, model training, hyperparameter tuning, model evaluation, and model interpretation.

The model that was ultimately chosen was determined by comparing a number of regression algorithms using MAE, RMSE, and R².

---

## Objective

This project's primary aim is to use the information available about each game to predict its sales.

The features used for modeling include:

- Console / Platform
- Genre
- Publisher
- Developer
- Release Year

The variable in question is total game sales, and in order to reduce the impact of the extreme values and the marked right skew of the original sales distribution it was subjected to a log transformation.

---

## Dataset

The information in the dataset relates to video games, listing their platform, genre, publisher, developer, release date, and sales.

The target variable used in this project is:

total_sales

A logarithmic transformation was applied:

log_total_sales = log1p(total_sales)

Before carrying out the modeling, any rows that had missing target values were deleted.

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

The analysis indicated that the total sales were highly right-skewed, which was the reason for applying a logarithmic transformation.

---

## Machine Learning Models

Five regression models were trained and evaluated:

1. Linear Regression
2. Decision Tree Regressor
3. Random Forest Regressor
4. XGBoost Regressor
5. Tuned XGBoost Regressor

The evaluation of the models used a test set that had been held back.

---

## Model Evaluation

The following metrics were used:

- The mean absolute error (MAE) is the average of the absolute differences between the actual and the predicted values.
- The Root Mean Squared Error (RMSE) places more weight on larger prediction errors.
- R², or R-squared, is a measure of the proportion of the variance in the target variable that is accounted for by the model.

### Results

| Model | MAE | RMSE | R² |
|---|---:|---:|---:|
| Linear Regression | 0.1905 | 0.2943 | 0.1487 |
| Decision Tree | 0.1927 | 0.3402 | -0.1376 |
| Random Forest | 0.1560 | 0.2586 | 0.3426 |
| XGBoost | 0.1600 | 0.2595 | 0.3380 |
| Tuned XGBoost | 0.1533 | 0.2495 | 0.3881 |

### Best Model

The Tuned XGBoost model achieved the best overall performance.

It obtained:

- MAE: 0.1533
- RMSE: 0.2495
- R²: 0.3881

The final model chosen was Tuned XGBoost, based on these evaluation metrics.

---

## Model Interpretation

The final Tuned XGBoost model was interpreted using feature importance and SHAP analysis.

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

SHAP analysis was likewise applied in order to examine the contribution of individual features to the model's predictions.

---

## Final Model Evaluation

The final Tuned XGBoost model was further evaluated using:

- Actual vs. Predicted
- Residual distribution
- Feature importance
- SHAP summary analysis

The Actual vs. Predicted plot shows that the model captures general patterns in the target variable, although prediction errors increase for some high-sales observations.

The distribution of the residuals is centred on zero, although it is a bit asymmetric and has a positive tail.

---

## Limitations

Several limitations should be considered:

- The dataset contains missing values in several variables.
- Video game sales are highly skewed, requiring a logarithmic transformation.
- The final model explains approximately 38.8% of the variance in the transformed target.
- The dataset does not include potentially important commercial variables such as marketing expenditure, advertising budget, game price, or review scores.
- Frequency encoding represents the frequency of publishers and developers rather than their individual identities or characteristics.
- Model performance is limited by the information available in the dataset.

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

This project provides a full machine learning workflow for forecasting video game sales.

Of all the models considered, Tuned XGBoost showed the best performance and thus exceeded the baseline regression and the tree-based models in terms of MAE, RMSE, and R².

The results also show how useful methods of interpreting models, such as feature importance and SHAP, are for understanding the various factors that contribute to machine learning predictions.
