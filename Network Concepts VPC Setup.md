# Building a VPC and Launch a Web Server

## Objectives
Create a virtual private cloud (VPC)
Create subnets
Configure a security group
Launch an Amazon Elastic Compute Cloud (Amazon EC2) instance into a VPC

I used Amazon Virtual Private Cloud (VPC) to create my own VPC and added additional components to produce a customized network for a Fortune 100 customer. 
I also created security groups for my EC2 instance. I then configure and customize an EC2 instance to run a web server and launch it into the VPC that looks like the following customer diagram:

## Customer Diagram

<img width="1114" height="511" alt="image" src="https://github.com/user-attachments/assets/59938b09-ab77-4d9c-ac14-e10ddc514e28" />

### Create VPC

I use the VPC Wizard to create a VPC, an internet gateway, and two subnets in a single Availablity Zone.
After creating a VPC, I then add subnets, Each subnet resides entirely within one availability zone.


#### Steps:

At the upper-right of these instructions, choose AWS. The AWS Management Console opens in a new tab.

Once you are in the AWS console, type and search for VPC in the search bar at the top. Select VPC from the list.

You are now in the Amazon VPC dashboard. You use the Amazon Virtual Private Cloud (Amazon VPC) service to build your VPC.

Choose Create VPC and configure the following options:

Resources to create: Choose VPC and more

Name tag auto-generation: UnCheck the box Auto-generate

IPv4 CIDR: Enter 10.0.0.0/16

IPv6 CIDR block: Choose No IPv6 CIDR block.

Tenancy: Choose Default.

Number of Availability Zones (AZs) :  1

Number of public subnets:  1

Number of private subnets:  1

Expand Customize subnets CIDR blocks

Public subnet CIDR block in us-west-2a: 10.0.0.0/24
Private subnet CIDR block in us-west-2a: 10.0.1.0/24
NAT gateways: Choose In 1 AZ

VPC endpoints: Choose None

On the Preview pane, name the resources as follows:

VPC: Lab VPC

Subnets (2)

First box, Public subnet one without name tag: Public Subnet 1
Second box, Private subnet one without name tag: Private Subnet 1
Route tables (2)

First box, Public route table without name tag: Public Route Table
Second box, Private route table without name tag: Private Route Table

#### These are the code preview commands

aws ec2 create-vpc --cidr-block "10.0.0.0/16" --instance-tenancy "default" 
aws ec2 modify-vpc-attribute --vpc-id "preview-vpc-1234" --enable-dns-hostnames '{"value":true}' 
aws ec2 describe-vpcs --vpc-ids "preview-vpc-1234" 
aws ec2 create-subnet --vpc-id "preview-vpc-1234" --cidr-block "10.0.0.0/24" --availability-zone "us-west-2a" 
aws ec2 create-subnet --vpc-id "preview-vpc-1234" --cidr-block "10.0.1.0/24" --availability-zone "us-west-2a" 
aws ec2 create-internet-gateway  
aws ec2 attach-internet-gateway --internet-gateway-id "preview-igw-1234" --vpc-id "preview-vpc-1234" 
aws ec2 create-route-table --vpc-id "preview-vpc-1234" 
aws ec2 create-route --route-table-id "preview-rtb-public-0" --destination-cidr-block "0.0.0.0/0" --gateway-id "preview-igw-1234" 
aws ec2 associate-route-table --route-table-id "preview-rtb-public-0" --subnet-id "preview-subnet-public-0" 
aws ec2 allocate-address --domain "vpc" 
aws ec2 create-nat-gateway --subnet-id "preview-subnet-public-0" --allocation-id "preview-eipalloc-0" 
aws ec2 describe-nat-gateways --nat-gateway-ids "preview-nat-0" --filter '{"Name":"state","Values":["available"]}' 
aws ec2 create-route-table --vpc-id "preview-vpc-1234" 
aws ec2 create-route --route-table-id "preview-rtb-private-1" --destination-cidr-block "0.0.0.0/0" --nat-gateway-id "preview-nat-0" 
aws ec2 associate-route-table --route-table-id "preview-rtb-private-1" --subnet-id "preview-subnet-private-1" 
aws ec2 describe-route-tables --route-table-ids  "preview-rtb-private-1" 


#### Preview

<img width="696" height="524" alt="image" src="https://github.com/user-attachments/assets/5b3c05b4-d696-4332-9102-892219e5d664" />

<img width="672" height="502" alt="image" src="https://github.com/user-attachments/assets/b2110c13-ae90-4597-8eb2-ca5bb312f062" />


### Now we create additional subnets 

Public subnet 2

<img width="1260" height="476" alt="image" src="https://github.com/user-attachments/assets/cd54fc15-9ead-4059-afd6-8c48ea087e95" />


### Associate the subnets and add routes

<img width="636" height="416" alt="image" src="https://github.com/user-attachments/assets/d2e79bda-6270-42d0-adc5-8a2a60d8de8b" />

<img width="634" height="460" alt="image" src="https://github.com/user-attachments/assets/548ae694-e14e-43f3-9c12-81e8ca619727" />

Private subnet 2

<img width="1253" height="512" alt="image" src="https://github.com/user-attachments/assets/ad50374d-3380-401b-9661-e238d4682919" />


We now have private and public subnets routed to the vpc 


## Create a VPC security group

<img width="620" height="452" alt="image" src="https://github.com/user-attachments/assets/f8fc6037-98d3-4eb8-a400-83acb2787bed" />

Successfully created a security group for my VPC


### Launch a web server instance

Now I luanch an EC2 instance into the new VPC

<img width="1313" height="543" alt="image" src="https://github.com/user-attachments/assets/e4e9d075-a1f7-4920-9f27-0451f4878f00" />


My User data 

#!/bin/bash
#Install Apache Web Server and PHP
yum install -y httpd mysql php
#Download Lab files
wget https://aws-tc-largeobjects.s3.us-west-2.amazonaws.com/CUR-TF-100-RESTRT-1/267-lab-NF-build-vpc-web-server/s3/lab-app.zip
unzip lab-app.zip -d /var/www/html/
#Turn on web server
chkconfig httpd on
service httpd start

<img width="607" height="124" alt="image" src="https://github.com/user-attachments/assets/224c56e5-0f62-43a6-b744-53e32953355f" />

Success!
<img width="1154" height="413" alt="image" src="https://github.com/user-attachments/assets/cb1fa97b-c85d-4520-b2e7-6de0f6caa696" />
