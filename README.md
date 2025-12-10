# Customer-Insights-PCA
This repository contains the .ipynb file and marketing campaign dataset for my Customer Insights PCA project. The purpose of this project was to create valuable insights about customer attributes by utilizing PCA in the EDA process. At the end of this project, I create 2 clusters of people which highlight the different profiles of these groups with their average attributes and the standard deviation from those means. 

## Preprocessing/Cleaning
- When I first started working with this dataset, I started by looking at the df.info() and df.describe() to get a high-level sense of the data. This helps me understand an approximate range of values for the fields that I will be working with.
- Next, I check to see if there are any missing values that need to be addressed. In this case, the column "Income" had 24 null values. To address this issue, I filled in these values with the median income of their education level. After I filled in the null values, I checked to make sure that no more nulls existed in the data and that my implementation worked.
- From here, I used the OrdinalEncoder to encode "Education" and preserve it's natural ranking. I cleaned up my dataset a bit more by removing the "Dt_Customer" column which contained the date the product was purchased and the "Customer_ID" column. 

## Fitting the Model
- After my dataset was cleaned, I built a correlation heat map to see if any strong relationships existed. I coded my map to indicate stronger correlations as lighter, while darker shades meant less correlated.
- Once I had my variables selected and standardized, I was ready to apply PCA to reduce dimensionality. This compresses the data while retaining ~85% of total variance to produce a low-dimensional representation suitable for clustering and visualization.
- Once I had my visualization of clusters, it then came time to identify top PCA drivers. I examined PCA loadings to determine which features most influence PC1, PC2, and PC3, enabling a business-readable interpretation of each axis.
- From here, I wanted to determine optimal number of clusters. I ran K-Means across a range of k values on the reduced PCA space and chose the best k using silhouette scores, ensuring compact, well-separated customer segments and resulted with k = 2 as the optimal amount.

## Cluster Interpretation & PCA-Space Separation
- Cluster structure PC1 vs. PC2
  - The strongest separation emerges in the first two principal components.
  - PC1 captures differences in overall purchasing/spending behavior, while PC2 reflects household structure and discount-driven activity.
  - Points in this space form two dense, well-separated groups, indicating that these dimensions contain the dominant signals differentiating customer types.
  - The model achieves its highest silhouette score when clustering in this 2-D space, confirming that PC1–PC2 best express the natural segmentation patterns.
- Cluster behavior in PC2 vs. PC3
  - Separation largely collapses when PC1 is removed; clusters blend across wide regions of the plot.
  - This confirms PC2 and PC3 alone do not contain enough discriminative structure to segment customers cleanly.
  - PC3 primarily adds diffuse behavioral noise rather than a clear new dimension of separation.
- Silhouette comparison across dimensions
  - 2 PCs → best silhouette (highest cohesion & separation)
  - Additional PCs (3, 5, 15+) progressively reduce silhouette quality
  - This indicates that most cluster-relevant variance lives in the first two components, whereas later components capture complexity that obscures cluster boundaries rather than sharpening them.
 - Cluster profiling summary
   - Profiling each cluster reveals consistent behavioral differences aligned with the PCA axes—one group is characterized by higher overall spending and catalog activity, while the other leans more toward discount-driven purchasing and larger households.
   - These differences validate both the PCA interpretation and the K-Means segmentation, showing that clusters are not only mathematically distinct but behaviorally meaningful.
  
## Summary
Across all PCA visualizations, the strongest and most meaningful cluster separation occurs in the PC1–PC2 space, where PC1 reflects overall spending behavior and PC2 captures household and discount-driven tendencies. Additional components like PC3 introduce variation but do not create new, well-defined segmentation boundaries, which is confirmed by steadily declining silhouette scores when clustering on 3, 5, or more PCs. This indicates that most of the true “cluster signal” resides in the first two components, and using only PC1–PC2 leads to tighter and more interpretable segments. Cluster profiling further validates this structure by showing consistent differences in spending levels, purchasing channels, and household characteristics between the groups. Overall, the segmentation is both statistically sound and behaviorally meaningful, providing a reliable foundation for customer insight and targeting.
