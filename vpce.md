# VPC Endpoint Policies

You can use an interface VPC endpoint to keep traffic between your Amazon VPC and Kinesis Data Streams from leaving the Amazon network. Interface VPC endpoints don't require an internet gateway, NAT device, VPN connection, or AWS Direct Connect connection. Interface VPC endpoints are powered by AWS PrivateLink, an AWS technology that enables private communication between AWS services using an elastic network interface with private IPs in your Amazon VPC. You do not need to change the settings for your streams, producers, or consumers. Simply create an interface VPC endpoint for your Kinesis Data Streams traffic from and to your Amazon VPC-based applications to start flowing through the interface VPC endpoint.

VPC endpoint policies enable you to control access by either attaching a policy to a VPC endpoint or by using additional fields in a policy that is attached to an IAM user, group, or role to restrict access to only occur via the specified VPC endpoint. These policies can be used to restrict access to specific streams to a specified VPC endpoint when used in conjunction with the IAM policies to only grant access to Kinesis data stream actions via the specified VPC endpoint.

# VPC Endpoint Code Deploy

For EC2 instances, this requires two VPC Interface endpoints 

- `com.aamazonaws.region.codedeploy` (API operations)
- `com.amazonaws.region.codedeploy-commands-secure` (Agent operations)

For ECS and Lambda, you only need API access.
- `com.aamazonaws.region.codedeploy` (API operations)

# Lambda functions and secretsmanager

If deploying a Lambda function in a private subnet in a VPC, then `com.amazonaws.region.secretsmanager` is required.

# SSM Session Manager

If there is no NAT gateway for a private subnet: 
- `com.amazonaws.region.ssm`. SSM Service. 443 inbound must be allowed on the SG for this endpoint.
- `com.amazonaws.region.ssmmessages`. SSM Session Manager. 443 inbound must be allowed.
- `com.amazonaws.region.ec2messages`. SSM Commands. 443 inbound must be allowed.
- `com.amazonaws.region.kms`. Optional KMS Encryption. 443 inbound must be allowed.

