# Machine-Learning
Airbnb housing feature in Machine Learning with SK-learn

# Outline:
1. Data Ingesting and Preprocessing
2. Exploratory Data Analysis (EDA) - summarize main characteristics with visual methods - OLAP (denormalization) - deal with missin values, tidy data (formats, columns, types), plotting
3. Feature Engineering - （与普通的cleaning不一样）这一步是 particularly base on ML 的进一步处理 - Feature engineering is the process of applying domain knowledge to extract features from raw data via data mining techniques. These features can be used to improve the performance of machine learning algorithms - 这个Project的FE重点在于对数据类型的改变(categorical -> numerical)让文字也能进入modeling，两种方式：1 简单的binary 01处理通过 apply and lambda function，2 当feature不能仅用function去转换的时候，使用 one-hot encoding by creating dummy columns for each desired feature
Conducted feature engineering by one-hot encoding with dummy columns that improved the ML algorithms.

¥	Evaluated ML models using confusion matrix and proved a great performance and accuracy on ML models.



5. Modeling
6. Evalue the performance using confusion matrix, get good accurate


SK-learn - classification model with/without PCA
SparkML - regression model with regularization (L1, L2, Net) with/without PCA
SparkML - random forest


# Classification Model
Goal: predict binary outcomes (wether the housing rating is high or low)
Step:
- create a new column that contains rating boolean (1 or 0) with certain cretria.
- Split Data into Train and Test, 80% for training, 20% for testing.
- Fit and predict the logistic regression with defalut parameters using sklearn, and calculate the accuracy. 准确度应该是不高，所以准备PCA？？？
- Initialize PCA 
1) Scale data first since PCA is not scale invariant
2) plotting the number of components with different variance ratio, and find the my best number of components.
3) using this number of components to fit a new training dataset.
- Logistic Regression with PCA
1) fit model with the training data after PCA
2) predict on the testing data
3) calculate accuracy: accuracy = (TP + TN) / n

Class
before PCA：0.6833
after PCA: 0.6835

问题: 

一些 improve ：
比如速度的提升 / 比如加一些regularization to avoid over-fitting and increase the performance
所以又用了 SparkML 和 3 种regularization
发现后者的 performance 要好一些

SparkML:
before PCA：0.6833
after PCA: 0.6835


# Improvement:

Part II: Distributed Machine Learning with Spark (32 points)
Apache Spark ML is a machine learning library that consists of common learning algorithms and utilities, including classification, regression, clustering, collaborative filtering, dimensionality reduction, and underlying optimization primitives.

Why Spark ML?

Standard implementations of machine learning algorithms require very powerful machines to be able to run. However, depending on high-end machines is not advantageous due to their high price and improper costs of scaling up. The idea of using distributed computing engines is to distribute the calculations to multiple low-end machines (commodity hardware) instead of a single high-end one. This definitely speeds up the learning phase and allows us to create better models.

2.2 Create Pipeline
Now we will create a pipeline. For this data, we just need a single stage with the assembler, but you could have other stages before that where you perform operations on the data like converting categorical strings in the features to numeric values, or do feature scaling operations.

In this step, we will create a pipeline with a single stage — the assembler. Fit the pipeline to your data and create the transformed dataframe and name it modified_data_sdf.

Now that we have the data in the format we need, we will create our train and test sets.

Conduct a train-test split where 80% of the data is assigned to the training set while the remaining 20% is assigned to the testing set.

Next,
Logistic Regression Using SparkML (models same as before but in SparkML)...
