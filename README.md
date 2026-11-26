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
7. Run five-fold shuffled cross-validation on the training partition only, comparing a mean-prediction baseline, Linear Regression and Random Forest.
8. Report fold-mean and fold-standard-deviation for MAE, RMSE and R². The held-out test partition is not used during cross-validation.
9. Compare MAE, RMSE and R² on the same held-out test set.
10. Review actual-versus-predicted values and Random Forest feature importance.
11. Generate one example prediction.

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
- The five-fold cross-validation results are internal estimates from the training partition. Fold variability should be considered alongside the mean scores.
- The final 20% holdout remains separate from cross-validation. It is evaluated after model fitting and does not provide independent-market validation.
- External validation and additional business variables are needed before making operational decisions.

## Run the notebook

Open `CodeAlpha_Sales_Prediction_(2).ipynb` in Jupyter or Google Colab and run all cells from top to bottom.

## Requirements

Python 3.10 or later. Install the project dependencies from the repository root:

```bash
python -m pip install -r requirements.txt
```

The notebook downloads the dataset from the public URL above, so execution requires internet access.

## Validation design

The notebook includes a five-fold shuffled cross-validation comparison on the 80% training partition. It evaluates a mean-prediction baseline, Linear Regression and Random Forest with MAE, RMSE and R². Both the mean and sample standard deviation across folds are reported. The final 20% holdout is kept out of cross-validation and remains the final same-source test set.

The cross-validation step reduces reliance on one random training split, but it does not replace time-based or external-market validation. The observations are small and independently sampled in the supplied dataset; no temporal deployment claim is made.

## Latest GitHub Actions validation

Latest verified successful main-branch workflow run checked on 24 November 2026: [GitHub Actions run #45313681720](https://github.com/krishankantpandey359-droid/Sales_Prediction/actions/runs/45313681720). This run verifies the checks configured in this repository's workflow; it does not replace manual testing of features outside CI.
