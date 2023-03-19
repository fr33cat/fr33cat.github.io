---
title: "Lambda Functions"
date: 2023-03-19T21:08:06Z
draft: true
---
# How to Exploit AWS Lambda Functions for Serverless Penetration Testing

Serverless computing is a paradigm that allows developers to run code without provisioning or managing servers. AWS Lambda is one of the most popular serverless platforms, which lets users run code in response to events such as HTTP requests, database changes, or messages from other services.

However, serverless computing also introduces new security challenges and attack vectors. In this blog post, we will explore how to exploit AWS Lambda functions for serverless penetration testing. We will demonstrate how to:

- Identify vulnerable Lambda functions
- Bypass common security controls
- Execute arbitrary commands and code
- Exfiltrate data and credentials
- Pivot to other AWS resources

## Identifying Vulnerable Lambda Functions

The first step of serverless penetration testing is to identify potential targets. There are several ways to discover Lambda functions, such as:

- Enumerating API Gateway endpoints that invoke Lambda functions
- Scanning S3 buckets that store Lambda function code
- Analyzing CloudFormation templates that deploy Lambda functions
- Leveraging IAM permissions that allow invoking or listing Lambda functions

Once we have a list of Lambda function names or ARNs (Amazon Resource Names), we can use the `aws lambda get-function` command to retrieve more information about each function, such as its runtime environment, handler name, role ARN, environment variables, and code location.

## Bypassing Common Security Controls

The next step is to bypass any security controls that may prevent us from exploiting the Lambda functions. Some of the common security controls are:

- Input validation and sanitization
- Output encoding and escaping
- Function policies and resource policies
- VPC isolation and firewalls

To bypass input validation and sanitization, we can try different injection techniques such as SQL injection, command injection, XSS injection, etc., depending on the type of input parameter and the handler logic. For example, if the input parameter is passed as an argument to a shell command executed by the handler function, we can try injecting shell metacharacters or subcommands.

To bypass output encoding and escaping, we can try different encoding schemes such as URL encoding, base64 encoding,
hexadecimal encoding etc., depending on how the output is processed by the handler function or other services. For example,
if the output is returned as an HTTP response by API Gateway,
we can try injecting HTML tags or JavaScript code.

To bypass function policies and resource policies,
we can try exploiting misconfigurations or weak permissions that allow us to invoke or modify the Lambda functions.
For example,
if the function policy allows anyone to invoke the function,
we can use `aws lambda invoke` command with any payload we want.
If the resource policy allows anyone to update the function configuration or code,
we can use `aws lambda update-function-code` command with our malicious code.

To bypass VPC isolation and firewalls,
we can try exploiting network vulnerabilities or misconfigurations that allow us access to internal resources.
For example,
if there are public IP addresses assigned to EC2 instances inside a private subnet,
we can scan them for open ports using nmap.
If there are SSH keys stored in S3 buckets accessible by our role,
we can download them using `aws s3 cp` command and use them to connect to EC2 instances.

## Executing Arbitrary Commands and Code

The ultimate goal of serverless penetration testing is
to execute arbitrary commands and code on
the underlying infrastructure hosting
the Lambda functions.
There are several ways
to achieve this goal,

such as:

-

Injecting commands into input parameters that are passed

to shell commands executed by

the handler function

-

Injecting code into input parameters that are evaluated

by dynamic languages such as Python,

Node.js,

or Ruby

-

Uploading malicious code using `aws lambda update-function-code`

command if we have permission

-

Using native libraries or system calls available in

the runtime environment

-

Using environment variables or secrets manager values

that contain commands or code

Once we have executed our commands or code,

we can perform various actions such as:

-

Enumerating files,

processes,

and network connections on

the host machine

-

Downloading additional tools,

scripts,

or malware using curl,

wget,

or powershell

-

Establishing reverse shells using netcat,

socat,

or powershell
