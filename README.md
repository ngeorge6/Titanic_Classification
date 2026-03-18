# Titanic Classification Pipeline

## Overview
This notebook trains and evaluates a Logistic Regression model on the Titanic dataset using pipelines, column transformers, GridSearchCV, and cross-validation. Results are saved in an Excel file with multiple sheets.

## Input Data
- Training data: `data/train.csv`  
- Required columns: `PassengerId`, `Survived`, `Pclass`, `Sex`, `Age`, `Cabin`, and other relevant features  
- The `Cabin` column is processed to create a `Deck` feature  
- Dataset source: [Kaggle – Titanic: Machine Learning from Disaster](https://www.kaggle.com/c/titanic)

## Preprocessing
- Numeric features: `Age` → missing values imputed using median or mean (selected by GridSearchCV)  
- Categorical features: `Pclass`, `Sex`, `Deck` → missing values imputed as `'X'` and one-hot encoded  
- `ColumnTransformer` ensures numeric and categorical pipelines are applied correctly  
- Remainder of columns are dropped

## Model
- Logistic Regression with solver `liblinear`  
- Hyperparameters tuned using GridSearchCV:  
  - `penalty`: l1 or l2  
  - Numeric imputer strategy: median or mean  
- Model evaluated using 5-fold cross-validation and a validation split (20% of training data)

## Output
- Output file: `data/Output_Titanic.xlsx`  
- Separate sheets in the Excel file:  
  - `Accuracy` – Validation accuracy of the model  
  - `Confusion_Matrix` – Confusion matrix for the validation set  
  - `Classification_Report` – Precision, recall, f1-score per class  
  - `CV_Scores` – Cross-validation scores for each fold

## Usage
1. Download the dataset from Kaggle and place `train.csv` in the `data/` folder  
2. Run all cells in the notebook  
3. Check `data/Output_Titanic.xlsx` for model evaluation results

## Project Structure
```
project_folder
│
├── data
│   ├── train.csv
│   └── Output_Titanic.xlsx
│
├── Titanic_Classification_Pipeline.ipynb
└── README.md
```

## Requirements
- Python 3  
- Libraries: `pandas`, `numpy`, `scikit-learn`, `openpyxl`

Install dependencies:
```
pip install pandas numpy scikit-learn openpyxl
```
