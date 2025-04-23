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

# Coding and Output

REG No: 212224230248

NAME: Santhose Arockiaraj J

### Reading the CSV file

```
import pandas as pd
df=pd.read_csv("/content/SAMPLEIDS (1).csv")
df
```
![image](https://github.com/user-attachments/assets/3e463418-72dc-406d-8fbc-6ce5eb628494)

```
df.shape
```
![image](https://github.com/user-attachments/assets/8b8742a5-1227-4e67-b55b-3b979d8e9a9b)

```
df.shape[0]# return the no. of rows
```
![image](https://github.com/user-attachments/assets/a374108d-06f0-4d72-8067-65fb6637edfb)
```
df.shape[1]# return the no.columns
```
![image](https://github.com/user-attachments/assets/e7147bec-ce4d-4a9d-b276-b1cb80e72f1a)
```
df.isnull()# return True if there is a null else return False
```
![image](https://github.com/user-attachments/assets/31c6427e-979c-4e50-933b-fa0e9202d16f)
```
df.isnull().sum()
```
![image](https://github.com/user-attachments/assets/140a49e7-5fbe-4803-abe4-a8b638db6235)
```
df.notnull()# return False if there is a null else return True
```
![image](https://github.com/user-attachments/assets/034d04c3-104d-4ac9-8115-c15c580b8868)
### Removing Null
```
#used to remove the null value based on the parameter passed
df.dropna(axis=0) #changes happen in rows
#it will only Temperorly remove the null value
```
![image](https://github.com/user-attachments/assets/32222ad5-38ca-4cf6-ac82-dc598c3697f3)
```
df.dropna(axis=1)
```
![image](https://github.com/user-attachments/assets/2ff8c0ad-2df7-4655-be78-08b1a79fde5d)
```
df.dropna(how='any')
```
![image](https://github.com/user-attachments/assets/d8eef543-a31c-43b1-92ab-7d1078838d8f)
```
df.dropna(how='all')#remove only when all the elements int the row is null
```
![image](https://github.com/user-attachments/assets/58692050-f492-4264-bae0-b56d60581bc0)
### Filtering and Selecting value with condition

```
dfs=df[df['TOTAL']>270]
dfs
```
![image](https://github.com/user-attachments/assets/a4a8f703-96d0-4926-b6e2-13b3e05aae14)

```
dfs=df[df['NAME'].str.startswith(('A','P'))& (df['TOTAL']>250)]
dfs
```
![image](https://github.com/user-attachments/assets/81666e80-56d7-4d18-be72-6c91316c4771)

### Using iloc() function //Slicing the data sets

```
df.iloc[:4]
```
![image](https://github.com/user-attachments/assets/9f9027c1-1655-41a2-9e18-df2322b9b1e5)

```
df.iloc[0:4,1:4]
```
![image](https://github.com/user-attachments/assets/f15f76dc-7420-428e-be51-f704ff5e3e8b)

```
df.iloc[[1,3,5],[1,3]]
```
![image](https://github.com/user-attachments/assets/f9188818-be2c-4540-935b-090896ec7b96)

### FILLING NULL VALUES
```
dff=df.fillna(0)
dff
```
![image](https://github.com/user-attachments/assets/c897da94-e153-4012-bdba-ca654585082b)
```
#Filling with MEAN(),FFILL(),BFILL()
df1=df['TOTAL'].fillna(value=df['TOTAL'].mean())
df1
```
![image](https://github.com/user-attachments/assets/caae471e-d630-463f-a2d6-14127a85f61e)
```
df.fillna(method='ffill')
```
![image](https://github.com/user-attachments/assets/95597ecd-3ea6-43ca-823b-24fbcd83648e)
```
df.fillna(method='bfill')
```
![image](https://github.com/user-attachments/assets/06943ece-622f-4695-b07f-ab49e3e50ed0)
```
import pandas as pd
df=pd.read_csv("/content/SAMPLEIDS.csv")
df['TOTAL'].fillna(value=df['TOTAL'].mean())
df
```
![image](https://github.com/user-attachments/assets/ced5d606-6ec9-4aa2-8af9-cc0299a28e47)
```
mn=df['TOTAL'].mean()
mn
```
![image](https://github.com/user-attachments/assets/2a3b7a2d-aadb-44e5-a139-5fd1e5da8b9c)
```
df['TOTAL']
```
![image](https://github.com/user-attachments/assets/97ea7c9a-ee05-4d81-8423-ef248e76da89)
```
amn=df['AVG'].mean()
amn
```
![image](https://github.com/user-attachments/assets/2aa188bd-dad3-4f70-b5bb-43487609a362)
```
df['AVG'].fillna(amn,inplace=True)
ing for df
```
![image](https://github.com/user-attachments/assets/fb797da5-8d3b-4fb2-87a4-b9bf029c780c)

### Checking for Duplicates

```
df.duplicated()
```
![image](https://github.com/user-attachments/assets/3a719ad0-7f98-4c86-8766-6e2deeda33ef)
```
df.drop_duplicates(inplace=True) #Removing dupilactes from data set permanently
df
```
![image](https://github.com/user-attachments/assets/b8de58af-c282-4300-a838-0e8a56cb44ef)
```
import seaborn as sns
sns.heatmap(df.isnull(),yticklabels=False,annot=True)
```
![image](https://github.com/user-attachments/assets/d91ff6a2-f871-4844-9eb0-8c8567ce72e3)
```
df.dropna(inplace=True)
sns.heatmap(df.isnull(),yticklabels=False,annot=True)
df
```
![image](https://github.com/user-attachments/assets/34ffe22a-8752-4ca0-acf2-2492bacc9fd3)

### OUTLIERS DETECTION AND REMOVAL USING IQR

```
from re import A
import pandas as pd
import numpy as np
import seaborn as sns
age=[1,3,28,27,25,92,30,39,40,50,26,24,29,94]
af=pd.DataFrame(age)
af
```
![image](https://github.com/user-attachments/assets/f554078b-10fb-41ca-b796-b28c371f3a4c)
```
sns.boxplot(data=af)
```
![image](https://github.com/user-attachments/assets/57fe594d-b28c-4d78-8d85-69c95bfe622d)
```
sns.scatterplot(data=af)
```
![image](https://github.com/user-attachments/assets/f39881e1-20e9-4b65-9235-989557330659)
```
q1=af.quantile(0.25)
q2=af.quantile(0.5)
q3=af.quantile(0.75)
iqr=q3-q1
iqr
```
![image](https://github.com/user-attachments/assets/23e8cb04-9d97-47f4-8de7-a41d3f33220f)

```
q1=np.percentile(af,25)
q3=np.percentile(af,75)
iqr=q3-q1
iqr
```
![image](https://github.com/user-attachments/assets/5e51e184-f6b8-4fc7-b61e-7fe7bd70b58c)
```
upper_bound=q3+1.5*iqr
lower_bound=q1-1.5*iqr
upper_bound
```
![image](https://github.com/user-attachments/assets/911008b2-ffd8-4451-853a-2e04ec949361)
```
lower_bound
```
![image](https://github.com/user-attachments/assets/2ffd3a18-92da-41b3-ba4b-179ad1f65a5c)
```
outlier=[x for x in age if x<lower_bound or x>upper_bound]
print("Q1 :",q1)
print("Q3 :",q3)
print("IQR :",iqr)
print("Lower Bound :",lower_bound)
print("Upper Bound :",upper_bound)
print("Outliers :",outlier)
```
![image](https://github.com/user-attachments/assets/bc95d47a-5743-4bd4-bc7d-ce96de705175)
```
#Actual Method
af=af[((af>=lower_bound)&(af<=upper_bound))]
af
```
![image](https://github.com/user-attachments/assets/94f9fe26-77c2-4848-802d-74f858980e27)
```
![image](https://github.com/user-attachments/assets/78d498a9-b3d2-4b31-80bc-c0bc811feb38)
```
![image](https://github.com/user-attachments/assets/806394c5-0d27-41c8-9614-193369dcb891)
```
sns.boxplot(data=af)
```
![image](https://github.com/user-attachments/assets/f96e12f8-1a4d-4e13-884d-051f8194fd0e)

```
sns.scatterplot(data=af)
```
![image](https://github.com/user-attachments/assets/1c8ec28e-75f4-4481-afd8-cc04b17d3476)
### OUTLIERS DETECTION AND REMOVAL USING Z
```

data=[1,2,2,2,3,1,1,15,2,2,2,3,1,1,2]
mean=np.mean(data)
std=np.std(data)
print('Mean of the dataset is',mean)
print('Standard deviation is',std)
```
![image](https://github.com/user-attachments/assets/e868fcd3-ca70-4ee3-9cf8-4b1d11eb5ec6)
```
threshold=3
outlier=[]
for i in data:
  z=(i-mean)/std
  if z>threshold:
    outlier.append(i)
print("Outlier in Dataset",outlier)
```
![image](https://github.com/user-attachments/assets/f9cfe77e-84a3-4cad-ad9c-3851241a9f82)


# Result
   Thus we have cleaned the data and removed the outliers ny detcection using IQR and Z-score.
