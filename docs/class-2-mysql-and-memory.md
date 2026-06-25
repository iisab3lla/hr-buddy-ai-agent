# Class 2 - MySQL and Memory

## Overview

Class 2 focused on connecting the AI agent to structured data using MySQL.

While the Vector Store is useful for general HR policies, employee-specific information is better stored in a relational database.

---

## Objective

The objective of this class was to allow the assistant to answer questions about individual employees.

Examples:

- Vacation balance;
- Time bank;
- Department;
- Job role;
- Work model;
- Admission date.

---

## Why MySQL Was Added

RAG is useful for unstructured text, such as documents and policies.

However, structured employee information should be stored in a database because it has a predictable format.

For example:

```text
Employee name
Department
Role
Vacation balance
Time bank
Work model
```

This type of information is easier to query using SQL.

---

## MySQL Database on Railway

Railway was used to host a MySQL database in the cloud.

The database contains a table called `funcionarios`, which stores fictitious employee data.

---

## Database Table

The main table used in the project is:

```sql
CREATE TABLE funcionarios (
    id INT AUTO_INCREMENT PRIMARY KEY,
    nome VARCHAR(100) NOT NULL,
    email VARCHAR(150) NOT NULL UNIQUE,
    departamento VARCHAR(100) NOT NULL,
    cargo VARCHAR(100) NOT NULL,
    data_admissao DATE NOT NULL,
    saldo_ferias INT NOT NULL DEFAULT 0,
    banco_horas DECIMAL(5,1) NOT NULL DEFAULT 0,
    regime VARCHAR(20) NOT NULL DEFAULT 'hibrido'
);
```

---

## MySQL Tool in n8n

The MySQL Tool was added to the AI Agent.

It was configured with the `Select` operation to read data from the `funcionarios` table.

Using read-only operations is safer because the agent does not need permission to insert, update, or delete employee data.

---

## Search by Employee Name

The tool was configured to search by the `nome` column.

The operator used was `Like`, allowing partial name matching.

Example:

```sql
WHERE nome LIKE '%Maria Souza%'
```

The model was instructed to use the format:

```text
%employee_name%
```

This helps the database return relevant matches even when the user input is not perfectly formatted.

---

## System Message

The AI Agent received a system message defining its role and behavior.

The system message included rules such as:

- Always answer in Portuguese;
- Only answer HR-related questions;
- Ask for the employee's full name when needed;
- Use MySQL for employee-specific data;
- Use the Vector Store for general HR policies;
- Do not invent personal data if the employee is not found.

---

## Memory and Identification

The memory node allows the assistant to remember information provided earlier in the conversation, such as the employee name.

Example:

```text
User:
Maria Souza

User:
How many vacation days do I have?
```

The assistant can use the remembered name to query MySQL.

---

## Important Security Note

Memory is not authentication.

In this proof of concept, the user identifies themselves by providing a name. In a real HR system, this would not be enough.

A production version should include:

- User authentication;
- Employee identity validation;
- Access control;
- Audit logs;
- Data privacy rules.

---

## Result

At the end of Class 2, the assistant could:

- Use RAG for general HR policies;
- Use MySQL for employee-specific information;
- Keep basic conversational context;
- Decide which data source was more appropriate for each user question.

---

## Key Learnings

In this class, I practiced:

- Creating a MySQL database on Railway;
- Designing a simple employee table;
- Connecting MySQL to n8n;
- Configuring an AI Agent tool;
- Using SQL data inside an AI workflow;
- Differentiating unstructured and structured data;
- Understanding why memory does not replace authentication.
