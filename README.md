# AV
#Question

Happy Customer Bank is a mid-sized private bank that deals in all kinds of banking products, like Savings accounts, Current accounts, investment products, credit products, among other offerings. The bank also cross-sells products to its existing customers and to do so they use different kinds of communication like tele-calling, e-mails, recommendations on net banking, mobile banking, etc. In this case, the Happy Customer Bank wants to cross sell its credit cards to its existing customers. The bank has identified a set of customers that are eligible for taking these credit cards. Now, the bank is looking for your help in identifying customers that could show higher intent towards a recommended credit card, given: Customer details (gender, age, region etc.) Details of his/her relationship with the bank (Channel_Code, Vintage, Avg_Asset_Value etc.)

Data dictionary

Variable	Description

ID	Unique Identifier for a row
Gender	Gender of the Customer
Age	Age of the Customer (in Years)
Region_Code	Code of the Region for the customers
Occupation	Occupation Type for the customer
Channel_Code	Acquisition Channel Code for the Customer (Encoded)
Vintage	Vintage for the Customer (In Months)
Credit_Product	If the Customer has any active credit product (Home loan,Personal loan, Credit Card etc.)
Avg_Account_Balance	Average Account Balance for the Customer in last 12 Months
Is_Active	If the Customer is Active in last 3 Months
Is_Lead(Target)	If the Customer is interested for the Credit Card , 0 : Customer is not interested , 1 : Customer is interested

Datasets:
1.	Train.csv
2.	Test.csv

Training Data Info:
#	Column	Non-Null Count	Dtype
0	ID	245725 non-null	object
1	Gender	245725 non-null	object
2	Age	245725 non-null	int64
3	Region_Code	245725 non-null	object
4	Occupation	245725 non-null	object
5	Channel_Code	245725 non-null	object
6	Vintage	245725 non-null	int64
7	Credit_Product	216400 non-null	object
8	Avg_Account_Balance	245725 non-null	int64
9	Is_Active	245725 non-null	object
10	Is_Lead	245725 non-null	int64

Testing Data Info
#	Column	Non-Null Count	Dtype
0	ID	105312 non-null	object
1	Gender	105312 non-null	object
2	Age	105312 non-null	int64
3	Region_Code	105312 non-null	object
4	Occupation	105312 non-null	object
5	Channel_Code	105312 non-null	object
6	Vintage	105312 non-null	int64
7	Credit_Product	92790 non-null	object
8	Avg_Account_Balance	105312 non-null	int64
9	Is_Active	105312 non-null	object

Step by step procedure

Explore Data (Training and Test)

Exploratory data analysis is an approach of analysing data sets to summarize their main characteristics, often using statistical graphics and other data visualization methods. It is the critical process of performing initial investigations on data so as to discover patterns, spot anomalies, test hypothesis and to check assumptions with the help of summary statistics and graphical representations. The major processes in EDA are:

    1. Handling Missing values
    2. Removing duplicates
    3. Outlier Treatment
    4. Normalizing and Scaling ( Numerical Variables)
    5. Encoding Categorical variables ( Dummy Variables)
    6. Bivariate Analysis

For the above process, some important libraries are imported,

    1. Numpy
    2. Pandas
    3. Seaborn and
    4. Matplotlip

For handling missing values and to remove duplicates, isnull() and duplicated() functions from pandas are used respectively.

Outliers, being the most extreme observations, may include the sample maximum or sample minimum, or both, depending on whether they are extremely high or low. However, the sample maximum and minimum are not always outliers because they may not be unusually far from other observations.

Using box and whiskers chart (boxplot) we can show the outlier in the data set.

If there are outliers in the data, they can be dealt with using any of the methods such as:

    1. Drop the outlier value
    2. Replace the outlier value using the __IQR__(Interquartile Range)
    3. Use Log Transform

Before the normalising split the data into numerical distribution data set using select_dtypes(). Then verify the skewness. The primary reason of the skew is that analysis based on normal distributions incorrectly estimates expected returns and risk. Skewness is a measure of symmetry, or more precisely, the lack of symmetry. A distribution, or data set, is symmetric if it looks the same to the left and right of the center point.

Kurtosis is a measure of whether the data is heavy-tailed or light-tailed relative to a normal distribution. That is, data sets with high kurtosis tend to have heavy tails, or outliers. Data sets with low kurtosis tend to have light tails, or lack of outliers. 

The histogram is an effective graphical technique for showing both the skewness and kurtosis of data set. Data scaling is a recommended pre-processing step when working with data. Data scaling can be achieved by normalizing or standardizing real-valued input and output variables. 

Next step is to build the models using LGBM (Light Gradient Boosted Machine) and XG boost. For that, we need to tune parameters using RandomizedSearchCV or GridSearchCV.

The performance of the models is measured using AUC-ROC. 

AUC_ROC means The Receiver Operator Characteristic (ROC) curve is an evaluation metric for binary classification problems. It is a probability curve that plots the TPR(True Positive) against FPR (False Positive) at various threshold values and essentially separates the ‘signal’ from the ‘noise’. The Area Under the Curve (AUC) is the measure of the ability of a classifier to distinguish between classes and is used as a summary of the ROC curve.

