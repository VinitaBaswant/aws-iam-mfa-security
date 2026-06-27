# Securing AWS with IAM Best Practices and Multi-Factor Authentication

A cloud security project implementing AWS Identity and Access Management best practices and Multi-Factor Authentication to protect critical cloud resources from unauthorized access.

## Project Overview

This project demonstrates how to secure an AWS environment by implementing IAM best practices and enabling Multi-Factor Authentication. It covers creating custom IAM users, groups, and roles with least-privilege policies, enabling MFA using virtual authenticator apps, configuring password policies, and verifying role-based access control to protect cloud resources from unauthorized access and misconfigurations.

Project link: https://www.linkedin.com/posts/vinita-baswant_aws-awssecurity-iam-activity-7315214333330833408-kdDD?utm_source=share&utm_medium=member_desktop&rcm=ACoAABpjHZ8B7Eh242YS93_LEpx-FHEw0zNv9ns

## Problem Statement

Cloud misconfigurations and weak access controls are among the leading causes of security breaches in AWS. This project addresses that by implementing a structured IAM security framework that enforces least privilege access, requires MFA for all users, and establishes governance policies to prevent unauthorized access to cloud resources.

## Key Features

Custom IAM Users and Groups - Organized access management for multiple users
Least Privilege Policies - JSON-based policies granting only required permissions
Multi-Factor Authentication - Virtual MFA via Google Authenticator for enhanced security
Password Policies - Enforce strong passwords and regular rotation
Role-Based Access Control - IAM roles for services and cross-account access
Security Compliance - Governance and audit-ready access configurations

## Technologies Used

AWS IAM - Identity and Access Management for users, groups, roles, and policies
AWS MFA - Multi-Factor Authentication using virtual devices
Google Authenticator - Virtual MFA device for one-time passwords
AWS CloudTrail - Audit logging for all IAM actions
AWS Organizations - Multi-account security governance (optional)

## Architecture Diagram

AWS Account
     |
     |
IAM Identity Center
     |
     |-- IAM Users
     |        |-- Developer Group (read-only S3, EC2)
     |        |-- Admin Group (full access with MFA required)
     |        |-- Billing Group (cost explorer access only)
     |
     |-- IAM Roles
     |        |-- EC2 Role (S3 read access)
     |        |-- Lambda Role (DynamoDB access)
     |
     |-- MFA Enforcement
              |
              |-- Virtual MFA via Google Authenticator
              |-- MFA required for console access
              |-- MFA required for sensitive API calls

## How It Works

1. Create IAM users for each team member instead of sharing root credentials
2. Organize users into groups based on job function and required access
3. Attach least privilege JSON policies to groups granting only necessary permissions
4. Enable MFA for all IAM users especially those with admin access
5. Users scan QR code with Google Authenticator to set up virtual MFA device
6. Configure IAM password policy requiring minimum length and complexity
7. Create IAM roles for AWS services to access other services securely

## Results and Impact

Eliminated root account usage for day-to-day operations
Enforced MFA across all IAM users reducing unauthorized access risk
Implemented least privilege policies minimizing blast radius of any breach
Established password governance policies for compliance requirements
Created audit-ready IAM configuration with CloudTrail logging enabled

## Setup and Deployment

Prerequisites
AWS Account with root access for initial setup
Google Authenticator app installed on mobile device
Understanding of JSON for policy documents

Steps
1. Log in as root and create an admin IAM user immediately
2. Enable MFA on the root account using Google Authenticator
3. Create IAM groups for different access levels
4. Write and attach JSON policies with least privilege permissions
5. Create individual IAM users and assign to appropriate groups
6. Enable MFA for each IAM user
7. Configure IAM password policy under Account Settings
8. Test access by logging in as each user and verifying permissions

## Sample IAM Policy (Least Privilege S3 Read)

The policy grants read-only access to a specific S3 bucket, allowing GetObject and ListBucket actions while denying all other operations. This follows the principle of least privilege by granting only the minimum permissions required.

## Project Structure

aws-iam-mfa-security
policies
  developer-policy.json
  admin-policy.json
  readonly-policy.json
docs
  iam-setup-guide.md
  mfa-configuration.md
  password-policy.md
screenshots
  iam-users.png
  mfa-setup.png
  policy-configuration.png
README.md

## Author

Vinita Baswant
LinkedIn: https://www.linkedin.com/in/vinita-baswant
GitHub: https://github.com/VinitaBaswant
