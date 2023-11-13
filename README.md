# Ex-09-Data-Visualization-2

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
Developed By: Sabitha P
Reg No: 212222040137
```
### Load Dataset
```python
import seaborn as sns
import pandas as pd
import matplotlib.pyplot as plt
df=sns.load_dataset("tips")
print(df)
```
# Output:
![image](https://github.com/sabithapaulraj/ODD2023-Datascience-Ex-09/assets/118343379/a4c30874-5b10-4441-9f8a-beff2f344491)

```python
df.isnull().sum()
```
# Output:
![image](https://github.com/sabithapaulraj/ODD2023-Datascience-Ex-09/assets/118343379/4f05391f-4fdd-45ec-a250-7e5bc89de623)

### Handling Outliers
```python
plt.figure(figsize=(5,5))
plt.title("Data with Outliers")
df.boxplot()
plt.show()
```
# Output:
![image](https://github.com/sabithapaulraj/ODD2023-Datascience-Ex-09/assets/118343379/b41d54ee-8e0f-424d-ae3f-755630c026cf)

### Removing outliers
```python
plt.figure(figsize=(9,6))
cols=["size","tip","total_bill"]
q1=df[cols].quantile(0.25)
q3=df[cols].quantile(0.75)
iqr=q3-q1
df=df[~((df[cols]<(q1-1.5*iqr))|(df[cols]>(q3+1.5*iqr))).any(axis=1)]
plt.title("dataset after removing outliners")
df.boxplot()
plt.show()
```
# Output:
![image](https://github.com/sabithapaulraj/ODD2023-Datascience-Ex-09/assets/118343379/a6ea5ea1-f3e5-4f0c-9e6b-1d473082ea84)

# 1) Which day of the week has the highest total bill amount ?
```python
# 1) Which day of the week has the highest total bill amount ?
sns.barplot(x=df['day'],y=df['total_bill'],hue=df['day'])
plt.legend(loc="center")
plt.title("Highest Total Bill Amount by day of the week")
plt.show()
```
# OuTput :
![image](https://github.com/sabithapaulraj/ODD2023-Datascience-Ex-09/assets/118343379/26567cd2-0c89-4be0-bbd5-62ed46643fde)


# 2) What is the average tip amount given by smokers and non_smokers?
```python
# 2) What is the average tip amount given by smokers and non-smokers?
sns.boxplot(x=df['smoker'],y=df['tip'],hue=df['smoker'])
plt.title("Average Tip Amount given by Smokers and Non-smokers")
```
# Output :
![image](https://github.com/sabithapaulraj/ODD2023-Datascience-Ex-09/assets/118343379/0821f152-fa0a-4297-a93d-a1406fec8d20)


# 3) How does the tip percentage vary based on the size of the dining party?
```python
# 3) How does the tip percentage vary based on the size of the dining party?
df["tip_percent"]=df["tip"]/df["total_bill"]
sns.scatterplot(x=df['size'],y=df['tip_percent'],data=df)
plt.title("Tip Percentage by Dining Party size")
```
# Output:
![image](https://github.com/sabithapaulraj/ODD2023-Datascience-Ex-09/assets/118343379/f3a9f0eb-18bc-4233-8481-ca53d5d09650)


# 4) Which gender tends to leave higher tips?
```python
# 4) Which gender tends to leave higher tips?
sns.boxplot(x=df['sex'],y=df['tip'],hue=df['sex'])
plt.title("Tips BAsed on gender")
```
# Output:
![image](https://github.com/sabithapaulraj/ODD2023-Datascience-Ex-09/assets/118343379/ead63fc3-2030-4ec4-9743-0ab356f4ecb2)


# 5) Is there any relationship between the total bill amount and the day of the week?
```python
sns.scatterplot(x=df['day'],y=df['total_bill'],hue=df['day'])
plt.legend(loc="best")
plt.title("Total bill amount by day of the week")
```
# Output:
![image](https://github.com/sabithapaulraj/ODD2023-Datascience-Ex-09/assets/118343379/e5bfc270-d2f8-43e6-a764-386fc50e1b6a)


# 6) How does the distribution of total bill amounts vary across different time periods (lunch vs. dineer)?
```python
sns.histplot(data=df,x="total_bill",hue="time",element="step",stat="density")
plt.title("Distribution of Total Bill Amounts by Time of Day")
plt.show()
```
# Output:
![image](https://github.com/sabithapaulraj/ODD2023-Datascience-Ex-09/assets/118343379/277ee427-31bc-4258-9a67-faec36f16df8)



# 7) Which dining party size group tends to have the highest average total bill amount?
```python
# 7) Which dining party size group tends to have the highest average total bill amount?
sns.barplot(x=df['size'],y=df['total_bill'],hue=df['size'])
plt.title("Average total Bill amount by Dininng party size]")
plt.show()
```
# Output:
![image](https://github.com/sabithapaulraj/ODD2023-Datascience-Ex-09/assets/118343379/6aa03d3f-99e0-4eb9-992d-b77176be10e0)


# 8) What is the distribution of tip amounts for each day of the week?
```python
# 8) What is the distribution of tip amounts for each day of the week?
sns.boxplot(x="day",y='tip',data=df)
plt.title("Tip amount by dy of Week")
plt.show()
```
# Output:

![image](https://github.com/sabithapaulraj/ODD2023-Datascience-Ex-09/assets/118343379/0d1e6047-dca8-4173-8ae2-e366199a3e95)


# 9) How does the amount vary based on the type of service (lunch vs. dinner)?
```python
# 9) How does the tip amount vary based on the type of service (lunch vs. dinner)?
sns.violinplot(x="time",y="tip",data=df)
plt.title("Tip Amount time Of day")
plt.show()
```
# Output:

![image](https://github.com/sabithapaulraj/ODD2023-Datascience-Ex-09/assets/118343379/446d4ea9-0ac2-4039-8283-23f3a9848971)

# 10) Is there any correlation between the total amount and amount and the tip amount ?
```python
# 10) Is there any correlation between the total bill amount and the tip amount?
sns.scatterplot(x="total_bill",y="tip",data=df)
plt.title("Correaltion between Tip Amount and Total Bill Amount")
plt.show()
```
# Output:

![image](https://github.com/sabithapaulraj/ODD2023-Datascience-Ex-09/assets/118343379/654c0250-25a1-470e-9ab5-c98c505ddc24)


# RESULT:
Thus, Data Visualization on a complex dataset has been performed successfully and the data is saved to a file.
