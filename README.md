# Sales Prediction using Python

## Project overview

This project explores how advertising expenditure relates to sales. It compares Linear Regression and Random Forest Regression using a held-out test set.

## Dataset

The notebook loads the Advertising dataset from the public `selva86/datasets` GitHub repository.

- Rows: 200
- Features: `TV`, `radio`, `newspaper`
- Target: `sales`

The notebook validates the required columns, numeric values, missing values and finite values before analysis. It removes exact duplicate rows and reports how many it removes. The notebook does not silently impute missing data.

## Workflow

1. Load and validate the dataset.
2. Inspect data types and descriptive statistics.
3. Check missing values and remove exact duplicate rows.
4. Explore sales distribution, feature relationships and correlations.
5. Split data into training and test sets (80/20, `random_state=42`).
6. Train Linear Regression and Random Forest Regression.
7. Compare MAE, RMSE and R² on the same held-out test set.
8. Run an additional shuffled five-fold cross-validation comparison on the 80% training partition only, reporting mean and standard deviation. The held-out 20% test partition is excluded from cross-validation.
9. Review actual-versus-predicted values and Random Forest feature importance.
10. Generate one example prediction.

## Saved evaluation results

The notebook's previously saved run reports:

| Model | MAE | RMSE | R² |
|---|---:|---:|---:|
| Linear Regression | 1.461 | 1.782 | 0.899 |
| Random Forest | 0.629 | 0.757 | 0.982 |

These metrics are from one fixed split of a small dataset. Re-run the notebook to reproduce them. A single split does not establish generalization to new markets or production data.

## Important limitations

- Correlation does not prove that advertising spend causes sales changes.
- Random Forest feature importance is model-specific, not a causal effect.
- The dataset has only 200 observations and three advertising predictors.
- The example prediction is an estimate in the dataset's sales units. It is not a business forecast.
- Five-fold cross-validation is run only on the 80% training partition, keeping the held-out 20% test set separate. It provides an internal stability check, not external validation. Additional business variables and an independent dataset are still needed before operational decisions.

## Run the notebook

Open `CodeAlpha_Sales_Prediction_(2).ipynb` in Jupyter or Google Colab and run all cells from top to bottom.

## Requirements

Python 3.10 or later with pandas, numpy, matplotlib, seaborn, scikit-learn, jupyter and nbconvert. The notebook downloads the dataset from the public URL above, so execution requires internet access.
