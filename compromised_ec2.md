# Compromised EC2 instance

- Capture instance metadata.
- Enable termination protection.
- Isolate the instance (no traffic outbound).
- Detach the instance from ASG.
- Deregister the instance from the ELB.
- Snapshot the ELB.
- Offline investigation: Forensic instance with the snapshot->volume attached.
- Tag the EC2 instance.
- Online investigation: Snapshot memory or capture network traffic.
- Automate with Lambda.
- Automate memory capture: SSM Run command.

# Compromised S3 bucket

- Identify the compromised S3 bucket using Guardduty.
- Identify the source of the malicious activity (e.g. IAM user, role) and the API calls using CloudTrail or Amazon Detective.
- Identify whether the source was authorized to make those API calls.
- Secure your S3 bucket, recommended settings: Block Public Access, Bucket Policies and User Policies, VPC endpoints for S3, S3 Presigned URLs, S3 access points, S3 ACLs.

# Compromised ECS Cluster

- Identify the affected ECS cluster using Guardduty.
- Identify the source of the malicious activity (container image, tasks).
- Isolate the impacted tasks (deny all ingress/egress using security groups).
- Evaluate the presence of malicious activity. (e.g. malware.)

# Compromised Standalone container

- Identify the maliciuous container using GuardDuty.
- Isolate the malicious cointainer (ingress/egress).
- Suspend all processes in the container (pause the container).
- OR stop the container and look at EBS snapshots retained by GuardDuty
- Evaluate the presence of malicious activity (e.g malware).

# Compromised RDS 

- Identify the affected DB instance and DB user using GuardDuty.
- If not legitmate, restrict network sources using SG and NACL, restrict the DB User access to RDS.
- Rotate the suspected RDS Users passwords.
- Review DB Audit Logs.
- Secure RDS DB using secrets manager to rotate password, use IAM DB Authentication for passwordless access.

# Compromised AWS Credentials

- Identify the IAM User using GuardDuty.
- Rotate the exposed AWS Credentials.
- Invalidate temporary credentials by attaching an explicit Deny policy to the affected IAM User with an STS Date condition.
- Check Cloudtrail Logs.
- Review AWS Resources.
- Verify AWS Account Information.

# Compromised IAM Role.

- Invalidate temporary credentials by attaching an explicit Deny policy to the affected IAM user with an STS Date condition.
- Revoke access for the identity to the linked AD if any.
- Check Cloudtrail Logs.
- Review AWS Resources.
- Verify AWS Account Information.

# Compromised Account

- Rotate and Delete AWS Access Keys
- Rotate and Delete any unauth IAM user credentials.
- Rotate and delete all EC2 key pairs
- Check Cloudtrail Logs.
- Review AWS Resources.
- Verify AWS Account Information.
