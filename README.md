# Real Estate Data Exploration and Cleaning

*Project from my data internship. Python.*

## Project Overview
Raw data is often messy, and messy data leads to wrong conclusions. This
project explores a California housing price dataset to find problems like
missing or unrealistic values, then cleans it so it is ready for analysis.

## Data Source
The datasets containing historical close price (final sales price)
data on real estate properties sourced from CRMLS (California Regional Multiple Listing
Service), including various features such as living area, number of bedrooms,
bathrooms, lot size, and close prices, with ClosePrice being the target variable.
Each row is one transaction.
Key columns include BathroomsTotalInteger, BedroomsTotal, and LivingArea.
The raw data is not included publically as requested by IDX Exchange.
See README.md.

## Methodology
1. Explored the data: size, column types, missing values, and distributions
   (01_exploration.ipynb).
2. Cleaned the data: [fixed bad values, handled missing values, standardized
   formats] (02_preprocessing.ipynb).
3. Evaluated the cleaned data on various models: Multiple Linear Regression, Decision Tree, Random Forest, LightGBM, and XGBoost.

## Tools & Libraries
Python, pandas, NumPy, matplotlib, Jupyter Notebook

## Key Findings
- All models performed better than the null model.
- Model performance capped out at around <0.9 R^2

## Limitations
- Cleaning choices (removing rows, filling in values) could affect results.
- Findings apply only to this dataset's time period and area.

## Reproducibility
1. Clone the repo and install packages: `pip install -r requirements.txt`
2. Put the dataset in the `data/` folder
3. Run `code/01_exploration.ipynb`, then `code/02_preprocessing.ipynb`.
