# Advanced IAM Policy Troubleshooting

## Project Overview
This project demonstrates how to create complex IAM policies with conditions such as time-based access and IP restrictions. It includes simulating permission errors, troubleshooting them using IAM Policy Simulator and CloudTrail logs, and documenting the resolution.

## Objectives
- Design and implement conditional IAM policies.
- Simulate and troubleshoot access permission errors.
- Analyze CloudTrail logs for access-related events.
- Document troubleshooting methodology and resolutions.

## Scenario
A test user needs to access AWS services under specific conditions:
- Access to S3 only during business hours (9 AM – 5 PM UTC).
- Access restricted to a specific IP range.
- Deny all other access outside these conditions.

## Steps Taken
1. Planned conditional IAM policies for time-based and IP-based restrictions.
2. Created IAM policies using JSON editor:
   - Time-based policy (`Policy-TimeBased.PNG`)
   - IP restriction policy (`Policy-IPRestriction.PNG`)
3. Created IAM users and attached the conditional policies.
4. Used **IAM Policy Simulator** to test allowed and denied access scenarios:
   - Verified allowed actions during business hours and from permitted IPs (`Policy-Simulator-Allowed.PNG`)
   - Verified denied actions outside conditions (`Policy-Simulator-Denied.PNG`)
5. Checked **CloudTrail logs** to confirm AccessDenied events for failed attempts (`CloudTrail-AccessDenied.PNG`)
6. Troubleshot errors and updated policies as needed (`Policy-JSON-Update.PNG`)

## Troubleshooting Table

| Issue | Possible Cause | Resolution |
|-------|----------------|------------|
| Access denied unexpectedly | Current time outside allowed range | Adjust system time or test during allowed hours |
| Access denied due to IP | User connecting from unpermitted IP | Update policy with correct IP range or test from allowed IP |
| IAM policy syntax error | JSON formatting issues | Validate JSON in IAM Policy Simulator |
| CloudTrail shows no events | Policy not attached or wrong user | Attach policy correctly and retry action |

## Key Learnings
- Learned the nuances of IAM policy conditions (time, IP, service restrictions).
- Practiced using IAM Policy Simulator for real-time testing.
- Developed troubleshooting skills using CloudTrail logs.
- Gained experience in documenting access errors and resolutions.

## Additional Resources
- [AWS IAM Policy Simulator](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies_testing-policies.html)
- [AWS CloudTrail Documentation](https://docs.aws.amazon.com/awscloudtrail/latest/userguide/cloudtrail-user-guide.html)

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

