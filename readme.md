## pandas Tutorial

### Introduction
Pandas is a powerful and flexible Python library for data manipulation and analysis. This tutorial covers the basic commands and functions in pandas, along with examples to help you get started.

---

### Table of Contents
1. [Importing pandas](#importing-pandas)
2. [Creating DataFrames](#creating-dataframes)
3. [Viewing Data](#viewing-data)
4. [Selecting Data](#selecting-data)
5. [Filtering Data](#filtering-data)
6. [Modifying Data](#modifying-data)
7. [Handling Missing Data](#handling-missing-data)
8. [Grouping and Aggregating Data](#grouping-and-aggregating-data)
9. [Merging and Joining DataFrames](#merging-and-joining-dataframes)
10. [Saving Data](#saving-data)
11. [Pivot Tables](#pivot-tables)
12. [Basic Plotting](#basic-plotting)
13. [Example Programs](#example-programs)

---

### Importing pandas
```python
import pandas as pd
```

### Creating DataFrames

#### From a dictionary
```python
# Creating a DataFrame from a dictionary
data = {'column1': [1, 2, 3], 'column2': [4, 5, 6]}
df = pd.DataFrame(data)
```

#### From a CSV file
```python
# Creating a DataFrame from a CSV file
df = pd.read_csv('file.csv')
```

#### From an Excel file
```python
# Creating a DataFrame from an Excel file
df = pd.read_excel('file.xlsx')
```

### Viewing Data
```python
# Display the first 5 rows
df.head()

# Display the last 5 rows
df.tail()

# Display a summary of the DataFrame
df.info()

# Display summary statistics
df.describe()
```

### Selecting Data
```python
# Selecting a single column
df['column1']

# Selecting multiple columns
df[['column1', 'column2']]

# Selecting rows by index
df.iloc[0]  # First row
df.iloc[0:5]  # First five rows

# Selecting rows and columns by labels
df.loc[0, 'column1']  # Element at row 0 and column 'column1'
df.loc[0:5, ['column1', 'column2']]  # First five rows of 'column1' and 'column2'
```

### Filtering Data
```python
# Filtering rows based on a condition
df[df['column1'] > 1]

# Filtering rows based on multiple conditions
df[(df['column1'] > 1) & (df['column2'] < 6)]
```

### Modifying Data
```python
# Adding a new column
df['column3'] = df['column1'] + df['column2']

# Modifying an existing column
df['column1'] = df['column1'] * 2

# Dropping a column
df = df.drop(columns=['column2'])

# Dropping rows
df = df.drop(index=[0, 1])  # Drops the first two rows
```

### Handling Missing Data
```python
# Check for missing values
df.isnull()

# Drop rows with missing values
df = df.dropna()

# Fill missing values
df = df.fillna(value=0)
```

### Grouping and Aggregating Data
```python
# Group by a column and aggregate
grouped = df.groupby('column1').sum()

# Aggregate with multiple functions
grouped = df.groupby('column1').agg({'column2': 'sum', 'column3': 'mean'})
```

### Merging and Joining DataFrames
```python
# Merging DataFrames
df1 = pd.DataFrame({'key': ['A', 'B', 'C'], 'value1': [1, 2, 3]})
df2 = pd.DataFrame({'key': ['A', 'B', 'D'], 'value2': [4, 5, 6]})
merged_df = pd.merge(df1, df2, on='key', how='inner')  # 'left', 'right', 'outer'

# Concatenating DataFrames
concat_df = pd.concat([df1, df2], axis=0)  # axis=1 for columns
```

### Saving Data
```python
# Save to CSV
df.to_csv('output.csv', index=False)

# Save to Excel
df.to_excel('output.xlsx', index=False)
```

### Pivot Tables
```python
# Creating a pivot table
pivot_df = df.pivot_table(index='column1', columns='column2', values='column3', aggfunc='mean')
```

### Basic Plotting
```python
import matplotlib.pyplot as plt

# Line plot
df.plot(x='column1', y='column2')

# Bar plot
df['column1'].value_counts().plot(kind='bar')

# Show plot
plt.show()
```

### Example Programs

#### Example 1: Basic DataFrame Operations
```python
import pandas as pd

# Creating a DataFrame
data = {'Name': ['Alice', 'Bob', 'Charlie'], 'Age': [25, 30, 35], 'City': ['New York', 'Los Angeles', 'Chicago']}
df = pd.DataFrame(data)

# Displaying the DataFrame
print("DataFrame:\n", df)

# Adding a new column
df['Salary'] = [70000, 80000, 90000]

# Filtering rows where Age > 30
filtered_df = df[df['Age'] > 30]

# Displaying the filtered DataFrame
print("Filtered DataFrame:\n", filtered_df)
```

#### Example 2: Grouping and Aggregation
```python
import pandas as pd

# Creating a DataFrame
data = {'Department': ['HR', 'HR', 'IT', 'IT', 'Finance'], 'Salary': [50000, 60000, 75000, 85000, 65000]}
df = pd.DataFrame(data)

# Grouping by Department and calculating mean salary
grouped_df = df.groupby('Department').mean()

# Displaying the grouped DataFrame
print("Grouped DataFrame:\n", grouped_df)
```

#### Example 3: Handling Missing Data
```python
import pandas as pd
import numpy as np

# Creating a DataFrame with missing values
data = {'Name': ['Alice', 'Bob', 'Charlie'], 'Age': [25, np.nan, 35], 'City': ['New York', 'Los Angeles', np.nan]}
df = pd.DataFrame(data)

# Displaying the DataFrame with missing values
print("DataFrame with missing values:\n", df)

# Filling missing values with a specified value
df_filled = df.fillna({'Age': 30, 'City': 'Unknown'})

# Displaying the DataFrame after filling missing values
print("DataFrame after filling missing values:\n", df_filled)
```



