# Project 2: EC2 No Internet Connectivity – VPC Routing Troubleshooting

## Environment
- AWS EC2 (Amazon Linux, t2.micro)
- Default VPC
- Internet Gateway
- Route Tables

## Problem
EC2 instance was unable to access the internet despite being in a running state.

## Symptoms
- ping and yum update commands failed
- SSH access to the instance was successful
- EC2 status checks passed

## Investigation
- Verified instance health and connectivity
- Reviewed Security Group inbound and outbound rules
- Analyzed subnet route table configuration

## Root Cause
The default route (0.0.0.0/0) to the Internet Gateway was missing in the VPC route table, blocking outbound internet traffic.

## Resolution
Restored the Internet Gateway route in the subnet route table.

## Outcome
Outbound internet connectivity was successfully restored.

## Key Learning
- Route tables control traffic flow at the subnet level
- Internet Gateway is required for outbound internet access
- Security Groups alone cannot provide internet connectivity
