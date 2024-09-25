# AWS Config

- Evaluate AWS resource configurations for desired settings.
- Snapshot of the current configuration of resources associated with your AWS Account.
- Retrieve configurations of resources that exist in your account.
- Retrieve historical configurations of one or more resources.
- Receive notifications when resources are created, modified or deleted.
- View relationship between resources.
- Outputs: S3, Systems Manager Automation, Cloudwatch events, SNS.
- Automated fixes using Systems Manager Automation.

## Aggregators

- The Aggregator is created in one AWS Account for a central config account.
- Aggregates rules, resources etc across multiple accounts and regions
- If useing AWS Org. no need to individual authorization.
- Rules are created in each individual source account.
- Can deploy rules to multiple target accounts using CloudFormation stack sets.

## Use Cases

- Audit IAM Policies.
- CloudTrail has been disabled.
- EC2 AMIs are not approved.
- SGs are open to the public.
- IGW added to unauthorized VPC.
- EBS volumes are not encrypted.
- RDS Databases are public.