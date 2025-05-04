# Instructions in case errors:
- For Group B2 Air, in case of file path error change the code to
  ```python
  df = pd.read_csv("M:/Downloads/DSBDA/grp B2/airquality_data.csv", encoding='cp1252', dtype={0: str})
  ```

- For Group B2 Heart, in Data Model Building part, in case of error change the code to
  ```python
  from sklearn.linear_model import LogisticRegression
  from sklearn.metrics import accuracy_score

  # Initialize the model
  model = LogisticRegression()

  # Fit the model with ravel() to convert y_train to 1D
  model.fit(x_train_scaled, y_train.ravel())

  # Make predictions
  y_pred = model.predict(x_test_scaled)

  # Evaluate accuracy
  accuracy = accuracy_score(y_test, y_pred)
  print("Accuracy:", accuracy)
```
