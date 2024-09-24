# Directory Services and Federation

Can have a one way or two way trust relationship with Microsoft AD (Windows EC2 instances able to be logged into using credentials from the corporate AD). AWS Managed Microsoft AD.

## AWS Directory Service Overview

- * AWS Managed Microsoft AD* - auth <-> [ On-Prem AD ] <- [ AWS Managed AD ] <-> auth. Trust relationship and two way communication with on On-Prem.
- * AD Connector* - auth <-> [ On-Prem AD ] <- [ AD Connector ] <-> auth. This is a Proxy Only.
- * Simple AD* - Samba based AD.

## ADSync 

Synchronisation to AzureAD /Office365

## ADFS

Federation to AzureAD/Office365.

## Apps that support MS authentication and authorization using AWS Directory Services

- Console
- Workspaces
- RDS
- Workdocs
- QuickSight
- Workmail

It also allows you to:

- Apply Group Policy.
- Use SSO with Apps and Services.
- Enable MFA with RADIUS.


# AD Connector

Self managed AD in corp office. Want these accounts to access AWS.

````
[ AD ] --> VPN --> [ AD Connector --> Amazon Workspaces ]
                    [            --> AWS Management Console (Provides federated sign-in by mapping AD identities to IAM Roles)]
                    [           <-> Windows EC2 (bidection, can join on prem domain) ]
````

## AWS Managed Microsoft AD Connectivity to on-premise AD

- Ability to connect to your on-premise AD to AWS Microsoft AD
- Must establish Direct Connect (DX) or VPN Connection
- Can setup three kinds of forest trust

### Forest Trust Types

- One way trust AWS -> On-Premise
- One way trust On-Premise -> AWS
- Two way forest trust AWS <-> On-Premise

## Active Directory Replication

The *only* way to create a replica of your AD in the cloud (if the VPN or DX goes down) is to create a Microsoft AD self-managed replica on a Windows EC2 instance.
# Directory Services and Federation

Can have a one way or two way trust relationship with Microsoft AD (Windows EC2 instances able to be logged into using credentials from the corporate AD). AWS Managed Microsoft AD.

## AWS Directory Service Overview

- * AWS Managed Microsoft AD* - auth <-> [ On-Prem AD ] <- [ AWS Managed AD ] <-> auth. Trust relationship and two way communication with on On-Prem.
- * AD Connector* - auth <-> [ On-Prem AD ] <- [ AD Connector ] <-> auth. This is a Proxy Only.
- * Simple AD* - Samba based AD.

## ADSync 

Synchronisation to AzureAD /Office365

## ADFS

Federation to AzureAD/Office365.

## Apps that support MS authentication and authorization using AWS Directory Services

- Console
- Workspaces
- RDS
- Workdocs
- QuickSight
- Workmail

It also allows you to:

- Apply Group Policy.
- Use SSO with Apps and Services.
- Enable MFA with RADIUS.


# AD Connector

Self managed AD in corp office. Want these accounts to access AWS.

````
[ AD ] --> VPN --> [ AD Connector --> Amazon Workspaces ]
                    [            --> AWS Management Console (Provides federated sign-in by mapping AD identities to IAM Roles)]
                    [           <-> Windows EC2 (bidection, can join on prem domain) ]
````

## AWS Managed Microsoft AD Connectivity to on-premise AD

- Ability to connect to your on-premise AD to AWS Microsoft AD
- Must establish Direct Connect (DX) or VPN Connection
- Can setup three kinds of forest trust

### Forest Trust Types

- One way trust AWS -> On-Premise
- One way trust On-Premise -> AWS
- Two way forest trust AWS <-> On-Premise

## Active Directory Replication

The *only* way to create a replica of your AD in the cloud (if the VPN or DX goes down) is to create a Microsoft AD self-managed replica on a Windows EC2 instance. You need to establish a trust between the AWS Managed Microsoft AD and the EC2 instance.

## AWS Directory Services AD Connector

AD Connector is a directory gateway to redirect directory requests to your on-premise Microsoft AD. 
- It has no caching capability.
- Manage users solely on-premise, no possiblity of setting up trust.
- VPN or DX
- Doesn't work with SQL server, doesn't do seamless joining, can't share directory.

