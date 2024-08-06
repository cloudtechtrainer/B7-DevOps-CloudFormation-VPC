# AWS CloudFormation Template for VPC Setup

This repository contains a CloudFormation template to create a VPC setup including subnets, an internet gateway, route tables, security groups, and EC2 instances.

## Prerequisites

- AWS CLI installed and configured with the necessary permissions.
- An existing EC2 KeyPair for SSH access to the instances.

## CloudFormation Template

The template creates:
- A VPC
- Public Subnet
- Internet Gateway
- Route Table
- Security Group
- EC2 Instance

## Parameters

- `VpcCidr`: The CIDR block for the VPC (default: `10.0.0.0/16`).
- `PublicSubnetCidr`: The CIDR block for the public subnet (default: `10.0.1.0/24`).
- `KeyName`: The name of an existing EC2 KeyPair to enable SSH access to the instance.
- `InstanceType`: The type of EC2 instance to launch (default: `t2.micro`).

## Usage

### Step 1: Save the Template

Save the CloudFormation template to a file named `template.yaml`.

### Step 2: Create Stack with below command from the directory where template.yaml is present
aws cloudformation create-stack --stack-name MyVPCStack \
  --template-body file://template.yaml \
  --parameters ParameterKey=InstanceType,ParameterValue=t2.micro

### Stem 3: Verify the resources created from the stack and use below command to delete the stack
aws cloudformation delete-stack --stack-name MyVPCStack

