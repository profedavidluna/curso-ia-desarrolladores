# Refactoring Exercise with AI

## Overview
This exercise focuses on the refactoring of a monolithic REST API case built using Node.js and Express, which has various code smells and vulnerabilities. The goal is to apply clean architecture and SOLID principles to enhance the security and maintainability of the code.

## Monolithic REST API Case
### Issues Identified:
1. **SQL Injection Vulnerability**: The API currently constructs SQL queries using untrusted input, making it vulnerable to SQL injection attacks.

2. **Lack of Separation of Concerns**: Business logic is intertwined with presentation logic, making it hard to maintain and test.

3. **Hardcoded Configuration**: Configuration values are hardcoded into the application, reducing flexibility and security.

4. **Inline Validation**: Input validation is done inline, which is not reusable and clutters the codebase.

5. **Mixed Business Logic with Presentation Layer**: The routes directly handle business logic, making the API difficult to extend.

### Example Vulnerable Code:
```javascript
app.post('/users', (req, res) => {
    const username = req.body.username;
    const password = req.body.password;
    const sql = `SELECT * FROM users WHERE username = '${username}' AND password = '${password}'`;
    db.query(sql, (err, results) => {
        if (err) throw err;
        res.json(results);
    });
});
```

### Python Class Violating SOLID Principles:
```python
class SalesReport:
    def generate_report(self):
        # Generates report including business logic here
        pass

    def format_report(self):
        # Formatting logic intermingled
        pass
```

## Refactoring Goals
- Apply **Clean Architecture** to separate layers distinctly.
- Implement **SOLID Principles** to enhance code structure and maintainability.
- Use **Security Best Practices** such as parameterized queries to prevent SQL injection.
- Utilize **Environment Variables** for configuration management.
- Implement centralized **Error Handling**.
- Use **Validation Middleware** for input validation.
- Ensure proper **Logging** for monitoring and debugging.
- Introduce **Testing** to validate the functionality and security of the application.

### Refactored Code Snippet (Node.js)
```javascript
// Using environment variables
const express = require('express');
const app = express();
const db = require('./db');
const { check, validationResult } = require('express-validator');

app.post('/users', [
    check('username').notEmpty().withMessage('Username is required'),
    check('password').notEmpty().withMessage('Password is required')
], (req, res) => {
    const errors = validationResult(req);
    if (!errors.isEmpty()) {
        return res.status(400).json({ errors: errors.array() });
    }
    const { username, password } = req.body;
    db.query('SELECT * FROM users WHERE username = ? AND password = ?', [username, password], (err, results) => {
        if (err) return res.status(500).send('Database error');
        res.json(results);
    });
});
```

### Refactored Python Class:
```python
class SalesReport:
    def __init__(self, data):
        self.data = data

    def generate_report(self):
        # Business logic separated from formatting
        pass

class ReportFormatter:
    def format(self, report):
        # Formatting logic handled separately
        pass
```