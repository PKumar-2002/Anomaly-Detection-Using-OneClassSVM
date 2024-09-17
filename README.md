# One-Class SVM for Anomaly Detection in Network Traffic (HTTP Service)

This project implements a One-Class Support Vector Machine (SVM) model for detecting anomalies in network traffic using the KDD Cup 1999 dataset. We focus specifically on network traffic that uses the HTTP service, and the model is trained to identify abnormal behavior (anomalies) in the data.

## Dataset
The dataset used in this project is the **KDD Cup 1999** dataset, which contains multiple features associated with network connections and labels indicating whether a connection is normal or an attack.

- **Training Data**: `kddcup.data_10_percent_corrected`
- **Test Data**: `corrected`

### Features:
- We filter the dataset to only include data related to HTTP service traffic and remove the `service` column.
- Categorical columns are label-encoded to convert them into numerical values.

## Data Preprocessing
1. **Label Encoding**: 
   - All categorical columns (including the `label` column) are transformed into numerical values using `LabelEncoder`.

2. **Standardization**:
   - The feature values are normalized using `StandardScaler` to ensure they are on the same scale.

3. **Dimensionality Reduction with PCA**:
   - Principal Component Analysis (PCA) is applied to reduce the dimensionality of the dataset, keeping only the top 20 principal components for further processing.

```python
pca = PCA(n_components=20)
x_train = pca.fit_transform(x_train)
x_val = pca.transform(x_val)
x_test = pca.transform(x_test)
