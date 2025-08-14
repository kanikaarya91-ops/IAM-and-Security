# KB Article – Advanced IAM Policy Troubleshooting

## Purpose
This Knowledge Base (KB) article provides step-by-step guidance for creating conditional IAM policies, troubleshooting access permission errors, and analyzing CloudTrail logs.

## Scope
Covers IAM policy conditions such as time-based access and IP restrictions for AWS services like S3.

---

## Step 1 – Create Conditional IAM Policies

### Time-Based Access Policy
- Allows users to access resources only during defined hours.
- Example JSON:
```json
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "AllowBusinessHoursAccess",
            "Effect": "Allow",
            "Action": "s3:*",
            "Resource": "*",
            "Condition": {
                "DateGreaterThan": {"aws:CurrentTime": "2025-08-14T09:00:00Z"},
                "DateLessThan": {"aws:CurrentTime": "2025-08-14T17:00:00Z"}
            }
        }
    ]
}
```

### IP Restriction Policy
Restricts access to specific IP addresses.

``` json
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "AllowSpecificIP",
            "Effect": "Allow",
            "Action": "s3:*",
            "Resource": "*",
            "Condition": {
                "IpAddress": {"aws:SourceIp": "203.0.113.0/24"}
            }
        }
    ]
}
```

## Step 2 – Assign Policies to IAM Users
- Create a new IAM user.
- Attach the conditional policies created above.
- Note user ARN and credentials.

## Step 3 – Test Using IAM Policy Simulator
- Open **IAM → Policy Simulator**.
- Select the IAM user.
- Test allowed actions within business hours and correct IP.
- Test denied actions outside allowed hours or from other IPs.

**Expected Results:**
- Allowed actions should show "Allowed".
- Denied actions should show "Denied".

## Step 4 – Analyze CloudTrail Logs
- Open **CloudTrail → Event History**.
- Filter by IAM user or event source.
- Look for **AccessDenied** events caused by policy conditions.

## Step 5 – Troubleshoot & Resolve
- Verify policy JSON for syntax errors.
- Check current time and IP against policy conditions.
- Adjust policy or user configuration as needed.

## Preventive Measures
- Document all conditional policies clearly.
- Regularly review IAM policies and CloudTrail logs.
- Use Policy Simulator before applying policies in production.

## Screenshots

### Time-Based Policy
![Time-Based Policy](./Policy-TimeBased.PNG)

### IP Restriction Policy
![IP Restriction Policy](./Policy-IPRestriction.PNG)

### IAM Policy Simulator - Allowed
![Policy Simulator Allowed](./Policy-Simulator-Allowed.PNG)

### IAM Policy Simulator - Denied
![Policy Simulator Denied](./Policy-Simulator-Denied.PNG)

### CloudTrail Access Denied Event
![CloudTrail Access Denied](./CloudTrail-AccessDenied.PNG)

### Updated Policy JSON
![Policy JSON Update](./Policy-JSON-Update.PNG)


## References
- [AWS IAM Policy Simulator Documentation](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies_testing-policies.html)
- [AWS CloudTrail Documentation](https://docs.aws.amazon.com/awscloudtrail/latest/userguide/cloudtrail-user-guide.html)

## Time-Based Policy Limitation

The time-based policy example in this guide uses a fixed date. As a result, access will only be allowed on that date.

### Why it matters
- Testing on other days will result in denied access.
- Shows the importance of understanding IAM condition keys and their limitations.

### Workaround for real-world use
1. **Automation Approach**
   - Create a CloudWatch Event (Scheduled Rule) that triggers at 9 AM every day.
   - Lambda function attaches the IAM policy allowing access.
   - CloudWatch Event triggers at 5 PM to detach the policy.
2. **SCP Approach**
   - If using AWS Organizations, SCPs can enforce daily access conditions with `aws:CurrentTime` combined with day-of-week conditions.


