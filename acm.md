# ACM

Create store and renew TLS X.509 certificates

- AWS own the Private key, inaccessible.
- Single domains, multiple domain names and wildcards.
- ELB
- Elastic Beanstalk
- Nitro Enclaves
- CloudFront
- CloudFormation
- Can create a private CA if required.
- Can then issue private certificates.
- Can import certificates from third party issuers.


## Identify expiring certificates and generate notifications.

````
[Cloudwatch cron] -> [ lambda ] <- [ACM DaysToExpiry] 
                        -> [ CloudWatch ] -> [ SecurityHub ]
                        -> [ SNS notification ]
                                
````

This option provides a scheduled solution to examine all expiring certificates in ACM, log all the findings in Security Hub, and generate a single notification through SNS for all certificates that are found. The option workflow is as follows: 1. CloudWatch runs the rule on a timer and invokes a Lambda function. 2. The function finds all certificates that have a DaysToExpiry metric in CloudWatch. 3. The function logs all the expiring certificates as findings in Security Hub. 4. The function publishes a notification to an SNS topic with the expiration details. 5. SNS creates a notification (most commonly, through email) to any subscribers of the topic.