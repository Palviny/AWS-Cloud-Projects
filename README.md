# AWS Cloud Projects

Welcome to my AWS Cloud Projects repository.

This repository documents my hands-on experience building, deploying, securing, monitoring, validating, and troubleshooting cloud infrastructure and applications using Amazon Web Services (AWS).

The goal is to document not only the final result, but also the architecture, implementation process, security decisions, validation, troubleshooting, and lessons learned from each project.

---

# Projects

## 1. PhotoShare — AWS Cloud Application

A containerized photo-sharing web application deployed on AWS.

The project demonstrates how compute, networking, storage, serverless processing, security, and monitoring services can be integrated to support a cloud-based application.

### AWS Services

- Amazon EC2
- Application Load Balancer (ALB)
- Amazon S3
- AWS Lambda
- Amazon RDS for MySQL
- Amazon CloudWatch
- Amazon VPC
- IAM
- AWS KMS
- AWS Secrets Manager
- Security Groups

### Architecture and Security

- Custom Amazon VPC with four subnets
- Public and private network segmentation
- Two Availability Zones
- Internet-facing Application Load Balancer
- Containerized PhotoShare application running on Amazon EC2
- RDS MySQL database deployed within the private network layer
- RDS public access disabled
- Amazon S3 used for image/object storage
- S3 Block Public Access enabled
- AWS Lambda triggered by S3 uploads for image metadata processing
- IAM roles used to provide AWS permissions without hardcoded access keys
- AWS Secrets Manager used to securely store database credentials
- AWS KMS used for encryption
- Security Groups used to control network access
- Amazon CloudWatch used for logging, monitoring, dashboards, and alarms

### Key Areas

- AWS VPC and network segmentation
- Public and private subnet design
- Application Load Balancing
- Containerized application deployment
- EC2 compute
- Relational database deployment
- Object storage
- Event-driven serverless processing
- IAM and least-privilege access
- Secrets management
- Encryption
- Security Groups
- CloudWatch monitoring and alarms
- Application validation
- Troubleshooting

[View PhotoShare Project](./PhotoShare/)

---

# Learning Objectives

Through these projects, I am developing practical experience with:

- AWS infrastructure
- Cloud networking
- VPC design
- Public and private subnet architecture
- Compute services
- Load balancing
- Database services
- Object storage
- Serverless architecture
- Identity and access management
- Secrets management
- Encryption
- Security Groups
- Monitoring and observability
- Application validation
- Troubleshooting
- Cloud architecture and design
- Infrastructure deployment
- DevOps practices

---

# Technologies

- Amazon Web Services (AWS)
- Linux
- Docker
- Git
- GitHub
- Python
- CloudWatch
- Infrastructure as a Service (IaaS)
- Serverless computing
- Containerization

---

# Security Focus

Security is considered throughout the design and implementation of these projects.

Key security practices demonstrated include:

- Separating public-facing and private resources through subnet architecture
- Restricting direct Internet access to sensitive resources
- Disabling public access to the database layer
- Blocking public access to S3 objects
- Using IAM roles instead of hardcoded AWS credentials
- Managing sensitive database credentials through AWS Secrets Manager
- Using encryption through AWS KMS
- Controlling network traffic with Security Groups
- Monitoring application and serverless workloads with CloudWatch

---

# Documentation Approach

Each project is documented with a focus on both implementation and understanding.

Project documentation may include:

- Architecture diagrams
- AWS resource configuration
- Network architecture
- Security design
- Implementation steps
- Application flow
- Validation and testing
- Monitoring and logging
- Troubleshooting
- Lessons learned

The architecture diagrams are designed to show how AWS services interact and how traffic and data move through the environment.

---

# Progress

This repository will continue to grow as I build and document additional AWS projects.

Future projects will expand into areas such as:

- AWS networking
- Serverless applications
- Infrastructure as Code
- Security engineering
- Monitoring and observability
- CI/CD
- DevOps
- Cloud architecture
- Additional AWS compute, storage, and database services
