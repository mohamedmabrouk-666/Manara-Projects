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

