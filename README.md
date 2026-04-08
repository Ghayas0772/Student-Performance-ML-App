# Student Performance Predictor

Predict a student’s race/ethnicity based on their academic scores using a Random Forest classifier.

---

## Project Overview

This project trains a Random Forest classifier to predict a student’s race/ethnicity using three academic scores:

* `math score`
* `reading score`
* `writing score`

The model is trained on the `StudentsPerformance.csv` dataset and includes preprocessing, scaling, and label encoding.  
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
* StudentsPerformance.csv# Dataset
* StudentPerformance_EDA.ipynb # Exploratory Data Analysis
* requirements.txt       # Python dependencies
* Dockerfile             # Optional Docker deployment
* README.md              # Project documentation


---

## Preprocessing Steps

- StandardScaler applied to numeric features
- LabelEncoder applied to target variable
- Train/test split (80/20) with stratification

---

## How to Run

### 1. Clone Repository
```bash
git clone https://github.com/Ghayas0772/Student-performance.git
cd Student-performance

### 2. Install Dependencies
pip install -r requirements.txt

### 3. Run Flask App
python app.py

Then open your browser at http://127.0.0.1:5000/ to interact with the model.

Using the Model in Python

### Model Performance

The Random Forest classifier was trained using the three scores to predict race/ethnicity.

Test Accuracy: 32%

This low accuracy is expected because predicting a student’s race/ethnicity from only three scores is challenging.

### Classification Report:
| Class   | Precision | Recall | F1-score | Support |
| ------- | --------- | ------ | -------- | ------- |
| group A | 0.17      | 0.06   | 0.08     | 18      |
| group B | 0.23      | 0.21   | 0.22     | 38      |
| group C | 0.33      | 0.39   | 0.36     | 64      |
| group D | 0.37      | 0.44   | 0.40     | 52      |
| group E | 0.32      | 0.25   | 0.28     | 28      |

### Confusion Matrix:
[[ 1  3  7  5  2]
 [ 2  8 15  9  4]
 [ 2 10 25 20  7]
 [ 0  7 20 23  2]
 [ 1  7  8  5  7]]
 ***Note***: Full evaluation metrics, plots, and analysis are available in StudentPerformance_EDA.ipynb.
 ### Notes
.pkl files are binary; download them from GitHub and load in Python using pickle.
The dataset StudentsPerformance.csv is included for reproducibility.
The project can be deployed with Docker or hosted on Heroku.

