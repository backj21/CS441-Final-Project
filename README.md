# CS441 Final Project: Flight Status Prediction

This project aims to predict flight delays and cancellations using various machine learning algorithms. Focusing on five strategic hub airports in the Midwest/Great Lakes region, the project implements and compares Logistic Regression, Random Forest, Support Vector Machines (SVM), and XGBoost models to classify flight status.

## 📂 Project Structure

The project is organized into directories based on the machine learning model used:

* **`Logistic_Regression/`**: Contains the Logistic Regression implementation (`CS_441_Final_Project_Logistic_Regression_Model.ipynb`).
* **`Random_Forest/`**: Contains the Random Forest classifier implementation (`CS441 Final Project Random Forest.ipynb`).
* **`SVM/`**: Contains the Support Vector Machine implementation (`CS 441 SVM.ipynb`), including data sampling and hyperparameter tuning.
* **`XGBoost/`**: Contains data curation scripts (`Data_Collection_&_Curation.ipynb`) and the modeling/evaluation notebook (`2_Modelling_and_Evaluation.ipynb`) which includes advanced feature engineering.

## 📊 Dataset

The project utilizes flight reporting data (e.g., `T_ONTIME_REPORTING.csv`), filtered to focus on flights originating from or destined for specific hub airports:
* **ORD** (O'Hare International Airport)
* **MDW** (Midway International Airport)
* **MKE** (Milwaukee Mitchell International Airport)
* **DTW** (Detroit Metropolitan Wayne County Airport)
* **MSP** (Minneapolis–Saint Paul International Airport)

**Target Variable:** `Flight_Status`
* **0:** On-Time
* **1:** Delayed (>15 minutes)
* **2:** Cancelled

## 🛠️ Methodology

### Data Preprocessing & Feature Engineering
* **Filtering:** Data is restricted to the 5 target airports.
* **Cleaning:** Removal of duplicate entries and handling missing values.
* **Feature Engineering:**
    * **Cyclical Time Encoding:** Departure times converted to Sine/Cosine components to preserve temporal relationships.
    * **Lagged Features:** Creation of features like `Lagged_Bad_Weather_or_Late_Air` and `Lagged_Failure_Rate` to capture delay propagation from previous flights.
* **Encoding:** Use of One-Hot Encoding and Target Encoding for categorical variables (Carrier, Origin, Destination).

### Models Implemented

1.  **Logistic Regression**
    * Used as a baseline model.
    * Solver: `saga`, Multi-class: `multinomial`.
    * **Performance:** ~80% Accuracy.

2.  **Random Forest**
    * Ensemble learning method using 200 estimators.
    * **Performance:** ~84.7% Validation Accuracy.

3.  **Support Vector Machine (SVM)**
    * Utilizes an RBF kernel with class balancing.
    * Includes hyperparameter tuning (GridSearchCV) for `C` and `gamma`.
    * **Performance:** ~66-68% Accuracy.

4.  **XGBoost**
    * Gradient boosting classifier with extensive hyperparameter search (comparing low complexity, optimal balance, high complexity, etc.).
    * **Performance:** Weighted F1-Score of ~0.70 (High Complexity model).

## 📈 Results Summary

| Model | Accuracy / F1-Score | Key Findings |
| :--- | :--- | :--- |
| **Logistic Regression** | ~80.0% Acc | Good baseline, struggles with minority classes. |
| **Random Forest** | ~84.7% Acc | Strong performance, handles non-linearities well. |
| **SVM** | ~66-68% Acc | Computationally expensive; required sampling (50k rows). |
| **XGBoost** | ~0.70 (Weighted F1) | Robust performance with advanced feature engineering. |

***
