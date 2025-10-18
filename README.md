# KNN-Linear-Regression

## ridge regression

- first we splitted the data into train,val,test

  ```py
    training_data = data.sample(frac=0.7,random_state = 42)
    rest_of_data = data.drop(training_data.index)
    validation_data = rest_of_data.sample(frac=0.5,random_state = 42)
    testing_data = rest_of_data.drop(validation_data.index)
  ```

- we calculated the weights with the ridge regularization using the following equation :

  $$
  w = (X^T X + \lambda I)^{-1} X^T y
  $$

  i did not add the N to the equation as sklearn computes the average not the total so, to have a fair comparision

  ```py
    I = np.eye(matrix_x.shape[1]) #identity
    I[0, 0] = 0 # removing the bias from the regularization
    inverse_m = np.linalg.pinv(np.dot(matrix_xt, matrix_x) + l * I)
    weights = np.dot(np.dot(inverse_m,  matrix_xt ), matrix_t)

  ```

- we tested many lambda using the validation data and the typical MSE equation

  ```py
  val = np.sum((y_predicted - target_validate)**2) / y_predicted.shap[0]
  ```
