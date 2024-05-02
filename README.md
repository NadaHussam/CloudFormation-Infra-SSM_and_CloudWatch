# CloudFormation-Infra-SSM_and_CloudWatch
# OVERVIEW 
This project automates the deployment of an AWS infrastructure using CloudFormation templates and leverages the AWS Systems Manager (SSM) Agent for additional configuration. It also integrates CloudWatch for monitoring and alerting.

# Prerequisites
- An AWS account
- AWS CLI configured
- Basic understanding of AWS CloudFormation, AWS Systems Manager, and AWS CloudWatch

# Components
## VPC
The VPC is configured with public and private subnets across multiple availability zones.
Internet Gateway is attached to allow internet access to instances in public subnets.
## EC2 Instances
EC2 instances are launched within the public subnets.
Instances have IAM roles attached for necessary permissions.
User data scripts are provided to install AWS Systems Manager Agent and Amazon CloudWatch Agent.
## Load Balancer
Application Load Balancer (ALB) is deployed to distribute traffic across EC2 instances.
Listener is configured on port 80 to forward traffic to the target group.
## Auto Scaling
Auto Scaling Group is set up to automatically scale the number of EC2 instances based on traffic load.
Scaling policies can be adjusted as needed for optimal performance.
## IAM Roles
IAM roles are created for EC2 instances with policies granting necessary permissions for Systems Manager and CloudWatch

# Deployment Steps
- Create an IAM Role
- Modify the provided CloudFormation template (YAML file) to meet your specific needs, such as instance type, security group configuration.
- Create or modify the SSM Document (YAML file) to define the installation steps for Nginx.
- Deploy the Stack: Use the AWS CloudFormation console or AWS CLI to deploy the CloudFormation template.
- Verify Installation: Once the stack is deployed, connect to the EC2 instance's public IP address in your web browser to confirm that Nginx is running. You can also check the CloudWatch console to see if CPU utilization metrics are being collected and if CloudWatch alarms are configured.

# Usage
- Access the Application: Use the public IP address to access your application (Nginx) in the web browser.
- Monitoring: Monitor the health and performance of your application using CloudWatch metrics (e.g., CPU utilization, network traffic) and logs collected from the EC2 instances.
