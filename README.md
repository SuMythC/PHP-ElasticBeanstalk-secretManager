# PHP Web Application with Elastic Beanstalk and AWS Secrets Manager

This project demonstrates a PHP web application deployed on AWS Elastic Beanstalk, utilizing AWS Secrets Manager for managing database credentials, and automating the CI/CD pipeline with AWS CodePipeline.

![diagram](https://github.com/user-attachments/assets/32559485-ed85-46c7-844e-2ae9118261ac)

## Architecture Overview

### 1. VPC Setup

Created three pairs of subnets:
- **2 Public Subnets**
- **2 Private Subnets for RDS**
- **2 Private Subnets for Web Application**

![Subnet](https://github.com/user-attachments/assets/525bc107-7690-405c-aa7a-e6c2d2a65d5d)

### 2. NAT Gateway

To minimize cost, a single NAT Gateway is deployed in a public subnet.

![NAT Gateway](https://github.com/user-attachments/assets/878109a9-8688-4ede-963e-a88dd99ca597)

### 3. RDS Subnet Group

A subnet group for RDS instances is created to ensure high availability.

![subnet group for rds](https://github.com/user-attachments/assets/d8f1c049-922b-4069-a138-3f83b2fcca7b)

### 4. RDS Instance

The RDS instance is provisioned in the private subnet to ensure that the database is not publicly accessible.

![RDS](https://github.com/user-attachments/assets/83a2f0e3-ce40-4ae0-819e-cf028b1308c2)

### 5. Secrets Manager Integration

AWS Secrets Manager is used to securely store and manage database credentials with automatic key rotation.

![Secrets Manager](https://github.com/user-attachments/assets/4274b75f-4b45-4b5b-bc61-24701983dd78)

![sm2](https://github.com/user-attachments/assets/0c660bf6-d8bf-4eba-97e7-36afb68325a0)

![sm4](https://github.com/user-attachments/assets/63292b8a-d69a-4e2b-894a-fdaa1934e07e)

<strong> Key Rotation Enabled: </strong><br>
![Secrets Manager - Rotation](https://github.com/user-attachments/assets/4d718643-b680-4827-a033-805713dcb3a5)

### 6. Elastic Beanstalk Environment Variables

Environment variables are configured in Elastic Beanstalk to link the application with the necessary secrets.

![Environment Variables](https://github.com/user-attachments/assets/8e209c8f-e05a-44d1-b868-1b8362dfdd6a)

### 7. Successful Elastic Beanstalk Deployment

Elastic Beanstalk successfully provisions an environment to host the PHP application.

![Elastic Beanstalk Successful](https://github.com/user-attachments/assets/56a20f02-d46a-483f-b3df-1a06dbd22dd6)

### 8. EC2 Instances for PHP Application

PHP application is deployed on EC2 instances across two availability zones for high availability.

![EC2 Instances](https://github.com/user-attachments/assets/5df6bd39-f432-4203-8493-7c073d2cec00)

### 9. Application Load Balancer (ALB)

An ALB is created in two availability zones to distribute traffic evenly across EC2 instances.

![ALB](https://github.com/user-attachments/assets/63b06a76-9db2-445b-9adf-a94ad0c9d8e8)
![ALB](https://github.com/user-attachments/assets/902a232f-9c67-4c47-9b0c-60748aaec5ba)

### 10. CI/CD with CodePipeline

AWS CodePipeline is used to automate the deployment process for the PHP application.

![CodePipeline](https://github.com/user-attachments/assets/b8f4be6b-2d63-47dd-93f4-d0c148a9cecb)

![web before update](https://github.com/user-attachments/assets/9e0e42af-c324-4538-bd4c-55411885738d)

## Testing CodePipeline

### 1. Code Update in GitHub

Make code changes in the GitHub repository to trigger the deployment.

![Commit Update](https://github.com/user-attachments/assets/844cd71d-2e65-4501-b5e6-285460acc49c)

### 2. CodePipeline Triggered

The commit in GitHub automatically triggers the pipeline, starting the deployment process.

![Pipeline Started](https://github.com/user-attachments/assets/266c95ad-7ad0-4516-bb3f-ad916c447653)

### 3. PHP Application Deployment

The PHP application is deployed on Elastic Beanstalk automatically.

![Deployment Started](https://github.com/user-attachments/assets/7edfb7e4-1b78-46b2-86d3-6a65d9df4003)

![updated](https://github.com/user-attachments/assets/9e015779-dde3-4606-afce-a36accc18c46)

# [Connection to Database]
![connection to db](https://github.com/user-attachments/assets/06db8e34-e238-40e0-af2e-2ba3eec4f98a)

<strong> Note: All code is given in repository </strong>
