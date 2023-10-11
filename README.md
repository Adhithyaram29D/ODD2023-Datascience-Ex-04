### AIM
To perform Multivariate EDA on the given data set.

### EXPLANATION
Exploratory data analysis is used to understand the messages within a dataset.
This technique involves many iterative processes to ensure that the cleaned data is further sorted to better understand the useful meaning.
The primary aim with exploratory analysis is to examine the data for distribution, outliers and anomalies to direct specific testing of your hypothesis.
### ALGORITHM
## STEP 1
Import the built libraries required to perform EDA and outlier removal.

## STEP 2
Read the given csv file

## STEP 3
Convert the file into a dataframe and get information of the data.

## STEP 4
Return the objects containing counts of unique values using (value_counts()).

## STEP 5
Plot the counts in the form of Histogram or Bar Graph.

## STEP 6
Use seaborn the bar graph comparison of data can be viewed.

## STEP 7
Find the pairwise correlation of all columns in the dataframe.corr()

## STEP 8
Save the final data set into the file

### CODE
## Diabetes.csv
```
import pandas as pd
import numpy as np
import seaborn as sns
from scipy import stats
import matplotlib.pyplot as plt
df = pd.read_csv("/content/diabetes.csv")
df.info()
df.isnull().sum()
sns.boxplot(data=df)

#DATA CLEANING
z = np.abs(stats.zscore(df['Glucose']))
dfc=df[(z<2)]
z = np.abs(stats.zscore(dfc['BloodPressure']))
dfc=dfc[(z<2)]
z = np.abs(stats.zscore(dfc['SkinThickness']))
dfc=dfc[(z<3)]
z = np.abs(stats.zscore(dfc['BMI']))
dfc=dfc[(z<2)]
z = np.abs(stats.zscore(dfc['Insulin']))
dfc=dfc[(z<2)]
z = np.abs(stats.zscore(dfc['DiabetesPedigreeFunction']))
dfc=dfc[(z<2)]
z = np.abs(stats.zscore(dfc['Age']))
dfc=dfc[(z<2)]
z = np.abs(stats.zscore(dfc['Outcome']))
dfc=dfc[(z<3)]

sb.boxplot(data=dfc)
plt.figure(figsize = (14,6))
sb.scatterplot(x = 'Glucose',y='BloodPressure',data = df)
sb.scatterplot(x = 'Glucose',y='Insulin',data = df)
sb.scatterplot(x = 'Glucose',y='DiabetesPedigreeFunction',data = df)
sb.scatterplot(x = 'Glucose',y='Age',data = df)
sb.heatmap(df.corr(),annot = True)
```
## Superstore.csv
```
import pandas as pd
import seaborn as sns
import numpy as np
from scipy import stats
import matplotlib as plt
df=pd.read_csv("/content/SuperStore.csv")
df.isnull().sum()

# FILLING NULL VALUES
df['Postal Code'] = df['Postal Code'].fillna(value=df['Postal Code'].mode()[0])
df.isnull().sum()
sb.boxplot(data=df)

# DATA CLEANING
z = np.abs(stats.zscore(df['Sales']))
df = df[z<3]
sb.boxplot(data=df['Sales'])
sb.scatterplot(x = 'Postal Code',y='Sales',data = df)
sb.scatterplot(x = 'Row ID',y='Sales',data = df)
sb.heatmap(df.corr(),annot = True)
```
### OUTPUT
## Diabetes.csv
## Before DataCleaning
![Screenshot 2023-10-07 091240](https://github.com/Adhithyaram29D/ODD2023-Datascience-Ex-04/assets/119393540/c07572be-0a75-400f-b486-d721f6b34cb4)
## After DataCleaning
![Screenshot 2023-10-07 091558](https://github.com/Adhithyaram29D/ODD2023-Datascience-Ex-04/assets/119393540/844b76a5-040a-45e0-a933-89c43b2c8fe0)
![Screenshot 2023-10-07 091612](https://github.com/Adhithyaram29D/ODD2023-Datascience-Ex-04/assets/119393540/83ac872b-52a4-42c2-abec-28683c9f47d0)
![Screenshot 2023-10-07 091630](https://github.com/Adhithyaram29D/ODD2023-Datascience-Ex-04/assets/119393540/50a407d9-618f-4b66-8136-273b065da6a9)
![Screenshot 2023-10-07 091644](https://github.com/Adhithyaram29D/ODD2023-Datascience-Ex-04/assets/119393540/75ec8f88-0528-4dfd-82b2-cdec949241e3)

# HeatMap
![Screenshot 2023-10-07 091658](https://github.com/Adhithyaram29D/ODD2023-Datascience-Ex-04/assets/119393540/2ef3e8cb-74ae-4790-9301-77ce644dc273)

## Superstore.csv
## BeforeDataCleaning
![download](https://github.com/Adhithyaram29D/ODD2023-Datascience-Ex-04/assets/119393540/1581c43e-1702-459c-b35e-ad61e1ee08dd)

## AfterDataCleaning
![download](https://github.com/Adhithyaram29D/ODD2023-Datascience-Ex-04/assets/119393540/871c76c5-094e-4b04-8f42-b44889f3ae02)
![download](https://github.com/Adhithyaram29D/ODD2023-Datascience-Ex-04/assets/119393540/3656c885-a48b-49dd-999a-ff33103a3cdb)
![download](https://github.com/Adhithyaram29D/ODD2023-Datascience-Ex-04/assets/119393540/fa9e56a6-8bcb-46ac-b8bf-7e6d50d7cd9e)

# HeatMap
![download](https://github.com/Adhithyaram29D/ODD2023-Datascience-Ex-04/assets/119393540/3c93372b-ef1d-4492-8a55-99af0bd62797)

### RESULT
Thus we have read the given data and performed the multivariate analysis with different types of plots.

