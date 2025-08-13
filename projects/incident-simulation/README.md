# Incident Handling Simulation

## Scenario
A user lost access due to expired AWS access keys, causing a disruption in their workflow.

## Problem Statement
User cannot access AWS resources via CLI due to expired credentials.

## Troubleshooting Steps
1. Verified the error message when user tried to access AWS CLI.
2. Checked AWS Console for user's active access keys.
3. Confirmed that access keys were expired.
4. Created new access keys for the user.
5. Updated the user's AWS CLI configuration.

## Root Cause
Access keys had expired and were not renewed timely.

## Resolution
Issued new access keys and guided the user to update their local AWS CLI configuration.

## Preventive Measures
- Documented key rotation procedures.
- Recommended enabling alerts for expiring credentials.

## Screenshots
(Add CLI output or AWS Console screenshots here)

---

