# Unsupervised_Machine_Learning

## Cryptocurrency Clusters

### Background

* This assignment is intended to assist with a new cryptocurrency investment portfolio. I will create a report that 
includes what cryptocurrencies are on the trading market and determine whether they can be grouped to create a classification 
system for this new investment. With the raw data, I will first need to process it to fit the machine learning models. Since 
there is no known classification system, I will need to use unsupervised learning. I will explore whether the cryptocurrencies 
can be grouped together with other similar cryptocurrencies. My findings will be shared using data visualization.


### Data Preparation

* Read `crypto_data.csv` into Pandas. The dataset was obtained from [CryptoCompare](https://min-api.cryptocompare.com/data/all/coinlist).

* Discard all cryptocurrencies that are not being traded by filtering for currencies that are currently being traded, then
 drop the `IsTrading` column from the dataframe.

* Remove all rows that have at least one null value.

* Filter for cryptocurrencies that have been mined. That is, the total coins mined should be greater than zero.

* In order for your dataset to be comprehensible to a machine learning algorithm, its data should be numeric. Since the coin names do not 
contribute to the analysis of the data, delete the `CoinName` from the original dataframe.

* Your next step in data preparation is to convert the remaining features with text values, `Algorithm` and `ProofType`, into numerical 
data. To accomplish this task, use Pandas to create dummy variables. 

        The file decreased from 7 columns and 1252 rows to 4 columns and 532 rows. 

* Standardize your dataset so that columns that contain larger values do not unduly influence the outcome.

### Dimensionality Reduction

* Creating dummy variables above dramatically increased the number of features in your dataset. Perform dimensionality reduction with PCA. Rather than specify the number of principal components when you instantiate the PCA model, it is possible to state the desired **explained variance**. For example, say that a dataset has 100 features. Using `PCA(n_components=0.99)` creates a model that will preserve approximately 99% of the explained variance, whether that means reducing the dataset to 80 principal components or 3. For this project, preserve 90% of the explained variance in dimensionality reduction. How did the number of the features change?

* Next, further reduce the dataset dimensions with t-SNE and visually inspect the results. In order to accomplish this task, run t-SNE on the principal components: the output of the PCA transformation. Then create a scatter plot of the t-SNE output. Observe whether there are distinct clusters or not.

### Cluster Analysis with k-Means

* Create an elbow plot to identify the best number of clusters. Use a for-loop to determine the inertia for each `k` between 1 through 10. 

        The best k value is located at the elbow where K=4.

### Recommendation

* Based on your findings, make a brief (1-2 sentences) recommendation to your clients. Can the cryptocurrencies be clustered together? If so, into how many clusters?
*  
![Screen Shot 2022-02-10 at 6 39 38 PM](https://user-images.githubusercontent.com/89491352/153515445-d29dd084-ddda-4c61-89f1-05cfd4b51e56.png)        ![Screen Shot 2022-02-10 at 6 39 21 PM](https://user-images.githubusercontent.com/89491352/153515413-6435c907-84e1-4975-9616-013eec56230f.png)

        
        At initial glance, there are 4 different clusters; however, 98.5% of the 532 classifications of cryptocurrencies are distributed in class '0' based 
        on feature similarities. There are 2 unique cryptocurrencies and 6 in class 3 that share similar features. Ultimately, plotting the results does not
        yield proper segmentation of the different classes. 

### References

Crypto Coin Comparison Ltd. (2020) Coin market capitalization lists of crypto currencies and prices. Retrieved from [https://www.cryptocompare.com/coins/list/all/USD/1](https://www.cryptocompare.com/coins/list/all/USD/1)

- - -

© 2021 Trilogy Education Services, LLC, a 2U, Inc. brand. Confidential and Proprietary. All Rights Reserved.

