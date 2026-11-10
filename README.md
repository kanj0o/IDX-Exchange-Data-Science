# Real Estate Data Exploration and Cleaning

*Project from my data science internship. Python.*

## Project Overview
Raw data is often messy, and messy data leads to wrong conclusions. This
project explores a California housing price dataset to find problems like
missing or unrealistic values, then cleans it so it is ready for analysis.

## Data Source
The data comes from CRMLS (California Regional Multiple Listing Service), a
real estate listing database, and was provided through my data internship
with IDX Exchange. I used 34 months of sold-property records for California.

Each row is one sold property. The target variable is ClosePrice (the final
sale price). Other key features include LivingArea, Bedrooms, Bathrooms, and
LotSize. I only used rows where PropertyType is "Residential" and
PropertySubType is "SingleFamilyResidence."

The raw data is not included in this repository because it was provided
through the internship and is not mine to redistribute. See data/README.md.

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
