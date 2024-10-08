# Inspector

## What does it scan?
- EC2 instances using SSM (needs an instance profile->role with SSM)
- Container Images pushed to ECR.
- Lambda Functions.

## What does it do ?

- Runs assessments that check for security exposures and vulnerabilities in EC2 instances.
- Can be scheduled.
- Needs an Agent for host assessments (can be done via Systems Manager)
- Network assessments do not require and agent
- Reports it's findings into Security Hub & Event Bridge.

## Network Assessments

- Network configuration analysis to check for ports reachable from outside the VPC.
- If the Inspector Agent is installed on your EC2s, the assessment also finds processes reachable on ports.
- Priced based on # of instance assessments.

## Host Assessments

- Vulnerability software (CVE), Host hardening (CIS), and security best practices.
- Requires an agent (auto install with SSM Run Command).
- Priced based on instance assessments.
