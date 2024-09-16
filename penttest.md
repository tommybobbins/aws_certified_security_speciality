# Pentest

AWS allow Pentest for the following 8 services:

- EC2, NAT GW, ELB
- RDS
- CloudFront
- Aurora
- API Gateways
- Lambda and Lambda edge
- LightSail
- ELBeanstalk

## Not allowed

- DNS Zone walking via Amazon Route 53 hosted zones.
- DoS, DDoS, Port flooding, Request flooding.

## DDoS Attack Simulation

- AWS DDoS Test Partner
- Target can be either protected resources or Edge optimized API Gateway subscribed to shield advanced.
- Must not originate from AWS.
- Must not exceed 20Gb/s.
- Must not exceed 5M packets/second for CloudFront or 50K packets/second for any other service.
