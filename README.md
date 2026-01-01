# q15WkH4dkPUakgoM
## Apziva Project 1: Happy Customers

This project aims to predict the customers' happiness based on survey responses.
The client aims to minimize the number of unhappy customers. It is crucial to identify the key features that lead to the customers' happiness.

## Files
EDA.ipynb: Exploratory Data Analysis of the data
Modeling.ipynb: Implementing ML models to predict the customers' happiness

## Conclusion
The project aims to predict the customers' happiness based on survey data.

To establish a baseline, I utilized LazyPredict to evaluate a wide range of machine learning models. By experimenting with various train-test splits and random seed values, I found models that consistently had had top performances: ExtraTreeClassifier, LabelPropagation, QuadraticDiscriminantAnalysis, LGBMClassifier, BernoulliNB consistently.

Following the initial analysis, I conducted more in-depth analysis on the selected models using their source libraries. After analyzing the performance metrics and confusion matrices, I narrowed down the list to ExtraTreeClassifier, QuadraticDiscriminantAnalysis and LGBMClassifier. Two models were eliminated during the process:
- The LabelPropagation model had poorer performance when running it with the source code, compared to running it with LazyPredict.
- The BernoulliNB model predicted all data points to be positive, as shown by its confusion matrix, which resulted in misleading performance scores.

To further enhance model performance, I applied feature selection / recursive feature elimination and ensembling techniques. I was careful that the ensembled model was passed to the estimator to ensure that the features selected reflected the ensembling models' choices.

The final implementation used a voting classifier that combined QuadraticDiscriminantAnalysis, LGBMClassifier and ExtraTreeClassifier. Using a refined feature set of X1 (my order was delivered on time), X3 (I ordered everything I wanted to order), X5 (I am satisfied with my courier), X6 (the app makes ordering easy for me), the model achieved the accuracy of 68%. I determined this set was optimal because eliminating the features further led to poorer performance.

My analysis led to key insights into the customer behavior:
- From the business perspective, I believe feature X4 (I paid a good price for my order) has small relavance to the customers' happiness. Customers who order  online tend to prioritize convenience over cost: they are aware that online orders are pricier than purchasing in-person.
- I had an intuition that feature X2 (contents of my order was as I expected) would significantly contribute to the customers' happiness. However, the violin showed nearly identical distributions for both happy and unhappy customers. This analysis indicates that the feature doesn't have a big impact on determining the customers' happiness.

I suggest the company to focus on features X1, X3, X5, X6 and improve the related operations. For predicting customer happiness, I suggest adapting the voting classifier(QuadraticDiscriminantAnalysis, LGBMClassifier and ExtraTreeClassifier) model.