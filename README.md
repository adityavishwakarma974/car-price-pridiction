# Car Price Prediction Using Machine Learning

## Project Overview

A beginner-friendly regression project that estimates a used vehicle's selling price from model year, reference price, distance driven, fuel type, seller type, transmission and previous-owner count. The supplied dataset and notebook run locally with relative paths.

## Problem Statement

Historical used-car listings contain different price and vehicle details. The project learns their relationship to provide an estimate that can support classroom demonstrations and explain how a basic prediction workflow works. Estimates are not appraisals and may not represent current market prices.

## Objectives

- Inspect and clean the provided data.
- Explore price patterns with labelled charts.
- Compare Linear Regression and Random Forest regression.
- Evaluate on a held-out test set and save the best complete pipeline.

## Dataset

The CSV is the 301-row CarDekho used-car dataset commonly distributed on Kaggle as [Vehicle dataset from CarDekho](https://www.kaggle.com/datasets/nehalbirla/vehicle-dataset-from-cardekho). This packaged copy was downloaded from a public [GitHub mirror CSV](https://raw.githubusercontent.com/RimjimRazdan/cars_price_prediction/master/car%20data.csv). The source file has 9 columns: `Car_Name`, `Year`, `Selling_Price`, `Present_Price`, `Kms_Driven`, `Fuel_Type`, `Seller_Type`, `Transmission`, and `Owner`. The notebook renames `Seller_Type` to `Selling_Type`, and excludes `Car_Name` from the compact model. Prices are in Indian rupees lakh; the data is historical and includes motorcycles as well as cars, so the word vehicle is also used in the report.

| Project feature | Meaning |
|---|---|
| `Year` | Model year |
| `Present_Price` | Reference or ex-showroom price in lakh |
| `Kms_Driven` | Distance driven, in kilometres |
| `Fuel_Type` | Petrol, Diesel or CNG |
| `Selling_Type` | Dealer or Individual seller |
| `Transmission` | Manual or Automatic |
| `Owner` | Previous-owner count |
| `Selling_Price` | Target selling price in lakh |

## Technologies Used

- Python
- Pandas
- NumPy
- Matplotlib
- Seaborn
- Scikit-learn
- Jupyter Notebook
- Joblib

## Machine Learning Models

- **Linear Regression:** simple baseline model for estimating a continuous price.
- **Random Forest Regressor:** ensemble of decision trees that can model nonlinear patterns.

Both models use a Scikit-learn pipeline. Numeric missing values are median-imputed, categorical missing values are most-frequent-imputed and categorical fields are one-hot encoded.

## Project Workflow

```text
Dataset
   ↓
Data Cleaning
   ↓
EDA
   ↓
Data Preprocessing
   ↓
Train/Test Split
   ↓
Model Training
   ↓
Model Evaluation
   ↓
Best Model
   ↓
Price Prediction
```

## Installation

```bash
pip install -r requirements.txt
```

## How to Run

From this folder, start Jupyter:

```bash
jupyter notebook
```

Open `AdityaVishwakarma_CarPricePrediction.ipynb` and run the cells from top to bottom. Keep `car_data.csv` in the same folder as the notebook. Running the save-model cell writes `car_price_model.pkl`.

## Project Files

```text
Car-Price-Prediction/
├── AdityaVishwakarma_CarPricePrediction.ipynb
├── AdityaVishwakarma_CarPricePrediction_ProjectReport.docx
├── requirements.txt
├── README.md
├── car_data.csv
├── car_price_model.pkl
└── figures/
```

## Results

The notebook used `train_test_split(test_size=0.20, random_state=42)`: 239 training rows and 60 test rows after exact-duplicate removal. Metrics below are from the executed notebook, not assumed values. Lower MAE/RMSE is better; higher R² is better.

| Model | MAE (lakh) | MSE (lakh²) | RMSE (lakh) | R² |
|---|---:|---:|---:|---:|
| Linear Regression | 1.4729 | 6.3708 | 2.5240 | 0.7528 |
| Random Forest | 1.4971 | 12.7285 | 3.5677 | 0.5061 |

Linear Regression was selected because it had the lowest test RMSE (2.5240 lakh) and highest R² (0.7528) on this split. Its average absolute error was 1.4729 lakh. The sample input in the notebook (2015, reference price 8.0 lakh, 30,000 km, Petrol, Dealer, Manual, 0 previous owners) is estimated at **INR 5.29 lakh** by the selected pipeline. The small historical dataset makes the scores sensitive to the train/test split; use the notebook to reproduce them and interpret as an educational benchmark.

## Future Scope

- Add more recent observations and vehicle condition, city and make/model information.
- Use cross-validation and hyperparameter tuning.
- Compare gradient boosting methods.
- Build an optional Streamlit interface and validate on later listings.

## Author

Aditya Vishwakarma
