# SES

||SES|SNS|
| --- | --- | --- |
| Use Case | Email | Notifications|
| Direction | Inbound | Push only |
| Model| Email service provider | Pub/Sub |
| Use Case | Transactional, marketing, notifications, announcements | Notifications| 
| Format | Email | Multiple formats including email|


## Mandatory TLS

Amazon SES uses opportunistic TLS by default. Change the behavior of SES by using configuration sets. Set the TlsPolicy property for a configuration set to Require
Use the CLI and PutConfigurationSetDeliveryOptionsto set the TlsPolicy property for a configuration set to Require.