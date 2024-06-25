# Cassandra-24
Data Science Event UDYAM'24


# Obesity Prediction

Obesity has become a global health crisis with significant implications for individuals' well-being and healthcare systems worldwide. Identifying individuals at risk of obesity and understanding the contributing factors are crucial steps in prevention and intervention strategies. This project aims to predict whether a person is on the verge of obesity based on various personal and lifestyle details.

## Table of Contents

- [Problem Statement]
- [Data Description]
- [Approach]
  - [1. Libraries Import]
  - [2. Data Cleaning]
  - [3. Exploratory Data Analysis (EDA)]
  - [4. Feature Engineering]
  - [5. Model Building]
  - [6. Model Tuning]
  - [7. Final Prediction]
- [Results]


## Problem Statement

Predict whether a person is on the verge of obesity based on various attributes such as age, height, weight, lifestyle habits, and more. The evaluation metric for the predictions is the F1 score.

## Data Description

The dataset consists of the following files:
- train.csv: The training set.
- test.csv: The test set.
- sample_submission.csv: A sample submission file in the correct format.

### Columns in the Dataset

- id: Identifier for each unique sample in the dataset.
- uid: Unique identifier for each sample in the dataset.
- Location: Area of person's residence.
- Gender: Gender of the person.
- Age: Age of the person.
- Height: Height of the person.
- Weight: Weight of the person.
- SMOKE: Boolean value indicating whether a person smokes or not.
- Water: Person's water intake levels.
- Hash: Unknown field.
- FHO: Family history of obesity.
- CHCF: Consumption of high-calorie food.
- CV: Consumption of vegetables.
- NCP: Number of main meals.
- CBC: Consumption of beverages with caloric value.
- CAEC: Consumption of food between meals.
- CA: Consumption of alcohol.
- FAF: Physical activity frequency.
- TI: Time spent on the Internet.
- Mode: Person's mode of transport.
- Obesity_level: Target variable.

## Approach

### 1. Libraries Import

Import necessary libraries for data manipulation, visualization, and model building.

### 2. Data Cleaning

- Dropped uid and Hash columns as they are unique for every row.
- Checked for duplicate rows (none found).
- Converted Weight column from object to float.
- Handled missing values in Height, Weight, FHO, CAEC, TI columns:
  - Filled Weight and Height with their mean values.
  - Filled FHO and CAEC with their mode values.
  - Converted CAEC and CA values of 0 to 'Never'.
  - Filled TI with its mean value.
- Corrected negative values in NCP and Water columns by converting them to positive values.

### 3. Exploratory Data Analysis (EDA)

Performed univariate analysis on each column to understand their distributions and identify any anomalies.

### 4. Feature Engineering

- Detected and removed outliers in Age and Height columns.
- Encoded the target variable Obesity_level.
- Initially used one-hot encoding for categorical variables, but switched to target encoding due to a large number of columns.
- Added BMI column calculated using Height and Weight.

### 5. Model Building

- Standardized the data using StandardScaler.
- Tried various models, with XGBoost giving the best results.

### 6. Model Tuning

Fine-tuned the hyperparameters of the XGBoost model using Optuna.

### 7. Final Prediction

Made final predictions on the test set and prepared the submission file in the required format.

## Results

- Final F1 Score: 90.27
- Ranked among the top 5 teams in the competition.

