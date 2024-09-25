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

## AWS Private CA

- Managed service allows you to create private CA including root and subordinate CAs.
- Can issue and deploy end-entity X509 certs.
- Certs are trusted only by your Org (not the internet).
- Integrates with EKS and any AWS service that uses ACM.
- Use cases: Encrypted TLS commununication, cryptographically signing code. Auth users, computers, API endpoints, IoT, Enterprise customers using PKI.