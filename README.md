# TaskFlow Cloud — AWS Cloud Practitioner Capstone

## 1. Project Overview

TaskFlow Cloud is a simple task management web application developed as a capstone project for learning AWS cloud architecture. Users can add tasks, assign priorities, mark tasks as completed, filter tasks, and delete tasks.

**Live frontend demo:** https://codepen.io/AKILESH-the-animator/pen/ogZExBr

## 2. Problem Statement

Users need a simple interface to organize tasks and track their completion status. This project demonstrates a task management interface and proposes a secure, scalable AWS architecture that could support a production version.

## 3. Current Implementation

The frontend is built using HTML, CSS, and JavaScript.

Features:
- Add and delete tasks
- Assign task priorities
- Mark tasks as completed
- Filter all, pending, and completed tasks
- Display task counts

**Current limitation:** Tasks are stored in browser memory and are not permanently saved. The frontend is a demonstration and is not connected to AWS services.

## 4. Proposed AWS Architecture

The production architecture is designed around the following services:

- **Amazon Route 53:** Domain name routing.
- **Amazon CloudFront:** Content delivery for static frontend assets.
- **Amazon S3:** Stores static website assets.
- **Application Load Balancer:** Distributes requests across application instances.
- **Amazon EC2 Auto Scaling:** Runs application instances across two Availability Zones.
- **Amazon RDS Multi-AZ:** Proposed relational database for persistent task storage and database failover.
- **Amazon VPC:** Separates public and private resources into appropriate subnets.
- **AWS IAM:** Applies least-privilege permissions.
- **AWS KMS:** Supports encryption at rest.
- **TLS/HTTPS:** Protects data in transit.
- **Amazon CloudWatch:** Collects logs and metrics and supports alarms.

These services are proposed design components and have not been deployed as part of this frontend demonstration.

## 5. Security Considerations

- Apply least-privilege access using IAM roles and policies.
- Keep the database in private subnets.
- Require encrypted connections using TLS/HTTPS.
- Encrypt supported data at rest using AWS KMS.
- Use security groups to restrict network access.
- Monitor application health and errors with CloudWatch.

## 6. Availability and Scalability

The proposed architecture distributes application instances across two Availability Zones. EC2 Auto Scaling can replace unhealthy instances, while an Application Load Balancer distributes traffic. RDS Multi-AZ is intended to improve database availability during supported failover scenarios.

These capabilities require deployment and testing before they can be considered verified.

## 7. Cost Management

This project uses a browser-based frontend demonstration and proposed architecture documentation. No AWS infrastructure is required to view the frontend.

Before deploying the proposed architecture, estimate monthly charges using the AWS Pricing Calculator. Account for EC2, the load balancer, RDS Multi-AZ, NAT gateways, storage, data transfer, CloudFront, and monitoring. Actual charges depend on region and usage.

**Budget constraint:** No paid AWS resources have been launched for this demonstration.

## 8. Future Improvements

- Connect the frontend to a backend API.
- Persist tasks in a database.
- Add authentication and user-specific task lists.
- Deploy the frontend to a hosting service.
- Implement and test the proposed AWS architecture.
- Prepare a detailed monthly cost estimate.

## 9. Technologies

HTML, CSS, JavaScript, GitHub, CodePen, and AWS architecture concepts.
