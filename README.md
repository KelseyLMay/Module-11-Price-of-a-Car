# Module-11-Price-of-a-Car
This repo contains the Jupyter notebooks, data, and graphs that explore features that affect the price of a car.

## Business Goals ##
My client is a used car sales business that wants to understand what characteristics of used cars most significantly influence their sale price in order to maximize profits by making data-driven decisions related to inventory, purchasing, and pricing. This type of business maximizes profitability by clearly understanding how different features (age, mileage, condition, etc.) influence resale value in order to avoid overpaying for low-margin vehicles, prioritizing stocking high margin vehicles, and set profitable and competitive prices.

## Understanding the Data ##
The data is pretty noisy and, while I did a lot of cleanup, more would be necessary to produce a more accurate model. Steps included:

1) Removed unnecessary (id-only) fields or fields that were missing significant amounts of data,
2) Checked for and removed outliers as indicated by box plots or domain knowledge. I relied on my limited knowledge of the domain to make decisions for this exercise, but in reality I would work with the client to develop better measures. For example, I decided on a minimum cut off for price and mileage but I think it's probably lower than where someone with more knowledge of the used car sales industry would put it.
3) Queried data to make sure it makes intuitive sense (there aren't "new" condition cars that have 200k miles, for example). There were actually a lot of issues with this. I combined some of the responses into broader buckets (including "new", "good", and "excellent" in one shared category for car condition for example), to try to address some of the variation, but there is definitely room to improve this as well.
4) Converted data as necessary for clarity and analysis. I used the year to calculate the car's age for further analysis vs relying on the year.
5) Created plots to better understand the core relationships. Scatterplots and box plots indicated that there is a relationship between the price of a car and its age, mileage, condition, and fuel type. However, it also appears like the data is still pretty noisy. See 
[Price by Age](https://github.com/KelseyLMay/Module-11-Price-of-a-Car/blob/main/plots/Price_by_Age.png), [Price by Condition](https://github.com/KelseyLMay/Module-11-Price-of-a-Car/blob/main/plots/Price_by_Condition.png), [Price by Fuel Type](https://github.com/KelseyLMay/Module-11-Price-of-a-Car/blob/main/plots/Price_by_Fuel_Type.png), [Price by Mileage](https://github.com/KelseyLMay/Module-11-Price-of-a-Car/blob/main/plots/Price_by_Mileage.png), [Price by Odometer Reading](https://github.com/KelseyLMay/Module-11-Price-of-a-Car/blob/main/plots/Price_by_Odometer_Reading.png), and [Price of Car by Year](https://github.com/KelseyLMay/Module-11-Price-of-a-Car/blob/main/plots/Price_of_Car_by_year.png)

## Process ##
The dataset was split into training and testing data, and models were built using Lasso and Ridge regression. The Lasso regression did not converge, suggesting the outcome might not be accurate. However, it did suggest that the higher priced cars were newer (younger than 2010), had less mileage (less than 100k miles), and a diesel fuel type. The lower priced cars were older (older than 2010), had higher mileage (over 150k miles), and in poor condition. 

Ridge regression estimates coefficients of multiple-regression models when variables are highly correlated (potentially factors like mileage and car age, for example). I did a grid search to find the best alpha for Ridge Regression and it was 100.

## Conclusion ##
My analysis indicates that newer cars (younger than 2010), cars with diesel fuel, or lower mileage (less than 100k miles) cars have the highest prices. In contrast, older cars (older than 2010), cars with higher mileage (more than 150k miles), or cars in poor condition have the lowest prices. I created a model that can be used to roughly predict the price of used cars based on certain criteria. However, the size of the mean squared error indicates that the data needs more cleaning or more data should be analyzed to create a model that can make more accurate predictions.