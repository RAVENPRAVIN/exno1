Exno:1
Data Cleaning Process

AIM
To read the given data and perform data cleaning and save the cleaned data to a file.

Explanation
Data cleaning is the process of preparing data for analysis by removing or modifying data that is incorrect ,incompleted , irrelevant , duplicated or improperly formatted. Data cleaning is not simply about erasing data ,but rather finding a way to maximize datasets accuracy without necessarily deleting the information.

Algorithm
STEP 1: Read the given Data

STEP 2: Get the information about the data

STEP 3: Remove the null values from the data

STEP 4: Save the Clean data to the file

STEP 5: Remove outliers using IQR

STEP 6: Use zscore of to remove outliers

Coding
import pandas as pd
df=pd.read_csv("Data_set.csv")
print(df)
df.hesd(10)
df.tail(10)
df.info()
df.isnull().sum()
df['show_name']=df['show_name'].fillna(df['aired_on'].mode()[0])
df['aired_on']=df['aired_on'].fillna(df['aired_on'].mode()[0])
df['original_network']=df['original_network'].fillna(df['aired_on'].mode()[0])
df.head()
df['rating']=df['rating'].fillna(df['rating'].mean())
df['current_overall_rank']=df['current_overall_rank'].fillna(df['current_overall_rank'].mean())
df.head()
df['watchers']=df['watchers'].fillna(df['watchers'].median())
df.head()
df.info()
df.isnull().sum()

READ_CSV

![read](https://github.com/RAVENPRAVIN/exno1/assets/146820534/34df5aec-c7bb-4244-b481-e3935f805dd1)


HEAD
![head](https://github.com/RAVENPRAVIN/exno1/assets/146820534/521b3b1c-6fd2-4f90-b35c-3e4da9debae9)


TAIL


![tail](https://github.com/RAVENPRAVIN/exno1/assets/146820534/d46fff3a-7d85-4ed3-b390-480bdb7453ef)


INFO
output
![info](https://github.com/RAVENPRAVIN/exno1/assets/146820534/d0527683-4027-467c-b5c2-8eb65ac5d93b)



ISNULL

![isnull](https://github.com/RAVENPRAVIN/exno1/assets/146820534/e3ff7b0a-33b4-4906-a814-74de89b05baf)



ISNULL.SUM

![sum](https://github.com/RAVENPRAVIN/exno1/assets/146820534/5227d7c3-144f-4862-9a9f-aacb5b31ae3b)


MODE

![mode](https://github.com/RAVENPRAVIN/exno1/assets/146820534/4fe6b52a-523b-45ac-9c68-83cb92ca30eb)



MEAN

![mean](https://github.com/RAVENPRAVIN/exno1/assets/146820534/8b66312c-c6fa-42ba-a310-1ee7ce7829de)



MEDIAN


![median](https://github.com/RAVENPRAVIN/exno1/assets/146820534/e30847a1-9b8a-4dd5-a33b-8c8ca1e32d99)




AFTER CLEANING


Result
Hence the given data is read and perform data cleaning and saved the cleaned data to a file.
