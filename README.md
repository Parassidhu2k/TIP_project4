# Welcome to FraudShield: Intelligent Credit Card Fraud Detection Project #

The goal is to detect fraudulent transactions using intelligent machine-learning techniques.

## Credit Card Fraud Transaction Analysis

### Libraries and Their Basic Uses

#### **1. pandas**

**Purpose**: Data manipulation and analysis.

- **Reading Data**:
    ```python
    import pandas as pd
    df = pd.read_csv("fraudTest.csv")
    ```
  - **Concept**: `pd.read_csv` loads data from a CSV file into a DataFrame named `df`.

- **Datetime Conversion**:
    ```python
    df['trans_date_trans_time'] = pd.to_datetime(df['trans_date_trans_time'], errors='coerce')
    ```
  - **Concept**: Converts a column to datetime format.

#### **2. numpy**

**Purpose**: Numerical operations.

- **Example**:
    ```python
    import numpy as np
    df['age'] = np.floor((df['trans_date_trans_time'].dt.year - df['dob'].dt.year))
    ```
  - **Concept**: `np.floor` is used for rounding numbers.

#### **3. matplotlib**

**Purpose**: Plotting graphs.

- **Example**:
    ```python
    import matplotlib.pyplot as plt
    plt.hist(df['amt'])
    plt.show()
    ```
  - **Concept**: `plt.hist` creates a histogram.

#### **4. seaborn**

**Purpose**: Statistical data visualization.

- **Example**:
    ```python
    import seaborn as sns
    sns.histplot(df['amt'])
    plt.show()
    ```
  - **Concept**: `sns.histplot` creates a histogram with enhanced aesthetics.

#### **5. re**

**Purpose**: Regular expressions for text processing.

- **Example**:
    ```python
    import re
    df['clean_col'] = df['raw_col'].apply(lambda x: re.sub(r'[^\w\s]', '', x))
    ```
  - **Concept**: `re.sub` is used to replace text patterns.

### Data Cleaning and Preprocessing

#### **Reading the Data**

```python
df = pd.read_csv("fraudTest.csv")
```

- **Concept**: Loads the CSV file into a DataFrame.

#### **Datetime Conversion**

```python
df['trans_date_trans_time'] = pd.to_datetime(df['trans_date_trans_time'], errors='coerce')
```

- **Concept**: Converts string dates to datetime objects.

#### **Gender Encoding**

```python
df['gender'] = df['gender'].str.lower().apply(lambda x: 1 if x == 'male' else 0)
```

- **Concept**: Converts gender to binary values.

#### **Special Characters Handling**

```python
df['clean_col'] = df['raw_col'].apply(lambda x: re.sub(r'[^\w\s]', '', x))
```

- **Concept**: Removes non-alphanumeric characters.

#### **Unnamed Columns Removal**

```python
unnamed_columns = [col for col in df.columns if 'Unnamed' in col]
df = df.drop(columns=unnamed_columns)
```

- **Concept**: Deletes unnecessary columns.

#### **Lowercase Conversion**

```python
df['text_col'] = df['text_col'].str.lower()
```

- **Concept**: Converts text to lowercase for consistency.

#### **Duplicate Records**

```python
df = df.drop_duplicates()
```

- **Concept**: Removes duplicate rows.

### Exploratory Data Analysis (EDA)

#### **Gender Distribution**

```python
sns.countplot(x='gender', data=df)
plt.show()
```

- **Concept**: Visualizes the count of each gender.

#### **Fraudulent vs. Non-Fraudulent Transactions**

```python
sns.countplot(x='is_fraud', data=df)
plt.show()
```

- **Concept**: Compares the number of fraudulent vs. non-fraudulent transactions.

#### **Distribution of Transaction Dates**

```python
sns.histplot(df['trans_date_trans_time'])
plt.show()
```

- **Concept**: Shows transaction date distribution.

#### **Transaction Amount vs. Fraud Status**

```python
sns.boxplot(x='is_fraud', y='amt', data=df)
plt.show()
```

- **Concept**: Compares transaction amounts for fraud vs. non-fraud cases.

#### **Distribution of Transaction Categories**

```python
sns.countplot(x='category', data=df)
plt.show()
```

- **Concept**: Shows the frequency of transaction categories.

#### **Age Distribution of Cardholders**

```python
df['age'] = df['trans_date_trans_time'].dt.year - df['dob'].dt.year
sns.histplot(df['age'])
plt.show()
```

- **Concept**: Visualizes the age distribution of cardholders.

#### **Transaction Amount vs. Cardholder Age**

```python
sns.scatterplot(x='age', y='amt', data=df, hue='is_fraud')
plt.show()
```

- **Concept**: Shows the relationship between age and transaction amount.

#### **Distribution of Merchant Locations**

```python
sns.scatterplot(x='merch_long', y='merch_lat', data=df, hue='is_fraud')
plt.show()
```

- **Concept**: Visualizes merchant locations on a map.

#### **Monthly Transaction Volume**

```python
df['month'] = df['trans_date_trans_time'].dt.month
sns.countplot(x='month', data=df)
plt.show()
```

- **Concept**: Displays transaction volume per month.

#### **Distribution of Transaction Times**

```python
df['hour'] = df['trans_date_trans_time'].dt.hour
sns.histplot(df['hour'])
plt.show()
```

- **Concept**: Shows transaction times throughout the day.

#### **Transaction Frequency by Cardholder**

```python
cardholder_freq = df.groupby(['first', 'last'])['trans_num'].count().reset_index()
cardholder_freq = cardholder_freq.sort_values(by='trans_num', ascending=False).head(10)
sns.barplot(x='trans_num', y='first', data=cardholder_freq)
plt.show()
```

- **Concept**: Displays the top cardholders by transaction frequency.

#### **Transaction Amount vs. City Population**

```python
sns.scatterplot(x='city_pop', y='amt', data=df, hue='is_fraud')
plt.show()
```

- **Concept**: Analyzes transaction amount vs. city population.

#### **Top 10 Job Categories**

```python
top_jobs = df['job'].value_counts().nlargest(10)
sns.barplot(x=top_jobs.index, y=top_jobs.values)
plt.show()
```

- **Concept**: Shows the most common job categories.

#### **Transaction Amount vs. Merchant Category**

```python
sns.boxplot(x='category', y='amt', data=df)
plt.xticks(rotation=45)
plt.show()
```

- **Concept**: Compares transaction amounts by merchant category.

#### **Fraudulent Transactions by State**

```python
sns.countplot(x='state', data=df[df['is_fraud'] == 1])
plt.xticks(rotation=45)
plt.show()
```

- **Concept**: Shows the distribution of fraudulent transactions by state.

#### **Average Transaction Amount by Gender**

```python
avg_amt_by_gender = df.groupby('gender')['amt'].mean().reset_index()
sns.barplot(x='gender', y='amt', data=avg_amt_by_gender)
plt.show()
```

- **Concept**: Compares average transaction amounts by gender.

#### **Distribution of Transaction Times by Gender**

```python
sns.histplot(df[df['gender'] == 1]['hour'], color='blue', label='Male')
sns.histplot(df[df['gender'] == 0]['hour'], color='pink', label='Female')
plt.legend()
plt.show()
```

- **Concept**: Compares transaction times for different genders.

#### **Fraudulent Transactions Over Time**

```python
fraud_over_time = df[df['is_fraud'] == 1].groupby(df['trans_date_trans_time'].dt.date).size()
fraud_over_time.plot()
plt.xlabel('Date')
plt.ylabel('Number of Fraudulent Transactions')
plt.show()
```

- **Concept**: Shows trends in fraudulent transactions over time.

#### **Total Transaction Amounts by Category and Gender**

```python
top_10_categories = df['category'].value_counts().nlargest(10).index
grouped = df[df['category'].isin(top_10_categories)].groupby(['category', 'gender'])['amt'].sum().unstack()
grouped.plot(kind='bar', stacked=True)
plt.show()
```

- **Concept**: Analyzes total transaction amounts by category and gender.

#### **Fraud Transactions by City Population Segment**

```python
df['city_pop_segment'] = pd.cut(df['city_pop'], bins=[0, 10000, 50000, 100000, 500000, 1000000, float('Inf')], labels=['<10k', '10k-50k', '50k-100k', '100k-500k', '500k-1M', '>1M'])
sns.countplot(x='city_pop_segment', data=df[df['is_fraud'] == 1])
plt.show()
```

- **Concept**: Shows fraud transactions by city population density.

#### **Fraud Transactions by Distance from Customer Residence**

```python
df['distance'] = np.sqrt((df['merch_lat'] - df['lat'])**2 + (df['merch_long'] - df['long'])**2)
plt.pie(df[df['is_fraud'] == 1]['distance'].value_counts().nlargest(5

), autopct='%1.1f%%')
plt.show()
```

- **Concept**: Visualizes fraud transactions by distance from residence.

#### **Top 10 Fraudulent Records**

```python
top_10_fraud = df[df['is_fraud'] == 1].nlargest(10, 'amt')
sns.barplot(x='amt', y='first', data=top_10_fraud)
plt.show()
```

- **Concept**: Shows the top 10 fraudulent transactions.

#### **Correlation Matrix**

```python
sns.heatmap(df.corr(), annot=True)
plt.show()
```

- **Concept**: Displays correlation between numeric columns.

### How to Use

1. **Clone Repository**:
    ```bash
    git clone https://github.com/Parassidhu2k/TIP_project4.git
    ```

2. **Install Libraries**:
    ```bash
    pip install pandas numpy matplotlib seaborn
    ```

3. **Open Jupyter Notebook**:
    - Open the `.ipynb` file in Jupyter Notebook to view and execute the code.





