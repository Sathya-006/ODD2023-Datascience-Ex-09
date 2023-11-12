# Ex-09-Data-Visualization-

## AIM
To Perform Data Visualization on a complex dataset and save the data to a file. 

# Explanation
Data visualization is the graphical representation of information and data. By using visual elements like charts, graphs, and maps, data visualization tools provide an accessible way to see and understand trends, outliers, and patterns in data.

# ALGORITHM
### STEP 1
Read the given Data
### STEP 2
Clean the Data Set using Data Cleaning Process
### STEP 3
Apply Feature generation and selection techniques to all the features of the data set
### STEP 4
Apply data visualization techniques to identify the patterns of the data.


# CODE
```
import seaborn as sns
import pandas as pd
import matplotlib.pyplot as plt
df=sns.load_dataset("tips")
print (df)
```
![image](https://github.com/Sathya-006/ODD2023-Datascience-Ex-09/assets/121661327/37602120-0cde-491d-8caf-18ea65b56e00)
```
df.isnull().sum()
```
![image](https://github.com/Sathya-006/ODD2023-Datascience-Ex-09/assets/121661327/c2ab6355-d95d-4c70-9b44-f8906ae23b70)
## FINDING OUTLIERS
```
plt.figure(figsize=(5,5))
plt.title("Data with outliers")
df.boxplot()
plt.show()
```
![image](https://github.com/Sathya-006/ODD2023-Datascience-Ex-09/assets/121661327/7f17e87d-e4eb-43ca-b6ad-a54cfbdb6815)
## REMOVING OUTLIERS
```
plt.figure(figsize=(5,5))
cols=['total_bill','tip','size']
Q1=df[cols].quantile(0.25)
Q3=df[cols].quantile(0.75)
IQR=Q3-Q1
df=df[-((df[cols]<(Q1 - 1.5 * IQR))[df[cols]>(Q3 + 1.5 + IQR)]).any(axis=1)]
df.boxplot()
plt.show()
```
![image](https://github.com/Sathya-006/ODD2023-Datascience-Ex-09/assets/121661327/69e1ee7f-54fb-4454-bdab-369453051046)
## 1.Which day of the week has the highest total bill amount?
```
sns.barplot(x=df['day'],y=df['total_bill'],hue=df['day'])
plt.legend(loc="center")
plt.title("Highest Total Bill Amount of day of the week")
plt.show()
```
![image](https://github.com/Sathya-006/ODD2023-Datascience-Ex-09/assets/121661327/cd0dc72d-5565-45be-ac27-2f74a7fee463)
## 2.What is the average tip amount given by smokers and non-smokers?
```
sns.boxplot(x=df['smoker'],y=df['tip'],hue=df['smoker'])
plt.title("Averaga tip amount given by somkers and non-smokers")
```
![image](https://github.com/Sathya-006/ODD2023-Datascience-Ex-09/assets/121661327/b423ee9d-41ea-4991-b6b2-17dd604cb295)
## 3.How does the tip percentage vary based on the size of the dining party?
```
df["tip_percent"]=df["tip"]/df["total_bill"]
sns.scatterplot(x=df['size'],y=df['tip_percent'],data=df)
plt.title("Tip percentage by dining party size")
```
![image](https://github.com/Sathya-006/ODD2023-Datascience-Ex-09/assets/121661327/20237c37-8504-484a-b580-68a7d8988024)
## 4.Which gender tends to leave higher tips?
```
sns.boxplot(x=df['sex'],y=df['tip'],hue=df['sex'])
plt.title("Tips based on gender")
```
![image](https://github.com/Sathya-006/ODD2023-Datascience-Ex-09/assets/121661327/d5aaeb76-67c8-46f7-93f0-0b81a75174a5)
## 5.Is there any relationshio between the bill amount and the day of the week?
```
sns.scatterplot(x=df['day'],y=df['total_bill'],hue=df['day'])
plt.legend(loc="best")
plt.title("Total bill amount by day of the week")
```
![image](https://github.com/Sathya-006/ODD2023-Datascience-Ex-09/assets/121661327/c6ed992b-f7de-4468-8f15-98850bfb6dcc)
## 6.How does the distribution of total billa mounts vary across different time periods(lunch vs. dinner)?
```
sns.histplot(data=df,x="total_bill",hue="time",element="step",stat="density")
plt.title("Distribution of total bill amounts by time of day")
plt.show()
```
![image](https://github.com/Sathya-006/ODD2023-Datascience-Ex-09/assets/121661327/d2f1f4ff-d3d9-44d7-b179-6f34c21df2fe)
## 7. Why dining party size group tends to have the highest average total bill amount?
```
sns.barplot(x=df['size'],y=df['total_bill'],hue=df['size'])
plt.title("Average total bill amount by dining party size")
plt.show()
```
![image](https://github.com/Sathya-006/ODD2023-Datascience-Ex-09/assets/121661327/de2500ff-1458-422a-a601-a17e1269f191)
## 8.What is the distribution of tip amounts for each day of the week?
```
sns.boxplot(x="day",y="tip",data=df)
plt.title("Tip amount by day of week")
plt.show()
```
![image](https://github.com/Sathya-006/ODD2023-Datascience-Ex-09/assets/121661327/44ad3a16-c099-40ae-b274-8fb5d49c238a)
## 9.How does the tip amount vary based on the type of service (lunch vs. dinner)?
```
sns.violinplot(x="time",y="tip",data=df)
plt.title("Tip amount by time of day")
plt.show()
```
![image](https://github.com/Sathya-006/ODD2023-Datascience-Ex-09/assets/121661327/8d6d066a-e4cd-44a5-886f-14f22bb1f01a)
## 10.Is there any correlation between the total bill amount?
```
sns.scatterplot(x="total_bill",y="tip",data=df)
plt.title("Correlation between tip amount and totalbill amount")
plt.show()
```
![image](https://github.com/Sathya-006/ODD2023-Datascience-Ex-09/assets/121661327/428225ac-aa01-490e-ab43-465819dbc28f)

## RESULT
Thus the Data Visualization on a complex dataset is performed and saved the data to a file

