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

![pandas screenshot_p2](https://github.com/user-attachments/assets/6b42f77d-d226-4427-9395-0a681b4731de)




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

![data modification screenshot_p2](https://github.com/user-attachments/assets/5dabc33a-4888-41e7-93b4-7162a913c362)


## DATA ANALYSIS
#### DATA FILTERING 

```Python
# Filtering out the relevant data needed to solve the problem statement 

is_USA = bikes_df["CustomerCountry"] == "United States"

usa_data = bikes_df[(is_USA)]

usa_data.head()
```

![data filtering screenshot_p2](https://github.com/user-attachments/assets/93908892-967b-40cf-a2a3-1a795977f51b)



#### DATA AGGREGATION
```Python
# aggregating the filtered data (USA sales data ) for each Customer 

total_profit_by_customer = usa_data.pivot_table(values = "Profit", index = "CustomerName", aggfunc = np.sum )

total_profit_by_customer

```

![data aggregation screenshot_p2](https://github.com/user-attachments/assets/3f8dbaff-6b3e-4c62-a36d-4d8e023d341e)

#### DATA SORTING 

```Python
# sorting the aggregated data 

# in order to rank the customers according to top profit


total_profit_by_customer.sort_values("Profit", ascending = False)

```

![data sorting screenshot_p2](https://github.com/user-attachments/assets/2a41b13d-edc5-4b8c-83b7-0a5c077f8e8f)


#### RESULT 

```Python
top_10_customers = total_profit_by_customer.sort_values("Profit", ascending = False).head(10)

top_10_customers
```

![result screenshot_p2](https://github.com/user-attachments/assets/c53d82c2-0bc7-40ef-926e-e69223173182)


## DATA VISUALIZATION

```Python
# VISUALIZING the Result

top_10_customers.plot(kind = "bar")

# Adding a Tile , and label

plt.title("The Top 10 Customers in the United States")

plt.ylabel("Total Profit ")
plt.xlabel("Customer Names")


# showing the result 

plt.show()
```

![data visualization screenshot_p2](https://github.com/user-attachments/assets/18fb85bc-4e84-457b-9cd0-8b4f1805e2cd)
