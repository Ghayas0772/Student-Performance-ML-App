# Student Performance Predictor

Predict student race/ethnicity based on their academic scores using Machine Learning.

## Project Overview

This project trains a Random Forest classifier to predict a student’s race/ethnicity based on three scores:

- Math Score
- Reading Score
- Writing Score

The model is trained on the StudentsPerformance.csv dataset and includes preprocessing, scaling, and label encoding.

A Flask app is included for interactive predictions using the saved model artifacts.
---
## Folder Structure
Student-performance/
* model/
  * model.pkl            # Trained Random Forest model
  * scaler.pkl           # Scaler for input features
  * label_encoder.pkl    # Label encoder for target variable
* templates/
  * index.html           # Flask app HTML template
* app.py                 # Flask app to serve predictions
* StudentsPerformance.csv  # Dataset
* StudentPerformance_EDA.ipynb # Exploratory Data Analysis
* requirements.txt       # Python dependencies
* Dockerfile             # Optional Docker deployment
* README.md              # Project documentation
---------
## How to Run

### 1. Clone Repository

```bash
git clone https://github.com/Ghayas0772/Student-performance.git
cd Student-performance
------
## 4. Using the Model in Python
import pickle
import numpy as np

# Load saved artifacts
with open("model/model.pkl", "rb") as f:
    model = pickle.load(f)
with open("model/scaler.pkl", "rb") as f:
    scaler = pickle.load(f)
with open("model/label_encoder.pkl", "rb") as f:
    le = pickle.load(f)
--------
# Example input: math, reading, writing scores
example = np.array([[80, 85, 90]])
example_scaled = scaler.transform(example)
pred_group = le.inverse_transform(model.predict(example_scaled))
print("Predicted race/ethnicity:", pred_group[0])
------
## Model Performance

The Random Forest classifier achieved around 32% test accuracy. The low accuracy is due to the difficulty of predicting multi-class labels (race/ethnicity) from only three scores.

Full evaluation metrics, confusion matrix, and analysis are available in StudentPerformance_EDA.ipynb.

##Notes
- .pkl files are binary; clicking them in GitHub will download the file. Load them in Python using pickle.
- Dataset is included (StudentsPerformance.csv) for reproducibility.
- The project can be deployed with Docker or hosted on Heroku using app.py.
