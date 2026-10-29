# AWS VPC Peering Project

## Project Overview
This project demonstrates secure private communication between two Amazon Virtual Private Clouds (VPCs) using AWS VPC Peering. It uses private EC2 instances, route tables, security groups, and a bastion host to validate connectivity.

## Architecture

**VPC A — `10.10.0.0/16`**
- Public subnet: `10.10.1.0/24`
- Private subnet: `10.10.2.0/24`
- Internet Gateway for the public subnet
- Bastion host for administrative SSH access
- Private EC2 instance: App-A (`10.10.2.10`)

**VPC B — `10.20.0.0/16`**
- Private subnet: `10.20.1.0/24`
- Private EC2 instance: App-B (`10.20.1.10`)
- No public IP assigned to App-B

**VPC Peering:** Connects VPC A and VPC B, allowing private communication through configured routes.

## AWS Services Used
- Amazon VPC
- VPC Peering
- Amazon EC2
- Route Tables
- Internet Gateway
- Security Groups
- AWS IAM

## Implementation
1. Created two VPCs with non-overlapping CIDR ranges.
2. Created public and private subnets.
3. Configured route tables and subnet associations.
4. Created and activated a VPC peering connection.
5. Added routes to the remote VPC CIDR in the required route tables.
6. Configured security groups to allow only the required administrative and ICMP traffic.
7. Launched a bastion host and two private EC2 instances.
8. Connected to the private instances through SSH and tested communication in both directions.

## Validation Results
- SSH access from the bastion host to App-A: **Successful**
- SSH access from the bastion host to App-B: **Successful**
- Ping from App-A to App-B: **Successful**
- Ping from App-B to App-A: **Successful**
- Packet loss during the App-A to App-B ping test: **0%**

## Security Considerations
- Private application instances have no public IPv4 addresses.
- Bastion SSH access is restricted to a specific client IP address.
- Security-group rules limit administrative and test traffic.
- Private keys and AWS credentials must never be committed to this repository.

## Learning Outcomes
This project strengthened my practical understanding of AWS networking, subnet design, route tables, VPC Peering, EC2 administration, security groups, SSH, and private network troubleshooting.

## Project Status
Core networking and bidirectional connectivity tests completed successfully.

**Note:** This repository documents the project. The GitHub Pages website will serve as a public project showcase; the AWS network itself remains a private cloud environment.
