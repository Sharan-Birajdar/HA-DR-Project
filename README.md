# High Availability & Disaster Management on AWS

https://github.com/Sharan-Birajdar/HA-DR-Project/blob/ba82345a32a87c5cb7e253a3a3a12b3bfdfb25a0/Images/Architecture.png?raw=true

## 📌 Project Overview

This project demonstrates the design and deployment of a **highly available and disaster-resilient architecture on AWS**.
The setup ensures:

* **High Availability (HA):** Applications remain online even during failures.
* **Disaster Recovery (DR):** Critical workloads can failover across AWS regions in case of regional outages.

---

## 🏗️ Architecture

The architecture consists of:

* **Two VPCs in different AWS Regions** (for DR & fault isolation).
* **Auto Scaling Groups (ASG)** in each region for scaling EC2 instances automatically.
* **Two EC2 Instances per region** to ensure redundancy within a region.
* **Elastic Load Balancer (ALB/ELB)** in each region to distribute traffic.
* **Amazon Route 53** configured with DNS failover to route traffic between regions.

📌 **Flow:**

1. Route 53 routes traffic to the nearest healthy region.
2. Load Balancers distribute requests to EC2 instances.
3. Auto Scaling adjusts the number of instances based on demand.
4. If one region goes down, Route 53 automatically redirects traffic to the other region.

---

## ⚙️ AWS Services Used

* **VPC (Virtual Private Cloud)** – Isolated networking environment.
* **EC2 (Elastic Compute Cloud)** – Web/app server instances.
* **Auto Scaling** – Automatic scaling of EC2 instances.
* **Elastic Load Balancer (ELB/ALB)** – Traffic distribution.
* **Route 53** – DNS service for failover and disaster recovery.
* **S3 (optional)** – Data backup and static content hosting.
* **CloudWatch** – Monitoring and alerts.

---

## 🚀 Deployment Steps

1. **Create VPCs** in two different AWS regions.
2. **Launch Auto Scaling Groups** in each VPC with EC2 instances.
3. **Attach Load Balancers** to distribute traffic across instances.
4. **Configure Route 53 Failover Policy**:

   * Primary: Region 1 Load Balancer
   * Secondary: Region 2 Load Balancer
5. **Test Failover:** Stop instances or simulate failure to check Route 53 failover.

---

## 📊 High Availability & Disaster Recovery Benefits

* **Fault Tolerance:** Even if one instance fails, others in the ASG handle traffic.
* **Regional Redundancy:** If an entire AWS region fails, traffic is redirected to another.
* **Scalability:** ASG ensures resources adjust based on demand.
* **Business Continuity:** Ensures uptime and availability during disasters.

---
