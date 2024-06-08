# Sales Analysis using Python

## Introduction
This README file will guide you through the process of creating a sales analysis using Python. We will use Jupyter Notebook along with libraries such as NumPy, Pandas, Matplotlib, and Seaborn. The analysis will cover several aspects, including data cleaning, exploration, and visualization.

## Requirements
Make sure you have the following libraries installed:
- numpy
- pandas
- matplotlib
- seaborn

You can install these libraries using pip:
```bash
pip install numpy
```
```bash
pip install pandas
```
```bash
pip install matplotlib
```
```bash
pip install seaborn
```


## Steps

1. **Load the Data**
   Load the data into a Pandas DataFrame.
   ```python
   import pandas as pd

   df = pd.read_csv('Sales Data.csv', encoding= 'unicode_escape')
   ```

2. **Display DataFrame Information**
   Display the information about the DataFrame to understand its structure.
   ```python
   df.info()
   ```

3. **Handle Null Values**
   Check for null values and remove them using `dropna()`.
   ```python
   pd.isnull(df).sum()
   df.dropna(inplace=True)
   ```

4. **Purchases and Purchase Amount by Gender**
   Create a bar graph to compare the number of purchases and purchase amount between males and females.
   ```python
   import matplotlib.pyplot as plt
   import seaborn as sns

   ax = sns.countplot(x='Gender',data = df)
   ax = sns.countplot(x='Gender',data = df)
   for bar in ax.containers:
     ax.bar_label(bar)
   ```
   ```python
   sales_gen = df.groupby(['Gender'], as_index=False)['Amount'].sum().sort_values(by='Amount',ascending = False)
   sns.barplot(x='Gender',y='Amount',data = sales_gen)
   
   ```

5. **Purchases and Purchase Amount by Age Group and Gender**
   Create a bar graph to compare the number of purchases and purchase amount amongst different age groups of males and females.
   ```python
   ax = sns.countplot(data = df,x='Age Group',hue='Gender')
   for bar in ax.containers:
       ax.bar_label(bar)
   ```
   ```python
   sales_age = df.groupby(['Age Group'],as_index = False)['Amount'].sum().sort_values(by='Amount',ascending=False)
   ax=sns.barplot(x='Age Group',y='Amount',data = sales_age)
   for bar in ax.containers:
       ax.bar_label(bar)
   ```

6. **Purchase Power by State**
   Create a graph to compare the purchase power between states, displaying only the top 10 states.
   ```python
   sales_state = df.groupby(['State'],as_index = False)['Orders'].sum().sort_values(by='Orders',ascending = False).head(10)
   sns.set(rc={'figure.figsize':(17,5)})  #to set the space and height around x and y axis
   ax=sns.barplot(data = sales_state,x='State',y='Orders')
   for bar in ax.containers:
       ax.bar_label(bar)
   ```
   ```python
   sales_state = df.groupby(['State'],as_index = False ['Amount'].sum().sort_values(by='Amount',ascending=False).head(10)
   sns.set(rc={'figure.figsize':(17,5)})
   sns.barplot(data=sales_state,x='State',y='Amount')
   ```

7. **Purchases and Amount Spent by Marital Status**
   Create a bar graph to compare the number of purchases and amount spent by marital status.
   ```python
   ax= sns.countplot(data=df,x='Marital_Status')
   sns.set(rc={'figure.figsize':(1,5)})
   for bar in ax.containers:
       ax.bar_label(bar)
   ```
   ```python
   sales_state = df.groupby(['Marital_Status','Gender'],as_index=False)['Amount'].sum().sort_values(by='Amount',ascending=False)
   sns.set(rc={'figure.figsize':(6,5)})
   sns.barplot(data = sales_state,x="Marital_Status",y='Amount',hue='Gender')
   ```

8. **Purchases and Amount Spent by Profession**
   Create a bar graph to compare the number of purchases and amount spent depending on the profession.
   ```python
   sns.set(rc={'figure.figsize':(20,5)})
   ax = sns.countplot(data = df,x='Occupation')
   for bar in ax.containers:
       ax.bar_label(bar)
   ```
   ```python
   sales_state = df.groupby(['Occupation'],as_index = False)['Amount'].sum().sort_values(by='Amount',ascending=False)
   sns.set(rc={'figure.figsize':(20,5)})
   sns.barplot(data = sales_state,x='Occupation',y='Amount')
   ```

9. **Number of Orders by Product Category and Product ID**
   Create a comparison of the number of orders in each product category and by product ID.
   ```python
   sns.set(rc={'figure.figsize':(25,5)})
   ax = sns.countplot(data = df,x='Product_Category')
   for bar in ax.containers:
       ax.bar_label(bar)
   ```
   ```python
   sales_state = df.groupby(['Product_Category'],as_index = False)['Amount'].sum().sort_values(by='Amount',ascending=False).head(10)
   sns.set(rc={'figure.figsize':(25,15)})
   sns.barplot(data = sales_state,x='Product_Category',y='Amount')
   ```
   ```python
   sales_state = df.groupby(['Product_ID'],as_index = False)['Orders'].sum().sort_values(by='Orders',ascending=False).head(10)
   sns.set(rc={'figure.figsize':(20,5)})
   fc=sns.barplot(data = sales_state,x='Product_ID',y='Orders')
   for bar in fc.containers:
       fc.bar_label(bar)
   ```

## Conclusion
Following these steps, you will be able to analyze the sales data effectively using Python and its libraries. This analysis includes data cleaning, exploration, and visualization to gain insights into purchase patterns and behaviors.
