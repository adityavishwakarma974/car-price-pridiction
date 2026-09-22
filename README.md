# 🚗 Car Price Prediction Using Machine Learning

A beginner-friendly **Machine Learning regression project** that predicts the selling price of a used vehicle based on historical CarDekho vehicle listings.

The project demonstrates an end-to-end machine learning workflow including data cleaning, exploratory data analysis, preprocessing, model training, model comparison, evaluation, model persistence, and sample price prediction.

> **Note:** This project is intended for educational purposes. The predictions are estimates based on a small historical dataset and should not be considered professional vehicle appraisals or current market prices.

---

## 📌 Project Overview

Used-vehicle prices can vary depending on factors such as model year, reference price, kilometres driven, fuel type, seller type, transmission, and previous ownership.

This project uses these features to predict the **Selling Price** of a vehicle using regression algorithms.

The project compares:

* **Linear Regression**
* **Random Forest Regressor**

After evaluation on a held-out test set, Linear Regression achieved the better performance on this particular dataset split.

---

## 🎯 Objectives

* Understand and clean the vehicle dataset
* Perform Exploratory Data Analysis (EDA)
* Identify relationships between vehicle features and selling price
* Handle numerical and categorical features
* Apply preprocessing without data leakage
* Train multiple regression models
* Compare model performance
* Evaluate models using standard regression metrics
* Save the trained machine learning pipeline
* Demonstrate prediction on a sample vehicle

---

## 📊 Dataset

The project uses the **Vehicle Dataset from CarDekho**, a commonly used 301-record used-vehicle dataset.

The dataset contains **301 historical records** and includes both cars and some motorcycles, so the term *vehicle* is used where appropriate.

### Dataset Features

| Feature         | Description                         |
| --------------- | ----------------------------------- |
| `Year`          | Vehicle model year                  |
| `Present_Price` | Reference/ex-showroom price in lakh |
| `Kms_Driven`    | Distance driven in kilometres       |
| `Fuel_Type`     | Petrol, Diesel or CNG               |
| `Selling_Type`  | Dealer or Individual seller         |
| `Transmission`  | Manual or Automatic                 |
| `Owner`         | Number of previous owners           |
| `Selling_Price` | Target selling price in lakh        |

`Car_Name` is excluded from the compact machine learning model.

### Dataset Source

The dataset is commonly distributed as the **Vehicle Dataset from CarDekho**.

---

## 🛠️ Technologies Used

| Category             | Technology          |
| -------------------- | ------------------- |
| Programming Language | Python              |
| Environment          | Jupyter Notebook    |
| Data Manipulation    | Pandas, NumPy       |
| Data Visualization   | Matplotlib, Seaborn |
| Machine Learning     | Scikit-learn        |
| Model Persistence    | Joblib              |

---

## 🤖 Machine Learning Models

### 1. Linear Regression

Linear Regression is used as a simple baseline model for predicting the continuous `Selling_Price` target.

### 2. Random Forest Regressor

Random Forest combines multiple decision trees and can model nonlinear relationships between vehicle features and price.

Both models use a Scikit-learn preprocessing pipeline.

---

## 🔄 Project Workflow

```text
Dataset
   ↓
Data Inspection
   ↓
Data Cleaning
   ↓
Exploratory Data Analysis
   ↓
Feature Selection
   ↓
Train/Test Split
   ↓
Data Preprocessing
   ↓
Model Training
   ↓
Model Evaluation
   ↓
Model Comparison
   ↓
Best Model Selection
   ↓
Price Prediction
   ↓
Model Persistence
```

---

## 🧹 Data Preprocessing

The project uses an **80/20 train-test split** with `random_state=42`.

After removing exact duplicate records:

* **239 rows** were used for training
* **60 rows** were used for testing

### Numerical Features

Missing numerical values are handled using **median imputation**.

### Categorical Features

Categorical features are processed using:

* Most-frequent imputation
* One-Hot Encoding
* `handle_unknown="ignore"`

All preprocessing steps are included inside the machine learning pipeline to help prevent preprocessing leakage.

---

## 📈 Exploratory Data Analysis

The project includes visualizations to explore:

* Selling price distribution
* Relationship between model year and selling price
* Relationship between reference price and selling price
* Kilometres driven
* Fuel type
* Transmission
* Other price-related patterns

The analysis shows a positive association between `Present_Price` and `Selling_Price`, while the selling-price distribution is right-skewed.

These observations describe the dataset and should not be interpreted as causal relationships.

---

## 📊 Model Evaluation

The models were evaluated using:

* **MAE** — Mean Absolute Error
* **MSE** — Mean Squared Error
* **RMSE** — Root Mean Squared Error
* **R² Score**

### Results

| Model             | MAE (lakh) | MSE (lakh²) | RMSE (lakh) |         R² |
| ----------------- | ---------: | ----------: | ----------: | ---------: |
| Linear Regression | **1.4729** |  **6.3708** |  **2.5240** | **0.7528** |
| Random Forest     |     1.4971 |     12.7285 |      3.5677 |     0.5061 |

Based on this particular 80/20 holdout split, **Linear Regression produced the lower RMSE and higher R²**, so it was used as the selected model.

The results are specific to this dataset and split; the dataset is relatively small and historical.

---

## 🔮 Sample Prediction

The notebook demonstrates a prediction using the following sample vehicle:

| Feature         | Value     |
| --------------- | --------- |
| Year            | 2015      |
| Present Price   | ₹8.0 lakh |
| Kms Driven      | 30,000 km |
| Fuel Type       | Petrol    |
| Selling Type    | Dealer    |
| Transmission    | Manual    |
| Previous Owners | 0         |

### Predicted Selling Price

**₹5.29 lakh**

This prediction is generated by the trained machine learning pipeline.

---

## 💾 Model Persistence

The trained pipeline is saved using **Joblib**:

```text
car_price_model.pkl
```

This allows the trained preprocessing and model pipeline to be reused without retraining from scratch.

---

## 📁 Project Structure

```text
Car-Price-Prediction/
│
├── AdityaVishwakarma_CarPricePrediction.ipynb
├── AdityaVishwakarma_CarPricePrediction_ProjectReport.docx
├── car_data.csv
├── car_price_model.pkl
├── requirements.txt
├── README.md
└── figures/
```

---

## ⚙️ Installation

Clone the repository:

```bash
git clone https://github.com/YOUR_USERNAME/Car-Price-Prediction.git
cd Car-Price-Prediction
```

Install the required Python libraries:

```bash
pip install -r requirements.txt
```

---

## ▶️ How to Run

Start Jupyter Notebook:

```bash
jupyter notebook
```

Open:

```text
AdityaVishwakarma_CarPricePrediction.ipynb
```

Make sure `car_data.csv` is in the same directory as the notebook.

Run the notebook cells from top to bottom.

The notebook will:

1. Load the dataset
2. Clean the data
3. Perform EDA
4. Preprocess features
5. Split the data
6. Train Linear Regression
7. Train Random Forest
8. Compare model performance
9. Generate evaluation visualizations
10. Make a sample prediction
11. Save the trained model

---

## 🚀 Future Improvements

* Add a larger and more recent vehicle dataset
* Include vehicle make and model
* Include location/city
* Include vehicle condition and service history
* Apply cross-validation
* Perform hyperparameter tuning
* Compare Gradient Boosting models
* Build an interactive **Streamlit** application
* Deploy the prediction model as a web application
* Monitor model performance on new vehicle listings

---

## ⚠️ Limitations

This project uses a relatively small historical dataset of **301 records**. The dataset also contains some motorcycles in addition to cars.

Therefore:

* Model performance may change with a different train/test split
* Predictions may not represent current market prices
* Results should not be generalized to the entire used-car market
* Predictions should be treated as educational estimates rather than professional valuations

---

## 📚 References

* Vehicle Dataset from CarDekho — Kaggle
* Scikit-learn Documentation
* Pandas Documentation
* Public CSV mirror used for the dataset

---

## 👨‍💻 Author

**Aditya Vishwakarma**

**Data Analytics | Python | SQL | Power BI | Machine Learning**

---

⭐ If you found this project useful, consider giving the repository a star!

