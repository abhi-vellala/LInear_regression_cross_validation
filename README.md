# Build own functions of Linear Regression Cross Validation

*This is a part of LiU's Machine Learning(732A99) curriculum (Lab1 Block1, Assignment 3)*

Here, functions for Linear Regression is created by using mathematical approach and it is cross-validated(5-fold) by creating another function to do so.

The problem statement is as follows:

1. Implement an R function that performs feature selection (best subset selection) in
linear regression by using k-fold cross-validation without using any specialized
function like lm() (use only basic R functions). Your function should depend on:

• X: matrix containing X measurements.

• Y: vector containing Y measurements.

• Nfolds: number of folds in the cross-validation.

You may assume in your code that matrix X has 5 columns. The function should plot the
CV scores computed for various feature subsets against the number of features, and it
should also return the optimal subset of features and the corresponding cross-validation
(CV) score. Before splitting into folds, the data should be permuted, and the seed 12345
should be used for that purpose.


You may assume in your code that matrix X has 5 columns. The function should plot the
CV scores computed for various feature subsets against the number of features, and it
should also return the optimal subset of features and the corresponding cross-validation
(CV) score. Before splitting into folds, the data should be permuted, and the seed 12345
should be used for that purpose.

