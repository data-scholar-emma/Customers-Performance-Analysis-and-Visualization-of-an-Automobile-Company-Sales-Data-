# Customers-Performance-Analysis-and-Visualization-of-an-Automobile-Company-Sales-Data-
A Data Science Project that Analysed  the sales performance of an Automobile company Based in the United States. The company’s sales transaction data generated over the past years was used for this  analysis.

## PROBLEM STATEMENT:  
Who are their Top 10 Most-Profitable Customers  in the United States ?

## DATA PRE-PROCESSING 
#### DATA LOADING 

```Python
##  importing all the necessary python packages


# solution 

import numpy as np 
import pandas as pd 
import matplotlib.pyplot as plt

print("The packages have been successfully imported")

```


```Python
# reading the sales data into a pandas dataframe



bikes_df = pd.read_csv("C:/Users/HP/Downloads/dowlnoad 2/bikes.csv")
bikes_df.head()    

```
####  Data Modification
```Python
# (1). Adding the following 3 columns to my pandas Dataframe:  bikes_df




# TotalCostPrice : To be obtained by (OrderQuantity x CostPrice_usd)


bikes_df["TotalCostPrice"] = bikes_df["OrderQuantity"] * bikes_df["CostPrice_usd"] 





# SalesRevenue : To be obtained by (OrderQuantity x SellingPrice_usd)


bikes_df["SalesRevenue"] = bikes_df["OrderQuantity"] * bikes_df["SellingPrice_usd"] 



# Profit : To be obtained by (SalesRevenue - TotalCostPrice)



bikes_df["Profit"] = bikes_df["SalesRevenue"] - bikes_df["TotalCostPrice"]


bikes_df.head()
```

