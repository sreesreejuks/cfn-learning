# Jenkins CloudFormation Template

A CloudFormation template that automates the deployment of a fully configured Jenkins server on Amazon EC2.

## Table of Contents
- [Overview](#overview)
- [Features](#features)
- [Prerequisites](#prerequisites)
- [Parameters](#parameters)
- [Resources Created](#resources-created)
- [Installation](#installation)
- [Security](#security)
- [License](#license)

## Overview
This CloudFormation template provisions a complete Jenkins CI/CD environment on an Amazon EC2 instance with Docker support. The template automates the entire setup process, including security group configuration, IAM roles, and Jenkins installation with essential plugins.

## Features
- Automated Jenkins installation on Amazon Linux 2
- Pre-installed Docker integration
- Git and Java support
- Essential Jenkins plugins pre-configured
- Proper security groups for controlled access
- IAM role with necessary permissions

## Prerequisites
- An AWS account
- An existing EC2 key pair for SSH access
- Basic knowledge of AWS CloudFormation
- Your IP address for security group configuration (optional)

## Parameters
The template accepts the following parameters:

| Parameter | Description | Default |
|-----------|-------------|---------|
| InstanceType | EC2 instance type | t2.micro |
| KeyName | Name of an existing EC2 KeyPair | *Required* |
| LatestAmiId | AMI ID for the EC2 instance | Latest Amazon Linux 2 |
| MyIP | Your IP address in CIDR format | 0.0.0.0/0 |

## Resources Created
This template creates the following AWS resources:

1. **EC2 Instance** - Runs Jenkins with the following installed:
   - Amazon Linux 2
   - Java 17 (Amazon Corretto)
   - Jenkins
   - Docker
   - Git
   - Essential Jenkins plugins

2. **Security Group** - Controls access to the instance:
   - Port 22 (SSH)
   - Port 80 (HTTP)
   - Port 443 (HTTPS)
   - Port 8080 (Jenkins)

3. **IAM Role and Instance Profile** - Provides the instance with:
   - SSM managed instance access
   - S3 read-only access

## Installation
1. Log in to your AWS Management Console
2. Navigate to CloudFormation
3. Create a new stack
4. Upload this template file
5. Fill in the required parameters
6. Launch the stack
7. Once deployment is complete, access Jenkins using the URL provided in the outputs

The initial admin password will be available in the instance's system log or at `/var/lib/jenkins/secrets/initialAdminPassword` on the instance.

## Security
By default, Jenkins and SSH access are restricted to the IP address specified in the `MyIP` parameter. For enhanced security, it's recommended to specify your actual IP address rather than using the default `0.0.0.0/0` which allows access from anywhere.

## License
MIT License

Copyright (c) 2025

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
