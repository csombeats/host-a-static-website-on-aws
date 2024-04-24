**Project: Hosting a Static Website on AWS**

### Overview
This project demonstrates the deployment of a static HTML web application on AWS infrastructure. The setup utilizes various AWS services and configurations to ensure reliability, security, and scalability.

### Project Resources
- **GitHub Repository:** [Link to GitHub Repository](https://github.com/aosnotes77/host-a-static-website-on-aws)
- **Reference Diagram:** [Reference Diagram](link_to_diagram)

### Deployment Steps
1. **Configured Virtual Private Cloud (VPC):**
   - Created both public and private subnets across two different availability zones to ensure high availability and fault tolerance.

2. **Deployed Internet Gateway (IGW):**
   - Facilitated connectivity between VPC instances and the wider Internet.

3. **Established Security Groups:**
   - Implemented as a network firewall mechanism to control traffic to EC2 instances.

4. **Utilized Multiple Availability Zones:**
   - Leveraged two availability zones to enhance system reliability and fault tolerance.

5. **Utilized Public Subnets:**
   - Infrastructure components like the NAT Gateway and Application Load Balancer were placed in public subnets.

6. **Implemented EC2 Instance Connect Endpoint:**
   - Enabled secure connections to assets within both public and private subnets.

7. **Positioned Web Servers in Private Subnets:**
   - Enhanced security by placing web servers (EC2 instances) within private subnets.

8. **Enabled Internet Access via NAT Gateway:**
   - Instances in private application and data subnets could access the Internet via the NAT Gateway.

9. **Hosted Website on EC2 Instances:**
   - Deployed the static website on EC2 instances.

10. **Employed Application Load Balancer (ALB) and Auto Scaling Group (ASG):**
    - Utilized an ALB and a target group to evenly distribute web traffic to an ASG of EC2 instances across multiple Availability Zones.

11. **Utilized Auto Scaling Group (ASG):**
    - Automatically managed EC2 instances to ensure website availability, scalability, fault tolerance, and elasticity.

12. **Version Control with GitHub:**
    - Web files were stored on GitHub for version control and collaboration.

13. **Secured Application Communications with Certificate Manager:**
    - Implemented secure application communications using AWS Certificate Manager.

14. **Configured Simple Notification Service (SNS):**
    - Configured to alert about activities within the Auto Scaling Group.

15. **Domain Registration and DNS Setup with Route 53:**
    - Registered the domain name and set up a DNS record using Amazon Route 53.

### Deployment Script
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
This project successfully demonstrates the deployment of a static website on AWS infrastructure, leveraging various AWS services and best practices for reliability, security, and scalability. The provided deployment script automates the setup process for convenience.
