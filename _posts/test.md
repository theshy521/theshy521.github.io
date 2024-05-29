# Operationalizing an AWS ML Project
In this project, you will complete the following steps:

Train and deploy a model on Sagemaker, using the most appropriate instances. Set up multi-instance training in your Sagemaker notebook.
Adjust your Sagemaker notebooks to perform training and deployment on EC2.
Set up a Lambda function for your deployed model. Set up auto-scaling for your deployed endpoint as well as concurrency for your Lambda function.
Ensure that the security on your ML pipeline is set up properly.


# Pre-condition
Attached scrips are available to run on AWS SageMaker platform


## Step 1 : Training and deployment on Sagemaker
Initial setup, training and deployment

1. Initial Setup
![Screenshot instance_type](/screenshots/notebook_instance.png)

I choose "ml.t3.medium" instance type due to it is a starter code so do not need high computing resource.

2. Download data to an S3 bucket
![Screenshot s3_buckets](/screenshots/s3_buckets.png)


3. Training and deployment
![Screenshot inference](/screenshots/endpoint.png)


## Step 2 : EC2 Training
After completing Step 1, you should have a notebook that completes model training and deployment on Sagemaker. The next step is to set up an EC2 instance and accomplish model training there.

1. EC2 Setup
![Screenshot ec2_instance](/screenshots/ec2_instance.png)

I choose "m5.xlarge" instance type and 5 instance count due to it is deep learning project,so it needs high computing resource.

![Screenshot ec2_model](/screenshots/ai_model.png)

After comparing the codes between "train_and_deploy-solution.ipynb" and "solution.py", I have found "solution.py" do not include hyparameter tuning, model deployment and inference part.Especially, to begin with training ai model to activate pre-built pytorch environment, run: 'source activate pytorch' and to activate base conda environment upon login, run: 'conda config --set auto_activate_base true'.


## Step 3 : Lambda function
Lambda functions enable your model and its inferences to be accessed by API's and other programs, so it's a crucial part of production deployment. I have add the enpoint name in "lambdafunction.py"


## Step 4 : Security Group
![Screenshot iam_lambda](/screenshots/IAM_lambda.png)
Add the "AmazonSageMakerFullAccess" for lambda role in IAM.

![Screenshot security_lambda](/screenshots/security_lambda.png)
Successfully testing lambda with two parameter: context type and image url
