### This project demonstrates an end-to-end machine learning workflow on AWS SageMaker using the built-in XGBoost algorithm. The goal is to predict whether a customer subscribes to a term deposit, based on the well-known Bank Marketing dataset.

#### Workflow Overview

Setup & Configuration

Create a unique S3 bucket.

Configure SageMaker and Boto3 sessions in the us-east-1 region.

Note: in us-east-1, S3 buckets must be created without a location configuration.

Data Ingestion

Download the pre-cleaned bank marketing dataset.

Load into a DataFrame and perform a 70/30 train-test split.

Preprocessing & Upload

Reorder data so the label column is the first field.

Save and upload train/test datasets to S3 in CSV format.

Model Training

Use the XGBoost 1.7-1 container in SageMaker.

Train on an ml.m5.2xlarge instance with managed spot training for cost savings.

Optimized hyperparameters include depth, learning rate, gamma, and number of rounds.

Deployment

Deploy the trained model as a real-time endpoint on an ml.m4.xlarge instance.

Enable CSV serialization and deserialization for data exchange.

Prediction & Evaluation

Predictions returned as probabilities between 0 and 1.

Rounded predictions achieve an overall classification accuracy of ~89.7%.

Key evaluation results:

No Purchase: ~91% correctly classified

Purchase: ~66% correctly classified

Cleanup

Delete the SageMaker endpoint after testing to avoid charges.

Clear or remove the S3 bucket used for training and test data.

Key Notes

Cost Efficiency: Spot training reduced training costs by over 60%.
