# KNN-Linear-Regression

## Ridge Regression

- First we split the data into train, val, test

  ```py
    training_data = data.sample(frac=0.7,random_state = 42)
    rest_of_data = data.drop(training_data.index)
    validation_data = rest_of_data.sample(frac=0.5,random_state = 42)
    testing_data = rest_of_data.drop(validation_data.index)
  ```

- We calculated the weights with the ridge regularization using the following equation :

  $$
  w = (X^T X + \lambda I)^{-1} X^T y
  $$

  I did not add the N to the equation as sklearn computes the average not the total so, to have a fair comparison

  ```py
    I = np.eye(matrix_x.shape[1]) #identity
    I[0, 0] = 0 # removing the bias from the regularization
    inverse_m = np.linalg.pinv(np.dot(matrix_xt, matrix_x) + l * I)
    weights = np.dot(np.dot(inverse_m,  matrix_xt ), matrix_t)

  ```

- We tested many lambda using the validation data and the typical MSE equation

  ```py
  val = np.sum((y_predicted - target_validate)**2) / y_predicted.shape[0]
  ```

## Coordinate Descent for Lasso Regression

### Implementation

1. Split the data - 70% train, 15% validation, 15% test.

2. Scaling - Used StandardScaler because the features have very different scales (income vs latitude, etc.)

3. Hyperparameter tuning - I tried different alpha values from 0.0001 to 10 using a log scale. Found the best one using validation set.

4. The actual coordinate descent - algorithm:
   - Starts with some initial coefficients
   - For each feature, it updates just that coefficient while keeping others fixed
   - Keeps iterating until convergence (or max iterations)
   - The L1 penalty term makes some coefficients shrink to exactly zero

### Key Parameters:

- `alpha`: The regularization strength (tuned using validation set)
- `max_iter`: Set to 5000 to make sure it converges
- `tol`: Convergence tolerance of 1e-4
- `fit_intercept`: Used True during hyperparameter tuning to give the model more flexibility when finding the best alpha value, but set to False for the final model since the scaled data doesn't need an additional intercept term and it makes the model more efficient.

### Results

The model ended up with:

- Test MSE: 48,308,633,688
- Test MAE: 208,467
