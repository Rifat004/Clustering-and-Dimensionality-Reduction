# Unsupervised Learning on Fashion MNIST Dataset

This repository contains code for performing unsupervised learning on the Fashion MNIST dataset using various dimensionality reduction techniques and clustering algorithms. The goals are to apply different techniques, determine the best applicable method for clustering the Fashion MNIST images and visualize the resulting clusters.

## Dataset

The Fashion MNIST dataset consists of training set of 60,000 examples and a test set of 10,000 examples. Each image is 28 pixels in height and 28 pixels in width, for a total of 784 pixels in total and associated with a label from 10 classes indicating as follows:

- 0 T-shirt/top
- 1 Trouser
- 2 Pullover
- 3 Dress
- 4 Coat
- 5 Sandal
- 6 Shirt
- 7 Sneaker
- 8 Bag
- 9 Ankle boot

## Workflow

1. **Data Preprocessing and EDA**: The dataset is loaded and being analyzed. The pixel values in an image typically range from 0 to 255 for grayscale images. By dividing all pixel values by 255, the values have been scaled down to be in the range of 0 to 1. This scaling ensures that all pixel values are on a similar scale.

2. **t-SNE Dimensionality Reduction**: t-SNE is used to reduce the high-dimensional feature space of the images into a 2-dimensional space, suitable for visualization. t-SNE can preserve the spatial relationship between data points after reducing the dimensionality of the data. It means that the nearby data (points with similar characteristics) in the original dimension will still be nearby in the lower dimension.

3. **K-means Clustering with Hyperparameter Tuning**: K-means clustering is applied to the t-SNE transformed data and perform hyperparameter tuning to find the best values for `n_init` and `max_iter`.

4. **Principal Component Analysis (PCA) Dimensionality Reduction**: PCA is a linear dimensionality reduction technique that transforms the data into a new coordinate system defined by its principal components. The principal components are orthogonal directions that capture the maximum variance in the data. By selecting a reduced number of principal components, we can represent the data in a lower-dimensional space while retaining most of its variance.

5. **Singular Value Decomposition (SVD) Dimensionality Reduction**: SVD is used to decompose the high-dimensional feature space of the images into its singular vectors and singular values. We can then select a reduced number of top singular vectors to project the data into a lower-dimensional space. SVD is commonly used for reducing the dimensionality of data while preserving its important features and is especially useful for large datasets.

6. **Truncated Singular Value Decomposition (Truncated SVD) Dimensionality Reduction**: Truncated SVD is a variant of SVD that allows us to select a specific number of top singular vectors to keep, effectively reducing the dimensionality of the data. By truncating the number of singular vectors, we can obtain a lower-dimensional representation that still captures most of the important information in the original data.

7. **Independent Component Analysis (ICA) Dimensionality Reduction**: ICA is a statistical technique used to find a linear transformation of the data so that the resulting components are statistically independent. ICA is particularly useful for separating mixed signals into their original sources. In the context of dimensionality reduction, ICA can be used to identify the most important independent components of the data, effectively reducing its dimensionality.

8. **Evaluation Metrics - Silhouette Score**: The silhouette score is used to evaluate the quality of the clustering results for different methods. The silhouette score is a popular evaluation metric used to assess the quality of clustering results. It provides a measure of how well each data point fits into its assigned cluster and how distinct the clusters are from each other. The silhouette score ranges from -1 to 1:

- A score close to +1 indicates that the data point is well-clustered and far from neighboring clusters. It suggests that the data point is appropriately assigned to its cluster and is well-separated from other clusters.

- A score close to 0 indicates that the data point is near the decision boundary between two clusters. It suggests that the data point is neither clearly associated with its cluster nor well-separated from other clusters.

- A score close to -1 indicates that the data point may have been assigned to the wrong cluster. It suggests that the data point is more similar to data points in other clusters than to its own cluster.

6. **Best Applicable Method**: Based on the silhouette scores, the best applicable method is Truncated SVD with K-means. Truncated SVD with K-means achieves the Silhouette Score of 0.4026751228973261 when applied to the training set. Then this method is applied on the test set.

## Results

When applied on the test data, Truncated SVD with K-means achieves Silhouette Score of 0.07754281788130456 (0.08). The results and plots for each step can be found in the notebook. The insights of the clustering performance of different methods and the best applicable technique for the Fashion MNIST dataset are provided.

## Conclusion

Unsupervised learning techniques, such as dimensionality reduction and clustering, offer valuable insights into the underlying structure of datasets without relying on labeled data. The result I obtained is not good enough. Tuning of more parameter in wider range and exploring other clustering techniques may come handy. I faced computational challenges during parameter tuning. However, this notebook can be a good start to go on further improvement.
