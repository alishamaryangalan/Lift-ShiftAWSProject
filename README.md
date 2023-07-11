# Lift-ShiftAWSProject

1. Multi-tier web application stack
2. Host & run on AWS cloud for production
3. Lift & shift strategy

Scenario:
1. Application services running on Physical/VMs.
2. Work load on datacenter

Cloud computing setup, workload is run on cloud platform --> IAAS, flexibility, elasticity, flexibility, scalability, automation

AWS services:
1. EC2 services - VM for tomcat, rabbitMQ, memcache, MySQL
2. Elastic load balancer - Nginx lb replacement
3. Autoscaling - Automation for VM scaling
4. S3, EFS Storage - Shared Storage
5. Route53 - private DNS Service
Additional services, IAM, EBS, ACM

Architecture:
1. URl --> endpoint - GoDaddy DNS
2. User browsers or app will use this endpoint, to connect to load balancer by using https, certificate for https encryption will be mentioned in ACM.
3. App load balancer will route request to Tomcat instances.
4. Tomcat service will be running on a set up EC2 instance which will be managed by autoscaling loads will be scaled in/out.
5. EC2 instances where Tomcat is running, will be in a separate security group and will allow traffic on port 8080 only on load balancer.
6. Backend servers - memcache, mysql, rabbitmq - their IP address will be mentioned in Route53 private DNS zone. 