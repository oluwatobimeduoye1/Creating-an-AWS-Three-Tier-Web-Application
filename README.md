# Creating-an-AWS-Three-Tier-Web-Application
This project sets up a secure and scalable three-tier architecture on AWS using a Virtual Private Cloud (VPC). It includes Amazon RDS for the database tier, EC2 instances for the application and web tiers, and integrates a load balancer with autoscaling for optimized performance, traffic distribution, and high availability.

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
![Screenshot 2025-07-03 021543](https://github.com/user-attachments/assets/32c76434-59c0-4640-99d2-5938fcd6ee0b)


