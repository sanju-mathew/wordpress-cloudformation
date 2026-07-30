# Serverless-Ready WordPress on AWS

## Overview

This project demonstrates the deployment of a highly available WordPress environment on AWS using AWS CloudFormation.

The aim of the project was to gain practical experience designing and deploying AWS infrastructure using Infrastructure as Code (IaC) rather than manually creating resources through the AWS Management Console.

The CloudFormation template provisions the complete environment required to run WordPress, including networking, compute, storage, database services and load balancing.

Although the project uses Amazon EC2 to host WordPress, it relies heavily on managed AWS services to reduce operational overhead and provide a scalable foundation.

---

## Project Objectives

The objectives of this project were to:

- Learn Infrastructure as Code using AWS CloudFormation
- Deploy a complete WordPress environment from a single template
- Separate the application from the database
- Implement shared persistent storage using Amazon EFS
- Improve availability using an Application Load Balancer and Auto Scaling Group
- Gain practical experience with core AWS networking services

---

## AWS Services Used

The project provisions the following AWS services:

- Amazon VPC
- Public Subnets across two Availability Zones
- Internet Gateway
- Route Tables
- Security Groups
- Application Load Balancer (ALB)
- EC2 Launch Template
- Auto Scaling Group
- Amazon EC2
- Amazon RDS (MySQL)
- Amazon Elastic File System (EFS)
- IAM
- AWS Systems Manager Parameter Store (latest Amazon Linux AMI)

---

## Architecture

The deployment consists of:

Internet

↓

Application Load Balancer

↓

Auto Scaling Group

↓

EC2 Instances running WordPress

↓

Amazon EFS (shared WordPress files)

↓

Amazon RDS MySQL database

All infrastructure is created automatically from a single CloudFormation template.

---

## Design Decisions

### Why CloudFormation?

CloudFormation allows the entire environment to be deployed consistently from version-controlled infrastructure code.

### Why an Application Load Balancer?

The ALB distributes incoming HTTP traffic across EC2 instances and provides a single entry point to the application.

### Why an Auto Scaling Group?

Using an Auto Scaling Group makes it possible to increase or replace EC2 instances without changing the overall architecture.

### Why Amazon EFS?

WordPress stores uploads locally by default. EFS provides shared persistent storage so multiple EC2 instances can access the same files.

### Why Amazon RDS?

Using RDS separates the database from the web servers and provides a managed database service with automated maintenance and backups.

---

## Deployment

Clone the repository:

```bash
git clone https://github.com/sanju-mathew/serverless-ready-wordpress.git
cd serverless-ready-wordpress
```

Deploy the CloudFormation template through the AWS Management Console or AWS CLI.

Provide the required parameters:

- EC2 Key Pair
- Database username
- Database password
- EC2 instance type

CloudFormation will provision the infrastructure automatically.

---

## Validation

After deployment I verified:

- CloudFormation completed successfully
- EC2 instances launched correctly
- Application Load Balancer routed traffic to WordPress
- WordPress connected successfully to Amazon RDS
- Amazon EFS provided persistent shared storage
- WordPress installation completed successfully through the browser

---

## Lessons Learned

This project helped me develop practical experience with:

- Infrastructure as Code
- AWS networking
- CloudFormation
- Auto Scaling
- Load Balancing
- Shared storage using Amazon EFS
- Deploying production-style AWS infrastructure

It also reinforced concepts covered in the AWS Solutions Architect Associate certification by applying them in a practical project.

---

## Future Improvements

Possible enhancements include:

- Move EC2 instances into private subnets
- Place Amazon RDS in private subnets
- Replace SSH access with AWS Systems Manager Session Manager
- Store database credentials in AWS Secrets Manager
- Add HTTPS using AWS Certificate Manager
- Integrate Route 53
- Add Amazon CloudWatch monitoring and alarms
- Implement CI/CD for automated deployments

---

## Repository Contents

```
wordpress_cloudformation.yaml
README.md
```

---

## Further Reading

A detailed walkthrough of this project is available on my blog:

https://homelab.sanjuprojects.uk/serverless%E2%80%91ready-wordpress-on-aws-via-cloudformation/