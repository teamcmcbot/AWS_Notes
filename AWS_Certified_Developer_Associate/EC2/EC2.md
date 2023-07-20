# EC2 Summary

## EC2 Overview
- EC2 is like a virtual machine hosted in AWS, providing flexible capacity, quick provisioning, and - pay-as-you-go pricing.
- Four pricing options: On-Demand, Reserved Instances, Spot Instances, and Dedicated.
- Instance types offer varying compute, memory, and storage capabilities.

## EBS (Elastic Block Store)
- EBS volumes are highly available and scalable storage for EC2 instances.
- EBS volume types: gp2 and gp3 (SSD), io1 and io2 (Provisioned IOPS), st1 (Throughput Optimized HDD), sc1 - (Cold HDD).
- EBS snapshots are point-in-time copies of EBS volumes, used for backups and volume creation.

## Elastic Load Balancer (ELB)
- Application Load Balancers: Intelligent load balancing for HTTP and HTTPS.
- Network Load Balancers: High-performance load balancing for TCP traffic.
- Classic Load Balancer: Legacy option supporting basic HTTP, HTTPS, and TCP load balancing.
- Gateway Load Balancers: Load balancing for third-party virtual appliances.
- X-Forwarded-For HTTP header provides the IPv4 address of the end user.

## Exam Tips
- Select EC2 instance types based on application requirements.
- Use On-Demand for flexibility, Reserved for known fixed requirements, Spot for cost savings with flexible - start/end times, and Dedicated for compliance needs.
- EBS gp2 for boot/general applications, gp3 for the latest generation, io1/io2 for online transaction - processing, io2 Block Express for high-performance applications, st1 for big data workloads, sc1 for less - frequently accessed data.
- EBS snapshots for backup and volume creation, encrypted snapshots yield encrypted volumes.
- Understand the different ELB types and their use cases.
- Troubleshoot 504 Gateway timeout errors by fixing application or database server issues.

## Route 53
- Route 53 is Amazon's DNS service, mapping domain names to AWS resources like EC2 instances and load balancers.
- Hosted zones are containers for DNS records for a domain.
- Aliases route traffic addressed to the zone apex to AWS resources.
- A records route traffic to resources using IPv4 addresses.

## AWS CLI
- Principle of least privilege: Assign users minimum required access.
- Use IAM groups for easier permissions management.
- Secret access keys are shown only once during creation; keep them safe.
- Avoid sharing key pairs; each developer should have their own.
- AWS CLI supports Linux, Windows, and MacOS.

## Roles with EC2
- Use IAM roles to grant EC2 instances access to AWS resources.
- Roles avoid hard-coding credentials on instances.
- IAM policies control roles' permissions.
- Roles can be attached and detached from running EC2 instances.

## RDS (Relational Database Service)
- RDS supports various database types: SQLServer, Oracle, MySQL, PostgreSQL, MariaDB, and Amazon Aurora.
- RDS is suitable for online transaction processing workloads, not online analytics processing.
- Automated backups: Enabled by default, provide point-in-time snapshots and transaction logs.
- Database snapshots: User-initiated, point-in-time snapshots, stored indefinitely.
- Enable encryption at creation time for RDS instances, it encrypts all underlying components using KMS.
- Multi-AZ: Provides an exact copy of the primary database in another availability zone for disaster recovery.
- Read replicas: Read-only copies used for scaling read performance.

## ElastiCache
- ElastiCache is an in-memory cache for read-heavy databases.
- Two options: memcached (simple, no persistence), redis (advanced features, persistence, multi-AZ).

## Parameter Store
- Parameter Store stores confidential information like passwords and connection strings.
- Values can be stored as plain text or encrypted.
- Integrated with various AWS services, like EC2, CloudFormation, Lambda, CodeBuild, CodePipeline, and CodeDeploy.

## Secrets Manager and Parameter Store
- Secrets Manager is for storing and accessing secrets securely, supporting automatic rotation of database passwords and API keys.
- Parameter Store is for broader use cases like configuration variables and license keys, but does not support database password rotation.

## MemoryDB for Redis
- In-memory database with ultra-fast performance, microsecond read, and single-digit millisecond write capability.
- Scalable to over 100 terabytes, suitable for high-performance microservices applications and online gaming.

## RDS Proxy
- Used to scale applications by pooling and sharing database connections, improving application scalability and database efficiency.
- Manages connections between the application and the RDS database, preserving connections during failover for faster failover times.
- Serverless and automatically scales to workload, deployable over multi-AZ for infrastructure failure protection.

## EC2 Image Builder
- Automates the creation and maintenance of AMI and container images.
- Four-step process: Select a base OS image, customize by adding software, test the image, and distribute it to chosen regions.
- AMIs are regional, and copies can be made to different regions with encryption.