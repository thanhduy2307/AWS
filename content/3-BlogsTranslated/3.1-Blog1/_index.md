---
title: "Blog 1"
date: "2025-09-09T19:53:52+07:00"
weight: 1
chapter: false
pre: " <b> 3.1. </b> "
---

{{% notice warning %}}
Note: The article below is an interpreted translation of an AWS Database Blog.  
Please do not copy it verbatim into any official report.
{{% /notice %}}

# Optimizing Code Conversion & Testing from Microsoft SQL Server and Oracle to PostgreSQL Using Amazon Bedrock  
**Authors:** Swanand Kshirsagar, Jose Amado-Blanco, Viswanatha Shastry Medipalli  
**Published:** June 2, 2025  
**Categories:** Amazon Aurora, Amazon RDS, AWS Bedrock, Schema Conversion, PostgreSQL, Technical How-to

---

Organizations today are modernizing their database infrastructure by migrating from legacy engines such as **Microsoft SQL Server** and **Oracle** to **PostgreSQL**, an open-source engine that provides cost benefits, flexibility, and strong scalability.

Migrating to PostgreSQL not only reduces licensing costs, but also enables innovation through PostgreSQL’s rich feature set.  
This blog explains how **Amazon Bedrock’s generative AI** can accelerate and simplify the process of converting and testing database code during migration.

Because **Amazon Q Developer** is built on top of Bedrock models, the same approach can also be applied when using Amazon Q Developer.

---

# Challenges in Heterogeneous Database Migration

Migrating from SQL Server or Oracle to PostgreSQL typically involves:

### **1. Schema Conversion**  
Translating tables, views, constraints, indexes, and data types into formats compatible with PostgreSQL.

### **2. Business Logic Conversion**  
Transforming stored procedures, triggers, functions, and error-handling logic into PL/pgSQL.

### **3. Data Migration**  
Executing ETL processes while ensuring accuracy, consistency, and type compatibility.

### **4. Application Code Updates**  
Adjusting SQL queries or ORM configuration to work correctly with PostgreSQL.

### **5. Performance Tuning**  
Optimizing SQL, indexing, and execution plans in the new PostgreSQL engine.

These tasks require significant manual effort and expertise—and introduce risk if errors go undetected.

---

# How Amazon Bedrock Helps

Amazon Bedrock can automate and optimize multiple migration steps using **generative AI**, reducing effort, time, and risk.

### **Automated Schema & Code Conversion**

Bedrock can analyze SQL Server or Oracle code and produce PostgreSQL-compatible:

- Table definitions  
- Stored procedures & functions  
- Triggers  
- Exception handling logic  

### **AI-Driven Data Transformation**

Bedrock models identify necessary adjustments for dates, numeric types, money types, and structural differences to match PostgreSQL.

### **Code Compatibility Insights**

Bedrock detects:

- Unsupported SQL Server functions  
- Oracle PL/SQL constructs  
- Proprietary syntax  
- Transaction behavior differences  

…and suggests equivalent PostgreSQL alternatives.

### **Intelligent Testing & Validation**

Bedrock can generate:- Test cases  
- Validation scripts  
- Code coverage analysis  

This ensures the converted code meets functional and performance requirements before production deployment.

### **Prompt Engineering for Accuracy**

Well-designed prompts can force Bedrock to:

- Preserve naming conventions  
- Follow PostgreSQL best practices  
- Maintain business logic accuracy  
- Reduce ambiguity  

Iterative prompt refinement improves conversion accuracy and reduces manual rework.

---

# Example: Converting SQL Server Procedure to PostgreSQL Function

Using Amazon Bedrock:

1. Open **Amazon Bedrock Console → Playgrounds → Chat/Text**  
2. Select **Anthropic → Claude 3.5 Sonnet**  
3. Paste prompt asking Bedrock to convert SQL Server procedure to PostgreSQL function.

Bedrock generates:

- A PostgreSQL `plpgsql` function  
- Equivalent logic  
- Error handling using PostgreSQL conventions  
- A full set of test cases covering:
  - Valid updates  
  - Invalid parameters  
  - No eligible employees  
  - Max increase cap  
  - Percentage-based increase  
  - Inactive employees  
  - Insufficient tenure  
  - Multiple employees  

If the initial response changes naming conventions (e.g., lowercase or underscores), you can request Bedrock to regenerate while **preserving original naming**.

---

# Test Coverage Analysis

Bedrock can also analyze the generated test cases and provide **coverage breakdown**, indicating which parts of the code are tested:

- Input validation  
- Salary calculation  
- Eligibility rules  
- Update operations  
- Logging  
- Exception handling  
- Return result logic  

Suggested additional tests may include:

- Edge date conditions  
- Large numeric values  
- Simulated database errors  

For full precision coverage, tools like **pgTAP** are recommended.

---

# Generating Supporting Database Objects

Upon request, Bedrock can generate:

- `CREATE TABLE` scripts (Employees, SalaryUpdateLog)  
- Sample testing data  
- Environment initialization scripts  

This helps you fully reproduce the example function locally during migration testing.

---

# Automating Test Execution Across Source & Target

You can integrate Bedrock APIs into a custom application to:

- Run test cases against SQL Server (source) and PostgreSQL (target)  
- Compare results automatically  
- Identify logic discrepancies  
- Measure performance differences  
- Generate migration summary reports  

This eliminates manual verification and accelerates modernization.

AWS Database Migration Service (AWS DMS) Schema Conversion accelerators can also support migration and code conversion workflows.

---

# Conclusion

AWS provides a powerful set of tools and services to modernize enterprise databases.  
This blog demonstrated how Amazon Bedrock can:

- Convert SQL Server/Oracle code to PostgreSQL  
- Generate complete test cases  
- Analyze code coverage  
- Produce supporting schema and test data  
- Improve accuracy through prompt refinement By incorporating Bedrock into your migration strategy, organizations can significantly reduce:

- Migration time  
- Operational cost  
- Risk of logic or compatibility errors  

To get started with Amazon Bedrock, refer to **Getting Started with Amazon Bedrock** in AWS documentation.