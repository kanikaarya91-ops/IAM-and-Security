# KB Article: Creating an IAM User with Least-Privilege Access

**Author:** Kanika Arya  
 
**Category:** AWS IAM  
**Purpose:** This document explains how to create an AWS IAM user, assign them to the correct group, apply least-privilege policies, and verify their access.

---

## Prerequisites
- AWS account with administrator access.
- AWS Management Console access.
- IAM permissions to create users, groups, and policies.

---

## Procedure

### 1️⃣ Sign in to AWS Management Console
- Go to: [https://console.aws.amazon.com/](https://console.aws.amazon.com/)  
- Log in as the **root user** or an **IAM user with Admin privileges**.

---

### 2️⃣ Create an IAM Group
1. In the AWS Console, navigate to **IAM**.
2. Select **User groups** → **Create group**.
3. Name the group:  
   - Example: `Support` (for read-only permissions)  
   - Example: `Admin` (for full access)  
4. Attach policies based on role:
   - `Support` → `AmazonS3ReadOnlyAccess`, `CloudWatchReadOnlyAccess`
   - `Admin` → `AdministratorAccess`
5. Click **Create group**.

---

### 3️⃣ Create an IAM User
1. In **IAM**, go to **Users** → **Create user**.
2. Enter username admin1,admin2,support1 etc
3. Select **Provide user access to the AWS Management Console**.
4. Set password:  
   - Choose **Custom password**.  
   - Check **Require password reset upon first sign-in**.
5. Click **Next**.

---

### 4️⃣ Assign User to a Group
1. In **Set permissions**, select **Add user to group**.
2. Choose the group created earlier (`Support` or `Admin`).
3. Click **Next** → **Create user**.

---

### 5️⃣ Test User Access
1. Log out of AWS Console.
2. Go to: [https://console.aws.amazon.com/](https://console.aws.amazon.com/)
    *(Replace `<account_id>` with your 12-digit AWS account ID)*
3. Sign in using the new IAM user credentials.
4. Verify:
- The user can only perform actions allowed by the assigned policies.
- Restricted actions result in an “Access Denied” error.

---

## IAM Policy Example (JSON)

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
##Troubleshooting


| Issue                              | Possible Cause                             | Solution                                     |
| ---------------------------------- | ------------------------------------------ | -------------------------------------------- |     |
| User can access more than intended | Policy attached grants broader permissions | Review policies and adjust actions/resources |
| User unable to perform any action  | No policies attached                       | Attach correct group or policy               |



##References
AWS KB: How do I create an IAM user and manage their permissions?
AWS IAM Policy Reference: https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies.html

