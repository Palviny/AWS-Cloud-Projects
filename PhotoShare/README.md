# PhotoShare — AWS Cloud Application

## Overview

PhotoShare is a cloud-hosted photo-sharing application deployed on Amazon Web Services (AWS).

The project demonstrates how application infrastructure, networking, storage, serverless processing, monitoring, and security services can work together to support a cloud application.

## Architecture

The application uses the following AWS services:

- Application Load Balancer (ALB)
- Amazon EC2
- Amazon S3
- AWS Lambda
- Amazon CloudWatch
- Amazon VPC
- IAM

## Current Architecture

User → Application Load Balancer → EC2 → PhotoShare Application

When a photo is uploaded:

PhotoShare Application → Amazon S3 → AWS Lambda → CloudWatch

## What I Built

- Deployed the PhotoShare application on AWS
- Containerized the application using Docker
- Configured an Application Load Balancer
- Configured networking within an AWS VPC
- Configured Amazon S3 for photo storage
- Configured an S3 event to trigger a Lambda function
- Created a Lambda function for photo metadata processing
- Configured CloudWatch monitoring
- Created a CloudWatch alarm for Lambda errors
- Tested the application through the Load Balancer
- Verified uploaded objects in Amazon S3
- Verified Lambda execution through CloudWatch logs

## Validation

The application was tested through the Application Load Balancer.

Validation included:

1. Accessing the PhotoShare application through the ALB DNS name
2. Uploading a photo
3. Verifying the photo appeared in Amazon S3
4. Verifying Lambda processing
5. Reviewing Lambda logs in CloudWatch
6. Monitoring Lambda errors using a CloudWatch alarm

## Lessons Learned

This project provided hands-on experience with:

- AWS networking
- Load balancing
- Dockerized applications
- Object storage
- Event-driven serverless architecture
- IAM permissions
- CloudWatch monitoring
- Troubleshooting AWS services
