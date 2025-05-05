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
# Details of all:

Breakdown of each command and its significance in **one sentence each**, based on **B1 Adult file** notebook:

---

### **General Setup**

```python
import pandas as pd
```

➡️ *Imports the pandas library, which is essential for data manipulation and analysis in Python.*

---

### **Loading and Viewing Data**

```python
df = pd.read_csv('adult_dataset.csv')
```

➡️ *Reads a CSV file named `adult_dataset.csv` into a pandas DataFrame called `df`.*

```python
df
```

➡️ *Displays the entire DataFrame to view the data.*

```python
df.describe()
```

➡️ *Provides statistical summaries (mean, count, std, etc.) for numerical columns in the DataFrame.*

---

### **Create Data Subsets**

```python
df.info()
```

➡️ *Displays information about the DataFrame, such as column data types, non-null counts, and memory usage.*

```python
df_subset_1 = df[['workclass','education','capital-gain']]
```

➡️ *Creates a new subset of the DataFrame with only the 'workclass', 'education', and 'capital-gain' columns.*

```python
df_subset_1
```

➡️ *Displays the first subset (`df_subset_1`) to verify its contents.*

```python
df_subset_2 = df[['race','native-country']]
```

➡️ *Creates a second subset of the DataFrame with the 'race' and 'native-country' columns.*

```python
df_subset_2
```

➡️ *Displays the second subset (`df_subset_2`).*

---

### **Merge Data**

```python
merged_data  = pd.concat([df_subset_1,df_subset_2],axis=1)
```

➡️ *Merges the two subsets column-wise to form a single DataFrame called `merged_data`.*

```python
merged_data
```

➡️ *Displays the merged DataFrame.*

---

### **Sort Data**

```python
merged_data.sort_values(by=['capital-gain'],ascending=False)
```

➡️ *Sorts the merged data in descending order based on the 'capital-gain' column.*

---

### **Transposing Data**

```python
merged_data.transpose()
```

➡️ *Transposes the merged DataFrame, switching rows with columns.*

```python
merged_data.T
```

➡️ *Another method (shortcut) to transpose the DataFrame using `.T`.*

---

### **Shape and Reshape Data**

```python
df
```

➡️ *Displays the original DataFrame again, likely to view its shape before reshaping.*

```python
pd.melt(df, id_vars =['education'], value_vars =['capital-gain'])
```

➡️ *Reshapes the DataFrame from wide to long format, keeping 'education' fixed and unpivoting 'capital-gain'.*

---
