# Churn prediction for Sparkify

Udacity nanodegree "Data scientist", project 4.0 ("Capstone project")

### Summary

In this project, I analyzed the log trace of a fictional music streaming service ("Sparkify") to predict churn events of customers. 
Churn events consist in cancellation requests of customers to the streaming service. Due to low barriers of product substitution and high customer acquisition costs, 
customer churn has a heavy impact on the business success of music streaming services. 
The dataset has been analyzed using Python / PySpark and Jupyter notebooks. The code has been executed locally (not in a Spark cluster). 

### General data

Autor: Christoph Wagner
Date of publication: 20/09/2020

### The dataset

The dataset has been created artificially by Udacity.com. Due to performance reasons, in this project, only a small subset (128 MB) of the original 12 GB dataset is used. 
The main problem of this project is to predict churn of the users involved in the dataset. 
Here, churn is defined as the access of page "Cancellation Confirmation" by the user, visible in the log trace of the music streaming service. 

Schema of the dataset:
root
- artist: string (nullable = true)
- auth: string (nullable = true)
- firstName: string (nullable = true)
- gender: string (nullable = true)
- itemInSession: long (nullable = true)
- lastName: string (nullable = true)
- length: double (nullable = true)
- level: string (nullable = true)
- location: string (nullable = true)
- method: string (nullable = true)
- page: string (nullable = true)
- registration: long (nullable = true)
- sessionId: long (nullable = true)
- song: string (nullable = true)
- status: long (nullable = true)
- ts: long (nullable = true)
- userAgent: string (nullable = true)
- userId: string (nullable = true)
 
More information about the exploratory data analysis can be found in the respective Jupyter notebook or in the linked blogpost article (see link below). 
 
### Steps of the analysis
- Loading / cleaning of the dataset
- Exploratory data analysis (EDA)
- Feature engineering
- Modelling

### Results
In the first modelling step, 7 different classifiers were compared in concerns of F1 score and accuracy on a test dataset:
*DecisionTreeClassifier
*GBTClassifier
*RandomForestClassifier
*LinearRegression
*LogisticRegression
*LinearSVC
*MultilayerPerceptronClassifier
The LinearRegression classifier obviously cannot be used when predicting a categorical (dichotomous) variable.
Regarding the F1 score, LogisticRegression turned out to be the best classifier, having position 2 regarding accuracy. 
Due to the high imbalance of churn vs. non-churn users, the F1 score is the better evaluation metric. 

In the second modelling step, LogsticRegression was tuned using a parameter grid. With the best parameter combination, the LogisticRegression model
could predict user churn with a F1 score of 0.65 and accuracy of more than 68 %. 
 
### File content

- README.md										README file 
- Sparkify_Exploration.ipynb					Jupyter notebook containing the exploratory data analysis
- Sparkify_Feature_Engineering_Modelling.ipynb	Jupyter notebook containing feature engineering and modelling

### Used frameworks
Software versions:
- Jupyter Notebook Server 6.0.3
- Python 3.8 (64 bit)

Python libraries used in the project:
- pyspark 2.4
- pytz
- numpy
- matplotlib
- pandas

### Installation / Usage

- Install the above mentioned libraries / software
- Clone Git repository: https://github.com/christoph1604/Udacity_DataScientist_Project4.0_Capstone_Sparkify.git
- Run the Jupyter notebooks: 
	cd <downloadpath>
	jupyter notebook

### URL to the related blopost article
 
https://medium.com/@cmf.wagner/churn-prediction-for-sparkify-6cc441eb7dbb