# What Drives the Price of a Car?

## Project Overview

This project explores a dataset from Kaggle containing information on **426,000 used cars** to identify the key drivers of used car prices. The original dataset contained information on 3 million used cars, which has been sampled to ensure optimal performance and processing efficiency.

## Framework

This project follows the **CRISP-DM (Cross-Industry Standard Process for Data Mining)** framework, which provides a standard process for data science projects:

- **Business Understanding**: Define objectives and convert them into data problem definitions
- **Data Understanding**: Explore and identify data quality issues
- **Data Preparation**: Construct the final dataset for modeling
- **Modeling**: Build and train regression models
- **Evaluation**: Assess model performance and quality
- **Deployment**: Deliver findings and insights to stakeholders

## Project Phases

### 1. Business Understanding

**Objective**: Identify key drivers for used car prices from a business perspective and translate this into a data science problem.

### 2. Data Understanding

Initial exploration steps to become familiar with the dataset and identify any quality issues:
- Load and inspect the data
- Examine data shape and types
- Check for missing values and outliers
- Identify data quality issues

### 3. Data Preparation

Prepare the dataset for modeling:
- Remove records with price ≤ 0
- Drop identifiers and high-cardinality columns (id, VIN, model, region)
- Sample 100,000 records for faster training
- Separate features (X) and target variable (y)
- Identify categorical and numeric columns

### 4. Data Preprocessing Pipeline

A scikit-learn pipeline handles preprocessing for both feature types:

**Numeric Features**:
- Imputation strategy: Median

**Categorical Features**:
- Imputation strategy: Most frequent value
- Encoding: One-Hot Encoding

**Train-Test Split**: 80% training, 20% testing (random_state=42)

### 5. Modeling

**Model**: Random Forest Regressor
- **n_estimators**: 200
- **max_depth**: 20
- **random_state**: 42
- **n_jobs**: -1 (parallel processing)

### 6. Evaluation Metrics

The model performance is evaluated using:

- **MAE (Mean Absolute Error)**: Average absolute error in dollars
- **RMSE (Root Mean Squared Error)**: Standard deviation of prediction errors in dollars
- **R² Score**: Proportion of variance explained by the model

## Installation & Setup

### Requirements

```
pandas
numpy
scikit-learn
jupyter
```

### Installation

```bash
pip install pandas numpy scikit-learn jupyter
```

## Usage

1. **Load the notebook**:
   ```bash
   jupyter notebook prompt_II.ipynb
   ```

2. **Ensure data is available**: Place the `vehicles.csv` dataset in the `data/` directory

3. **Run cells sequentially** following the CRISP-DM phases:
   - Import libraries
   - Load and clean data
   - Prepare features and target
   - Build preprocessing pipeline
   - Train model
   - Evaluate performance

4. **Output**: Model performance metrics (MAE, RMSE, R²)

## Project Structure

```
.
├── prompt_II.ipynb          # Main Jupyter notebook
├── data/
│   └── vehicles.csv         # Dataset (426K cars)
├── images/
│   ├── kurt.jpeg           # Project cover image
│   └── crisp.png           # CRISP-DM framework diagram
└── README.md               # This file
```

## Key Insights

The Random Forest model identifies which features have the strongest relationship with car prices. By analyzing feature importance, we can determine the primary drivers of used car pricing in the market.

## Model Output

```
Model Performance
=================
MAE  : $[Amount]
RMSE : $[Amount]
R²   : [Score]
```

## Deployment

The findings are organized as a business report detailing:
- Primary findings about price drivers
- Model performance metrics
- Recommendations for stakeholders
- Key insights for decision-making

## Notes

- The dataset is sampled to 100,000 records for computational efficiency
- Random state (42) is used throughout for reproducibility
- Missing values are handled automatically through the preprocessing pipeline
- The model uses parallel processing (n_jobs=-1) for faster training

## License

MIT License

## Author

Saroja Bandaru

## References

- Dataset source: Kaggle
- Framework: CRISP-DM (Cross-Industry Standard Process for Data Mining)
- ML Library: scikit-learn
