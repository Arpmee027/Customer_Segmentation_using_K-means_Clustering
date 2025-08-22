# Customer_Segmentation_using_K-means_Clustering
Identifying customer segments for online retail with the use of K-means clustering

## Project Overview
This project focuses on performing customer segmentation for an online retail dataset using the K-means clustering algorithm. The goal is to group customers into distinct segments based on their purchasing behavior, enabling a better understanding of customer value and allowing for targeted marketing strategies. The analysis is based on the **Recency, Frequency, Monetary Value (RFM)** model, a widely used marketing technique for analyzing customer value.

## Dataset
The analysis uses the `Online Retail.csv` dataset. This dataset contains transaction data for a online retail store.
### Columns:
- `InvoiceNo`: Invoice number. A 'C' prefix indicates a cancellation.
- `StockCode`: Product (item) code.
- `Description`: Product description.
- `Quantity`: The quantity of each item per transaction.
- `InvoiceDate`: Date and time of the invoice.
- `UnitPrice`: Unit price of the item.
- `CustomerID`: Unique identifier for each customer.
- `Country`: The country where the customer resides.

## Methodology
The project follows a standard data science workflow:

### 1. Data Loading and Exploration
The raw data is loaded and a preliminary exploration is performed to understand its structure, check for missing values, and identify any anomalies.

### 2. Data Cleaning and Preprocessing
The dataset is cleaned to ensure the quality of the analysis. This involves:
- Dropping rows with missing `CustomerID` values.
- Removing canceled orders (invoices with an `InvoiceNo` containing 'C').
- Converting the `InvoiceDate` column to a datetime object for time-based calculations.
- Creating a new `TotalPrice` column by multiplying `Quantity` and `UnitPrice`.

### 3. RFM Analysis
The core of the segmentation is based on the RFM model:
- **Recency**: The number of days since the customer's last purchase. A lower number indicates a more recent interaction.
- **Frequency**: The total number of purchases made by the customer. A higher number indicates a more frequent customer.
- **Monetary Value**: The total amount of money spent by the customer. A higher value indicates a high-spending customer.
These three metrics are calculated for each unique `CustomerID`.

### 4. Data Scaling
The RFM metrics are on different scales (e.g., Recency in days, Monetary in currency units), which can bias the K-means algorithm. To address this, the RFM data is standardized using `StandardScaler` to ensure all features contribute equally to the clustering process.

### 5. K-means Clustering
The K-means algorithm is used to group customers.
- **Elbow Method**: The Elbow Method is applied to determine the optimal number of clusters (`k`). This method plots the within-cluster sum of squares (WCSS) against the number of clusters. The "elbow" of the curve, where the rate of decrease in WCSS slows down, suggests the optimal number of clusters.
- **Clustering**: The K-means model is trained with the optimal number of clusters, and each customer is assigned to a cluster.

### 6. Cluster Profiling and Visualization
After clustering, the characteristics of each cluster are analyzed and visualized. This step provides insights into the different customer segments. Visualizations include:
- Histograms to show the distribution of Recency, Frequency, and Monetary values within each cluster.
- Bar plots to show the average RFM values per cluster.
- Scatter plots to visualize the clusters in two-dimensional space (e.g., Recency vs. Monetary).

## Requirements
The following Python libraries are required to run this notebook:
- `pandas`
- `numpy`
- `datetime`
- `matplotlib`
- `seaborn`
- `scikit-learn`
- `warnings`
You can install them by installing the requirements.txt using pip:
`pip install -r requirements.txt`

## How to Run
1. Place the `Online Retail.csv` file in the same directory as the Jupyter Notebook.
2. Open the notebook in a Jupyter environment.
3. Run the cells sequentially to execute the analysis.