---
weight: 1
title: "AWS"
---

# Pentesting AWS Environments: A Beginner's Guide

AWS (Amazon Web Services) is a cloud computing platform that offers a variety of services such as computing, storage, networking, database, analytics, security and more. AWS customers can use these services to build and run applications on the cloud, without having to worry about managing the underlying infrastructure.

However, as with any IT system, AWS environments are not immune to security risks and vulnerabilities. Penetration testing (or pentesting) is a method of evaluating the security posture of an AWS environment by simulating a malicious attack and trying to exploit any weaknesses or flaws.

Pentesting can help AWS customers identify and mitigate security issues in their cloud infrastructure, as well as comply with regulatory requirements and industry standards. In this blog post, we will cover some of the basics of pentesting AWS environments, such as:

- What are the benefits and challenges of pentesting AWS environments?
- What are the permitted and prohibited activities for pentesting AWS environments?
- What are some of the tools and techniques for pentesting AWS environments?

## Benefits and Challenges of Pentesting AWS Environments

Pentesting AWS environments can provide several benefits for both AWS customers and service providers. Some of these benefits include:

- Improving the security awareness and resilience of the cloud infrastructure
- Detecting and preventing potential data breaches or cyberattacks
- Enhancing the trust and confidence of customers and stakeholders
- Demonstrating compliance with security best practices and regulations

However, pentesting AWS environments also poses some challenges that need to be considered before conducting a pentest. Some of these challenges include:

- Understanding the shared responsibility model between AWS and its customers
- Obtaining prior approval from AWS for certain types of pentests
- Following the policies and guidelines set by AWS for pentesting
- Avoiding any disruption or damage to the cloud services or other customers

## Permitted and Prohibited Activities for Pentesting AWS Environments

AWS has a customer support policy for penetration testing that defines what types of activities are permitted or prohibited for pentesting its services. According to this policy:

- Customers can perform security assessments or penetration tests on their own **AWS infrastructure** without prior approval from AWS for certain services listed under "Permitted Services".
  - These services include Amazon EC2 instances, WAF, NAT Gateways, Elastic Load Balancers, Amazon RDS, Amazon CloudFront etc.
  - Customers can also host their own security assessment tooling within the **AWS IP space** or other cloud provider for on-premises testing.
  - All security testing that includes **Command-and-Control (C2)** requires prior approval from **AWS**.
  - Customers should ensure that their activities are aligned with **the policy** set out by **AWS**.
  
- Customers are **not permitted** to conduct any security assessments or penetration tests on **AWS infrastructure** or **the AWS services themselves**.
  - If customers discover a security issue within any of **the AWS services**, they should contact **AWS Security** immediately.
  - If **AWS receives an abuse report** for activities related to customer's security testing,
    they will forward it to them. Customers should provide approved language detailing their use case,
    including a point-of-contact that they can share with any third-party reporters.

Some examples of prohibited activities include:

- DNS zone walking via Amazon Route 53 Hosted Zones
- DNS hijacking via Route 53
- DNS Pharming via Route 53
- Denial-of-service (DoS), Distributed Denial-of-service (DDoS), Simulated DoS,
Simulated DDoS (These are subject to DDoS Simulation Testing policy)
Port flooding Protocol flooding Request flooding (login request flooding,
API request flooding)

Customers seeking to test non-approved services will need to work directly with their **AWS Support Team**.

## Tools And Techniques For Pentesting Aws Environments

There are many tools available online that can help you perform various tasks related to pentesting aws environments such as reconnaissance,
enumeration,
exploitation,
post-exploitation etc.

Some examples of these tools include:

### Nmap

Nmap is a popular network scanning tool that can help you discover hosts,
ports,
services,
operating systems etc.
on your target network.
