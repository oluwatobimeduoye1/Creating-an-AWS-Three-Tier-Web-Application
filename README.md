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

## Setting Up Resources
- Download project code from GitHub
- Create an S3 bucket for asset storage ![Screenshot 2025-07-03 031442](https://github.com/user-attachments/assets/898534bc-d194-4da8-b97b-543e08d13982)
- Create an IAM role for EC2 instances with necessary permissions ![Screenshot 2025-07-03 030357](https://github.com/user-attachments/assets/c6ca24d7-39c8-4fa0-bdc8-ba483c969b05) ![Screenshot 2025-07-03 030507](https://github.com/user-attachments/assets/b9093d3d-d17b-4edd-9be2-7676885d5da2) ![Screenshot 2025-07-03 030610](https://github.com/user-attachments/assets/738e04db-535f-4087-9e10-cb6b68e75789)
- Configure VPC
1. Create VPC ![Screenshot 2025-07-03 032730](https://github.com/user-attachments/assets/4a661131-372b-43a4-8379-033b8bbc658c)
2.  Create subnet. ![Screenshot 2025-07-03 034239](https://github.com/user-attachments/assets/f9d3dd56-a331-44d8-bc6d-13224b17ee9b) ![Screenshot 2025-07-03 034314](https://github.com/user-attachments/assets/dc7d6eaf-b964-4cfe-9f54-ff85059081a9) ![Screenshot 2025-07-03 034404](https://github.com/user-attachments/assets/cac8fb47-ecad-4d84-a8ff-1f1729bece1c) ![Screenshot 2025-07-03 034622](https://github.com/user-attachments/assets/5d62b907-29b3-45fa-a774-663094a342d5)
- create and attach an Internet Gateway.
![Screenshot 2025-07-03 035221](https://github.com/user-attachments/assets/87ecbcd3-4e27-4d42-8aec-581233dad137) ![Screenshot 2025-07-03 035301](https://github.com/user-attachments/assets/9ba76380-606b-4807-89ee-20304a72b780) ![Screenshot 2025-07-03 040315](https://github.com/user-attachments/assets/7c9e3945-5cdb-432f-bf7d-74a16a88109a) ![Screenshot 2025-07-03 040417](https://github.com/user-attachments/assets/d7388a08-7533-43ba-9bea-3002f4377deb)
- Create NAT Gateway: As we have 2 public subnets, we require 2 NAT Gateways
![Screenshot 2025-07-03 041354](https://github.com/user-attachments/assets/1ad2ebf1-b66b-4c58-b1a9-4d8e548f5070) ![Screenshot 2025-07-03 041743](https://github.com/user-attachments/assets/bcbdd769-c36d-455a-a1d7-f6cb4a03fa35) ![Screenshot 2025-07-03 042059](https://github.com/user-attachments/assets/01672b4b-1f56-4854-81a4-bbf04d532882)
- Routing Configuration :
we will create the route tables one for web tier and the other for app tier. The Public Route table will help us to route the traffic from the VPC to the Internet gateway.
Whereas Private Route Table will route app layer traffic destined for outside the VPC to the NAT gateway in the respective availability zone.
#### Public route table
![Screenshot 2025-07-03 042957](https://github.com/user-attachments/assets/8f92f9ec-b951-4991-8f45-bbb21417848f) ![Screenshot 2025-07-03 043043](https://github.com/user-attachments/assets/6a1e532e-716a-4834-947f-ca7d00881873) 
#### Edit routes.
By adding a Route that directs traffic from the VPC to the internet gateway. In other words, for all traffic destined for IPs outside the VPC CIDR range, add an entry that directs it to the internet gateway as a target  ![Screenshot 2025-07-03 044004](https://github.com/user-attachments/assets/747b9c3b-3ac8-41a1-8ef4-eee6b2718ddf) ![Screenshot 2025-07-03 044417](https://github.com/user-attachments/assets/0d7aa43e-3530-414e-9997-caa2cd3c7f81)

#### Edit the Subnet Associations of the route table
![Screenshot 2025-07-03 044918](https://github.com/user-attachments/assets/16ecb1cd-f3bd-41f2-8592-275a1c6da862) ![Screenshot 2025-07-03 045049](https://github.com/user-attachments/assets/b091b3ed-7e5a-4c1d-9d9b-5466e71b886c) ![Screenshot 2025-07-03 045444](https://github.com/user-attachments/assets/a91669e0-ac4d-4dc4-9451-669ef1c96c96)

#### Private route table
Now create an app layer private subnet. These route tables will route app layer traffic destined for outside the VPC to the NAT gateway in the respective availability zone
![Screenshot 2025-07-04 035202](https://github.com/user-attachments/assets/26dccf6e-d5cd-4d6c-9759-bf19cbf492b3) ![Screenshot 2025-07-04 035251](https://github.com/user-attachments/assets/daab7b36-e2d0-40ad-bea2-086490bb4649)

#### Edit PRIVATE routes.
Click on Add route and enter the destination as 0.0.0.0/0 and select the NAT Gateway as Target and select the NAT-GW-AZ1 and click on save changes.
![Screenshot 2025-07-04 035931](https://github.com/user-attachments/assets/f0494ab8-d1a9-4d61-82be-962f86f1b8ce) ![Screenshot 2025-07-04 040130](https://github.com/user-attachments/assets/0048f5f5-bee3-41e7-98e7-2db9b0c8687d)
#### Edit the Subnet Associations of the Private route table
associate the private app subnet in az1
![Screenshot 2025-07-04 041620](https://github.com/user-attachments/assets/be0adaf7-45ad-4ca1-91b7-357a45204933) ![Screenshot 2025-07-04 041933](https://github.com/user-attachments/assets/372a560c-a344-4cb9-99e0-a512ac4a4902) 
- Create Security Groups
Security groups will tighten the rules around which traffic will be allowed to our Elastic Load Balancers and EC2 instances
##### The first security group to create is for the public, internet facing load balancer. Enter the name as internet-facing-lb-sg and description as External Loadbalancer SG.
![Screenshot 2025-07-04 042922](https://github.com/user-attachments/assets/bbf09836-39a7-43e3-9e85-02f81a8e4562) ![Screenshot 2025-07-04 042922](https://github.com/user-attachments/assets/71413096-8460-4154-8d1c-c4a87cc02044)
##### The second security group you’ll create is for the public instances in the web tier. This allows inbound traffic from internet-facing-lb-sg and My IP address
![Screenshot 2025-07-04 044059](https://github.com/user-attachments/assets/9a5c2ec9-da27-4082-94b5-167636bc64fb) ![Screenshot 2025-07-04 044210](https://github.com/user-attachments/assets/5d9871bf-0d84-42d6-97ac-6298258f0f8c)
##### Next,  create Internal Loadbalancing Security Group that allows http traffic from web-tier sg
![Screenshot 2025-07-04 045001](https://github.com/user-attachments/assets/8d93cbc5-1aed-4f0a-84df-3b01d333608a) ![Screenshot 2025-07-04 045115](https://github.com/user-attachments/assets/7e7c9ae6-3784-4667-a987-21661ed62adf)

##### The fourth security group we’ll configure is for our private instances. 4000 is the port our app tier application is running on and allows our internal load balancer to forward traffic on this port to our private instances. You should also add another route for port 4000 that allows MY IP for testing.
![Screenshot 2025-07-04 050126](https://github.com/user-attachments/assets/390a6236-b734-4370-bfad-ba588cecd2d1) ![Screenshot 2025-07-04 050213](https://github.com/user-attachments/assets/4b15d9bb-2a29-4833-bc79-841db3f54a1c) ![Screenshot 2025-07-04 050426](https://github.com/user-attachments/assets/7808ffb9-c144-4f63-984c-25521e6c2d99)
##### The fifth security group we’ll configure protects our private database instances. For this security group, add an inbound rule that will allow traffic from the private instance security group to the MYSQL/Aurora port (3306).
![Screenshot 2025-07-04 051205](https://github.com/user-attachments/assets/c204d572-a934-4597-ac31-f3e09b8f10d7) ![Screenshot 2025-07-04 051255](https://github.com/user-attachments/assets/e045a4a0-f969-46d3-9dfc-7c4d7e1e21cd)

- Database Deployment
#####  Create DB subnet group
![Screenshot 2025-07-04 053431](https://github.com/user-attachments/assets/c4fc29ee-c6db-4369-b777-4c3c0b27153c) ![Screenshot 2025-07-04 053657](https://github.com/user-attachments/assets/87d5b15d-d5ea-4950-95da-c89e262075b6)

##### Create Aurora MySQL-Compatible



 

