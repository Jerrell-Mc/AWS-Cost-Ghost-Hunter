# AWS GhostHunter – Cost Governance Project

## Overview
AWS GhostHunter is a serverless cost governance solution designed to identify unattached EBS volumes (“ghost resources”) that silently generate unnecessary cloud costs.

This project demonstrates real-world cloud financial operations (FinOps), security-first IAM design, and event-driven automation using native AWS services.

---

## Problem Statement
Unattached EBS volumes are often left behind after EC2 instances are terminated, resulting in ongoing storage charges and reduced cost visibility.

In growing AWS environments, these orphaned resources are easy to miss without automated auditing.

---

## Solution Architecture
GhostHunter uses a serverless architecture to automatically scan for unattached EBS volumes and notify stakeholders on a scheduled basis.

### Key Capabilities
- Automated weekly cost audits
- Read-only IAM permissions (least privilege)
- Event-driven execution with no servers to manage
- Email notifications via Amazon SNS

---

## Architecture Diagram
![GhostHunter Architecture]GhostHunter-Architecture.drawio.png

---

## AWS Services Used
- **AWS Lambda** – Executes the audit logic
- **Amazon EC2** – Source of EBS volume inventory
- **Amazon EventBridge** – Scheduled automation trigger
- **Amazon SNS** – Email notifications
- **AWS IAM** – Secure role-based access control

---

## How It Works
1. EventBridge triggers the Lambda function on a weekly schedule
2. Lambda scans for EBS volumes in an `available` (unattached) state
3. Identified volumes are logged and summarized
4. A cost visibility report is sent via SNS email

---

## Security Considerations
- Lambda runs under a dedicated IAM role
- Permissions are restricted to read-only EC2 access
- No credentials are hardcoded
- Root access is never used

---

## Business Impact
This solution provides continuous visibility into hidden AWS storage costs and helps organizations proactively prevent billing inefficiencies without manual audits.

---

## Future Enhancements
- Cost estimation per volume
- Tag-based ownership tracking
- Multi-region scanning
- Optional approval-based cleanup workflow
- Terraform-based deployment (Infrastructure as Code)

**Jerrell McNeal**
AWS Certified Solutions Architect – Associate
