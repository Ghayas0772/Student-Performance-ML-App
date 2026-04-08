# Student Performance Predictor

Predict student race/ethnicity based on their academic scores using Machine Learning.

## Project Overview

This project trains a Random Forest classifier to predict a student’s race/ethnicity based on three scores:

Features used for prediction:
- math score
- reading score
- writing score
Target:
- race/ethnicity (group A–E)

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


Clarify dataset and features
You mention three scores: Math, Reading, Writing. It’s good to explicitly state:
Features used for prediction:
- math score
- reading score
- writing score
Target:
- race/ethnicity (group A–E)
Add preprocessing note
Since you scale features and label-encode the target, mention it briefly:
Preprocessing steps:
- StandardScaler applied to numeric features
- LabelEncoder applied to target variable
- Train/test split with stratification (80/20)
Model Performance Section
Include your exact results:
Model Performance:
- Random Forest Classifier (200 trees)
- Test accuracy: 32%
- Low accuracy due to predicting multi-class labels from only three features
- Full metrics and confusion matrix are in `StudentPerformance_EDA.ipynb`
Code snippets in Markdown
Use fenced code blocks with python for Python code:
```python
# Load saved artifacts
import pickle, numpy as np

with open("model/model.pkl", "rb") as f:
    model = pickle.load(f)
with open("model/scaler.pkl", "rb") as f:
    scaler = pickle.load(f)
with open("model/label_encoder.pkl", "rb") as f:
    le = pickle.load(f)

# Example input
example = np.array([[80, 85, 90]])
example_scaled = scaler.transform(example)
pred_group = le.inverse_transform(model.predict(example_scaled))
print("Predicted race/ethnicity:", pred_group[0])

6. **Minor typos / clarity**  
- “Hero” → likely you mean **Heroku** for hosting.  
- Consistently use `Student-performance` (with dash) instead of variations.  

---

If you want, I can **rewrite your full README in ready-to-paste Markdown**, fully structured with folders, instructions, model usage, and performance, so it’s clean and GitHub-ready.  

Do you want me to do that?
