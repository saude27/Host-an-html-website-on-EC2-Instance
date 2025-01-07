
# Hosting an HTML Website on EC2

This project demonstrates Hosting an HTML website on Amazon EC2, leveraging a variety of AWS services to ensure high availability, scalability, and fault tolerance.

## Architecture Overview

The deployment utilizes the following AWS services and configurations:

1. **Virtual Private Cloud (VPC):** Configured with public and private subnets across two availability zones.
2. **Internet Gateway:** Ensures connectivity between VPC instances and the Internet.
3. **Security Groups:** Acts as a network firewall mechanism.
4. **Availability Zones:** Resources are distributed across two zones for enhanced reliability and fault tolerance.
5. **Public Subnets:** Hosts infrastructure components like the NAT Gateway and Application Load Balancer.
6. **Private Subnets:** Ensures secure hosting of web servers (EC2 instances).
7. **NAT Gateway:** Enables instances in private subnets to access the Internet.
8. **EC2 Instances:** Deploy the HTML application.
9. **Application Load Balancer (ALB):** Distributes traffic to an Auto Scaling Group.
10. **Auto Scaling Group (ASG):** Manages EC2 instances for scalability and fault tolerance.
11. **AWS Certificate Manager:** Secures application communication with SSL/TLS.
12. **Simple Notification Service (SNS):** Sends notifications for ASG activities.
13. **Route 53:** Manages domain name and DNS records.

## Installation Script

#!/bin/bash
yum update -y
yum install -y httpd
cd /var/www/html
yum install git -y
wget https://github.com/saude27/Host-an-html-website-on-EC2-Instance.git
git clone https://github.com/saude27/Host-an-html-website-on-EC2-Instance.git
cp -r Host-an-html-website-on-EC2-Instance/techmax.zip /var/www/html
unzip techmax.zip
cp -r techmax/* /var/www/html
rm -rf techmax.zip techmax
rm -rf Host-an-html-website-on-EC2-Instance Host-an-html-website-on-EC2-Instance.git
systemctl enable httpd
systemctl start httpd

## Key Features

- **High Availability:** Resources are distributed across multiple availability zones.
- **Scalability:** Auto Scaling Group adjusts the number of EC2 instances based on demand.
- **Security:** Private subnets, security groups, and SSL/TLS ensure robust security.
- **Fault Tolerance:** Automatic failover capabilities with multiple availability zones.

## Additional Resources

- **Scripts:** Deployment and installation scripts are provided in the repository.
- **Architecture Diagram:** Visual representation of the infrastructure setup.

## Contact

For inquiries or issues, please contact:

**Saudat Akande**  
Email: [akandesaudat2711@gmail.com](mailto:akandesaudat2711@gmail.com)
