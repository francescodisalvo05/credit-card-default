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

> For further datails on the EDA step, please consider looking at [this](https://github.com/francescodisalvo05/credit-card-default/blob/main/notebooks/EDA.ipynb) notebook or directly on the proposed [report](https://github.com/francescodisalvo05/credit-card-default/blob/main/DiSalvoFrancesco_S282418.pdf).

## References

| `Report`  | `EDA` | `Preprocessing`  | `Modeling` |
| ------------- | ------------- | ------------- | ------------- |
| [link](https://github.com/francescodisalvo05/credit-card-default/blob/main/DiSalvoFrancesco_S282418.pdf) | [link](https://github.com/francescodisalvo05/credit-card-default/blob/main/notebooks/EDA.ipynb) | [link](https://github.com/francescodisalvo05/credit-card-default/blob/main/notebooks/preprocessing.ipynb) | [link](https://github.com/francescodisalvo05/credit-card-default/blob/main/notebooks/modeling.ipynb)

