# PhotoShare — AWS Cloud Application

## Overview

PhotoShare is a cloud-hosted photo-sharing application deployed on Amazon Web Services (AWS).

The project demonstrates how application infrastructure, networking, storage, serverless processing, monitoring, and security services can work together to support a cloud application.

The project was designed with a focus on network segmentation, controlled access to application resources, secure storage of images and credentials, event-driven processing, and operational monitoring.

---

## Architecture

PhotoShare uses the following AWS services:

- Amazon VPC
- Application Load Balancer (ALB)
- Amazon EC2
- Amazon S3
- AWS Lambda
- Amazon RDS for MySQL
- Amazon CloudWatch
- IAM
- AWS KMS
- AWS Secrets Manager
- Security Groups

The infrastructure is organized into network, application, storage, serverless processing, security, and monitoring components.

---

## VPC and Network Architecture

PhotoShare was deployed within a custom Amazon VPC containing four subnets distributed across two Availability Zones.

The network was separated into public and private subnet layers according to resource exposure requirements.

### Public Subnets

The public subnet layer supports resources that require Internet-facing connectivity.

The Application Load Balancer is configured as an Internet-facing load balancer and is deployed across two Availability Zones.

The PhotoShare EC2 application is deployed within the public application layer and runs the containerized PhotoShare application.

### Private Subnets

The private subnet layer is used for sensitive application data.

The Amazon RDS MySQL database is deployed within the private network layer with public access disabled.

This prevents the database from being directly accessible from the Internet and limits database connectivity to authorized application resources.

### Network Design

The VPC architecture provides:

- One custom VPC
- Four subnets
- Two Availability Zones
- Public and private network segmentation
- An Internet-facing Application Load Balancer
- Private database infrastructure
- Security Groups controlling network traffic

---

## Application Load Balancer

An Application Load Balancer (ALB) provides the public entry point for PhotoShare.

The load balancer was configured with:

- Load balancer type: Application
- Scheme: Internet-facing
- IP address type: IPv4
- Availability Zones: Two
- DNS-based access

Users access the PhotoShare application through the ALB rather than connecting directly to backend application resources.

The ALB routes incoming application traffic to the PhotoShare application running on Amazon EC2.

---

## EC2 and Docker Application

Amazon EC2 provides the compute layer for the PhotoShare application.

The application was containerized using Docker and deployed on the EC2 instance.

The application flow is:

User → Application Load Balancer → EC2 → PhotoShare Application

The EC2 instance provides the environment in which the Dockerized PhotoShare application runs.

IAM permissions are provided through an EC2 IAM role rather than hardcoded AWS access keys.

---

## Amazon RDS

Amazon RDS for MySQL provides the relational database layer for the application.

The database was configured within the private network layer.

Security controls include:

- RDS deployed in the private subnet layer
- Public access disabled
- Network access controlled through Security Groups
- Database credentials stored in AWS Secrets Manager

The database is not intended to be directly accessible from the public Internet.

---

## Amazon S3

Amazon S3 provides object storage for uploaded photos.

The S3 bucket was configured with:

- Block Public Access enabled
- Application-based access to stored images
- S3 event notifications for uploaded objects

Photos are stored in Amazon S3 rather than directly on the EC2 instance.

The application handles access to the stored objects rather than exposing the S3 bucket publicly.

---

## AWS Lambda

AWS Lambda provides serverless processing for uploaded photos.

An S3 upload event triggers the Lambda function automatically.

The processing flow is:

PhotoShare Application
→ Amazon S3
→ S3 Event
→ AWS Lambda
→ Metadata Processing

The Lambda function processes photo metadata in the background without requiring a continuously running server for the processing task.

Lambda permissions are provided through an IAM role rather than hardcoded AWS credentials.

---

## IAM and Access Control

IAM roles were used to provide AWS permissions to application components.

The project includes IAM roles for:

- EC2
- Lambda

The roles allow AWS resources to access the services they require without embedding long-term AWS access keys in application code.

This approach reduces credential exposure and supports the principle of granting resources only the permissions required for their operations.

---

## AWS Secrets Manager

AWS Secrets Manager is used to securely store sensitive database credentials.

Database credentials are retrieved at runtime rather than being stored directly in application source code.

This prevents sensitive credentials from being committed to the Git repository or embedded directly into the application.

---

## AWS KMS and Encryption

AWS KMS is used to support encryption of sensitive data.

Encryption provides an additional layer of protection so that stored sensitive information is not exposed in plaintext.

KMS-managed encryption is part of the project's security architecture.

---

## Security Groups

Security Groups are used to control network traffic between the different components of the PhotoShare environment.

The security design is intended to restrict access to only the required application and database communication paths.

The database layer is particularly protected by preventing public access and limiting connectivity to authorized application resources.

---

## CloudWatch Monitoring

Amazon CloudWatch is used for monitoring, logging, and operational visibility.

The project includes:

- Lambda execution logs
- Lambda error monitoring
- CloudWatch dashboards
- CloudWatch alarms
- Application and infrastructure monitoring

A CloudWatch alarm was configured to monitor Lambda errors.

Lambda execution was also verified through CloudWatch logs during application testing.

---

## Application Flow

The main application request flow is:

```text
User
  |
  v
Internet
  |
  v
Application Load Balancer
  |
  v
EC2
  |
  v
Dockerized PhotoShare Application
