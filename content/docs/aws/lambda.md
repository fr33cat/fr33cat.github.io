# How to Pentest AWS Lambda Functions

AWS Lambda is a serverless computing service that allows you to run code without provisioning or managing servers. Lambda functions can be triggered by various events, such as HTTP requests, S3 bucket changes, DynamoDB streams, etc. Lambda functions can also access other AWS services and resources through IAM roles and policies.

Pentesting AWS Lambda functions can be challenging, as they are ephemeral, scalable, and isolated. However, there are some techniques that can help you discover and exploit vulnerabilities in Lambda functions and their configurations.

## Discovering Lambda Functions

One of the first steps in pentesting AWS Lambda functions is to find out which functions exist and how they are invoked. There are several ways to do this:

- Use the AWS CLI or SDK to list all the functions in a region: `aws lambda list-functions --region <region>`
- Use the AWS Management Console to browse through the functions and their triggers
- Use tools like [Lambhack](https://github.com/Coalfire-Research/Lambhack) or [Pacu](https://github.com/RhinoSecurityLabs/pacu) to enumerate Lambda functions and their metadata
- Use passive reconnaissance techniques such as DNS enumeration, subdomain scanning, web crawling, etc. to find endpoints that invoke Lambda functions
- Use active reconnaissance techniques such as port scanning, banner grabbing, fuzzing, etc. to identify Lambda function endpoints and their parameters

## Exploiting Lambda Functions

Once you have discovered some Lambda functions and their triggers, you can try to exploit them by sending malicious inputs or requests. Some of the common attack vectors are:

- Injection attacks: If the Lambda function accepts user input or parameters from an event source (such as API Gateway), you can try to inject malicious code or commands that will execute on the underlying container or environment. For example, you can use [Server-Side Template Injection (SSTI)](https://portswigger.net/research/server-side-template-injection) techniques to execute arbitrary code on a function that uses a templating engine (such as Jinja2) for rendering HTML responses.
- Privilege escalation attacks: If the Lambda function has an IAM role attached to it that grants access to other AWS resources or services (such as S3 buckets, DynamoDB tables, EC2 instances, etc.), you can try to abuse those permissions by performing unauthorized actions on those resources or services. For example, you can use [Server-Side Request Forgery (SSRF)](https://portswigger.net/web-security/ssrf) techniques to make requests from the function's container to internal AWS endpoints (such as metadata service) that will return sensitive information (such as IAM credentials) that you can use for further exploitation.
- Denial-of-service attacks: If the Lambda function has a limited concurrency limit or timeout value set for it (which is common for cost optimization purposes), you can try to exhaust those limits by sending multiple concurrent requests or long-running requests that will prevent other legitimate requests from being processed. For example, you can use [Slowloris](https://github.com/gkbrk/slowloris) tool to send partial HTTP requests that will keep connections open with the function's endpoint until it reaches its concurrency limit.

## Mitigating Risks

To prevent or reduce the impact of pentesting attacks on AWS Lambda functions, there are some best practices that should be followed by developers and administrators:

- Use secure coding practices and frameworks when developing Lambda functions
- Validate and sanitize user input and parameters before processing them
- Implement proper error handling and logging mechanisms for debugging purposes
- Restrict access to Lambda function endpoints using authentication and authorization mechanisms (such as API keys)
- Apply least privilege principle when assigning IAM roles and policies to Lambda functions
- Monitor and audit Lambda function activity using CloudWatch Logs and CloudTrail
