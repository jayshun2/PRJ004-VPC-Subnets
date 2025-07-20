# PRJ004-VPC-Subnets
Create a secure and scalable AWS network using a Virtual Private Cloud (VPC) with public and private subnets. This project demonstrates how to separate internet-facing resources from internal infrastructure using best practices like NAT gateways, route tables, and subnet isolation. Part of the "52 AWS Projects in 52 Weeks" series.

VPC with Public/Private Subnets
Overview
This project demonstrates how to create a secure and scalable network on AWS using a Virtual Private Cloud (VPC) with both public and private subnets. It’s a foundational setup that mimics real-world cloud infrastructure — separating internet-facing components (like web servers) from internal resources (like databases). This design improves security and control over your cloud environment.
Architecture
The core AWS services used in this project include:
Amazon VPC – Creates a private, isolated network in the AWS cloud.


Subnets – Public subnets are configured to allow internet access; private subnets are isolated from direct public traffic.


Internet Gateway (IGW) – Enables outbound internet access for public subnet resources.


NAT Gateway – Allows instances in the private subnet to initiate outbound connections to the internet, without allowing inbound connections.


Route Tables – Direct traffic appropriately based on subnet and gateway configuration.


EC2 Instances – Launched in both public and private subnets to test connectivity and routing.


These components work together to create a secure environment where public-facing services are accessible externally, while sensitive systems remain protected and internal.
Getting Started
Prerequisites:
AWS account (Free Tier eligible)


IAM user with admin privileges


Basic terminal or console navigation knowledge


Steps:
Log in to the AWS Management Console.


Navigate to the VPC Dashboard and create a new VPC with CIDR block 10.0.0.0/16.


Create two subnets:


10.0.1.0/24 for the public subnet


10.0.2.0/24 for the private subnet


Create and attach an Internet Gateway to the VPC.


Set up a Route Table for the public subnet and add a route to the Internet Gateway.


Allocate an Elastic IP and create a NAT Gateway in the public subnet.


Create another Route Table for the private subnet and add a route through the NAT Gateway.


Launch one EC2 instance in the public subnet (with a public IP) and one in the private subnet (no public IP).


Configure Security Groups to allow SSH access to the public instance and internal access to the private one.


Usage
Connect to the EC2 instance in the public subnet via SSH.


From there, SSH into the private instance using its private IP (bastion-style access).


Test internet access from the private instance (e.g., ping google.com) to confirm NAT Gateway functionality.


Cleanup
To avoid incurring charges:
Terminate both EC2 instances.


Delete the NAT Gateway.


Release the Elastic IP.


Delete subnets, route tables, Internet Gateway, and finally the VPC.


Optional Enhancements
Deploy a bastion host for managed access to the private subnet.


Add more subnets in multiple Availability Zones for high availability.


Integrate AWS Systems Manager for secure instance access without SSH.


Enable VPC Flow Logs to monitor traffic and diagnose issues.


License
MIT License

