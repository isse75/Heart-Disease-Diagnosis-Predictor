# 🫀 Heart Disease Diagnosis Predictor

A machine learning project that predicts heart disease risk using clinical data from the UCI Cleveland Heart Disease dataset. This end-to-end ML solution includes data analysis, model training, and deployment via Docker and cloud services.

*An end-to-end machine learning solution for heart disease prediction using clinical indicators and streamlined deployment.*

---

## 🚀 Quick Start

### 📍 Live Demo

**Streamlit App**: [https://heart-disease-predictor-75.streamlit.app/](https://heart-disease-predictor-75.streamlit.app/)

### Run Locally

```bash
# Clone and setup
git clone https://github.com/isse75/ML_Zoomcamp.git
cd ML_Zoomcamp/midterm-project
pip install pipenv
pipenv install --dev
pipenv shell

# Run Jupyter notebooks (optional)
jupyter lab

# Streamlit app
cd streamlit_app/
streamlit run streamlit_app.py
```

### Docker Deployment

```bash
# Pull image
docker pull issedugou/heart_disease:latest

# Run container
docker run -p 9696:9696 issedugou/heart_disease:latest

# Or build from source
cd app/
docker build -t heart-disease-api .
docker run -p 9696:9696 heart-disease-api
```

---

## 📄 Table of Contents

* [📌 Problem Statement](#problem-statement)
* [🎯 Project Goals](#project-goals)
* [📊 Dataset Information](#dataset-information)
* [📁 Project Structure](#project-structure)
* [⚙️ Setup and Installation](#setup-and-installation)
* [🔍 Exploratory Data Analysis](#exploratory-data-analysis)
* [🤖 Model Training & Evaluation](#model-training--evaluation)
* [🚀 Deployment](#deployment)
* [📈 Results](#results)
* [👤 Author](#author)
* [📄 License](#license)

---

## 📌 Problem Statement

Heart disease remains the leading cause of death in the UK. Many of these deaths are preventable through early diagnosis. However, existing diagnostic tests are costly and underutilised. This project investigates whether routine clinical data collected by GPs can be used to build a predictive model for early risk assessment.

Using the Cleveland Clinic dataset of 303 patients, this project builds a model to analyse medical indicators such as age, cholesterol, chest pain, and blood pressure to predict heart disease risk.

---

## 🎯 Project Goals

* 🔍 Conduct exploratory data analysis (EDA)
* 🫠 Train and evaluate ML models (focus on Logistic Regression)
* 📅 Containerise the API with Docker
* 👥 Create Streamlit frontend for user interaction
* 📃 Ensure reproducibility and portability across environments

---

## 📊 Dataset Information

### 🔹 Source

* [UCI Heart Disease Dataset](https://archive.ics.uci.edu/dataset/45/heart+disease)

### 🔹 Overview

* 303 patients from the Cleveland Clinic
* 14 clinical attributes (subset from original 76)
* Binary target: heart disease present (1) or not (0)

### 🔹 Key Features

* **Demographics**: Age, sex
* **Symptoms**: Chest pain type, exercise-induced angina
* **Vitals**: Resting blood pressure, maximum heart rate
* **Lab Results**: Cholesterol, fasting blood sugar
* **Diagnostics**: ECG, ST depression, thalassemia, vessel fluoroscopy

### 🔹 Target Variable

* `0`: No heart disease
* `1`: Heart disease present (binarised)

---

## 📁 Project Structure

```
.
├── data/                    # Data files
│   └── Heart_disease_cleveland_new.csv
├── images/                   # Visualisation assets
├── streamlit_frontend/       # Streamlit frontend
│   ├── .streamlit/           # Config and secrets
│   │   ├── config.toml
│   │   └── secrets.toml
│   ├── requirements.txt
│   └── streamlit_app.py
├── Notebook.ipynb            # EDA and model training
├── Train.ipynb               # Alternative or legacy notebook
├── train.py                  # Training script
├── predict.py                # Inference script
├── predict-test.py           # Test predictions script
├── model_C=1.0.bin           # Trained model artefact
├── Dockerfile                # Docker image definition
├── Pipfile                   # Pipenv dependency file
├── Pipfile.lock              # Pipenv lock file
├── .gitignore
└── README.md
```

---

## ⚙️ Setup and Installation

### Prerequisites

* Python 3.12+
* Docker
* Git

### Environment Setup

```bash
# Clone repository
cd ML_Zoomcamp/midterm-project
pip install pipenv
pipenv install --dev
pipenv shell
```

### Jupyter Notebook

```bash
jupyter lab
```

### Streamlit App

```bash
cd streamlit_app/
streamlit run streamlit_app.py
```

### Docker

```bash
cd app/
docker build -t heart-disease-api .
docker run -p 9696:9696 heart-disease-api
```

---

## 🔍 Exploratory Data Analysis

The dataset is relatively balanced in terms of the target classes. Key observations from the exploratory phase include:

* **Chest pain type** is a strong categorical predictor
* **Age** and **maximum heart rate** are key continuous features
* No severe class imbalance is present

Correlation and feature distribution analyses revealed that chest pain type, age, and thalassemia have a notable relationship with heart disease status.

---

## 🤖 Model Training & Evaluation

### Process

* Train/val/test split: 60/20/20
* Categorical: One-Hot Encoding via DictVectorizer
* Model: Logistic Regression with hyperparameter tuning
* Evaluation: AUC, accuracy, precision, recall, F1

### Hyperparameter Tuning

* KFold Cross-validation used for reliable evaluation
* Tested C values from 0.001 to 1000
* **C = 1** yielded the best average performance

### Threshold Selection

* **0.39** selected as optimal threshold for accuracy

---

## 🚀 Deployment

### Streamlit Frontend

* Real-time predictions
* Hosted on Streamlit Cloud

### Flask API Backend

* Containerised REST API
* Deployed via AWS Elastic Beanstalk

```bash
# Docker image info
issedugou/heart-disease-api:latest
```

---

## 📈 Results

Final model performance on the test set:

* Accuracy: 0.85
* ROC AUC: 0.9222
* Precision: 0.83
* Recall: 0.91
* F1 Score: 0.87

**Key insight**: Logistic Regression performed well with stable results. Model confidence is strongest around chest pain, thalassemia type, and age.

---

## 👤 Author

**Isse Dugou**

* GitHub: [@isse75](https://github.com/isse75)
* LinkedIn: [Isse Dugou](https://linkedin.com/in/issedugou)
* Email: [isse.dugou@outlook.com](mailto:isse.dugou@outlook.com)

---

## 📄 License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.
