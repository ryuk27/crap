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

Below is a **command-by-command breakdown**, each explained in **one concise sentence** regarding its purpose or significance for **B2 Air**:

---

### 📥 **Data Loading and Initial Exploration**

```python
import pandas as pd
import numpy as np
```

➡️ *Imports pandas for data manipulation and numpy for numerical operations.*

```python
df = pd.read_csv("M:/Downloads/DSBDA/grp B2/airquality_data.csv", encoding='cp1252', dtype={0: str})
```

➡️ *Reads the air quality dataset with specified encoding and forces the first column to string data type.*

```python
df.head()
```

➡️ *Displays the first 5 rows to get an overview of the dataset.*

```python
df.info()
```

➡️ *Prints a concise summary of the dataset including data types and non-null counts.*

```python
df.columns
```

➡️ *Lists all column names of the DataFrame.*

---

### 🧼 **Data Cleaning**

```python
df['so2'] = df['so2'].astype('float32')
df['no2'] = df['no2'].astype('float32')
df['rspm'] = df['rspm'].astype('float32')
df['spm'] = df['spm'].astype('float32')
df['date'] = df['date'].astype('string')
```

➡️ *Converts selected columns to more memory-efficient data types.*

```python
df.info()
```

➡️ *Verifies the updated data types and memory usage after conversion.*

```python
df = df.drop_duplicates()
```

➡️ *Removes any duplicate rows from the dataset.*

```python
df.isna().sum()
```

➡️ *Counts missing values in each column.*

```python
percent_missing = df.isnull().sum() * 100 / len(df)
percent_missing.sort_values(ascending=False)
```

➡️ *Calculates and sorts the percentage of missing data in descending order.*

```python
df = df.drop(['stn_code', 'agency','sampling_date','location_monitoring_station','pm2_5'], axis=1)
```

➡️ *Drops columns with excessive missing data or low relevance.*

---

### 🧩 **Handling Missing Data**

```python
col_var = ['state', 'location', 'type','date']
col_num = ['so2','no2','rspm','spm']
```

➡️ *Separates categorical and numerical columns for targeted preprocessing.*

```python
for col in df.columns:
    if df[col].dtype == 'object' or df[col].dtype == 'string':
        df[col] = df[col].fillna(df[col].mode()[0])
    else:
        df[col] = df[col].fillna(df[col].mean())
```

➡️ *Fills missing values in categorical columns with mode and numerical columns with mean.*

```python
df.isna().sum()
```

➡️ *Confirms that all missing values have been filled.*

---

### 🔗 **Data Integration**

```python
subSet1 = df[['state', 'type']]
subSet2 = df[['state','location']]
```

➡️ *Creates two subsets for potential merging or analysis.*

```python
concatenated_df = pd.concat([subSet1, subSet2], axis=1)
```

➡️ *Concatenates the two subsets horizontally to form a combined DataFrame.*

---

### 🛠️ **Error Correction (Outlier Removal)**

```python
def remove_outliers(column):
    Q1 = column.quantile(0.25)
    Q3 = column.quantile(0.75)
    IQR = Q3 - Q1
    threshold = 1.5 * IQR
    outlier_mask = (column < Q1 - threshold) | (column > Q3 + threshold)
    return column[~outlier_mask]
```

➡️ *Defines a function to remove outliers from a numeric column using the IQR method.*

```python
col_name = ['so2', 'no2', 'rspm', 'spm']
for col in col_name:
    df[col] = remove_outliers(df[col])
```

➡️ *Applies the outlier removal function to key pollutant columns.*

---

### 📊 **Data Visualization (Outlier Check)**

```python
import seaborn as sns
import matplotlib.pyplot as plt
```

➡️ *Imports libraries for data visualization.*

```python
plt.figure(figsize=(10, 6))
for col in col_name:
    sns.boxplot(data=df[col])
    plt.title(col)
    plt.show()
```

➡️ *Creates boxplots to visually inspect outliers in pollutant columns.*

---

### 🔄 **Data Transformation**

```python
from sklearn.preprocessing import LabelEncoder
```

➡️ *Imports `LabelEncoder` for encoding categorical features.*

```python
encoder = LabelEncoder()
for col in df.columns:
    df[col] = encoder.fit_transform(df[col])
```

➡️ *Encodes all columns (including categorical ones) into numeric form for model readiness.*

---

Details of **"B4 Heart"** code step by step, just like we did before.

---

### 📁 **1. Loading the Dataset**

```python
import pandas as pd
df = pd.read_csv('heart.csv')
```

✅ **Purpose**:

* This imports the `pandas` library and loads the CSV file `heart.csv` into a DataFrame `df`.

---

### 🧹 **2. Dropping Duplicates**

```python
df = df.drop_duplicates()
```

✅ **Purpose**:

* Removes any duplicate rows from the dataset.
* After this, rows go from 303 ➡️ 302.

---

### 🧼 **3. Checking for Missing Values**

```python
df.isna().sum()
```

✅ **Purpose**:

* Checks if there are any missing (NaN) values in each column.
* Output shows all columns have 0 missing values — the data is clean.

---

### 📊 **4. Correlation Heatmap**

```python
import seaborn as sns
import matplotlib.pyplot as plt

plt.figure(figsize=(10,6))
sns.heatmap(df.corr(), cmap='YlGnBu', annot=True)
```

✅ **Purpose**:

* Visualizes the correlation between features.
* Helps identify which features are positively/negatively correlated with `output`.
* `annot=True` shows the actual correlation values inside each cell.

---

### 📈 **5. Line Charts by Age**

#### a. Chest Pain Type vs Age

```python
sns.lineplot(data=df, x=df.age, y=df.cp, hue='output')
```

✅ **Purpose**:

* Shows how chest pain types (`cp`) vary across age groups, separated by disease presence (`output`).

#### b. Resting Blood Pressure vs Age

```python
sns.lineplot(data=df, x=df.age, y=df.trtbps, hue='output')
```

✅ **Purpose**:

* Observes how resting blood pressure (`trtbps`) changes with age, separated by heart disease outcome.

#### c. Cholesterol vs Age

```python
sns.lineplot(data=df, x=df.age, y=df.chol, hue='output')
```

✅ **Purpose**:

* Compares cholesterol levels across ages for those with and without heart disease.

#### d. Exercise-induced Angina vs Oldpeak

```python
sns.lineplot(df, x=df.oldpeak, y=df.exng, hue='output')
```

✅ **Purpose**:

* `exng` (exercise-induced angina) vs `oldpeak` (ST depression) colored by disease status.
* Shows relationship between angina and ST depression.

---

### 📊 **6. Histograms**

#### a. Output Distribution by Sex

```python
sns.histplot(data=df, x=df.output, hue=df.sex)
```

✅ **Purpose**:

* Shows how many males vs females have heart disease (`output`).

#### b. Chest Pain Type by Sex

```python
sns.histplot(data=df, x=df.cp, hue=df.sex)
```

✅ **Purpose**:

* Compares chest pain types between men and women.

#### c. Chest Pain Type by Output

```python
sns.histplot(data=df, x=df.cp, hue='output')
```

✅ **Purpose**:

* Shows how chest pain types are distributed for people with and without heart disease.

#### d. Age Distribution by Output

```python
sns.histplot(data=df, x=df['age'], hue='output')
```

✅ **Purpose**:

* Visualizes which age ranges have more heart disease cases.

#### e. Resting BP by Output

```python
sns.histplot(data=df, x=df.trtbps, hue='output')
```

✅ **Purpose**:

* Compares resting blood pressure across patients with and without heart disease.

---

### 🔍 **7. Pairplot for Selected Features**

```python
temp_df = df[['age','cp', 'trtbps','chol','fbs','oldpeak','output']]
plt.figure(figsize=(15,10))
sns.pairplot(temp_df, hue="output")
plt.title("Looking for Insites in Data")
plt.legend("HeartDisease")
plt.tight_layout()
plt.plot()
```

✅ **Purpose**:

* `pairplot` shows scatter plots and distributions for selected features.
* Makes it easier to visually detect patterns, clusters, or outliers related to heart disease.

---

### 🧮 **8. Subplot: Distribution of Each Column**

```python
plt.figure(figsize=(15,10))
for i, col in enumerate(temp_df.columns, 1):
    plt.subplot(4, 3, i)
    plt.title(f"Distribution of {col} Data")
    sns.histplot(df[col], kde=True)
    plt.tight_layout()
    plt.plot()
```

✅ **Purpose**:

* Plots the distribution of each selected column using subplots (in a 4x3 grid).
* `kde=True` adds a smoothed curve on top of the histogram for better insight.

---
