# Liquor Sales Analysis Project
This project is the final assignment for Reatcode Group - Workearly Greece, where we were provided with a finance liquor sales SQL database containing data on liquor sales in the state of Iowa, USA, between 2012 and 2020. The goal of this project is to analyze and visualize the dataset for the period between 2016 and 2019.
# Data Retrieval #
I started by extracting the data from the SQL database provided, with MySQL Workbench , using the following query to select data between 2016 and 2019:

```sql
SELECT * FROM finance_liquor_sales
WHERE date >= '2016-01-01' AND date <= '2019-12-31';`
```
# Data Cleanup #
After exporting the data to an Excel file, i noticed some inconsistencies in the data, such as variations in the case of city names and extra digits in zip codes so i performed data cleaning and transformation using Power Query in Excel and then i deleted the original table.

![Alt text](https://github.com/jimiatro/Liquor_Sales_Analysis_Project_For_Workearly/blob/main/Power%20Query.png)

# Data Analysis #
I used Jupyter Notebook for data aggregation and analysis. The Python code for this step is shown below:


``` python
# Import Pandas library
import pandas as pd
```



``` python
# Read the excel file into a Pandas DataFrame
data = pd.read_excel('sales 2016-2019.xlsx')
```


``` python
# The most popular items based on the maximum sale_dollars per zip code
popular_items = data.groupby('zip_code')['sale_dollars'].max()
```



``` python
# Total sales across all stores
total_sales = data['sale_dollars'].sum()
```

``` python
# Percentage of sales per store 
percentage = (data.groupby(['store_number'])['sale_dollars'].sum()/ total_sales) *100
```

``` python
# Average sales per store
average_sales = data.groupby(['store_number'])['sale_dollars'].mean()
```

# Data Visualization #
Used Tableau Public to create interactive visualizations, allowing us to explore the data in a more intuitive way. Some of the visualizations created include:

- Bottles sold Map
- Sales percentage per store
- Average sales per store
- Sold bottles per zip code


 ![Alt text](https://github.com/jimiatro/Liquor_Sales_Analysis_Project_For_Workearly/blob/main/Tableau%20Dashboard.png)



# License #

This project is licensed under the GPL-3.0 license - see the [LICENSE](https://github.com/Workearly/Final-Assignment/blob/main/LICENSE) file for details.

# Feedback #
I would love to hear your thoughts on my project! If you have any suggestions or comments, please feel free to open an issue or send me an email at jimiatro@hotmail.com.
