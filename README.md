# Lab Assignment: Hierarchical and DBSCAN Clustering

### Name: Avinna Bhattarai

### Course: MSCS 634

### Date: July 13, 2025

## Purpose of the Lab

This lab explores and compares two fundamental clustering algorithms: **Agglomerative Hierarchical Clustering** and **DBSCAN**. The objective was to apply these methods to the `sklearn` Wine dataset to understand their practical application, the influence of their parameters, and how to evaluate and interpret the results.

## Step 1: Data Preparation and Exploration

The initial step involved preparing the dataset for clustering analysis.

* **Loaded the Wine dataset** from `sklearn.datasets`.

* **Examined the dataset’s structure** using pandas functions like `.head()`, `.info()`, and `.describe()`.

* **Standardized the features** using `StandardScaler`. This was a crucial step to ensure that all features, regardless of their original scale, contributed equally to the distance-based calculations used by both clustering algorithms.

## Step 2: Hierarchical Clustering

In this step, Agglomerative Hierarchical Clustering was applied to group the data.

* The algorithm was configured to create **3 clusters**, a choice justified by both the known number of classes in the dataset and the structure revealed in the dendrogram.

* The resulting clusters were visualized using a 2D scatter plot, showing a clear partitioning of the data.

* An **interactive dendrogram** was generated to visualize the entire hierarchical structure, confirming that three main branches was a natural and appropriate choice.

## Step 3: DBSCAN Clustering

The DBSCAN algorithm was applied to find density-based clusters. This step highlighted the importance of parameter tuning.

* Initial attempts with untuned parameters failed to produce meaningful clusters.

* Through an iterative process of adjusting the `eps` parameter, an optimal value of **`eps=2.4`** (with `min_samples=5`) was identified.

* With the tuned parameters, DBSCAN successfully identified distinct clusters and isolated several noise points.

* The quality of the clustering was validated with strong evaluation scores:

  * **Silhouette Score**: 0.196

  * **Homogeneity Score**: 0.504

  * **Completeness Score**: 0.552

## Step 4: Analysis and Insights

### Hierarchical Clustering

* The interactive dendrogram clearly showed the data naturally branching into three main groups, justifying the choice of `n_clusters=3`.

* The scatter plot confirmed this by showing three visually distinct and relatively well-separated clusters. This indicates the algorithm effectively partitioned the data according to its underlying structure.

* **Strength**: The dendrogram provides a great visualization of the entire hierarchy, making the choice of `k` transparent.

* **Weakness**: The method is less flexible and requires the user to specify the number of clusters beforehand.

### DBSCAN

* The initial run with untuned parameters failed to find a meaningful structure. However, after an iterative tuning process, an optimal value of `eps=2.4` was found.

* With the tuned parameters, DBSCAN successfully identified distinct clusters while also isolating noise points, confirmed by a strong positive Silhouette Score and good Homogeneity and Completeness scores.

* **Strength**: Its ability to find natural cluster structures and identify noise without needing the number of clusters specified beforehand is a major advantage.

* **Weakness**: The process proved its primary weakness: extreme sensitivity to the `eps` and `min_samples` parameters, which requires a careful, empirical tuning process to be effective.

### Final Comparison

* **Hierarchical Clustering** provided a straightforward path to success because the number of clusters (`k=3`) was a reasonable assumption for this dataset, a choice well-supported by the dendrogram.

* **DBSCAN** was more challenging. Its success was highly dependent on parameter tuning. The process highlighted both its greatest weakness (parameter sensitivity) and its greatest strength (discovering a good clustering structure on its own). Once tuned, it produced a high-quality result without prior knowledge of the number of clusters.

## Key Challenges Faced

1. **Parameter Tuning for DBSCAN**: The most significant challenge was finding the optimal `eps` value. The lab demonstrated that a small change could cause the algorithm to either merge all points into one cluster or classify all points as noise.

2. **Visualization of High-Dimensional Data**: Visualizing the 13-dimensional Wine dataset in 2D required simplification. The scatter plots, while useful, only show a projection of the data, and the actual clustering occurs in the full-dimensional space.

3. **Interpreting Initial Dendrogram**: The initial full dendrogram was unreadable due to the number of data points. The key decision was to use an interactive or truncated version to make the visualization meaningful for analysis.

## Files Included

* `README.md` - This explanatory file.

* `Lab5.ipynb` - The Jupyter Notebook containing all the code and analysis for the lab.
