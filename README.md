# Default of credit card
Credit card default happens when you have become severely delinquent on your credit card payments. For example, the U.S. federal government allows student debt to be delinquent for 270 days before declaring it to be in default. It is a delicate status because it will affect the relationship among the client and the card issuer but more important, it will decrease the probability to get approved for future credit-based services. The goal of this analysis is to predict if a client will go in default in the following month by using the Default of [Credit Card Clients Data Set as a reference](http://archive.ics.uci.edu/ml/datasets/default+of+credit+card+clients)

---

Final project for the `Mathematics in Machine Learning` course @ PoliTo

---

## EDA
`Default of Credit Card Clients` Data Set contains 30,000 instances of credit cardstatus collected in Taiwan from April 2005 to September 2005. These informationwere collected because Taiwan’s card issuers expected to reach acard debt pricespick in the third quarter of 2006. In particular, for each record (namely, eachclient) we have demographic information, credit data, history of payments and billstatements.

As one may image, this dataset is `highly imbalanced`, with around 78% of the observations classified as 0 (no-default).

<p align="center">
  <img src="https://github.com/francescodisalvo05/credit-card-default/blob/main/images/readme-00.png"> 
</p>

> For further datails on the EDA step, please consider looking at [this](https://github.com/francescodisalvo05/credit-card-default/blob/main/notebooks/EDA.ipynb) notebook or directly at the proposed [report](https://github.com/francescodisalvo05/credit-card-default/blob/main/DiSalvoFrancesco_S282418.pdf).

## Preprocessing

### Outliers - Local Outliers Factor (LOF)
The `Local Outlier Factor` (LOF) algorithm is an unsupervised method that computes the local density deviation of a given data point with respect to its k-nearest neighbors. It considers as outliers the data points that have a significantly lower density than their neighbors.

### Feature scaling - Normalization
Feature scaling is the process through which you change the values of numericcolumns in the dataset to use a common scale, without distorting differences in theranges of values or losing information. 

Here the `z-normalization`has been applied. It is performed by removing on each data point the mean μ and dividing it for the standard deviation σ. Hence, the normalized dataset will have mean equal to zero and standard deviation equal to one.

### Dimensionality reduction - PCA
Dimensionality reduction is the transformation of the data from an high dimensional space to a low dimensional space. It has several advantages, one of them is that it helps avoiding the `curse of dimensionality`[...].

The most used technique for dimensionality reduction is `Principal ComponentAnalysis` (PCA). It can be interpreted from different point of views, in particular it can bealso seen as avariance maximization problem. In fact, each principal componentwill explain some variance of the initial dataset through a linear combination ofthe features.

In order to determine the proper number of principal components it is necessaryto look for a trade off between the proportion of variance explained and the numberof principal components. A rule of thumb is to choose as many components until you reach a satisfactory variance percentage (80%−90%). We obtain a cumulative explained variance of 85% with `11 Principal Componnets`.

<p align="center">
  <img src="https://github.com/francescodisalvo05/credit-card-default/blob/main/images/10-PCA.svg" height="350px"/>
</p>

### Resampling
Whenever a model learn from an imbalanced dataset, it will be harder to make very accurate predictions, because most of the models tend to prefer the majority class. In fact, in such a circumnstances it is a common practise to rebalance (only) the training set.  Balancing a dataset can be done through under-sampling the majority class, over-sampling the minority class or even with both of these two techniques.

We have tested `Near-Miss V3` (under-sampling), `SMOTE`(over-sampling), `SMOTEEN` (under- and over-sampling).

<p align="center">
  <img src="https://github.com/francescodisalvo05/credit-card-default/blob/main/images/12-resampling-02.svg" height="200px"/>
</p>

> For further datails on the Preprocessing step, please consider looking at [this](https://github.com/francescodisalvo05/credit-card-default/blob/main/notebooks/preprocessing.ipynb) notebook or directly at the proposed [report](https://github.com/francescodisalvo05/credit-card-default/blob/main/DiSalvoFrancesco_S282418.pdf).

## Model evaluation
Since we are dealing with an heavy imbalanced dataset, maximizing the `accuracy` is not the best option because we may have an high number of correct classification, mostly from the majority class (that we know will be preferred by the algorithm). In fact, we are strongly interested in the number of False Negatives (i.e. default classified as no default) without forgetting the number of False Positives (i.e. no default classified as default). Hence, we decided to maximize the `F1` score on our tests with special attention to the `Recall`.

## Model selection
In this section we explored different approaches and different models for solving our problem. In particular we have studied `Random Forest`, `K Nearest Neighbors`, `Support Vector Machines` and and `Logistic Regression`, following the Empirical Risk Minimization (ERM) paradigm.

> If you want to deep dive into the theory behind these algorithms, have a look at the proposed [report](https://github.com/francescodisalvo05/credit-card-default/blob/main/DiSalvoFrancesco_S282418.pdf).

## Results

|`Random Forest`| `Support Vector Machine`| 
| ------------- | ----------------------- |
| <img src="https://github.com/francescodisalvo05/credit-card-default/blob/main/images/res-rf.png" /> | <img src="https://github.com/francescodisalvo05/credit-card-default/blob/main/images/res-svc.png" /> | 

|`K Nearest Neighbors`| `Logistic Regression`| 
| ------------- | ----------------------- |
| <img src="https://github.com/francescodisalvo05/credit-card-default/blob/main/images/rs-knn.png" /> | <img src="https://github.com/francescodisalvo05/credit-card-default/blob/main/images/rr-lr.png" /> | 

## Complete pipeline
Here's a graphic representation of the full-pipeline, considering all the preprocessing activities described above.

<p align="center">
  <img src="https://github.com/francescodisalvo05/credit-card-default/blob/main/images/pipeline.jpg" height="200px"/>
</p>

## Conclusions
Different machine learning alorithms have been tested, as well as different pre-processing techniques. Tu sum up, our goal was to maximize the F1-score, the harmonic mean between precision and recall with a particular attention to the Recall. The `best F1-score` was obtained by `Random Forest (0.51)` whereas the `highest recall` - that may be preferred in such a circumnstances - was achieved by `Support Vector Machine (0.67)`.

> If you want to see some more detailed observations of the results, have a look at the proposed [report](https://github.com/francescodisalvo05/credit-card-default/blob/main/DiSalvoFrancesco_S282418.pdf).

## References

| `Report`  | `EDA` | `Preprocessing`  | `Modeling` |
| ------------- | ------------- | ------------- | ------------- |
| [link](https://github.com/francescodisalvo05/credit-card-default/blob/main/DiSalvoFrancesco_S282418.pdf) | [link](https://github.com/francescodisalvo05/credit-card-default/blob/main/notebooks/EDA.ipynb) | [link](https://github.com/francescodisalvo05/credit-card-default/blob/main/notebooks/preprocessing.ipynb) | [link](https://github.com/francescodisalvo05/credit-card-default/blob/main/notebooks/modeling.ipynb)

