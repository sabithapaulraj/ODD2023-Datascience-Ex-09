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
plt.figure(figsize=(8, 6))
sns.barplot(x='day', y='total_bill', data=df, estimator=sum, ci=None)
plt.title('Total Bill Amount by Day of the Week')
plt.show()
plt.figure(figsize=(10, 6))
sns.boxplot(x='day', y='total_bill', data=df)
plt.title('Total Bill Amount by Day of the Week (Boxplot)')
plt.show()
```
# Ouput :
![image](https://github.com/sabithapaulraj/ODD2023-Datascience-Ex-09/assets/118343379/ddd0186a-20bd-4397-ad98-8bbdc1f7a36e)
![image](https://github.com/sabithapaulraj/ODD2023-Datascience-Ex-09/assets/118343379/710c34e5-7def-4bbe-a848-9e911b124ee9)

# 2) What is the average tip amount given by smokers and non_smokers?
```python
# 2) What is the average tip amount given by smokers and non-smokers?
plt.figure(figsize=(8, 6))
sns.barplot(x='smoker', y='tip', data=df, estimator='mean', ci=None)
plt.title('Average Tip Amount for Smokers and Non-Smokers')
plt.show()

plt.figure(figsize=(8, 6))
sns.pointplot(x='smoker', y='tip', data=df, ci=None)
plt.title('Tip Amount for Smokers and Non-Smokers (Pointplot)')
plt.show()
```
# Output :
![image](https://github.com/sabithapaulraj/ODD2023-Datascience-Ex-09/assets/118343379/844fe5fa-07f4-438e-850d-528ef4cb9503)
![image](https://github.com/sabithapaulraj/ODD2023-Datascience-Ex-09/assets/118343379/17e0b136-339f-4c1f-a624-13f067e98aae)

# 3) How does the tip percentage vary based on the size of the dining party?
```python
# 3) How does the tip percentage vary based on the size of the dining party?
# Calculate tip percentage
df['tip_percentage'] = (df['tip'] / df['total_bill']) * 100

# Plot tip percentage based on the size of the dining party
plt.figure(figsize=(10, 6))
sns.scatterplot(x='size', y='tip_percentage', data=df)
plt.title('Tip Percentage by Dining Party Size')
plt.show()

plt.figure(figsize=(10, 6))
sns.barplot(x='size', y='tip_percentage', data=df, ci=None)
plt.title('Tip Percentage by Dining Party Size (Barplot)')
plt.show()
```
# Output:
![image](https://github.com/sabithapaulraj/ODD2023-Datascience-Ex-09/assets/118343379/0972ef1f-d0ce-412e-8bc9-4865c101b062)
![image](https://github.com/sabithapaulraj/ODD2023-Datascience-Ex-09/assets/118343379/c4e8dfa8-1c9c-4a16-af8c-061e7fe18a47)

# 4) Which gender tends to leave higher tips?
```python
# 4) Which gender tends to leave higher tips?
plt.figure(figsize=(8, 6))
sns.boxplot(x='sex', y='tip', data=df)
plt.title('Tip Amount by Gender (Boxplot)')
plt.show()

plt.figure(figsize=(8, 6))
sns.barplot(x='sex', y='tip', data=df, estimator='mean', ci=None)
plt.title('Average Tip Amount by Gender')
plt.show()
```
# Output:
![image](https://github.com/sabithapaulraj/ODD2023-Datascience-Ex-09/assets/118343379/e9ebf430-bb46-41dc-adcd-bd6f3f300121)
![image](https://github.com/sabithapaulraj/ODD2023-Datascience-Ex-09/assets/118343379/6e44e3ce-8211-46ca-bbe8-0d5980852244)

# 5) Is there any relationship between the total bill amount and the day of the week?
```python
# 5) Is there any relationship between the total bill amount and the day of the week?
plt.figure(figsize=(10, 6))
sns.boxplot(x='day', y='total_bill', data=df)
plt.title('Total Bill Amount by Day of the Week')
plt.show()
```
# Output:
![image](https://github.com/sabithapaulraj/ODD2023-Datascience-Ex-09/assets/118343379/6338967c-c304-4112-a376-c6b4cee6c567)

# 6) How does the distribution of total bill amounts vary across different time periods (lunch vs. dineer)?
```python
# 6) How does the distribution of total bill amounts vary across different time periods (lunch vs. dinner)?
plt.figure(figsize=(8, 6))
sns.boxplot(x='time', y='total_bill', data=df)
plt.title('Total Bill Distribution for Lunch and Dinner')
plt.show()
```
# Output:
![image](https://github.com/sabithapaulraj/ODD2023-Datascience-Ex-09/assets/118343379/52c3def4-6861-42af-a464-2f8eb8dea127)


# 7) Which dining party size group tends to have the highest average total bill amount?
```python
# 7) Which dining party size group tends to have the highest average total bill amount?
plt.figure(figsize=(10, 6))
sns.barplot(x='size', y='total_bill', data=df, estimator='mean', ci=None)
plt.title('Average Total Bill Amount by Dining Party Size')
plt.show()

plt.figure(figsize=(10, 6))
sns.boxplot(x='size', y='total_bill', data=df)
plt.title('Average Total Bill Amount by Dining Party Size (Boxplot)')
plt.show()
```
# Output:
![image](https://github.com/sabithapaulraj/ODD2023-Datascience-Ex-09/assets/118343379/7fced2a2-f3ff-4751-8440-003d74938bc2)
![image](https://github.com/sabithapaulraj/ODD2023-Datascience-Ex-09/assets/118343379/11ed15a9-6595-477b-9a78-905363a76e5a)

# 8) What is the distribution of tip amounts for each day of the week?
```python
# 8) What is the distribution of tip amounts for each day of the week?
plt.figure(figsize=(12, 6))
sns.boxplot(x='day', y='tip', data=df)
plt.title('Tip Amount Distribution by Day of the Week')
plt.show()
```
# Output:

![image](https://github.com/sabithapaulraj/ODD2023-Datascience-Ex-09/assets/118343379/86f17cc8-06ed-4ea1-b5cf-27db40bf204e)

# 9) How does the amount vary based on the type of service (lunch vs. dinner)?
```python
# 9) How does the tip amount vary based on the type of service (lunch vs. dinner)?
plt.figure(figsize=(8, 6))
sns.boxplot(x='time', y='tip', data=df)
plt.title('Tip Amount Variation for Lunch and Dinner')
plt.show()

plt.figure(figsize=(8, 6))
sns.pointplot(x='time', y='tip', data=df, ci=None)
plt.title('Tip Amount Variation for Lunch and Dinner (Pointplot)')
plt.show()
```
# Output:

![image](https://github.com/sabithapaulraj/ODD2023-Datascience-Ex-09/assets/118343379/aae1aaf1-9268-4758-9aca-5c1ddecbe2c9)

![image](https://github.com/sabithapaulraj/ODD2023-Datascience-Ex-09/assets/118343379/c48c6d4b-1a9c-441a-a145-a3bb3e27927b)

# 10) Is there any correlation between the total amount and amount and the tip amount ?
```python
# 10) Is there any correlation between the total bill amount and the tip amount?
plt.figure(figsize=(8, 6))
sns.scatterplot(x='total_bill', y='tip', data=df)
plt.title('Correlation Between Total Bill Amount and Tip Amount')
plt.show()

sns.pairplot(df, vars=['total_bill', 'tip'])
plt.suptitle('Correlation Between Total Bill Amount and Tip Amount (Pair Plot)')
plt.show()
```
# Output:

![image](https://github.com/sabithapaulraj/ODD2023-Datascience-Ex-09/assets/118343379/45154c27-a62c-4541-b631-c64d7deac4b3)

![image](https://github.com/sabithapaulraj/ODD2023-Datascience-Ex-09/assets/118343379/8c8d437d-3ee9-4bc2-96f3-a3df1700fb67)

# RESULT:
Thus, Data Visualization on a complex dataset has been performed successfully and the data is saved to a file.
