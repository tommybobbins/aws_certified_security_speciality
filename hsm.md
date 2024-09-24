# HSM

- Hardware Security Module.
- Generate your own encryption keys in the cloud.
- Manage encryption keys using FIPS 140-2 Level 3 validated HSM. (Can use KMS for Level 2)
- Runs in your VPC.
- Retain control of your encrpytion keys - you control access and AWS has no visibility of encryption.

## Integration with AWS and 3rd Party Services

- Through integration with AWS KMS.
- Configure KMS Custom Key Store with CloudHSM.
- EBS, S3, RDS.
- Supports RDS Oracle TDE through KMS (kms encrypts EBS volume through a custom key store).

## Integration with 3rd party services

- Allows creating and storing keys in CloudHSM.
- Use cases: SSL/TLS Offload, Windows Server CA, Oracle TDE, Microsoft SignTool, Java Keytool.

Share the private subnets of the Cloud HSM Clusters in AWS RAM. Cannot share CloudHSM itself.

