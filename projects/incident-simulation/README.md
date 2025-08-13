# Incident Handling Simulation: Expired AWS Access Keys

## Project Overview
This project simulates a real-world incident where a user lost access to AWS resources due to expired access keys.  
It demonstrates troubleshooting, root cause analysis, resolution, and preventive measures—showing your ability to handle operational incidents efficiently.

---

## Scenario
A user lost access due to expired AWS access keys, causing a disruption in their workflow.

---

## Problem Statement
The user could not access AWS resources via CLI due to expired credentials.

---

## Troubleshooting Steps
1. Verified the error message when the user attempted to access AWS CLI.
2. Checked the AWS Console for the user's active access keys.
3. Confirmed that the existing access keys were expired.
4. Created new access keys for the user.
5. Updated the user's AWS CLI configuration to use the new keys.
6. Tested access to confirm the issue was resolved.

---

## Root Cause
Access keys had expired and were not renewed in a timely manner.

---

## Resolution
- Issued new access keys to the user.
- Guided the user to update their local AWS CLI configuration.
- Confirmed that the user could now access AWS resources without errors.

---

## Preventive Measures
- Documented key rotation procedures.
- Recommended enabling alerts for expiring credentials.
- Suggested periodic review of active IAM credentials.

---

## Key Learnings
- Importance of **credential management** and timely key rotation.
- How to **troubleshoot AWS CLI access issues** systematically.
- Value of **incident documentation** for knowledge sharing and preventive measures.

---

## Screenshots
_Add relevant screenshots here (AWS Console, CLI output, or key creation process)_:  

![CLI Error Message](projects/incident-simulation/Documentaion/cli-error.png)
![AWS Console - Access Keys](projects/incident-simulation/Documentaion/access-keys.png)  
![Updated CLI Config](projects/incident-simulation/Documentaion/cli-update.png)

---

## References
- AWS KB: [Managing Access Keys for IAM Users](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_credentials_access-keys.html)
- AWS CLI Configuration Guide: [https://docs.aws.amazon.com/cli/latest/userguide/cli-configure-quickstart.html](https://docs.aws.amazon.com/cli/latest/userguide/cli-configure-quickstart.html)
