# Class project

Thera Bank Customer Conversion
Converting current depositors to depositors/borrowers
# Business Understanding
<pre>Context: who is Thera Bank? 
Problem: too many deposit (liability) customers, not enough loaners (asset) customers
Creative solution: target current customers as opposed to attracting new ones
<pre/>

# Business Goal 
<pre>
Determine which of Thera Bank’s current deposit-only customers have a high likelihood of taking out a loan, and target them for marketing loan products. 
<pre/>

# Data Understanding
Here’s a screenshot of the first few rows of our dataset, which we got it from Kaggle. The dataset has 5000 instances and 14 columns. Each instance represents a current depositor in Thera Bank. And there are no missing values in this dataset. The blue box includes our 12 attributes, the red box includes our target variable which is whether customers accept personal loan offered in the last marketing campaign, with 0 meaning no, and 1 meaning yes. Since we have a specific target which is to identify who will become our borrowers, this is a classification problem.

# Data Preparation 
There are several steps in our data preparation. 
First, we look at the distribution of the target variable. On the left, is the bar graph for two classes. We can see that we have 4520 zeros, and only 480 ones. So we may need resampling in our modeling process, which will be discussed more in details in later slides. 
The second is to deal with 52 negative values in experience. We decided to replace those values using the median experience from people from the same age instead of the mean experience from the whole dataset. 
The third will be dealing with two ordinal variables, family and education. Family has 4 levels, and education has 3 levels. Even though we can simply put the two variables into our model, we decided to create dummy variables in our KNN and Logistic regression model. And it actually performed better.


# correlation
The last step before modeling is that we want to see whether multicollinearity exists. We conduct correlation analysis among our variables and found that age and experience is highly correlated with a correlation coefficient of 0.994. When choosing whether to keep age or experience, we decided to keep age and remove experience for two reasons. First, when looking at the correlation of the two variables with target variable, age is slightly more correlated with personal loan than experience. In addition, we have all accurate ages for the whole dataset, while we replace some abnormal values in experience, and these values may not be correct. So we believe keeping age is a more appropriate approach. For other variables besides age and experience, the correlation are mostly weak and moderate. So now we have 11 attributes and 1 target variable for modeling.

# Modeling
This is our Modeling process before resampling. Firstly, we split our data into training and test. Then we build 3 models which are DT,KNN and LR. As for KNN, we first standardized x. Then we use Grid Search cross validation to find the best parameters for all 3 models. Take DT for example, the best criterion is Gini and the max depth is 20. In KNN, the k neighbors is 1 and the weights are uniform. The penalty is L1 and balance between the complexity and fit is 1 in LR. We then fit out model with the best hyper parameters to test the generalized performances.


 






