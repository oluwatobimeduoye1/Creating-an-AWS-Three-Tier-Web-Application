# Creating-an-AWS-Three-Tier-Web-Application
This project sets up a secure and scalable three-tier architecture on AWS using a Virtual Private Cloud (VPC). It includes Amazon RDS for the database tier, EC2 instances for the application and web tiers, and integrates a load balancer with autoscaling for optimized performance, traffic distribution, and high availability.
![Screenshot 2025-07-03 021543](https://github.com/user-attachments/assets/32c76434-59c0-4640-99d2-5938fcd6ee0b)
# OBJECTIVE 
To architect and deploy a production-ready, highly available e-commerce web application on AWS using a secure and scalable three-tier architecture. This project demonstrates proficiency in AWS infrastructure design by integrating:

- Web Tier: EC2 instance running Apache Web Server

- Application Tier: EC2 instance hosting a Node.js backend

- Database Tier: Amazon Aurora (MySQL-compatible) for managed, fault-tolerant storage

The infrastructure is distributed across multiple Availability Zones for high availability, protected with well-defined security groups, and equipped with auto scaling and load balancing to ensure optimal performance under variable traffic.

This project highlights practical DevOps skills in cloud provisioning, network isolation, system hardening, and automated scalability—ideal for roles in cloud engineering, DevOps, and infrastructure automation.  


# Project Overview
The three-tier architecture is a widely adopted model for building scalable and maintainable applications. It divides the application into three distinct layers:

- Presentation Tier: The front-end user interface ( e.g a web server or browser).

- Logic Tier: The application’s core functionality and business logic (e.g Node.js app).

- Data Tier: The backend database system (e.g, Amazon Aurora).
This separation of concerns enhances scalability, security, and ease of maintenance. The diagram below illustrates a typical structure of a simple three-tier application: 
![Screenshot 2025-07-03 020442](https://github.com/user-attachments/assets/786dd489-fb05-49f8-8585-d3b7381ab278)

### Architecture Layers
This project follows a three-tier architecture model, dividing the system into distinct functional layers to improve scalability, maintainability, and security:

🔹 Web Tier :
Acts as the top level of the application.

Handles user interaction through web browsers.

Sends and renders content (HTML, CSS, JavaScript).

Forwards user inputs to the application tier.

Hosted on an EC2 instance running Apache Web Server.


🔹 Application Tier:
Also known as the logic or middleware layer.

Implements business logic and processes user requests.

Interacts with both the web tier and data tier.

Manages sessions, application workflows, and data processing.

Runs on an EC2 instance with a Node.js backend.

🔹 Data Tier :
Consists of a managed relational database using Amazon Aurora (MySQL-compatible).

Stores and retrieves application data.

Ensures data security, integrity, and high availability.

Accessible only by the application tier through secure connections.

## This activity guide cover steps for:
 1. Setting Up Resources
✅ Download project code from GitHub

✅ Create an S3 bucket for asset storage

✅ Create an IAM role for EC2 instances with necessary permissions

🌐 2. Configuring the VPC
✅ Create a custom VPC and public/private subnets

✅ Enable internet connectivity via Internet Gateway

✅ Configure route tables for public and private traffic

✅ Set up Security Groups for web, app, and DB tiers

🗄️ 3. Database Deployment
✅ Create DB subnet groups within private subnets

✅ Deploy Amazon Aurora MySQL cluster

✅ Ensure DB is only accessible from the application tier

⚙️ 4. Application Tier Deployment
✅ Launch EC2 instance in private subnet

✅ Connect to the instance securely

✅ Configure the database connection in environment variables

✅ Deploy and start the Node.js application

✅ Verify communication between app and database

📶 5. Internal Load Balancer & Auto Scaling (App Tier)
✅ Create a custom AMI from the configured app instance

✅ Set up a target group for the app tier

✅ Deploy an internal Application Load Balancer (ALB)

✅ Create a launch template and Auto Scaling Group for dynamic scaling

🌍 6. Web Tier Deployment
Update web tier configuration files
Launch EC2 instance in public subnet
connect and configure Apache to forward requests to the internal load balancer

☁️ 7. External Load Balancer & Auto Scaling (Web Tier)
Create a custom AMI from the configured web instance
Set up a target group for the web tier
Deploy an internet-facing Application Load Balancer
Configure a launch template and Auto Scaling Group for the web tier

## Key Concepts
- S3 Bucket: Amazon S3 buckets provide scalable object-based cloud storage for storing and retrieving data in AWS.

- IAM Role: An IAM role is an AWS identity with specific permissions that can be assumed by trusted entities to access AWS resources securely.

- VPC: Amazon VPC enables you to create a logically isolated virtual network within AWS to launch and manage resources securely.

- Subnets: Subnets partition a VPC into smaller network segments to organize and isolate resources based on function or security.

- Route Tables: Route tables control how traffic is directed between subnets and gateways within a VPC.

- Internet Gateway: An internet gateway allows resources within a VPC to communicate with the public internet.

- NAT Gateway: A NAT gateway enables instances in private subnets to access external services without exposing them to inbound internet traffic.

- Security Groups: Security groups act as virtual firewalls to control inbound and outbound traffic at the instance level.

- Amazon Aurora: Amazon Aurora is a fully managed, MySQL and PostgreSQL-compatible relational database engine with high performance and availability.

- EC2 Instances: Amazon EC2 provides scalable virtual servers on-demand to deploy and manage applications in the AWS Cloud.

- AMI: An AMI is a pre-configured template used to launch EC2 instances with a specific operating system and software setup.

- Target Group: Target groups route incoming traffic from load balancers to registered targets like EC2 instances based on health checks.

- Launch Template: Launch templates store instance launch parameters to streamline and standardize EC2 instance creation.

- Load Balancing: Load balancing distributes network traffic evenly across multiple servers to ensure high availability and reliability.

- Auto Scaling: AWS Auto Scaling automatically adjusts computing resources to maintain application performance while optimizing costs.

