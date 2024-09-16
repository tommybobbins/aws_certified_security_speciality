# GuardDuty

- Intelligent threat discovery.
- ML anomaly detection
- One Click, 30 day trial.
- CloudTrail Events Logs: CloudTrail Management Events + CloudTrail S3 Data Events.
- VPC Flow Logs: Unusual traffic, unusual IPs.
- DNS Logs: Check EC2s are not sending encoded data in DNS queries.
- Optional features: EKS Audit Logs, RDS & Aurora, EBS, Lambda, S3 Data Events.
- Setup EventBridge rules to target AWS Lambda or SNS.
- Protect against Crypto attacks (dedicated 'finding' for it).

## Multi Account Strategy

Associate Member accounts with the Adminstrator Account. Administrator account can add and remove member accounts, manage guard duty with the associated member accounts, manage findings, suppression rules, trusted IP lists, threat lists.

## Findings Automated Response

Findings are potential security issues, automate response issues using EventBridge. Send alerts to SNS (Email, Lambda, Slack, Chime). Findings are published in the local and Administrator account.
Each finding has a severity values between 0.1 to 8+ (Low, Medium, High), the naming convention is: `ThreatPurpose:ResourceType/ThreatFamilyName.DetectionMechanism!Artiface`
Can generate samplefindings to test that the alerting mechanism is working.

### Trusted IP lists
Public IPs only
### Threat IP list
Known Malicious IPs and Ranges
### Suppression Rules
- Automatically filter and archive new findings (low value findings, false-positives, unimportant threats)
- Can suppress entire findings or define more granualar criteria (e.g. suppress ec2 instances)
- Supressed findings are not sent to Security Hub, S3, Detective or Eventbridge.
- Supressed findings are visible in the archive.

### Troubleshooting

Q: GuardDuty is activated but didn't generate any DNS based findings.
A: Only processes DNS logs if you use the default VPC DNS resolver. Other DNS resolvers will not generate DNS based findings.
  If GuardDuty is suspended or disabled, no finding types will be generated. Best practice is to enable guardduty even in regions you do not use.

