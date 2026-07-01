# cloudlaunch
cloudlaunch


🚀 CloudLaunch – Highly Available Web Application

📌 Project Overview

This project redesigns a single-server web application into a highly available, scalable, and secure AWS architecture.

The goal is to eliminate downtime and ensure the application remains accessible under varying traffic conditions  

⸻

🏗️ Architecture Summary

The solution uses:

* Amazon EC2 – Web servers
* Auto Scaling Group (ASG) – Ensures scalability
* Application Load Balancer (ALB) – Traffic distribution
* Amazon RDS (MySQL) – Managed database (private)
* Amazon S3 – Object storage
* IAM – Access control
* VPC – Network isolation

⸻

🌐 Architecture Diagram (Logical)

                    Internet
                        │
                ┌───────────────┐
                │ Load Balancer │
                └──────┬────────┘
                       │
         ┌─────────────┴─────────────┐
         │                           │
   ┌──────────────┐           ┌──────────────┐
   │   EC2 (AZ1)  │           │   EC2 (AZ2)  │
   └──────┬───────┘           └──────┬───────┘
          │                           │
          └─────────────┬─────────────┘
                        │
                ┌──────────────┐
                │     RDS      │
                │ (Private DB) │
                └──────────────┘
                ┌──────────────┐
                │      S3      │
                └──────────────┘

⸻

⚙️ Implementation Steps

1️⃣ Linux Server Setup (EC2)

* Launched Ubuntu EC2 instance
* Created:
    * User: developer
    * Group: webadmins
* Configured:
    * /opt/cloudlaunch directory
    * Permissions and ownership
* Installed web server (Nginx/Apache)
* Hosted a custom webpage

⸻

2️⃣ IAM Configuration

* Created:
    * IAM User
    * IAM Group
* Assigned least privilege permissions (S3 upload only)

✅ Principle:
Only required access is granted → reduces security risks

⸻

3️⃣ Amazon S3

* Created S3 bucket
* Uploaded:
    * Profile image
    * PDF
    * Logo
* Enabled versioning

⸻

4️⃣ Networking (VPC)

* Custom VPC created with:
    * 2 Public Subnets
    * 2 Private Subnets
* Configured:
    * Internet Gateway
    * Route Tables

⸻

5️⃣ High Availability Setup

* Created:
    * Launch Template
    * Auto Scaling Group
        * Min: 2
        * Desired: 2
        * Max: 4
* Configured:
    * Application Load Balancer
    * Target Group

✅ Result:
Traffic distributed across multiple EC2 instances

⸻

6️⃣ Database (RDS)

* Created MySQL RDS instance
* Deployed in private subnet
* Disabled public access
* Connected via EC2 using MySQL client

⸻

🔐 Security Considerations

* RDS placed in private subnet (not public)
* Security Groups restrict access (port 3306 only from EC2)
* IAM uses least privilege principle
* Sensitive services not exposed to internet

⸻

📸 Required Screenshots

Include:

* EC2 instances
* Auto Scaling Group
* Load Balancer
* Target Group (healthy)
* IAM User & Group
* S3 bucket
* RDS database

⸻

🌍 Final Deliverable

🔗 ALB DNS Link

Your deployed application must be accessible via:

http://arn:aws:elasticloadbalancing:us-east-1:740163003712:loadbalancer/app/cloudlaunch-alb/58656abeeb23ad69

⸻

✅ Project Status

✔ Fully deployed
✔ Highly available
✔ Secure architecture implemented
✔ All AWS services integrated

⸻
