# IAM Credentials Report (account-level). 
List all your account users and the status of their various credentials. Creates a .csv.

# IAM Access Advisor (user-level)
Access advisor shows the service permissions granted to a user and when those services were last accessed.
Use this information to revise your policies.


# IAM Access Analyzer

Find out which resources are shared externally

- S3 buckets
- IAM Roles
- KMS Keys
- Lambda
- SQS
- Secrets manager

Define a zone of trust = AWS Account, AWS Org.
Access from outside the zone of trust-> findings.

## Policy Validation

- Validates your policy against IAM policy grammar and best practices
- General warnings, security warnings, errors, suggestions
- Actionable recommendations

## IAM Access Analyzer Policy Generation

- Generates IAM policy based on access activity.
- CloudTrail logs is reviewed to generate the policy with fine grained permissions.
- Build from the CloudTrail logs (90 days).

