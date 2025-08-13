# IAM & Access Control Demo

## Overview
This project demonstrates how to configure AWS IAM roles, groups, and policies to implement secure access control for different user groups.

## Objectives
- Create IAM users, groups, and roles.
- Apply least-privilege access policies.
- Manage user permissions securely.
- Document onboarding and access setup.

## Steps Performed
# IAM Demo Project: User and Group Management with Least Privilege

## Project Overview
This project demonstrates foundational AWS Identity and Access Management (IAM) skills by creating users, groups, and roles with least-privilege policies. It highlights secure permission management, onboarding, and testing of user access.

---

## Objectives
- Create IAM users, groups, and roles.
- Apply least-privilege access policies.
- Manage user permissions securely.
- Document onboarding and access setup.

---

## Steps Performed

### 1. Plan IAM Structure
- Defined roles: `Admin` (full access) and `Support` (limited access).
- Selected appropriate AWS managed policies and created custom policies where needed.

### 2. Create IAM Groups
- Created two IAM groups: `Admin` and `Support`.

### 3. Attach Policies to Groups
- Attached AWS managed policy `AdministratorAccess` to the `Admin` group.
- Created and attached a custom policy with least privileges to the `Support` group.

#### Custom Support Group Policy JSON

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": [
        "ec2:Describe*",
        "s3:ListBucket",
        "s3:GetObject",
        "cloudwatch:GetMetricData"
      ],
      "Resource": "*"
    }
  ]
}
```
4. Create IAM Users
Created users admin1 and admin2 added to the Admin group.
Created users support1 and support2 added to the Support group.
5. Enable Multi-Factor Authentication (MFA)
Enforced MFA on all users to enhance account security.

6. Test User Permissions
Verified that Admin users have full AWS access.
Verified that Support users have restricted permissions as per policy.
Tested access denial on disallowed actions.
7. Document Onboarding & Access Setup
Created onboarding documentation covering:
User creation and group assignment.
Password reset and MFA setup.
Troubleshooting common permission issues.

## Key Learnings
- Importance of least-privilege principle.
- Role-based access management.
- Managing permissions for multiple users effectively.

## Screenshots
![Users Created](projects/iam-demo/PwdReset.PNG)
---

