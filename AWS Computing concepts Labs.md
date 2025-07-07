# Working with AWS Lambda
### Utilization of EC2, lambda and MySQL

In this lab, I deployed and configured an AWS Lambda based serverless computing solution. The Lambda function generates a sales analysis report by pulling data from a database and emailing the results daily. The database connection information is stored in Parameter Store, a capability of AWS Systems Manager. The database itself runs on an Amazon Elastic Compute Cloud (Amazon EC2) Linux, Apache, MySQL, and PHP (LAMP) instance


### Architecture design
![image](https://github.com/user-attachments/assets/b3701c5e-74b0-4326-84ce-5ddb8f616356)

### Objective

After completing this lab, I was able to do the following:

Recognize necessary AWS Identity and Access Management (IAM) policy permissions to facilitate a Lambda function to other Amazon Web Services (AWS) resources.

Create a Lambda layer to satisfy an external library dependency.

Create Lambda functions that extract data from database, and send reports to user.

Deploy and test a Lambda function that is initiated based on a schedule and that invokes another function.

Use CloudWatch logs to troubleshoot any issues running a Lambda function.



### Deployment
From identity and access management roles notice that lambda.amazonaws.com is listed as a trusted entity, which means that the Lambda service can use this role.

![image](https://github.com/user-attachments/assets/8f97ff21-5086-4b01-86ad-f8c5a61f64a5)

Notice the four policies assigned to this role:

AmazonSNSFullAccess provides full access to Amazon SNS resources.

AmazonSSMReadOnlyAccess provides read-only access to Systems Manager resources.

AWSLambdaBasicRunRole provides write permissions to CloudWatch logs (which are required by every Lambda function).

AWSLambdaRole gives a Lambda function the ability to invoke another Lambda function


![image](https://github.com/user-attachments/assets/e85693ed-6c1a-4530-8112-63e0960480c6)




#### Creating a Lambda Layer

I created a Lambda layer named pymysqlLibrary and uploaded the client library into it so that it can be used by any function that requires it. Lambda layers provide a flexible mechanism to reuse code between functions so that the code does not have to be included in each function’s deployment package


![image](https://github.com/user-attachments/assets/a497ca1c-2b98-45ef-a835-3225dd67e72b)


Adding the Lambda layer to the function


![image](https://github.com/user-attachments/assets/cec43620-02d9-462a-b66d-a4b0d015e2ea)


Importing the code for the data extractor Lambda function written in python

The Lambda function code is imported and displays in the Code source panel

![image](https://github.com/user-attachments/assets/bc0c5e5a-1fed-4c7d-b4c4-7455f7f616d4)



