# EXNO2DS
# AIM:
To perform Exploratory Data Analysis on the given data set.
      
# EXPLANATION:
  The primary aim with exploratory analysis is to examine the data for distribution, outliers and anomalies to direct specific testing of your hypothesis.
  
# ALGORITHM:
STEP 1: Import the required packages to perform Data Cleansing,Removing Outliers and Exploratory Data Analysis.

STEP 2: Replace the null value using any one of the method from mode,median and mean based on the dataset available.

STEP 3: Use boxplot method to analyze the outliers of the given dataset.

STEP 4: Remove the outliers using Inter Quantile Range method.

STEP 5: Use Countplot method to analyze in a graphical method for categorical data.

STEP 6: Use displot method to represent the univariate distribution of data.

STEP 7: Use cross tabulation method to quantitatively analyze the relationship between multiple variables.

STEP 8: Use heatmap method of representation to show relationships between two variables, one plotted on each axis.

## CODING AND OUTPUT
```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns

dt=pd.read_csv('titanic_dataset.csv')
dt
dt.info()

#DISPLAY NO OF ROWS AND COLUMNS
print("Number of rows:", dt.shape[0])
print("Number of columns:", dt.shape[1])

#SET PASSENGER ID AS INDEX COLUMN
dt.set_index('PassengerId', inplace=True)

dt.describe()

# USE VALUE COUNT FUNCTION AND PERFROM CATEGORICAL ANALYSIS
categorical_cols = dt.select_dtypes(include=['object']).columns
for col in categorical_cols:
  print(f"\nValue counts for {col}:\n{dt[col].value_counts()}")
```
![Screenshot 2024-09-13 190246](https://github.com/user-attachments/assets/01d34c25-cf0b-475f-928e-f2050152a576)
![Screenshot 2024-09-13 190302](https://github.com/user-attachments/assets/c588bef6-ce25-4e95-80d7-f1725f8fea9e)
![Screenshot 2024-09-13 190311](https://github.com/user-attachments/assets/81071be4-1ad6-4771-a8d5-653bb46f8094)

```python
# USE COUNTPLOT AND PERFORM UNIVARIATE ANALYSIS FOR THE "SURVIVED" COLUMN IN TITANIC DATASET
# IDENTIFY UNIQUE VALUES IN "PASSENGER CLASS" COLUMN
# RENAMING COLUMN

import matplotlib.pyplot as plt
sns.countplot(x='Survived', data=dt)
plt.show()

print(dt['Pclass'].unique())
dt.rename(columns = {'Sex':'Gender'}, inplace = True)
dt
```
![Screenshot 2024-09-13 190502](https://github.com/user-attachments/assets/d0747259-7835-4883-86d1-ca12a56c6898)
![Screenshot 2024-09-13 190519](https://github.com/user-attachments/assets/e70f21bb-4259-4c10-a27b-5a2ce7806916)

```python
# USE CATPLOT METHOD FOR BIVARIATE ANALYSIS
# fig, ax1 = plt.subplots(figsize=(8,5))
# graph = sns.countplot()
# graph.set_xticklabels(graph.get_xticklabels())
# for p in graph.patches:
#                       height = p.get_height()
#                       graph.text(p.get_x()+p.get_width()/2, height + 20.8,height ,ha="left")
# USE BOXPLOT METHOD TO ANALYZE AGE AND SURVIVED COLUMN
import matplotlib.pyplot as plt
sns.catplot(x='Survived', hue='Gender', kind='count', data=dt)
plt.show()

sns.boxplot(x='Survived', y='Age', data=dt)
plt.show()
```
![Screenshot 2024-09-13 190638](https://github.com/user-attachments/assets/52cddc0a-5fd5-44a8-a18c-2864168d8826)
![Screenshot 2024-09-13 190647](https://github.com/user-attachments/assets/3f79f3cb-37e6-44e1-8a81-ab8e38f87da3)

```python

# USE BOXPLOT METHOD AND ANALYZE THREE COLUMNS(PCLASS,AGE,GENDER)
# USE CATPLOT METHOD AND ANALYZE THREE COLUMNS(PCLASS,SURVIVED,GENDER)
# IMPLEMENT HEATMAP AND PAIRPLOT FOR THE DATASET

import matplotlib.pyplot as plt
sns.boxplot(x='Pclass', y='Age', hue='Gender', data=dt)
plt.show()
sns.catplot(x='Pclass', hue='Gender', kind='count', data=dt)
plt.show()

# Heatmap
corr_matrix = dt.select_dtypes(include=np.number).corr() # Select only numerical columns for correlation calculation
sns.heatmap(corr_matrix, annot=True, cmap='coolwarm')
plt.show()
# Pairplot
sns.pairplot(dt)
plt.show()
```
![Screenshot 2024-09-13 190740](https://github.com/user-attachments/assets/f0404c4f-d74f-4189-9e2a-60a1866ad797)
![Screenshot 2024-09-13 190751](https://github.com/user-attachments/assets/148bba55-9b34-42ad-a948-4a0fd94ded10)
![Screenshot 2024-09-13 190802](https://github.com/user-attachments/assets/cc228d3c-ba3f-45dc-9ec0-6687ae0d08d4)
![Screenshot 2024-09-13 191102](https://github.com/user-attachments/assets/84c7e31c-91ff-4382-8edc-b424ef53b86b)
![Screenshot 2024-09-13 191119](https://github.com/user-attachments/assets/cbe97b37-6b61-4321-9397-f5894b627184)
# RESULT
Thus the data analysis has been implemented succesfully.
