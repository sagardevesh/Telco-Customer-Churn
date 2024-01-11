## Telco-Customer-Churn
This project aims to predict customer churn by analyzing relevant customer data in the Telco customer churn dataset.

Here is the link to the original [Telco Customer Churn Dataset](https://www.kaggle.com/datasets/blastchar/telco-customer-churn) on Kaggle. 

The first step in this project was to understand the data and perform feature engineering. We also had to add a new column 'tenure' that would calculate the tenure of the customer with the company considering the date on which this project was run, as the base date.

Next, we created Data Quality Reports for continuous and categorical features, which looked like below:-

![image](https://github.com/sagardevesh/Telco-Customer-Churn/assets/25725480/d768bb2e-18e7-4aee-ac4c-7d2ae41ddd9d)
Continuous features report

![image](https://github.com/sagardevesh/Telco-Customer-Churn/assets/25725480/ccd85c8c-79cc-4355-9dc6-98e55fd3646c)
Categorical features report

The next step was to perform feature visualisation for continuous features, which was a part of data understanding. For eg, the below chart shows the count of customers versus their monthly charges:-

![image](https://github.com/sagardevesh/Telco-Customer-Churn/assets/25725480/93bcba42-2415-4a75-bb84-18cd5d925d70)

Further, we performed feature visualisation for categorical features. For eg, below is the chart for the male and the female ratio in the Telco customers:-

![image](https://github.com/sagardevesh/Telco-Customer-Churn/assets/25725480/efba58a7-24ca-497c-90e8-44b51bf3c9aa)

Another categorical feature visualation chart is below, portraying the number of customers using the phone service of Telco:-

![image](https://github.com/sagardevesh/Telco-Customer-Churn/assets/25725480/50a474ee-25e7-4934-a521-356ac95cface)

The next task was to address data quality issue in the dataset and do some preprocessing. For eg, checking for missing values, converting 'Date' column into datetime format and dropping any features that may be unnecessary or irrelevant in predicting customer churn. 

### Chi-Square Test

We  performed Chi-square test to check the correlation between 2 features in the dataframe. Our null hypothesis is that any two given features are not correlated with each other and are independent. If the P-value comes higher than 0.05, our null hypothesis will be accepted. Otherwise, we will reject our null hypothesis and conclude that the 2 features are highly correlated.

For example, the p-value of the chi-square test for the features 'OnlineSecurity' and 'OnlineBackup' came out to be 0, indicating that they are highly correlated. That is, customers opting for online security also opted for online backup in most of the cases. This is also meant that we could go ahead and drop one of these 2 features as having both the features will not improve the accuracy of our model. 

Next, we performed one-hot encoding for all the categorical features which would convert the values of those features into binary values of 0 and 1.

### Finding patterns in the data

We wanted to understand the patterns in the data, and the relationships between the features. For eg, the below figure shows that as the tenure of the customer increases, the use of phone services also increases.
![image](https://github.com/sagardevesh/Telco-Customer-Churn/assets/25725480/1fa18c16-83ea-43a7-8ac8-ba8ddb091030)

More such relationsips can be found in the python file.

### Feature selection

We had too many features in the dataset, and to reduce the feature set we calculated the correlation coefficient of each feature with respect to the 'Churn' column(target variable). We selected the top 3 features to build our model, which were- 'Contract_Month-to-month', 'Contract_Two year' and 'TotalCharges'.

### Random Forest Classifier
The base model we used was a Random Forest Classifier. The split of data into train, test and valiation set was in the ratio 40:30:30. 

Next we used evaluation metrics like mean absolute error and accuracy to evaluate the base model. Based on these accuracy scores, we could analyse that the model was able to predict values with the highest accuracy on the training data with a near perfect score. This was followed with accuracy score on testing data which was 70% and lastly, validation data with a score of 68%. Below is the portrayal of the same:-

![image](https://github.com/sagardevesh/Telco-Customer-Churn/assets/25725480/0496da1c-b71a-40ca-96f2-e881c01be117)

 Later we performed hyperparameter tuning to improve the performance of the Random Forest Classifier.

### Avoiding Overfitting

To avoid overfitting of data, we ensured that the model gets trained on bigger training data size. Since we split our model into training , testing and validation data in the ratio of 40:30:30, it ensured the model got trained on a larger data size than the ratio of data it had to predict. This would decrease the generalisation of any kind in the data that might have led to overfitting.

Another method we used to avoid overfitting was by simplifying the dataset by removing any kind of null and 'Nan' values that may have caused error rate or mean computation to deflect.

### Feefforward Neural Network:-

We performed similar steps to predict customer churn, but this time using a feedforward neural network. Below is how a feefforward neural network looks like:-

![image](https://github.com/sagardevesh/Telco-Customer-Churn/assets/25725480/473415df-25e7-4864-a484-4ee9236f99c9)

We used 'keras' library to build simple package of feedforward neural network, and used 'relu' as our activation function.

### Learning curve

After training our model, we evaluated its performance on our testing data and plotted model's learning curve over loss function using 10 epochs. Below is how the learning curve looked like:-

![image](https://github.com/sagardevesh/Telco-Customer-Churn/assets/25725480/081f44aa-6dd1-46ce-96d4-d247c58cd352)

After evaluation of the model, we got an average training accuracy of 0.75 and testing accuracy of 0.72.

### Avoiding overfitting

To avoid overfitting of data, we simplify our model by reducing complexities with respect to input, hidden and output layers and limiting them to 1. We also perform early stopping of our training process. By early-stopping, we ensure the data generalisation error doesn't occur.

******************************************************************************************************************

## Steps to run on local machine/jupyter notebook:
To run this assignment on your local machine, you need the following software installed.

*******************************************************
Anaconda Environment

Python
*********************************************************

To install Python, download it from the following link and install it on your local machine:

https://www.python.org/downloads/

To install Anaconda, download it from the following link and install it on your local machine:

https://www.anaconda.com/products/distribution

After installing the required software, clone the repo, and run the following command for opening the code in jupyter notebook.

jupyter notebook A1-Sagar_Devesh-Sarthak_Pandit.ipynb
This command will open up a browser window with jupyter notebook loading the project code.

You need to upload the dataset from the git repo to your jupyter notebook environment.




