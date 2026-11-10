# California Home Price Prediction

*Data science internship project. Python.*

## Project Overview
How much will a California home sell for? This project cleans real home-sale
data, builds new features, and compares five prediction models. The best
model predicts sale prices with a typical error of about 7%, which could help
buyers, sellers, and lenders estimate a home's value.

## Data Source
The data comes from CRMLS (California Regional Multiple Listing Service), a
real estate listing database, and was provided through my data internship
with IDX Exchange. I used 34 months of sold-property records for California.

Each row is one sold property. The target variable is ClosePrice (the final
sale price). Other key features include LivingArea, Bedrooms, Bathrooms, and
LotSize. I only used rows where PropertyType is "Residential" and
PropertySubType is "SingleFamilyResidence."

The raw data is not included because it was provided through the internship
and is not mine to redistribute.

## Methodology
1. **Exploration** (`01_exploration.ipynb`): checked the size, column types,
   missing values, and distributions.
2. **Cleaning** (`02_preprocessing.ipynb`): removed rows with missing prices,
   set impossible values to missing, fixed bad coordinates, converted HOA fees
   to monthly amounts, and handled other missing values using training data
   only so test data does not leak into training.
3. **Feature engineering** (`feature_engineering.ipynb`): added features such
   as property age, time of year, past median price per square foot by zip
   code and county, and school district information.
4. **Models** (`03` to `05` notebooks): linear regression (baseline), decision
   tree, random forest, XGBoost, and LightGBM, tuned with grid search. Models
   were chosen on validation data and scored on the most recent month as the
   test set.

## Tools & Libraries
Python, pandas, NumPy, scikit-learn, LightGBM, XGBoost, GeoPandas,
matplotlib, seaborn, Jupyter Notebook

## Key Findings
| Model | Test R-squared | Test MdAPE |
|-------|----------------|------------|
| Linear Regression (baseline) | 0.79 | 14.2% |
| Decision Tree | 0.74 | 9.9% |
| Random Forest | 0.86 | 8.1% |
| XGBoost | 0.88 | 7.4% |
| LightGBM (best) | 0.88 | 7.3% |

- The best model (LightGBM) typically misses a home's price by about 7%.
- Feature engineering helped a lot: the linear regression's R-squared went
  from about 0.67 to 0.79.
- The linear regression predicted negative prices for some homes and
  underpredicted very expensive ones, so a straight-line model is not enough.

## Limitations
- Cleaning choices (removing rows, filling in values) could affect results.
- Findings apply only to this dataset's time period and area.
- Very high-priced homes are harder to predict accurately.
- The models show association, not what causes prices to change.

## Reproducibility
1. Clone the repo and install packages: `pip install -r requirements.txt`
2. Get the raw CRMLS sold-property files (access requires permission from the
   data provider) and put them in `data/sold/raw/`.
3. Run the notebooks in order: `01_exploration`, `02_preprocessing`,
   `feature_engineering`, `03_baseline_model`, `04_model_comparison`,
   `05_advanced_models`.
4. The school district step needs the CA School District Areas 2024-25
   shapefile from data.ca.gov. It skips itself if the file is missing.
