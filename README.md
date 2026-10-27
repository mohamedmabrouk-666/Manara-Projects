# Project 1:Scalable Web Application with ALB and Auto Scaling

## 1. Solution Architecture Diagram

![AWS Architecture Diagram](/images/Project01.png)

## 2. Project Description

Deploy a scalable and highly available web application on AWS using Amazon EC2 instances across two Availability Zones. The architecture uses an Application Load Balancer, Auto Scaling, Amazon CloudFront, and Amazon RDS Multi-AZ to improve availability, scalability, performance, and security.

## 3. AWS Services and Their Roles

- **Amazon VPC:** Provides public and private subnets across two Availability Zones.
- **Amazon EC2:** Runs the web application in private subnets.
- **Auto Scaling Group (ASG):** Automatically adjusts the number of EC2 instances based on demand.
- **Application Load Balancer (ALB):** Distributes incoming requests across healthy EC2 instances.
- **AWS WAF:** Protects the application against common web attacks.
- **Amazon CloudFront:** Caches static assets to improve performance.
- **Amazon RDS Multi-AZ:** Provides a highly available relational database.
- **Amazon CloudWatch:** Monitors infrastructure and triggers alarms.
- **Amazon SNS:** Sends notifications from configured alarms.
- **NAT Gateway:** Enables outbound internet access from private subnets when required.
- **Security Groups and Network ACLs:** Control network traffic and help secure resources.

## 4. Key Features

- High availability across two Availability Zones.
- Automatic scaling based on application demand.
- Load balancing across healthy application instances.
- Secure network.
- Database high availability with RDS Multi-AZ.
- Static content caching with CloudFront.
- Monitoring and notifications using CloudWatch and SNS.
## ========================================
# Project02 "Serverless Image Processing Pipeline with S3, SQS & Lambda"

## 1. Solution Architecture Diagram

![AWS Architecture Diagram](/images/Project02.png)

## 2. Project Description

Build a serverless image processing pipeline on AWS that automatically processes uploaded images. When an image is uploaded to an Amazon S3 source bucket, an event is sent to an Amazon SQS queue. AWS Lambda processes the image by resizing , then stores the processed image in a destination S3 bucket.

Amazon DynamoDB stores image metadata, and Amazon SNS sends notifications about job completion or failure over Email.

## 3. AWS Services and Their Roles

- **Amazon S3:** Stores uploaded source images and processed images, with bucket policies, event notifications, and lifecycle rules.
- **Amazon SQS:** Buffers image-processing requests and decouples uploads from processing.
- **Amazon SQS Dead-Letter Queue (DLQ):** Stores messages that fail processing repeatedly.
- **AWS Lambda:** Processes images by resizing and applying watermarks.
- **AWS Lambda Layers:** Packages image-processing dependencies such as Pillow or Sharp that we upload into lambda function.
- **Amazon API Gateway:** Provides an endpoint for generating pre-signed upload URLs.
- **Amazon DynamoDB:** Stores image metadata, upload timestamps, dimensions, and processing status.
- **Amazon SNS:** Sends notifications when processing jobs succeed or fail.

## 4. Key Features

- Event-driven image processing using S3, SQS, and Lambda.
- Asynchronous processing with message retries and a Dead-Letter Queue.
- Automated image resizing and watermarking.
- Image metadata storage using DynamoDB.
- Secure uploads using pre-signed URLs.
- Processing status notifications using SNS.
- S3 lifecycle rules for storage management.

## ========================================
# Project 3: Serverless REST API with Cognito Auth, DynamoDB & WAF

## 1. Solution Architecture Diagram

![AWS Architecture Diagram](/images/Project03.png)

## 2. Project Description

Build a serverless REST API for a To-Do or customer records application using Amazon API Gateway, AWS Lambda, and Amazon DynamoDB. Secure the API with Amazon Cognito and AWS WAF, improve performance with caching and CloudFront, and monitor request execution using AWS X-Ray.

## 3. AWS Services and Their Roles

- **Amazon API Gateway:** Creates the REST API, handles authorization, usage plans, and response caching.
- **Amazon Cognito:** Manages user sign-up, sign-in, and JWT-based authentication.
- **AWS Lambda:** Executes CRUD operations for application records.
- **Amazon DynamoDB:** Stores application data using tables and Global Secondary Indexes (GSIs).
- **AWS WAF:** Protects the API using rate-based rules and managed security rules.
- **Amazon CloudFront:** Provides edge delivery for the API and static frontend.
- **Amazon S3:** Hosts static frontend files built with React or Vue.
- **AWS X-Ray:** Traces requests across API Gateway, Lambda, and DynamoDB.

## 4. Key Features

- Secure API access using Cognito authentication and JWT tokens.
- CRUD operations for application records.
- DynamoDB table design.
- API protection using AWS WAF.
- API Gateway response caching to reduce backend load.
- CloudFront integration.
- Distributed tracing with AWS X-Ray.

