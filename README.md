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
- 
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

## =======================================

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

## =======================================

# Project 4: Hybrid Cloud Connectivity with Transit Gateway and Site-to-Site VPN

## 1. Solution Architecture Diagram

![AWS Architecture Diagram](/images/Project04.png)

## 2. Project Description

Design a hybrid cloud network that connects an on-premises data center to multiple AWS VPCs for Development, Staging, and Production environments. AWS Transit Gateway acts as the central network hub, while AWS Site-to-Site VPN provides secure connectivity between the data center and AWS. Route 53 Resolver enables private DNS resolution between on-premises hosts and AWS resources. AWS Network Firewall inspects network traffic, AWS RAM enables Transit Gateway sharing across accounts, and CloudTrail and AWS Config help audit and track network configuration changes.

## 3. AWS Services and Their Roles

- **Amazon VPC:** Creates isolated networks for Dev, Staging, and Production environments with non-overlapping CIDR ranges.
- **AWS Transit Gateway:** Acts as the central hub connecting multiple VPCs and the on-premises network through attachments and routing tables.
- **AWS Site-to-Site VPN:** Establishes an encrypted connection between AWS and the on-premises data center using IPsec tunnels, with optional dynamic routing through BGP.
- **AWS Direct Connect:** Provides a dedicated network connection between the on-premises data center and AWS as an alternative to VPN, depending on bandwidth, cost, and connectivity requirements.
- **Amazon Route 53 Resolver:** Enables DNS queries between on-premises networks and AWS using inbound and outbound endpoints.
- **AWS Resource Access Manager (RAM):** Shares the Transit Gateway with other AWS accounts.
- **AWS Network Firewall:** Inspects and filters network traffic to help protect VPCs and control traffic between networks.
- **AWS CloudTrail:** Records AWS API activity to help audit changes to network resources.
- **AWS Config:** Tracks resource configurations and evaluates them against configuration rules.

## 4. Key Features

- Hybrid connectivity between an on-premises data center and AWS.
- Centralized multi-VPC networking using Transit Gateway.
- Secure Site-to-Site VPN connectivity with BGP routing.
- Private DNS resolution across on-premises and AWS networks.
- Transit Gateway sharing across multiple AWS accounts.
- Centralized network traffic inspection using AWS Network Firewall.
- Network configuration auditing and tracking with CloudTrail and AWS Config.
- Comparison of Site-to-Site VPN and Direct Connect.

## =======================================

# Project 5: Multi-Region Disaster Recovery with Route 53 Failover

## 1. Solution Architecture Diagram

![AWS Architecture Diagram](/images/Project05.png)

## 2. Project Description

Build a multi-region disaster recovery architecture for a web application running primarily in **us-east-1**, with warm standby resources in **eu-west-1**.Amazon Aurora Global Database replicates database changes across regions, while Amazon S3 Cross-Region Replication.Tables help maintain data availability across regions. EC2 Auto Scaling Groups maintain minimal standby capacity and scale up during failover. AWS CloudFormation StackSets deploy consistent infrastructure, AWS Backup protects resources, and CloudWatch with EventBridge supports monitoring and failover automation.

## 3. AWS Services and Their Roles

- **Amazon Aurora Global Database:** Replicates database data from the primary cluster to a secondary-region cluster for disaster recovery.
- **Amazon EC2 + Auto Scaling Groups (ASG):** Run the application in both regions, maintaining minimal standby capacity and scaling up when needed.
- **AWS CloudFormation StackSets:** Deploy and manage consistent infrastructure across multiple AWS accounts and regions.
- **AWS Backup:** Centralizes backup plans and protects supported resources, including RDS databases and EC2 instances.
- **Amazon CloudWatch:** Monitors application and infrastructure metrics and generates alarms when problems occur.
- **Amazon EventBridge:** Routes events to trigger automated recovery workflows, such as invoking Lambda functions during failover.

## 4. Key Features

- Multi-region disaster recovery across `us-east-1` and `eu-west-1`.
- Warm Standby architecture with reduced capacity in the secondary region.
- Automatic DNS failover using Route 53 health checks.
- Cross-region database replication using Aurora Global Database.
- Automatic scaling of standby resources during recovery.
- Consistent multi-region deployments using CloudFormation StackSets.
- Centralized backups with AWS Backup.
- Monitoring and recovery automation using CloudWatch and EventBridge.
- Comparison of Backup & Restore, Pilot Light, Warm Standby, and Multi-Site Active-Active strategies.

## =======================================

# Project 6: Containerized Microservices with ECS Fargate and Service Discovery

## 1. Solution Architecture Diagram

![AWS Architecture Diagram](/images/Project06.png)

## 2. Project Description

Build a containerized Node.js application by splitting a monolithic application into three independent microservices: **Auth, Orders, and Notifications**. Amazon ECS Fargate runs the containers without requiring server management, while Amazon ECR stores their Docker images. An Application Load Balancer routes external requests to the appropriate microservice. AWS Secrets Manager securely provides credentials and API keys at runtime, while ElastiCache for Redis stores shared session data across container instances. AWS CodePipeline and CodeDeploy automate blue/green deployments with rollback support.

## 3. AWS Services and Their Roles

- **Amazon ECS Fargate:** Runs the microservices as containers without managing the underlying servers.
- **Amazon ECR:** Stores private Docker images and scans images for vulnerabilities.
- **Application Load Balancer (ALB) + Target Groups:** Routes incoming requests to the appropriate ECS service using path-based routing.
- **AWS Secrets Manager:** Securely stores database credentials and API keys and provides them to containers at runtime.
- **Amazon ElastiCache (Redis):** Stores shared session data accessible by multiple stateless container instances.
- **AWS CodePipeline:** Automates the CI/CD pipeline stages for application delivery.
- **AWS CodeDeploy:** Manages blue/green deployments for ECS services and supports automatic rollback.

## 4. Key Features

- Containerized Node.js microservices: Auth, Orders, and Notifications.
- Docker image management using Amazon ECR.
- Serverless container management with ECS Fargate.
- Path-based traffic routing through an Application Load Balancer.
- Secure runtime secrets management.
- Shared session caching with Redis.
- Automated blue/green deployments with rollback support.

## =======================================

# Project 7: Serverless Data Lake and Analytics Pipeline

## 1. Solution Architecture Diagram

![AWS Architecture Diagram](/images/Project07.png)

## 2. Project Description

Build a serverless data lake for retail transaction analytics using Amazon S3. Kinesis Data Firehose delivers incoming transaction data to the raw zone in S3. AWS Glue Crawlers discover the data schema, while Glue ETL jobs transform raw JSON data into partitioned Parquet files stored in the curated zone. Processed data can then be aggregated into the aggregated zone for reporting. Amazon Athena runs SQL queries on the data, and Amazon QuickSight visualizes business KPIs in interactive dashboards using SPICE caching. AWS Lake Formation manages fine-grained data access, EventBridge Scheduler triggers scheduled ETL jobs, and IAM with AWS KMS manages permissions and encryption.

## 3. AWS Services and Their Roles

- **Amazon S3:** Stores the data lake in three zones: Raw, Curated, and Aggregated. Supports lifecycle policies and Intelligent-Tiering storage.
- **Amazon Kinesis Data Firehose:** Ingests transactional data and delivers it to S3 with configurable buffering and compression.
- **AWS Glue:** Uses Crawlers to discover schemas, the Data Catalog to store metadata, and ETL jobs to transform JSON data into partitioned Parquet format.
- **Amazon Athena:** Runs serverless SQL queries directly against data stored in S3, with partitioning to reduce scanned data and query costs.
- **AWS Lake Formation:** Manages fine-grained data permissions, including supported table-, column-, and row-level access controls.
- **Amazon QuickSight:** Creates dashboards and visualizes KPIs, using SPICE for in-memory data caching and supported row-level security.
- **Amazon EventBridge Scheduler:** Runs Glue ETL jobs on a defined schedule.
- **AWS IAM:** Controls access to AWS resources through users, roles, and policies.
- **AWS Key Management Service (KMS):** Manages encryption keys used to protect data at rest.

## 4. Key Features

- Serverless data lake with Raw, Curated, and Aggregated zones.
- Transaction data ingestion using Kinesis Data Firehose.
- Schema discovery and metadata management using AWS Glue.
- JSON-to-Parquet transformation with partitioned data storage.
- Cost-efficient SQL analytics using Amazon Athena.
- Fine-grained data governance with AWS Lake Formation.
- Interactive KPI dashboards using Amazon QuickSight and SPICE.
- Scheduled ETL processing using EventBridge Scheduler.
- Access control and encryption using IAM and KMS.

## =======================================

# Project 8: Secure Multi-Tier Architecture with GuardDuty, KMS & Security Hub

## 1. Solution Architecture Diagram

![AWS Architecture Diagram](/images/Project08.png)

## 2. Project Description

Design a secure three-tier application consisting of web, application, and data tiers. AWS WAF and AWS Shield Standard help protect the application from web exploits and DDoS attacks, while AWS KMS encrypts data at rest and encryption in transit protects communication. AWS Secrets Manager securely stores database credentials and supports automatic credential rotation. Amazon GuardDuty detects suspicious activity, and AWS Security Hub centralizes security findings and compliance checks. AWS CloudTrail records API activity. IAM and SG on instances level and ACLs on subnet level.

## 3. AWS Services and Their Roles

- **AWS KMS:** Manages customer-managed encryption keys used to protect supported resources and data at rest.
- **AWS Secrets Manager:** Securely stores secrets and supports automatic rotation of Amazon RDS credentials.
- **Amazon GuardDuty:** Detects potential threats, such as reconnaissance, unusual API activity, and cryptocurrency mining.
- **AWS Security Hub:** Aggregates security findings and evaluates security posture against supported standards, such as CIS AWS Foundations Benchmark and PCI DSS.
- **AWS Config:** Tracks resource configurations, evaluates compliance rules, and supports automatic remediation for configured non-compliant resources.
- **AWS CloudTrail:** Records AWS API activity for auditing and investigation, with log file integrity validation available for supported trails.
- **AWS WAF:** Helps protect web applications against common web exploits, including SQL injection and cross-site scripting.
- **AWS Shield Standard:** Provides automatic protection against common network and transport layer DDoS attacks.
- **AWS IAM:** Manages identities, roles, and permissions using the principle of least privilege.
- **Amazon EventBridge:** Routes security-related events to configured targets to initiate response workflows.
- **AWS Lambda:** Executes automated incident response and remediation actions.

## 4. Key Features

- Three-tier application security architecture.
- Encryption at rest using AWS KMS and encryption in transit.
- Centralized secret management and automatic RDS credential rotation.
- Threat detection with Amazon GuardDuty.
- Centralized security findings and compliance checks using Security Hub.
- Resource configuration auditing with AWS Config.
- API activity logging with CloudTrail.
- Web application and DDoS protection using WAF and Shield Standard.
- Automated incident response using EventBridge and Lambda.
- Least-privilege access and organization-level permission guardrails using IAM .
