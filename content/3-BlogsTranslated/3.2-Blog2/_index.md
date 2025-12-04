---
title: "Blog 2"
date: "2025-09-09T19:53:52+07:00"
weight: 2
chapter: false
pre: " <b> 3.2. </b> "
---



# Structured JSON Logging for .NET Lambda Functions  
**Author:** Norm Johanson  
**Published:** November 7, 2024  
**Categories:** .NET, AWS Lambda, Developer Tools

---

**Norm Johanson** is a software developer with over 25 years of experience building many types of applications. Since 2010, he has worked at AWS, focusing on improving the experience for .NET developers. You can find him on Twitter **@socketnorm** and GitHub **@normj**.

AWS has announced **structured JSON logging support** for the .NET managed runtime in AWS Lambda. This enhancement brings the .NET managed runtime in line with previously released **Lambda logging controls**, allowing developers to change the logging format and log levels through the Lambda API.

Formatting log messages as **JSON documents** makes it significantly easier to search, filter, and analyze Lambda logs—especially when monitoring, debugging, or creating automated alarms based on specific log fields.

---

# Enabling Structured JSON Logging

By default, Lambda logs use **plain text** format.  
You can switch a function to **JSON log format** using AWS tooling, including:

- AWS Lambda Console  
- .NET CLI tool **Amazon.Lambda.Tools**  
- AWS Tools for PowerShell  
- AWS CLI  

In the Lambda Console, the logging configuration is available under:

**Configuration → Monitoring and operations tools → Logging configuration**

Beginning with **Amazon.Lambda.Tools version 5.11.0**, new command-line switches were added:

- `--log-format`  
- `--log-application-level`  
- `--log-system-level`  
- `--log-group`  

Example deployment enabling JSON logging:

```bash
dotnet tool install -g amazon.lambda.tools
dotnet lambda deploy-function <function-name> --log-format JSON