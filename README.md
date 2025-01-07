# Hosting an HTML Website on Amazon EC2

This project demonstrates the deployment of an HTML website on Amazon EC2, utilizing AWS services to deliver high availability, scalability, and fault tolerance.

---

## Architecture Overview

The deployment architecture incorporates the following AWS services and configurations:

### 1. **Virtual Private Cloud (VPC)**
   - Configured with public and private subnets across two availability zones to ensure redundancy.

### 2. **Internet Gateway**
   - Enables connectivity between VPC instances and the Internet.

### 3. **Security Groups**
   - Acts as a network firewall to regulate inbound and outbound traffic.

### 4. **Availability Zones**
   - Resources are distributed across two zones for enhanced reliability and fault tolerance.

### 5. **Public Subnets**
   - Hosts key infrastructure components, such as:
     - **NAT Gateway**
     - **Application Load Balancer (ALB)**

### 6. **Private Subnets**
   - Provides secure hosting for web servers (EC2 instances).

### 7. **NAT Gateway**
   - Allows instances in private subnets to securely access the Internet.

### 8. **EC2 Instances**
   - Serves as the web server hosting the HTML application.

### 9. **Application Load Balancer (ALB)**
   - Efficiently distributes incoming traffic to instances in the Auto Scaling Group.

### 10. **Auto Scaling Group (ASG)**
   - Ensures scalability and fault tolerance by dynamically adjusting the number of EC2 instances based on traffic demand.

### 11. **AWS Certificate Manager (ACM)**
   - Secures communication through SSL/TLS certificates.

### 12. **Amazon Simple Notification Service (SNS)**
   - Sends notifications for Auto Scaling Group activities.

### 13. **Amazon Route 53**
   - Manages domain name and DNS records for seamless traffic routing.

---

## Installation Script

Below is the installation script used to configure the EC2 instances with the required software and deploy the HTML application:

```bash
#!/bin/bash
# Update the system
yum update -y

# Install Apache HTTP server
yum install -y httpd

# Navigate to the web server's root directory
cd /var/www/html

# Install Git
yum install git -y

# Clone the repository and deploy the application
wget https://github.com/saude27/Host-an-html-website-on-EC2-Instance.git
git clone https://github.com/saude27/Host-an-html-website-on-EC2-Instance.git
cp -r Host-an-html-website-on-EC2-Instance/techmax.zip /var/www/html
unzip techmax.zip
cp -r techmax/* /var/www/html

# Clean up unnecessary files
rm -rf techmax.zip techmax
rm -rf Host-an-html-website-on-EC2-Instance Host-an-html-website-on-EC2-Instance.git

# Enable and start the HTTP server
systemctl enable httpd
systemctl start httpd
```

---

## Key Features

- **High Availability:** Resources are deployed across multiple availability zones to ensure minimal downtime.
- **Scalability:** Auto Scaling Group automatically adjusts the number of EC2 instances based on traffic demand.
- **Security:** Combination of private subnets, security groups, and SSL/TLS certificates ensures robust security.
- **Fault Tolerance:** Redundant architecture enables automatic failover in case of resource failure.

---

## Additional Resources

- **Scripts:** All deployment and installation scripts are available in the GitHub repository.
- **Architecture Diagram:** Visual representation of the infrastructure is provided for better understanding.

---

## Contact Information

For questions, support, or issues, please contact:

**Saudat Akande**  
**Email:** [akandesaudat2711@gmail.com]
