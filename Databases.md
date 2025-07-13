# Databases

During my AWS re/Start journey, I gained practical knowledge of cloud-based database concepts, focusing on both relational and non-relational models. 
Using the AWS Management Console, I worked with Amazon RDS to launch and manage relational databases like MySQL and PostgreSQL, 
learning about automated backups, multi-AZ deployments, and read replicas for high availability and performance. 
I also explored Amazon DynamoDB to understand NoSQL principles, including partition keys, sort keys, and throughput settings. 
This hands-on experience taught me how to provision, secure, and monitor databases in the cloud, emphasizing scalability, reliability, and data integrity.


## HANDS-ON PROJECT: RDS Instance with MySQL/Aurora


Provision a relational database instance (RDS) in the cloud using:

Amazon Aurora (Provisioned) or MySQL as the database engine

Dev/Test or Free Tier templates

Burstable instance types like db.t3.micro or db.t3.small

Select optimal configurations based on performance and cost:

Avoided standby (Multi-AZ) setups for simplicity

Used gp2 (General Purpose SSD) storage, capped to 100 GB

Chose on-demand pricing model

Securely configure networking and access:

Used a pre-configured Lab VPC

Assigned appropriate security groups to allow LinuxServer connection

Enabled public access and recorded the DB endpoint

Worked with SSH keys and Linux connectivity:

Downloaded PEM or PPK for secure login

Connected to an EC2-based LinuxServer using SSH

Installed and used MySQL client to interact with RDS

Created and manipulated SQL data:

Designed relational tables (RESTART, CLOUD_PRACTITIONER)

Inserted sample records

Queried and joined tables using INNER JOIN

Practiced schema design, foreign keys, and data consistency principles



### SQL Commands Used in my Work

 #### Creating Tables:

 
CREATE TABLE RESTART (
  student_id INT,
  student_name VARCHAR(100),
  restart_city VARCHAR(100),
  graduation_date DATETIME
);


#### Inserting Data:

INSERT INTO RESTART VALUES (1, 'Alice', 'Cape Town', '2025-06-01 10:00:00');



#### Selecting and Joining:

SELECT 
  RESTART.student_id,
  RESTART.student_name,
  CLOUD_PRACTITIONER.certification_date
FROM RESTART
INNER JOIN CLOUD_PRACTITIONER
ON RESTART.student_id = CLOUD_PRACTITIONER.student_id;




## Security in AWS Databases
My work included:

Key pair management (PEM/PPK) for secure SSH

Security group rules to control inbound traffic

IAM (implicitly) for permission and access control

Using VPC to isolate your DB and connect it securely


## Monitoring & Maintenance

Enhanced monitoring with OS-level metrics

Performance Insights

Automated backups and point-in-time recovery

Storage auto-scaling and read replica support


## Summary of What I’ve Practiced

| Skill                    | Description                                                                                    |
| ------------------------ | ---------------------------------------------------------------------------------------------- |
| **Provisioning**         | Launched and configured an RDS instance manually                                               |
| **LinuxOps**             | SSH into EC2 instance, install packages, run CLI                                               |
| **Database Ops**         | Created schemas, inserted data, queried with SQL                                               |
| **Security**             | Used SSH keys, security groups, and VPC config                                                 |
| **Data modeling**        | Designed relational tables with a 1-to-many relationship                                       |
| **Cloud best practices** | Used on-demand pricing, avoided standby for cost, and used low-cost storage and instance types |


