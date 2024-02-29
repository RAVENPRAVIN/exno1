# Exno:1
Data Cleaning Process

# AIM
To read the given data and perform data cleaning and save the cleaned data to a file.

# Explanation
Data cleaning is the process of preparing data for analysis by removing or modifying data that is incorrect ,incompleted , irrelevant , duplicated or improperly formatted. Data cleaning is not simply about erasing data ,but rather finding a way to maximize datasets accuracy without necessarily deleting the information.

# Algorithm
STEP 1: Read the given Data

STEP 2: Get the information about the data

STEP 3: Remove the null values from the data

STEP 4: Save the Clean data to the file

STEP 5: Remove outliers using IQR

STEP 6: Use zscore of to remove outliers


# Coding
### Data Cleaning Process
```
import pandas as pd

# Read CSV file
df = pd.read_csv('Data_set.csv')

# Display information about the CSV
print(df.info())
print(df.describe())

# Check for null values in the dataset
null_values = df.isnull().sum()
print(null_values)

# Display the sum of null values in each row
print(df.isnull().sum(axis=1))

# Drop null values
df_dropped = df.dropna()

# Fill null values with a constant value "O"
df_filled_const = df.fillna("O")

# Fill null values with ffill or bfill method
df_filled_ffill = df.fillna(method='ffill')
df_filled_bfill = df.fillna(method='bfill')

# Calculate mean value of a column and fill it with null values
mean_age = df['age'].mean()
df_filled_mean = df.fillna({'age': mean_age})

# Display the final dataframes
print(df_dropped)
print(df_filled_const)
print(df_filled_ffill)
print(df_filled_bfill)
print(df_filled_mean)

```
### Outlier Detection and Removal
```
import pandas as pd
import seaborn as sns
from scipy import stats

# Data
age = [1, 3, 28, 27, 25, 92, 30, 39, 40, 50, 26, 24, 29, 94]
data = [1, 12, 15, 18, 21, 24, 27, 30, 33, 36, 39, 42, 45, 48, 51, 54, 57, 60, 63, 66, 69, 72, 75, 78, 81, 84, 87, 90, 93, 96, 99, 158]

# Creating DataFrames
af = pd.DataFrame(age, columns=['Age'])
df = pd.DataFrame(data, columns=['Value'])

# Boxplot to detect outliers
sns.boxplot(x=af['Age'])
# plt.show()  # Use this if not using Jupyter Notebook or any other environment that displays plots automatically

# IQR Method
Q1 = af['Age'].quantile(0.25)
Q3 = af['Age'].quantile(0.75)
IQR = Q3 - Q1
lower_bound = Q1 - 1.5 * IQR
upper_bound = Q3 + 1.5 * IQR
outliers_af = af[(af['Age'] < lower_bound) | (af['Age'] > upper_bound)]
print("Outliers detected using IQR method:")
print(outliers_af)

# Remove outliers
af_no_outliers = af[(af['Age'] >= lower_bound) & (af['Age'] <= upper_bound)]

# Boxplot to check if outliers are removed
sns.boxplot(x=af_no_outliers['Age'])
# plt.show()

# Boxplot to detect outliers
sns.boxplot(x=df['Value'])
# plt.show()

# Z Score Method
z_scores = stats.zscore(df['Value'])
threshold = 3
outliers_df = df[(z_scores < -threshold) | (z_scores > threshold)]
print("\nOutliers detected using Z-score method:")
print(outliers_df)

# Remove outliers
df_no_outliers = df[(z_scores > -threshold) & (z_scores < threshold)]

# Boxplot to check if outliers are removed
sns.boxplot(x=df_no_outliers['Value'])
# plt.show()
```

# OUTPUT
# Data Cleaning Process
## READ_CSV
![csv read](https://github.com/ARAVIND23005370/exno1/assets/148514836/55d8ad9f-0426-454d-9143-9714e007506f)

## HEAD
![heads](https://github.com/ARAVIND23005370/exno1/assets/148514836/3083695f-be75-4d66-b98d-52728348633b)

## INFO
![info](https://github.com/ARAVIND23005370/exno1/assets/148514836/cd2d226f-e041-4859-a391-d01073bcafc0)

## DESCRIBE
![DESCRIBE](https://github.com/ARAVIND23005370/exno1/assets/148514836/3dd3d646-062f-4f61-85bf-adc38bae3501)

## ISNULL
![isnull](https://github.com/ARAVIND23005370/exno1/assets/148514836/51f4b9b8-7b7d-4491-8bf2-136c5394010f)

## ISNULL.SUM
![sums](https://github.com/ARAVIND23005370/exno1/assets/148514836/cca31b84-1d62-42f0-9c80-72e2d146a376)

## Fill null values with a constant value "O"
![out15](https://github.com/ARAVIND23005370/exno1/assets/148514836/12f73c6e-5865-480c-b039-55481efbf294)


## FILL NULL VALUES WITH ffill or bfill METHOD
![out16](https://github.com/ARAVIND23005370/exno1/assets/148514836/a76f988c-893e-4727-a833-915ed8d597bd)

## MODE
![mode](https://github.com/ARAVIND23005370/exno1/assets/148514836/edcc17fc-6a07-4b25-b3aa-d282bf55460c)

## MEAN
![mean](https://github.com/ARAVIND23005370/exno1/assets/148514836/d2a47b81-e26f-4bbc-9b96-443467b289c3)

## MEDIAN
![median](https://github.com/ARAVIND23005370/exno1/assets/148514836/0e6c34b4-ac45-4b56-8dcb-5314176941eb)

## AFTER CLEANING
![out14](https://github.com/ARAVIND23005370/exno1/assets/148514836/c6562fc1-728c-4b03-af97-beae082440de)


# Outlier Detection and Removal
# using IQR Methed
##  Data
![out1](https://github.com/ARAVIND23005370/exno1/assets/148514836/061096f3-ddb6-46ed-ae0e-28865c4b5984)


##  Boxplot to detect outliers
![out3](https://github.com/ARAVIND23005370/exno1/assets/148514836/8f46656a-295f-456a-83d6-5af0526eb779)

## IQR Method
![out9](https://github.com/ARAVIND23005370/exno1/assets/148514836/984ff3db-8600-4acf-9188-19cb6357c1a3)

##  Remove outliers
![out12](https://github.com/ARAVIND23005370/exno1/assets/148514836/f5a53c68-b550-42e3-a9ea-77c2fae0142a)

## Boxplot to check if outliers are removed
![out5](https://github.com/ARAVIND23005370/exno1/assets/148514836/58d88dbb-2c8a-4a3c-9a0f-8552423541ae)


# using Z-Score Method
## Data
![out10](https://github.com/ARAVIND23005370/exno1/assets/148514836/7940f266-c7ba-48a0-aa9b-442a7dddb139)

## Boxplot to detect outliers
![out6](https://github.com/ARAVIND23005370/exno1/assets/148514836/7c3a3823-045e-4ae1-ad6e-4aa9ad826ded)


## Z Score Method
![out7](https://github.com/ARAVIND23005370/exno1/assets/148514836/707b4849-06db-49d6-95a1-48220dfe21a2)

## Remove outliers

![out12](https://github.com/ARAVIND23005370/exno1/assets/148514836/86f54e8c-9843-41c3-8e29-36f9d25280a3)

## Boxplot to check if outliers are removed


![out13](https://github.com/ARAVIND23005370/exno1/assets/148514836/1728ded3-3462-480b-8435-79f4705662f8)


# Result
         
Hence the given data is read and perform data cleaning and saved the cleaned data to a file.
