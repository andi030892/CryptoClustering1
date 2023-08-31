
# Crypto-Clustering Challenge

## TABLE OF CONTENTS

1. Project Description
2. Installation
3. Contributing
4. Acknowledgements
5. Licenses

### 1. PROJECT DESCRIPTION

In this [project](https://bootcampspot.instructure.com/courses/3337/assignments/54011?module_item_id=961925), the goal is to use [Python](https://www.python.org/) (particularly through the [sklearn](https://en.wikipedia.org/wiki/Scikit-learn) library) and [unsupervised machine learning](https://en.wikipedia.org/wiki/Unsupervised_learning) to [cluster](https://developers.google.com/machine-learning/clustering/overview#:~:text=In%20machine%20learning%20too%2C%20we,relies%20on%20unsupervised%20machine%20learning.) [cryptocurrencies](https://en.wikipedia.org/wiki/Cryptocurrency) based on their patterns of 24-hour or seven-day price changes. (NB - Substantively, the project just groups cryptocurrencies that have had similar price change behaviors, i.e., it is descriptive.)

- **Prepare the Data and Find the Best Value for `k` Using the Original Data**

After exploring the data, sklearn's [StandardScaler](https://scikit-learn.org/stable/modules/generated/sklearn.preprocessing.StandardScaler.html) was used in preprocessing to [normalize](https://en.wikipedia.org/wiki/Normalization_(statistics)) all dimensions of the data on a single scale. The best value for `k` (i.e., the number of clusters) was calculated by running [K-Means](https://serokell.io/blog/k-means-clustering-in-machine-learning) 11 times on the dataset and plotting the results, thereby using the [Elbow method](https://www.analyticsvidhya.com/blog/2021/01/in-depth-intuition-of-k-means-clustering-algorithm-in-machine-learning/) heuristic to determine when minimizing inertia (i.e., the [within-cluster sum of squares (WCSS)](https://support.minitab.com/en-us/minitab/21/help-and-how-to/statistical-modeling/multivariate/how-to/cluster-k-means/interpret-the-results/all-statistics-and-graphs/#:~:text=The%20within%2Dcluster%20sum%20of%20squares%20is%20a%20measure%20of,a%20large%20sum%20of%20squares.)) is balanced by diminishing returns in adding more clusters.

_**Question 1:**_ What is the best value for `k`?

_**Answer:**_ It was demonstrated that the best value for `k` = _4_. After that point, the line becomes mostly horizontal, because more clusters only reduce the inertia by a small amount. See **Figure 1**.

**Figure 1** | *Elbow curve for `k` (number of clusters) using the original normalized data.*

- **Cluster Cryptocurrencies with K-Means Using the Original Data**

K-Means was then used to train the data to produce four clusters of the relationship between 24-hour and seven-day cryptocurrency price changes. The value of clustering is that the machine can determine and display patterns it discovers by itself, without pre-established labels. See **Figure 2**.

**Figure 2** | *Predicted clusters from the original normalized data of the relationship between 24-hour and seven-day cryptocurrency price changes.*

- **Optimize Clusters with Principal Component Analysis**

[Principal component analysis (PCA)](https://en.wikipedia.org/wiki/Principal_component_analysis) was used to fit the dimensions of the dataset to a predetermined three principal components. (NB - A volume of _three_ is often used for principal components because it mirrors the three dimensions of Euclidian space and is therefore easy to comprehend and visualize.)

_**Question 2:**_ What is the total explained variance of the three principal components?

_**Answer:**_ The total explained variance of the dataset when all dimensional variance is reduced to three principal components is _0.3719856 + 0.34700813 + 0.17603793_ = **0.89503166**, or almost 90%. In other words, _even after PCA reduces dimensionality, it still captures a large amount of the original dataset's variance._

- **Find the Best Value for k Using the PCA Data**

The optimal value for `k` was now determined with the Elbow method again, this time using the output data from PCA. See **Figure 3**.

**Figure 3** | *Elbow curve for `k` (number of clusters) using the PCA output data.*

_**Question 3:**_ What is the best value for `k` when using the PCA data?

_**Answer:**_ The best value for `k` = _4_. After that point, the line becomes mostly horizontal, because more clusters only reduce the inertia by a small amount.

_**Question 4:**_ Does it differ from the best `k` value found using the original data?

_**Answer:**_ No, the optimal value for `k` in both cases = _4_. This consistency in the optimal `k` value between the original scaled data and the PCA-reduced data provides additional confidence in the clustering. It suggests that the underlying structure of the data, in terms of how the data points group together, is maintained _even after the dimensionality reduction of PCA_ (i.e., "throwing away" some data).

- **Cluster Cryptocurrencies with K-means Using the PCA Data**

K-Means was used again, this time to train the PCA-output data, to produce four clusters of the relationship between the first two of three principal components (`PC1` and `PC2`). These two are used in a two-dimensional plot because they each explain more variance in the original dataset than `PC3`. See **Figure 4**.

**Figure 4** | *Predicted clusters from the PCA-output data of the relationship between the first and second of three principal components, which explain the most variance of the original dataset.*

- **Visualize and Compare the Results**

Composite plots of Elbow curves and clusters for the original normalized data and the PCA-output data were compared side-by-side for a final assessment.

_**Question 5:**_ After visually analyzing the cluster analysis results, what is the impact of using fewer features to cluster the data using K-Means?

_**Answer:**_ The impact of using PCA data results in tighter, more compact, less dispersed clusters. This is because the goal of PCA is to _capture as much of the variance in the data with fewer features (i.e., principal components)_. This can help clarify patterns in the data, especially when visualizing it. With less "noise", clusters are more condensed.

### 4. ACKNOWLEDGEMENTS

In addition to using the resources listed above, the author acquired query responses in OpenAI's [ChatGPT](https://chat.openai.com/) 3.5 and 4 apps, and the [VSCode GitHub Copilot](https://github.com/features/copilot) app V1.

The author also consulted code and results from a similar project publicly accessible in a [GitHub](https://github.com/) repository and recoverable through [Google](https://www.google.com/) and comparable search engines:

- [Leigh, John](https://www.linkedin.com/in/johnleigh101/): Chicago, Illinois, USA, May 2023. [CryptoClustering](https://github.com/JLeigh101/CryptoClustering)

### 5. LICENSES

- This program is allowed for free use via the [Creative Commons Zero v1.0 Universal](https://creativecommons.org/publicdomain/zero/1.0/) license.

WORKED WITH ADAM GLANTZ ON THIS CHALLENGE
