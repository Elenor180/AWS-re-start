# AWS Identity and Access Management (IAM)

In many business environments, access involves a single login to a computer or a network of computer systems that provides the user access to all resources on the network.
This access includes rights to personal and shared folders on a network server, company intranets, printers, and other network resources and devices. 
Unauthorized users can quickly exploit these same resources if the access control and associated authentication procedures are not set up properly.

In this lab, I explored users, user groups, and policies in the AWS Identity and Access Management (IAM) service

## Objectives 

Create and apply an IAM password policy
Explore pre-created IAM users and user groups
Inspect IAM policies as applied to the pre-created user groups
Add users to user groups with specific capabilities active
Locate and use the IAM sign-in URL
Experiment with the effects of policies on service access

## Architectural diagram 

<img width="2200" height="1100" alt="image" src="https://github.com/user-attachments/assets/89d8ee37-f083-4d99-8274-ea8beac6e3fe" />



### Create an account password policy

I created a custom password policy for my AWS account. 
This policy affects all the users associated with the account.

In this task, I strengthened the password requirements by creating a custom password policy. 
The various password options that I selected have now made the passwords that the users create much more difficult to crack.

<img width="637" height="407" alt="image" src="https://github.com/user-attachments/assets/edb141d1-a16f-48b6-987a-cfc7b6d325b8" />

