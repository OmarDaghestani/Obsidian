---
Module: SQL Injection
Difficulty: Low
Status: Completed
Date_Started: 2023-10-26
Date_Completed: 2023-10-26
Tags: dvwa, sql_injection, low, web_security
---

# SQL Injection - Low

## 1. Description

This module demonstrates a basic SQL Injection vulnerability where user input is directly concatenated into a SQL query without proper sanitization or parameterization. The application searches for user IDs.

## 2. Objective

Retrieve information from the database that is not intended to be publicly accessible, specifically, list all users.

## 3. Vulnerable Code (if applicable)

```php
// ...
$id = $_GET['id'];
$query = "SELECT first_name, last_name FROM users WHERE user_id = $id;";
// ...
```

## 4. Exploitation Steps

### 4.1. Reconnaissance/Analysis

Observed the "User ID" input field. Tried simple numeric inputs like `1`, `2`. The page responded with corresponding user names.

### 4.2. Attack Vector/Payload

Used a union-based SQL injection to extract data.

### 4.3. Proof of Concept (PoC)

Entering the payload `1' OR 1=1 UNION SELECT user, password FROM users --` into the User ID field resulted in a list of all usernames and their hashed passwords appearing on the page.

## 5. Mitigation

For this specific case, using prepared statements with parameterized queries would prevent the SQL injection. The 'Impossible' difficulty demonstrates this.

```php
// ...
$stmt = $pdo->prepare("SELECT first_name, last_name FROM users WHERE user_id = :id;");
$stmt->bindParam(':id', $id);
$stmt->execute();
// ...
```

6. Tools Used
[[Burp Suite]] (for intercepting requests and replaying)
Manual Browser Input

7. Lessons Learned
Understood how easily SQL injection can occur when input is directly concatenated.
The importance of understanding basic SQL syntax for crafting effective payloads.
The -- comment in MySQL is crucial for ignoring the rest of the original query.


8. References
DVWA SQL Injection Source Code
OWASP Top 10 - A03:2021-Injection
PortSwigger SQL Injection Cheatsheet



