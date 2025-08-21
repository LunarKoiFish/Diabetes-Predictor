🩺 Diabetes Predictor App
---
📌 Overview
---
This project predicts diabetes risk using logistic regression on a dataset of health indicators. The dataset includes over 250,000 records with demographic and health-related features.

The project has two main components:

Data Analysis & Modeling – Logistic regression with feature scaling and hyperparameter optimization.

Flask Web Application – An interactive web interface for users to input health data and receive real-time diabetes risk predictions.

🎯 Objectives
---
Build a logistic regression model to classify diabetes status (No diabetes, Pre-diabetic, Diabetic).

Evaluate model performance using accuracy, precision, recall, and confusion matrix.

Optimize model with feature scaling and hyperparameter tuning.

Deploy a Flask web app for interactive user input and prediction.

Provide a user-friendly interface with Bootstrap styling and real-time feedback.

🛠️ Tools & Technologies
---
Python – data processing and modeling

Flask – web application framework

Bootstrap – responsive front-end design

pandas / numpy – data manipulation

scikit-learn – logistic regression, scaling, evaluation metrics

SQLAlchemy / SQLite – querying dataset

joblib – saving and loading models

GitHub – version control and project documentation

📁 Dataset
---
Source: diabetes_health_indicators.db (SQLite database)

Key Features Used:

* HighBP, HighChol, CholCheck, BMI, Smoker, Stroke, HeartDiseaseorAttack

* PhysActivity, Fruits, Veggies, HvyAlcoholConsump, AnyHealthcare, NoDocbcCost

* GenHlth, MentHlth, PhysHlth, DiffWalk, Sex, Age, Education, Income

Target Variable:

* Diabetes_012

* 0: No diabetes

* 1: Pre-diabetic

* 2: Diabetic

🧹 Data Preparation Steps
---
Data Loading: Queried SQLite database using SQLAlchemy and loaded into a pandas DataFrame.

Feature Separation:

X: All features except Diabetes_012

y: Target variable Diabetes_012

Train-Test Split: Used train_test_split with random_state=42.

Scaling: Applied StandardScaler to improve model convergence.

📊 Model & Evaluation
---
Logistic Regression Model (Scaled Features):

Confusion Matrix:

[[52203     0  1275]
 [ 1090     0    89]
 [ 7196     0  1567]]


Accuracy: 0.85

Macro-average F1-score: 0.39

Feature Coefficients (Examples):

Feature	No diabetes	Pre-diabetic	Diabetic
HighBP	-0.397	0.075	0.323
BMI	-0.022	-0.004	0.026
HvyAlcoholConsump	0.452	-0.012	-0.440
GenHlth	-0.167	-0.094	0.261
⚙️ Hyperparameter Optimization
---
Tested C values: [1e-7, 1e-6, 1e-5, 1e-4, 0.001, 0.01, 0.1, 1, 10, 100, 1000]

Evaluated accuracy, precision, recall for each model version.

Stored results in data_model_optimization_results.

💻 Flask Web App
---
The web app allows users to input health data and receive a diabetes risk prediction:

Responsive design with Bootstrap

Input fields dynamically generated from model features (feature_details)

Form supports binary, scaled, and numeric inputs

Real-time prediction results displayed after submission

Reset Form button to clear all inputs

Screenshot of Form UI:
<img width="600" alt="Diabetes Web App Form" src="https://user-images.githubusercontent.com/yourusername/screenshots/diabetes_form.png">

Usage Example:

# Run the Flask app
export FLASK_APP=app.py
flask run


Open your browser at http://127.0.0.1:5000/

Enter health details and submit to get prediction

💾 Saving the Model
---
Final model and scaler saved with joblib:

joblib.dump((logi_model, scaler), 'Resources/diabetes_logi_regress_model.pkl')


Loading in Flask App:

model, scaler = joblib.load('Resources/diabetes_logi_regress_model.pkl')
new_data_scaled = scaler.transform(user_input)
prediction = model.predict(new_data_scaled)

🔗 Project Files
---
Resources/diabetes_health_indicators.db – Dataset

Resources/diabetes_logi_regress_model.pkl – Trained model & scaler

DiabetesPredictor.ipynb – Jupyter Notebook workflow

app.py – Flask web app

templates/index.html – Form UI with Bootstrap

data_model_optimization_results.csv – Hyperparameter optimization results

📜 License
---
This project is licensed under the MIT License. Feel free to use or adapt the work with proper attribution.

📬 Contact
---
For questions or collaborations:

📧 koifish.analytics@gmail.com

💼 [LinkedIn](https://www.linkedin.com/in/davidjian00/)
