# Client VPN Authentication Types

## AD Auth

- Auth against Microsoft AD (User Based).
- AWS Managed Microsoft AD or on-premise AD through AD connector.
- Supports MFA.

## Mutual Auth

- Use certificates to perform the authentication (Cert based).
- Must upload the server certificate to AWS Certificate Manager.
- Recommended to use one client certificate per User.

## SSO (IAM Identity Centre/ AWS SSO)

- Auth against SAML 2.0 based identity providers (User based).
- Establish a trust relationship between AWS and the identity provider.
- Only one identity provider at a time.

