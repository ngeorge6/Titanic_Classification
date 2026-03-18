Titanic Classification Pipeline

This notebook trains and evaluates a Logistic Regression model on the Titanic dataset using pipelines, column transformers, GridSearchCV, and cross-validation. Results are saved in an Excel file with multiple sheets.

Input Data
Training data: data/train.csv
1. Must include columns: PassengerId, Survived, Pclass, Sex, Age, Cabin, and other relevant features.
2. The Cabin column is processed to create a Deck feature.
3. The data can be obtained from Kaggle: Titanic - Machine Learning from Disaster

Preprocessing
Numeric features: Age → missing values imputed using median or mean (selected by GridSearchCV).
Categorical features: Pclass, Sex, Deck → missing values imputed as 'X' and one-hot encoded.
ColumnTransformer ensures numeric and categorical pipelines are applied correctly.
Remainder of columns are dropped.

Model
Logistic Regression with solver liblinear.
Hyperparameters tuned using GridSearchCV:
1. penalty: l1 or l2
2. Numeric imputer strategy: median or mean
Model evaluated using cross-validation (5-fold) and a validation split (20% of training data).

Output
Saved to data/Output_Titanic.xlsx with separate sheets:
1. Accuracy – Validation accuracy of the model.
2. Confusion_Matrix – Confusion matrix for the validation set.
3. Classification_Report – Detailed precision, recall, f1-score per class.
4. CV_Scores – Cross-validation scores for each fold.

Usage
Download the dataset from Kaggle and place train.csv in the data/ folder.
Run all cells in the notebook.
Check data/Output_Titanic.xlsx for model evaluation results.