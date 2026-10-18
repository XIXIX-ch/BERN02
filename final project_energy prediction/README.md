# Predicting Building Energy Demand with Limited Data

This project predicts building heating load using the [UCI Energy Efficiency dataset](https://archive.ics.uci.edu/dataset/242/energy+efficiency). It compares multiple linear regression with random forest regression and investigates how far the original eight predictors can be reduced without a substantial loss of predictive accuracy.

## Analysis workflow

1. Load the Energy Efficiency dataset from `ucimlrepo`.
2. Split the data into 80% training data and 20% test data.
3. Fit a multiple linear regression baseline.
4. Fit a random forest using all eight predictors.
5. Apply Recursive Feature Elimination to retain five predictors.
6. Examine correlations among the five selected predictors.
7. Evaluate a three-feature random forest using:
   - Surface Area
   - Overall Height
   - Glazing Area
8. Select the smallest model whose cross-validation RMSE is within 10% of the best random forest.
9. Evaluate the selected model once on the unused test set.

## Final result

The selected model was a three-feature random forest.

| Metric | Test result |
|---|---:|
| MAE | 0.374 |
| RMSE | 0.502 |
| R² | 0.998 |

The final model reduced the predictor count from eight to three while retaining strong predictive performance on this dataset.

## Repository contents

- `energy prediction-1.ipynb` - complete analysis, model comparison, feature selection, figures, and results
- `requirements.txt` - Python package versions used to run the notebook

## Requirements

- Python 3.12 (developed with Python 3.12.14)
- Internet access on the first run so `ucimlrepo` can retrieve the dataset

## Installation

Create and activate a virtual environment or Conda environment:

```bash
conda create -n energy-efficiency python=3.12
conda activate energy-efficiency
python -m pip install -r requirements.txt
```

## Running the notebook

Start JupyterLab:

```bash
jupyter lab "energy prediction-1.ipynb"
```

Alternatively, open the notebook in Visual Studio Code, select the environment created above as the kernel, and run all cells from top to bottom.

## Reproducibility

The train-test split, cross-validation folds, and random forest models use `random_state=42`. Feature selection is performed on the training data, and the test set is reserved for final evaluation.

## Author

Xi Chen
