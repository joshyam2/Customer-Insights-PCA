# Customer-Insights-PCA
This repository contains the .ipynb file and marketing campaign dataset for my Customer Insights PCA project. The purpose of this project was to create valuable insights about customer attributes by utilizing PCA in the EDA process. At the end of this project, I create 2 clusters of people which highlight the different profiles of these groups with their average attributes and the standard deviation from those means. 

## Preprocessing/Cleaning
- When I first started working with this dataset, I started by looking at the df.info() and df.describe() to get a high-level sense of the data. This helps me understand an approximate range of values for the fields that I will be working with.
- Next, I check to see if there are any missing values that need to be addressed. In this case, the column "Income" had 24 null values. To address this issue, I filled in these values with the median income of their education level. After I filled in the null values, I checked to make sure that no more nulls existed in the data and that my implementation worked.
- From here, I used the OrdinalEncoder to encode "Education" and preserve it's natural ranking. I cleaned up my dataset a bit more by removing the "Dt_Customer" column which contained the date the product was purchased and the "Customer_ID" column. 

## Fitting the Model
- After my dataset was cleaned, I built a correlation heat map to see if any strong relationships existed. I coded my map to indicate stronger correlations as lighter, while darker shades meant less correlated. 
