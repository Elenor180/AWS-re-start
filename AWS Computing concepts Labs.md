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

