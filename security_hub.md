# AWS Security Hub

Central security tool to manage security across several AWS accounts and automate security checks.
Integrated dashboards showing current security and compliance to be able to take Action.
Aggregates alerts from:
- Config.
- GuardDuty.
- Inspector.
- Macie.
- IAM Access Analyzer.
- AWS Systems Manager.
- AWS Firewall Manager.
- AWS Health.
- AWS Partner Network Solutions.

To make it work, you *must* enable AWS Config first.
Events are generated in Eventbridge.

## Features
- Cross Region Aggregation.
- AWS Organizations Integration - either default Organization management account or use a dedicated account.
- AWS Config must be enabled on all member accounts.

## Standards

- CIS AWS Foundational Security Best Practices
- CIS AWS Foundations Benchmark
- PCI DSS v3.2.1

## Integration with GuardDuty

- Automatically enabled when SecurityHub is enabled.
- GuardDuty sends findings to SecurityHub.
- Findings are sent in AWS Security Finding Format (ASFF).
- 5 minutes for a finding to arrive in SecurityHub
- Archiving GuardDuty and SecurityHub are separate tasks.

## INPUTS

- AWS Config
- Firewall Manager
- Guard Duty
- AWS Health
- IAM Access Analyzer
- Inspector
- IoT device defender
- Macie
- SSM Patch Manager

## OUTPUTS

- Audit Manager
- AWS Chatbot
- Amazon Detective
- Trusted Advisor
- SSM Explorer and OpsCenter

## 3rd Party Integration
### Send findings to Security Hub

- 3coresec
- Alertlogic
- aqua

### Receive findings from Security Hub

- Atlassian
- Fireeye
- Fortinet

### Update findings in security hub

- Atlassian
- servicenow

### Workflow status

 - Move findings to New->Notified->Suppressed->Resolved.

### Insights

- Collection or related findings that identifies a security area that requires attention and intervention.
- e.g. EC2 instances with poor security practices.
- Brings findings from across finding providers.
- Each Insight is defined by Group By statement and optional filters.
- Built-in managed insights.
- Custom Insights.

### Custom Actions

Automate SecurityHub with Eventbridge. 
