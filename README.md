# Disaster Response Pipeline

## Project Overview

This project applies data engineering and machine learning to analyze disaster response messages. The goal is to build a model and a web application that classifies these messages into relevant categories, helping disaster relief agencies respond more efficiently.

You will work with real messages sent during disaster events. The system includes a machine learning pipeline for categorizing messages and a web app interface for emergency workers to input new messages and view classification results. The app also provides data visualizations to help understand message trends.

---

## Project Structure

The project is divided into three main components:

### 1. ETL Pipeline (`data/process_data.py`)

- **Loads** the `messages` and `categories` datasets.
- **Merges** the datasets into a single data frame.
- **Cleans** the data to prepare it for machine learning.
- **Saves** the cleaned data into a SQLite database for later use.

### 2. Machine Learning Pipeline (`models/train_classifier.py`)

- **Loads** data from the SQLite database.
- **Splits** the data into training and test sets.
- **Builds** a pipeline that processes text and applies machine learning algorithms.
- **Trains** and **optimizes** the model using GridSearchCV.
- **Evaluates** the model on a test set and reports results.
- **Exports** the trained model as a pickle file for deployment.

### 3. Flask Web App (`app/run.py`)

- Provides a **user interface** for emergency workers to enter new messages.
- **Predicts** message categories using the trained model.
- **Displays** classification results and data visualizations.

---

## How to Run the Project

Follow these steps to set up and run the project from scratch:

### 1. Data Cleaning

From the project directory, run:

```bash
python data/process_data.py data/disaster_messages.csv data/disaster_categories.csv data/DisasterResponse.db
```

- This command takes the raw data, cleans it, and stores it in a SQLite database (`DisasterResponse.db`).

### 2. Train the Classifier

After cleaning the data, train the model by running:

```bash
python models/train_classifier.py data/DisasterResponse.db models/classifier.pkl
```

- This trains the classifier and saves the model as a pickle file (`classifier.pkl`) in the `models` directory.
- Training may take a few minutes (approximately 4 minutes with grid search).

### 3. Start the Web App

Navigate to the `app` directory and run:

```bash
python run.py
```

- This starts the Flask web app.
- Access the app via the URL provided in your terminal to input messages and view results.

---

## Notes on Model Performance

- The data is **highly imbalanced**, meaning some categories are much more common than others.
- The model achieves **high accuracy (~0.94)**, but recall (its ability to find all relevant cases) is lower (~0.6).
- Exercise caution if using this model for real-world decision-making or production—high accuracy can be misleading with imbalanced data.

---

## Project Files Overview

```
.
├── app
│   ├── run.py                  # Flask app runner
│   ├── static/
│   │   └── favicon.ico         # Web app favicon
│   └── templates/
│       ├── go.html             # Classification result page
│       └── master.html         # Main page
├── data
│   ├── DisasterResponse.db      # SQLite database (cleaned data)
│   ├── disaster_categories.csv  # Raw data
│   ├── disaster_messages.csv    # Raw data
│   └── process_data.py          # ETL script
├── img                         # Visualization images
├── models
│   └── train_classifier.py      # ML pipeline script
```

---

## Software Requirements

- **Python 3.6.6**
- All necessary libraries are listed in `requirements.txt`.
- Uses standard libraries such as `collections`, `json`, `operator`, `pickle`, `pprint`, `re`, `sys`, `time`, and `warnings`.

---

## Summary

This project demonstrates the complete workflow for building a disaster response message classifier—from data cleaning to model training to deployment as a web app. You will gain experience in data engineering, machine learning, and web development, all with a focus on practical, real-world impact.