# Coordinate Descent for Lasso Regression

## Implementation

1. Split the data - 70% train, 15% validation, 15% test.

2. Scaling - Used StandardScaler because the features have very different scales (income vs latitude, etc.)

3. Hyperparameter tuning - I tried different alpha values from 0.0001 to 10 using a log scale. Found the best one using validation set.

4. The actual coordinate descent - algorithm:
   - Starts with some initial coefficients
   - For each feature, it updates just that coefficient while keeping others fixed
   - Keeps iterating until convergence (or max iterations)
   - The L1 penalty term makes some coefficients shrink to exactly zero

##Key Parameters:

- `alpha`: The regularization strength (tuned using validation set)
- `max_iter`: Set to 5000 to make sure it converges
- `tol`: Convergence tolerance of 1e-4
- `fit_intercept`: Used True during hyperparameter tuning to give the model more flexibility when finding the best alpha value, but set to False for the final model since the scaled data doesn't need an additional intercept term and it makes the model more efficient.

## Results

The model ended up with:

- Test MSE: 48,308,633,688
- Test MAE: 208,467
