**End-to-End Feature Store and Churn Prediction Pipeline on AWS**

**Project Overview:**
This project demonstrates an end-to-end machine learning pipeline for customer churn prediction built using AWS cloud services and containerized deployment. It covers the complete lifecycle from data ingestion and feature storage to model training, container-based deployment, and real-time inference. The project uses Docker to package the inference logic and dependencies, which is deployed to AWS Lambda using a container image stored in Amazon ECR.

**Problem Statement**
Customer churn is a critical business problem for subscription-based services. Retaining existing customers is often more cost-effective than acquiring new ones. This project aims to analyze customer behavior data, build a churn prediction model, and deploy it in a scalable, secure, and production-ready cloud environment.

**Objectives**
The objectives of this project are:
-- Build a reusable feature store using DynamoDB
-- Train and evaluate a churn prediction model
-- Containerize the inference logic using Docker
-- Deploy the container image using AWS Lambda and Amazon ECR
-- Ensure secure credential management with IAM roles
-- Demonstrate an end-to-end production-style ML workflow

**Architecture Overview**
The pipeline follows these steps:
1. Data Ingestion
Raw customer data is uploaded and stored in Amazon S3.
2. Feature Engineering and Feature Store
Relevant features are processed and stored in Amazon DynamoDB, which acts as a centralized feature store.
3. Model Training
A machine learning model (Logistic Regression) is trained using Python and scikit-learn.
4. Model Serialization
The trained model is serialized using joblib.
5. Containerization Using Docker
The inference code, model loading logic, and dependencies are packaged into a Docker container using a Dockerfile.
6. Image Storage
The Docker image is pushed to Amazon ECR (Elastic Container Registry).
7. Serverless Deployment
AWS Lambda is configured to run using the container image from ECR.
8. Inference
Lambda fetches customer features from DynamoDB, loads the model from S3, and returns churn predictions in JSON format.

**Technologies Used**
1.Cloud Services:
-- Amazon S3 for raw data and model storage
-- Amazon DynamoDB as a feature store
-- AWS Lambda for serverless inference
-- Amazon ECR for container image storage
-- AWS IAM for secure access management

2.Programming, ML, and DevOps:
-- Python
-- Pandas and NumPy
-- Scikit-learn
-- Joblib
-- Boto3
-- Docker

3.Security and Credential Management:
-- No AWS credentials are hardcoded in the codebase.

4.Authentication and authorization are handled using:
-- AWS CLI configuration for local development
-- IAM roles attached to AWS Lambda for runtime permissions
-- This ensures secure access and makes the repository safe for public GitHub use.

**Project Structure**

1.churn_prediction
Contains the Jupyter notebook used for:
-- Data preprocessing
-- Feature engineering
-- Model training
-- Model evaluation
-- Model serialization

2.lambda_container
Contains the containerized Lambda inference setup:
-- app.py (Lambda handler code)
-- requirements.txt (Python dependencies)
-- Dockerfile (Docker image configuration)

3.README.md
-- Project documentation.
-- How to Run Locally:
Step 1: Configure AWS credentials
Run aws configure and provide valid AWS credentials.

Step 2: Install dependencies
Install Python dependencies using pip install -r requirements.txt.

Step 3: Run the notebook
Open and execute the notebook in the churn_prediction folder to train and save the model.

Step 4: Build Docker image
Navigate to the lambda_container folder and build the Docker image using Docker.

Step 5: Push image to ECR
Authenticate Docker with ECR and push the image.

Step 6: Deploy Lambda
Create an AWS Lambda function using the container image from ECR.

**Model Output**
The deployed Lambda function returns:
-- Churn prediction (0 = No Churn, 1 = Churn)
-- Churn probability


**Key Highlights:**
1.End-to-end ML pipeline on AWS
2.Feature store using DynamoDB
3.Containerized inference using Docker
4.Serverless deployment via AWS Lambda
5.Secure IAM-based authentication
6.Production-ready architecture

**Future Enhancements**
1.Potential improvements include:
2.API Gateway integration for public REST API
3.CI/CD pipeline for automated deployments
4.Advanced models such as XGBoost
5.SageMaker Feature Store integration
6.Monitoring using CloudWatch metrics

**Author**
Devara Lasya
