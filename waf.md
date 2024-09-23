# AWS WAF

Filter web traffic based on conditions including IP addresses, HTTP headers and body and custom URIs. WAF makes it easy to create rules to block web exploits like SQL injection and XSS.

## AWS WAF LOGS

Destinations for AWS WAF logs:

- Amazon CloudWatch Logs
- Amazon Simple Storage Service
- Amazon Kinesis Data Firehose


## WAF protects

- CloudFront.
- ALB.
- API Gateway.
- AppSync for GraphQL

## WAF RULES

Baseline Rule Groups/ Use case specific Rule Groups

- Geo match
- IP set match
- Regex pattern set
- Size constraint
- SQLi attack
- String match
- XSS scripting.

### Baseline Rule Groups

- AWSManagedRulesCommonRuleSet
- AWSManagedRulesAdminProtectionRuleSet

### Use-case specific Rule Groups

- AWSManagedRulesSQLiRuleSet
- AWSManagedRulesWindowsRuleSet
- AWSManagedRulesPHPRuleSet
- AWSManagedRulesWordPressRuleSet

### IP Reputation Rule Groups

- AWSManagedRulesAmazonIPReputationList
- AWSManagedRulesAnonymousIPList

### BotContralManagedRuleGroup

- AWSManagedRulesBotControlRuleSet


## Rule Actions

- Allow
- Block
- Count
- CAPTCHA
