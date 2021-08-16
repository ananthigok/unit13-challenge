# Unit 13 Homework Assignment - The Power of the Cloud and Unsupervised Learning

## Clustering Crypto

![Cryptocurrencies coins](Images/cryptocurrencies-coins.jpg)
_[Cryptocurrencies coins by Worldspectrum](https://www.pexels.com/@worldspectrum?utm_content=attributionCopyText&utm_medium=referral&utm_source=pexels) | [Free License](https://www.pexels.com/photo-license/)_

### Background

This task involves generating a report of what cryptocurrencies are available on the trading market and how they can be grouped using classification. This is done by putting unsupervivsed learning skills into action by lustering cryptocurrencies and creating plots to present the results.

The following main tasks are accompolished:

* **[Data Preprocessing](#Data-Preprocessing):** Prepare data for dimension reduction with PCA and clustering using K-Means.

* **[Reducing Data Dimensions Using PCA](#Reducing-Data-Dimensions-Using-PCA):** Reduce data dimension using the `PCA` algorithm from `sklearn`.

* **[Clustering Cryptocurrencies Using K-Means](#Clustering-Cryptocurrencies-Using-K-Means):** Predict clusters using the cryptocurrencies data using the `KMeans` algorithm from `sklearn`.

* **[Visualizing Results](#Visualizing-Results):** Create some plots and data tables to present your results.

---

### Files

* [crypto_clustering.ipynb](Starter_Files/crypto_clustering.ipynb)

---

### Instructions

#### Data Preprocessing has been done 

In this section, loaded the information about cryptocurrencies and performed data preprocessing tasks.  
The following method has been used to load the data:

1. Using the provided `CSV` file, create a `Path` object and read the file data directly into a DataFrame named `crypto_df` using `pd.read_csv()`.

With the data loaded into a Pandas DataFrame, continued with the following data preprocessing tasks.

3. Kept only the necessary columns: 'CoinName','Algorithm','IsTrading','ProofType','TotalCoinsMined','TotalCoinSupply'

4. Kept only the cryptocurrencies that are trading.

5. Kept only the cryptocurrencies with a working algorithm.

6. Removed the `IsTrading` column.

7. Removed all cryptocurrencies with at least one null value.

8. Removed all cryptocurrencies that have no coins mined.

9. Dropped all rows where there are 'N/A' text values.

10. Stored the names of all cryptocurrencies in a DataFrame named `coins_name`, use the `crypto_df.index` as the index for this new DataFrame.

11. Removed the `CoinName` column.

12. Created dummy variables for all the text features, and stored the resulting data in a DataFrame named `X`.

13. Standardized all the data of the `X` DataFrame with StandardScaler` from `sklearn. This is important prior to using PCA and K-Means algorithms.

#### Reducing Data Dimensions Using PCA
Reduced the dimensions of the `X` DataFrame down to three principal components with `PCA` algorithm from `sklearn`.

Created a DataFrame named `pcs_df`  with the `crypto_df.index` as the index for this new DataFrame.


#### Clustering Cryptocurrencies Using K-Means

Cluster the cryptocurrencies using the PCA data with KMeans` algorithm from `sklearn`.

Performed the following tasks:

1. Created an Elbow Curve to find the best value for `k` using the `pcs_df` DataFrame.

2. The best value for `k` was determined by the `Kmeans` algorithm which predicted the `k` clusters for the cryptocurrencies data with the `pcs_df`.

3. Created a new DataFrame named `clustered_df`, that includes the following columns `"Algorithm", "ProofType", "TotalCoinsMined", "TotalCoinSupply", "PC 1", "PC 2", "PC 3", "CoinName", "Class"`.  The index of the `crypto_dfmaintain was maintained.

#### Visualizing Results

In this section, created some data visualization to present the final results. Performed the following tasks:

1. Created a 3D-Scatter using Plotly Express to plot the clusters using the `clustered_df` DataFrame. Included the following parameters on the plot: `hover_name="CoinName"` and `hover_data=["Algorithm"]` to show this additional info on each data point.

2. With `hvplot.table` created a data table with all the current tradable cryptocurrencies. The table has the following columns: `"CoinName", "Algorithm", "ProofType", "TotalCoinSupply", "TotalCoinsMined", "Class"`

3. Created a scatter plot using `hvplot.scatter`, to present the clustered data about cryptocurrencies having `x="TotalCoinsMined"` and `y="TotalCoinSupply"` to contrast the number of available coins versus the total number of mined coins. With the `hover_cols=["CoinName"]` parameter, included the cryptocurrency name on each data point.