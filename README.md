# Ads Click Prediction Project Overview

## Key Question
1. How can we enable marketers who only knows SQL to do ad-hoc querying and dashboarding on big data?
2. Can we predict the likelihood of an advertisement being clicked before it goes live?

## Topic
An advertisement is only worth the amount of attention it gets. For anyone trying to promote content, the main objective is to capture the eye of a potential customer and convince them to buy or use their product. For businesses looking to increase their presence online, this can be a monumental task. With a crowded field of competition, every click matters. Our goal with this project is to help businesses predict how effective their advertisement will be before they launch it. 

## Dataset
Our data comes from a kaggle competition featuring the data from the content discovery platform Outbrain. The data consist of eight tables containing over 100GB total. There is a lot we can accomplish with this data, and using various big data tools listed below we hope to accomplish the following:
> Data Source: https://www.kaggle.com/c/outbrain-click-prediction/data.

> Dataset Relationships:

![Table Relationships](https://github.umn.edu/liang625/aws-click-big/blob/master/dataset%20relationships.PNG)

## Approach
1. Understand user behavior using AWS Quicksight
2. Build a Model that successfully predicts whether a user will click on an ad, rank the likelihood an ad will be clicked given a set of recommendations

![Approach Framework](https://github.umn.edu/liang625/aws-click-big/blob/master/Framework.png)

We used Amazon S3 to store our data, used Amazon Athena and QuickSight to perform EDA, and used Apache Spark, Amazon SageMaker, EC2, and EMR to create our model.

### Set Up Instructions
1. Set up Amazon S3 bucket, follow the instructions here: https://docs.aws.amazon.com/AmazonS3/latest/user-guide/create-bucket.html
2. Open Athena to create database using data on S3, this step is easy Athena provide UI interface to create table, you just need to worry about the querying. For instructions https://docs.aws.amazon.com/athena/latest/ug/getting-started.html
3. Build QuickSight Dashboard. We purchased 30GB SPICE amount, an in-memory optimized calculation engine, so that it only take less than 3 secs to refresh the visulization. 
4. Set up and launch an EC2 instance, follow the instructions here: https://docs.aws.amazon.com/efs/latest/ug/gs-step-one-create-ec2-resources.html. Make sure you save your key-pair in the directory you know for further use.
5. Set up an EMR environment and create a cluster, following the instructions here: https://docs.aws.amazon.com/emr/latest/ManagementGuide/emr-gs.html. Make sure you set up through 'advanced setting', so that you can choose 'JupyterHub' and 'Spark' in the Software Configuration section. After getting your cluster in running mode, you can click the 'JupyterHub', which leads you to a Jupyternotebook platform to create your own coding script for feature engineering.
6. Create an Amazon SageMaker Notebook Instance and launch it, follow the instructions here: https://docs.aws.amazon.com/sagemaker/latest/dg/gs-console.html. After launching your SageMaker Notebook instance, you can start to create a training job by clicking the "training job" in the guidance on the screen to the left.


## Dashboard Demo
We used Athena to perform querying and feed the result to QuickSight for Dashboarding. QuickSight demonstrated its strong power in handling big dataset, with 30GB data for visualization, the entire dashboard only spends less than 30s to update.

**Desktop**

![Dashboard Demo Desktop](https://github.umn.edu/liang625/aws-click-big/blob/master/quicksight_desktop.jpeg)


## Main files
`sql query for viz.html`: Some SQL queries used in Spark SQL or Amazon Athena

`feature_engineering.ipynb`: Feature engineering and table exploration in PySpark on Amazon EMR cluster

`model.tar.gz`: Compressed model created from Amazon SageMaker

`Xgboost Modeling Result.md`: Information about the model result


