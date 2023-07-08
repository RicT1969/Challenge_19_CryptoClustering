# Challenge_19_CryptoClustering

<p><h2>Use of unsupervised learning to predict if cryptocurrencies are affected by 24-hour or 7-day price changes.</h2></p>

<p>In this challenge the K-means module from scikit-learn was used to create clusters of Cryptocurrencies using price change percentage data over different periods of time. These include periods of: 24 hours, 7-days, 14-days, 30-days, 60-days, 200-days and 1 year.</p>

<h2>Method</h2><ol>
<li>The data was imported into a pandas DataFrame for manipulation and for plotting.</li>

<li>Scale the data to reduce the influence of variables:</li><ul>
<li>It prevents variables with larger scales from overshadowing others, ensuring that each variable contributes equally to the clustering process.</li>
<li>Ensures that distance calculations are based on comparable scales, allowing for a fair assessment of the proximity between data points.</li>
<li>Helps normalise distributions so that the vairables roughly follow a Gaussian distribution</li></ul>

<li>Use the 'elbow method' to find the best value for k Using the Original Scaled DataFrame:</li><ul>
<li>The elbow method is used to determine the optimal number of clusters in a k-means clustering algorithm.</li>
<li>It plots the variance (inertia) of the clusters against the number of clusters and identifies the "elbow" point (or point of inflection) in the plot. The elbow point represents the number of clusters where the decrease in variance starts to level off significantly.</li>
<li>The value of the point of inflection provides a balance between minimising within-cluster variance and avoiding excessive complexity.</li><ul>
<li>The process involved creating a list with the number of k values from 1 to 11.</li>
<li>Create an empty list to store the inertia values.</li>
<li>Create a loop to compute the inertia for each value of k and asign to a dictionary to allow for plotting the elbow curve<./li>
<li>Plot a line chart with the inertia values computed with the different values ofk to identify the optimal value for k.</li></ul></ul>
<li><b>The optimal value of k = 4.</b></li>

<p><li>Cluster Cryptocurrencies with K-means Using the Original Scaled Data<:/li></:>p><ul>
<li>K-means model initialised with the best value for k (4).</li>
<li>Fit the K-means model using the original scaled DataFrame.</li>
<li>TPredict the clusters to group the cryptocurrencies using the original scaled DataFrame.</li>
<li>A scatter plot was used to create a visualisation of the clusters using hvPlot.</li></ul>

<li>Optimise Clusters with Principal Component Analysis:</li></ol><ul>
<li>The same steps were taken to calculate and represent the cluster results for the data having applied a Principle Component Analysis (PCA) to reduce the freatures to three principle components</li>
<li>PCA determines the proportion of variance in the data accounted for by each principal component (i.e. each column of data).</li>
<li>The 'explained variance' describes the proportion of the total variance in the dataset for each principal component, allowing us to exclude elements not contributing significantly to the overall variability of the dataset.</li>
<li>The 'explained variance' is expressed as a percentage, and it is computed by dividing the variance of each principal component by the total variance of the dataset. The sum of the explained variances of all the principal components is equal to 100%.</li>
<li>The 'explained variance' provides insights into the relative importance of each component and aids dimensionality reduction and feature selection, hopefully allowing for better outcomes from the k-means model</li>
<li>The 'explained variance' of the features indicated that three principal components were responsible for 89.5% of total variance. Therefore 3 principle components would be the ooptimal number for the k-means model without losing the necessary information from the original data.</li>
<li>the PCA results were recorded in a DataFrame as PC1, PC2, PC3.
<li>As before an 'elbow test' was applied and the optimised number of clusters was determined to be 4.</li>
<li>The PCA data was subject of the k-means model, and the resulting clusters represented on a scatter plot and compared with the earlier plot of the original data.</li></ul>

<h3>Conclusions</h3>
<p>Based on visually analysing the cluster analysis results, what’s the impact of using fewer features to cluster the data by using K-means?</p><ol>
<li>On inital view the clusters look similar, most data points being clustered into two distinct group; however the PCA resuls are generally more tightly clustered with some improvement in the distinction between the clusters. </li>
<li>Both analyses show the same two cryptocurrencies, celsius_degree_token and ethland, being obvious outsiders. Both form groups of their own; however, within the PCA set of data they are seperated by a greater degree.</li>
<li>The clearest difference between the two scatter plots is in the colour selection. Both results have a similar green cluster, but the second cluster is coloured differently: red for the original data, and blue for the PCA results. Whether this is of any significance would require investigation. It might be indicative that the groupings contain different elements; equally however, the PCA analysis will have influenced the positioning of points in relation to each other, and those variations may be the reason for the different colour assignment.</li>
<li>In terms of impact, the tighter clusters suggests that the PCA analysis has captured the underlying patterns and structure in the data more effectively than the original features and indicates that original high-dimensional features might have contained redundant or noisy information hindering effective clustering.</li>
<li>Tighter clusters provide greater interpretability, revealing more defined patterns than in the original dataset.</li></ol>

<p>Broader conclusions in relation to whether unsupervised learning can predict if cryptocurrencies are affected by 24-hour or 7-day price changes?</p>p>
<p>The initial question asked whether unsupervised learning can be used to predict if cryptocurrencies are affected by 24-hour or 7-day price changes. In the case of clustering models, although they can provide insights into this topic, models like k-means are primarily exploratory and descriptive tools rather than predictive models.  Whilst we can observe distinct groups and potentially identify  patterns or characteristics within each cluster, the clusters only represent similarities in the data and do not necessarily capture relevant relationships or predict the future behavior based on specific time periods. To investigate further we would also need to employ predictive modeling techniques, such as regression or time series analysis. These models would take into account the historical price data and other factors that may indicate future price changes.</p>

<h2>Source</h2>
https://holoviz.org/tutorial/Composing_Plots.html
https://hvplot.holoviz.org/user_guide/Plotting.html
https://stackoverflow.com/questions/58086573/set-title-to-a-simple-holoviews-plot-python
https://stackoverflow.com/questions/49147774/what-is-random-state-in-sklearn-model-selection-train-test-split-example
https://stackoverflow.com/questions/32612180/eliminating-warnings-from-scikit-learn
https://www.analyticsvidhya.com/blog/2021/01/in-depth-intuition-of-k-means-clustering-algorithm-in-machine-learning/#What_Is_the_Elbow_Method_in_K-Means_Clustering?
https://machinelearningmastery.com/how-to-fix-futurewarning-messages-in-scikit-learn/#:~:text=This%20can%20be%20achieved%20by,generally%2C%20to%20ignore%20all%20warnings.
