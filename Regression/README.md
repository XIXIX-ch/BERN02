# Weighted Local Regression for Air Pollution Data

This project implements a weighted local linear regression function from scratch and applies it to an air-pollution dataset.

The objective is to predict the total age-adjusted mortality rate per 100,000 people (`MORT`) for areas where 10%, 18%, and 25% of families have an income below $3000 (`POOR`).

## Method

For each prediction value, the analysis:

1. Selects the 15 observations with the closest `POOR` values.
2. Assigns tricube weights so that observations closer to the prediction point receive greater influence.
3. Fits a weighted local linear regression using matrix operations.
4. Estimates the expected mortality rate and its standard error.

The weighted coefficients are calculated as:

```text
beta = (X.T W X)^(-1) X.T W y
```

The residual variance is estimated without weights, following the exercise instructions.

## Results

| POOR (%) | Predicted MORT | Standard error |
|---:|---:|---:|
| 10 | 899.794 | 19.457 |
| 18 | 956.156 | 19.677 |
| 25 | 1011.086 | 26.056 |

The predicted mortality rate increased as the percentage of low-income families increased. The prediction at `POOR = 25%` had the largest standard error and therefore the greatest uncertainty.

These results describe an association and should not be interpreted as evidence that poverty causes higher mortality.

## Repository contents

- `Regression.ipynb` - complete analysis and weighted local regression implementation
- `pollution_cleaneddata.csv` - air-pollution observations used in the analysis
- `pollution_metadata.txt` - variable definitions and data-source information

## Requirements

- Python 3.12
- NumPy
- pandas
- Jupyter Notebook or Visual Studio Code with the Jupyter extension

Install the required Python packages with:

```bash
python -m pip install numpy pandas notebook ipykernel
```

## Running the analysis

Place the notebook and both data files in the same directory. Then start Jupyter Notebook:

```bash
jupyter notebook Regression.ipynb
```

Alternatively, open `Regression.ipynb` in Visual Studio Code, select a Python kernel, and run all cells from top to bottom.

## Author

Xi Chen
