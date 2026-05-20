# AWS Application Load Balancer Network Integration Lab

## Project Overview

This project demonstrates how to configure AWS Application Load Balancers (ALBs), Target Groups, and Listener Rules to route traffic between two different application versions using path-based routing.

The lab simulates a real-world production scenario where multiple versions of an application are deployed and traffic is redirected dynamically using ALB listener rules.

---

## Architecture

- AWS EC2 Instances
- Application Load Balancers (ALB)
- Target Groups
- Listener Rules
- Path-based Routing
- Public Subnets
- Security Groups
- Multi-AZ Deployment

---

## Project Objectives

- Create and configure Target Groups
- Deploy two Application Load Balancers
- Configure Listener Rules
- Implement Path-based Routing
- Redirect traffic between application versions
- Validate routing behavior using ALB DNS endpoints

---

## AWS Services Used

- Amazon EC2
- Application Load Balancer (ALB)
- Target Groups
- VPC
- Security Groups

---

## Implementation Steps

### 1. Created Target Groups
- Application-V1
- Application-V2

Each target group contained EC2 instances hosting separate application versions.

---

### 2. Configured Application Load Balancers

Created:
- app-load-balancer-v1
- app-load-balancer-v2

Features:
- Internet-facing ALBs
- Multi-AZ configuration
- Public subnet deployment

---

### 3. Configured Listener Rules

Implemented path-based redirects:

| Source URL | Redirect Target |
|------------|----------------|
| /v2 | Version 2 Application |
| /v1 | Version 1 Application |

Used:
- HTTP Listener (Port 80)
- 301 Permanent Redirects

---

## Challenges Faced

### 1. Listener Rules Not Working Immediately
**Issue:** Path redirects did not work instantly after configuration.

**Resolution:**  
Waited for ALB provisioning and listener rule propagation to complete before retesting.

---

### 2. Incorrect Redirect Host Formatting
**Issue:** Redirect failed because the ALB DNS URL contained:
- `http://`
- trailing `/`

**Resolution:**  
Removed protocol and trailing slash from the host value in redirect configuration.

---

### 3. Target Health Check Delays
**Issue:** Instances initially appeared unhealthy.

**Resolution:**  
Verified:
- Security group rules
- Correct target group association
- HTTP accessibility on port 80

---

## Key Learning Outcomes

- Practical experience with AWS ALB configuration
- Understanding of path-based routing
- Multi-version application deployment strategy
- Traffic redirection using listener rules
- Real-world cloud networking concepts

---

## Future Improvements

- Add HTTPS with ACM Certificates
- Implement Auto Scaling Groups
- Integrate CloudWatch Monitoring
- Add Route 53 custom domain routing
- Configure CI/CD deployment pipeline

---

## Author

Akhil Puppala
Cloud & AI Infrastructure Enthusiast
