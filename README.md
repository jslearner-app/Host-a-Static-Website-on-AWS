**Project: Hosting a Static Website on AWS**

This project focuses on deploying a static HTML web application on Amazon Web Services (AWS) infrastructure. Below is a comprehensive guide on the setup and deployment process, along with the resources and configurations utilized.

### Overview

The project aims to host a static HTML web application on AWS infrastructure, ensuring reliability, scalability, and security. Key components utilized include Amazon EC2 instances, Virtual Private Cloud (VPC), Internet Gateway, Security Groups, NAT Gateway, Application Load Balancer, Auto Scaling Group, GitHub for version control, Certificate Manager for secure communications, Simple Notification Service (SNS) for alerts, and Route 53 for DNS management.

### Deployment Steps

1. **Set Up Virtual Private Cloud (VPC):**
   - Configured a VPC with public and private subnets across two availability zones for enhanced fault tolerance.
   - Deployed an Internet Gateway to facilitate connectivity between VPC instances and the wider Internet.

2. **Configure Security Groups:**
   - Established Security Groups as a network firewall mechanism to control inbound and outbound traffic to EC2 instances.

3. **Deploy EC2 Instances:**
   - Positioned web servers (EC2 instances) within private subnets for enhanced security.
   - Utilized EC2 Instance Connect Endpoint for secure connections to assets within both public and private subnets.
   - Hosted the website on EC2 instances.

4. **Implement Load Balancing and Auto Scaling:**
   - Employed an Application Load Balancer and a target group for evenly distributing web traffic to an Auto Scaling Group of EC2 instances across multiple Availability Zones.
   - Utilized an Auto Scaling Group to automatically manage EC2 instances, ensuring website availability, scalability, fault tolerance, and elasticity.

5. **Version Control and Collaboration:**
   - Stored web files on GitHub for version control and collaboration.

6. **Security and Monitoring:**
   - Secured application communications using Certificate Manager.
   - Configured Simple Notification Service (SNS) to alert about activities within the Auto Scaling Group.

7. **Domain Name and DNS Setup:**
   - Registered the domain name and set up a DNS record using Route 53.

### Deployment Script

Below is a deployment script used to set up the environment and deploy the static website on an EC2 instance:

```bash
#!/bin/bash
# Switch to the root user to gain full administrative privileges
sudo su
# Update all installed packages to their latest versions
yum update -y
# Install Apache HTTP Server
yum install -y httpd
# Change the current working directory to the Apache web root
cd /var/www/html
# Install Git
yum install git -y
# Clone the project GitHub repository to the current directory
git clone https://github.com/aosnotes77/host-a-static-website-on-aws.git
# Copy all files, including hidden ones, from the cloned repository to the Apache web root
cp -R host-a-static-website-on-aws/. /var/www/html/
# Remove the cloned repository directory to clean up unnecessary files
rm -rf host-a-static-website-on-aws
# Enable the Apache HTTP Server to start automatically at system boot
systemctl enable httpd
# Start the Apache HTTP Server to serve web content
systemctl start httpd
```

### Conclusion

This project demonstrates the setup and deployment of a static website on AWS, utilizing various services and configurations to ensure reliability, scalability, security, and efficient management of web resources. By following the provided instructions and utilizing the deployment script, users can replicate the environment and host their static websites on AWS with ease.
