# Class project

Thera Bank Customer Conversion
Converting current depositors to depositors/borrowers
# Business Understanding
Context: who is Thera Bank? 
Problem: too many deposit (liability) customers, not enough loaners (asset) customers
Creative solution: target current customers as opposed to attracting new ones


# Business Goal 

Determine which of Thera Bank’s current deposit-only customers have a high likelihood of taking out a loan, and target them for marketing loan products. 


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

# Evaluation
 Discuss how the result of the data mining is/should be evaluated. 
Two and three
Basd on stands out, distract your attention, mainly closer look at the results of decision trees.
-Accuracy: decision tree
-Errors: Decision tree just makes a few mistakes here. And we are more focused on the mistake in the left lower corner. This will make us miss out opportunities to earn loan interest. This is the lowest among three models. However, we consider the cost of the mistake in the right upper corner to be low. Just imagine the cost of sending an email to customers even if they ignore. To truly weigh the importance of these two mistakes,  we need real-world cost-benefit information. I will mention some benefits we will have in the next slide.
-ROC: ROC is a good measure for unbalanced data. Logistic’s auc is slightly higher than decision tree. But the optimal point, which is closest to the northwest corner, is on decision tree. Carefully looking at the green curve here for logistic, it has higher true positive rates but at the cost of increasing false positive rate dramatically. Again, it relies on cost-benefit matrix. So we just stick to the best result we got from decision trees. 


 






