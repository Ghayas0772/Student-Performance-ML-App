# Student Performance Predictor

Predict a student's race/ethnicity group based on academic performance using a Random Forest Classifier.

This machine learning project uses three academic scores to predict a student's race/ethnicity category. The project includes data preprocessing, model training, evaluation, model persistence, and a Flask web application for interactive predictions.

##  Features

* Random Forest Classification Model
* Data preprocessing and feature scaling
* Label encoding for target classes
* Interactive Flask web application
* Model persistence using Pickle (`.pkl`)
* Reproducible machine learning workflow
* Docker deployment support

## Project Overview

The model predicts a student's race/ethnicity group using the following academic scores:

### Input Features

* Math Score
* Reading Score
* Writing Score

### Target Variable

* Race/Ethnicity Group

Possible classes:

* Group A
* Group B
* Group C
* Group D
* Group E

## Project Structure

```plaintext
Student-performance/
│
├── model/
│   ├── model.pkl                 # Trained Random Forest model
│   ├── scaler.pkl                # Feature scaler
│   └── label_encoder.pkl         # Label encoder
│
├── templates/
│   └── index.html                # Flask application UI
│
├── app.py                        # Flask web application
├── StudentsPerformance.csv       # Dataset
├── StudentPerformance_EDA.ipynb  # Exploratory Data Analysis
├── requirements.txt              # Python dependencies
├── Dockerfile                    # Docker deployment
├── .gitignore
└── README.md
```

##  Data Preprocessing

The following preprocessing techniques were applied:

### Feature Scaling

Numeric features were standardized using:

```python
from sklearn.preprocessing import StandardScaler

scaler = StandardScaler()
```

### Label Encoding

Target labels were encoded using:

```python
from sklearn.preprocessing import LabelEncoder

encoder = LabelEncoder()
```

### Train-Test Split

The dataset was divided into:

* 80% Training Data
* 20% Testing Data

Using stratified sampling to maintain class distribution.

---

##  Model Development

### Algorithm

The model was trained using:

```python
from sklearn.ensemble import RandomForestClassifier

model = RandomForestClassifier()
```

### Why Random Forest?

* Handles nonlinear relationships
* Reduces overfitting through ensemble learning
* Works well on structured tabular data
* Provides strong baseline performance

---

##  Setup Instructions

### 1. Clone Repository

```bash
git clone https://github.com/Ghayas0772/Student-performance.git
cd Student-performance
```

### 2. Create Virtual Environment

```bash
python -m venv venv
```

---

### 3. Activate Environment

#### Windows

```bash
venv\Scripts\activate
```

#### Mac/Linux

```bash
source venv/bin/activate
```

---

### 4. Install Dependencies

```bash
pip install -r requirements.txt
```

---

## ▶️ Run the Application

Start the Flask application:

```bash
python app.py
```

Open your browser:

```text
http://127.0.0.1:5000/
```

---

## 🌐 Web Application

The Flask application provides:

* Score input form
* Prediction results
* Simple user interface
* Real-time model inference

Components:

* Flask Backend
* HTML Frontend
* Trained Model
* Feature Scaler
* Label Encoder

---

## 💻 Using the Model in Python

```python
import pickle
import numpy as np

# Load model
with open("model/model.pkl", "rb") as f:
    model = pickle.load(f)

# Load scaler
with open("model/scaler.pkl", "rb") as f:
    scaler = pickle.load(f)

# Load encoder
with open("model/label_encoder.pkl", "rb") as f:
    encoder = pickle.load(f)

# Sample input
sample = np.array([[72, 80, 75]])

# Scale features
sample_scaled = scaler.transform(sample)

# Predict
prediction = model.predict(sample_scaled)

# Decode class label
result = encoder.inverse_transform(prediction)

print(result)
```

---

## 📈 Model Performance

### Test Accuracy

```text
32%
```

### Interpretation

The relatively low accuracy is expected because predicting race/ethnicity solely from academic scores is inherently difficult.

Academic performance alone is not a strong indicator of demographic characteristics.

---

## 📋 Classification Report

| Class   | Precision | Recall | F1-Score | Support |
| ------- | --------- | ------ | -------- | ------- |
| Group A | 0.17      | 0.06   | 0.08     | 18      |
| Group B | 0.23      | 0.21   | 0.22     | 38      |
| Group C | 0.33      | 0.39   | 0.36     | 64      |
| Group D | 0.37      | 0.44   | 0.40     | 52      |
| Group E | 0.32      | 0.25   | 0.28     | 28      |

---

## 📊 Confusion Matrix

```text
[[ 1  3  7  5  2]
 [ 2  8 15  9  4]
 [ 2 10 25 20  7]
 [ 0  7 20 23  2]
 [ 1  7  8  5  7]]
```

---

## 🔍 Exploratory Data Analysis

The notebook `StudentPerformance_EDA.ipynb` contains:

* Dataset exploration
* Data cleaning
* Feature analysis
* Visualizations
* Correlation analysis
* Model training experiments
* Performance evaluation

---

## 📝 Notes

* `.pkl` files are binary serialized machine learning artifacts.
* Download model files directly from GitHub before loading.
* The dataset is included for reproducibility.
* Docker deployment is supported.
* Can be deployed to Azure App Service, Heroku, Render, or Railway.

---

## 🧰 Technologies Used

* Python
* Pandas
* NumPy
* Scikit-Learn
* Random Forest Classifier
* Flask
* Pickle
* Jupyter Notebook
* Docker

---

## 🚀 Future Improvements

* Hyperparameter tuning
* Cross-validation
* Model comparison (XGBoost, SVM, Logistic Regression)
* Streamlit dashboard
* Cloud deployment
* User authentication
* Predict academic outcomes instead of demographic attributes

---

## 👨‍💻 Author

**Ghayasudin Ghayas**

MS Data Science | AI & Machine Learning Enthusiast

Data Scientist | Machine Learning Engineer

Azure AI & Generative AI Practitioner

---

## 📄 License

This project is intended for educational, research, and learning purposes.

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

