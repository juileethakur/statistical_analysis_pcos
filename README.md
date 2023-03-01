# Case Study of Categorizing the Factors in women with PCOS

This project focuses on the factors that affect an ovarian condition in most women called PolyCystic Ovarian Syndrome. Polycystic Ovary Syndrome (PCOS) is a health problem that affects women of childbearing age.

Women with PCOS may have infrequent or prolonged menstrual periods or excess male hormone (androgen) levels. The ovaries may develop numerous small collections of fluid (follicles) and fail to regularly release eggs. Women with PCOS have a hormonal imbalance and metabolism problems that may affect their overall health. PCOS manifests as a variety of symptoms.

The exact cause of PCOS is unknown. Early diagnosis and treatment and weight loss may reduce the risk of long-term complications such as type 2 diabetes and heart disease before they turn 40 yrs old.

PCOS affects 1-in-10 women:

10% women of child bearing age estimated to have PCOS
50% women go undiagnosed
4.3 Billion cost to the American healthcare system to diagnose and treat women with PCOS
The risk of women with PCOS developing endometrial cancer is increased by 3 times

Thus, in this project we will be focusing on different factors that affect the menstruation cycle, the infertility and the well-being of any woman based on the health and lifestyle. My goal is to use the PCOS dataset on a variety of statistical methods that can be implemented to extract necessary features and get accurate predictions.

# Methodology

1. Normality Test - First, we perform the normality test to check if the data is normal or not. For this we apply the multivariate normality test and get overall normality. We use the multivariate_normality function from pingouin library. Then, to check for each column separately we apply the Shapiro Wilk Test on each column individually and obtain the results. We import the shapiro method from the scipy.stats library. Based on the normality test, we perform the later analysis of ANOVA and categorical data.

2. Mann-Whitney Test - Since, the data is not normal, Mann-whitney test is applied for the comparison of two samples. Here, I applied the test between the response variable data["PCOS(Y/N)"] and remaining columns of the dataset. For this, we use the mannwhitneyu method from the scipy.stats library.

3. Kruskal Wallis Test - Again, since the data is not normal, we apply the Kruskal Wallis test for One-way ANOVA. For this, we use the kruskal method from the scipy.stats library. From this we understand if the means are different are not. But we do not understand for which samples they are actually different.

4. Nemenyi Post-hoc Test - To check which samples are different from each other, we apply the Nemenyi Test. We check the test for the same columns that we used in the Kruskal Wallis test, to get insight on which columns have different means. For this, we use the posthoc_nemenyi_friedman method from scikit_posthocs library.

5. Chi-square test for analysis - For analysis of categorical data, we use chi-square test as we have more than two columns to analyse. Using the chi-square test, we get the p-value for testing the hypothesis. If the p-value is significantly lower, we use the Cramver's V to conclude our interpretation. For this, we use the crosstab method from researchpy library.

6. Logistic Regression - Since my response variable is binary, I used the logistic regression to analyse the accuracy. For this I used the LogisticRegression method from sklearn.linear_model. The classification report shows the accuracy and the F-1 score.

7. Ridge and Lasso Regression - After performing logistic regression, I perform Ridge regression and Lasso regression for the logistic one to check the accuracy of the same. For this, I used Ridge() and Lasso() methods respectively from sklearn.linear_model.

8. Forward and Backward Selection - We then perform forward and backward selection in order to get the top best features i.e. attributes from the dataset.

9. Bootstrap and k-fold validation - We perform Bootstraping and k-fold validation amongst the resampling method using Lasso and compare the accuracy of the same.

10. Principle Component Analysis (PCA) - Using the best features that we obtained, we apply the technique of dimensionality reduction and obtain the confusion matrix which helps us obtain the accuracy and compare with the rest. For this, we import PCA method from sklearn.decomposition library.

11. Polynomial Regression - Since, fitting data in a linear manner can give far less accuracy, we use polynomial regression. We use PolynomialFeatures method from sklearn.preprocessing library and compare the errors for second, third, fourth and fifth order polynomials.

12. Generalised Additive Models (GAM) - In GAM, the linear response variable "PCOS(Y/N" depends linearly on unknown smooth functions of some predictor variables from the dataset. We infer the performance based on them.
