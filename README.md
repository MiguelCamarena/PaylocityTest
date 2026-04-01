# Paylocity Benefits QA Challenge

## 👨‍💻 Tester
Miguel Camarena

## 📌 Overview
This report documents the findings from testing the Paylocity Benefits Dashboard application, covering both UI and API layers.

The goal was to identify defects, validate business logic, and evaluate system reliability.

---

## 🔍 Scope
- UI Testing
- API Testing
- Business Logic Validation
- Security & Edge Cases

---

## ⚠️ Key Findings

### 🔴 Critical Issues
- Authentication bypass (user can access data without login)
- No input validation (invalid/negative data accepted)
- Missing API validation and error handling

### 🟠 High Issues
- Incorrect HTTP status codes (most of time 200)
- Missing response contract in Swagger
- CORS misconfiguration

### 🟡 Medium Issues
- PUT endpoint not REST compliant
- Salary can be modified without validation

### 🟢 Low Issues
- UI misalignment issues
- Missing confirmation messages

---

## 📐 Business Logic Validation

The system calculations were validated based on:

- $2000 per paycheck
- 26 paychecks/year
- $1000/year per employee
- $500/year per dependent

✔ Calculations are correct  
❌ No validation or constraints enforced  

---

## 📂 Reports

- 👉 [UI Bugs](./ui-bugs.md)
- 👉 [API Bugs](./api-bugs.md)

---

## 🧠 Conclusion

The application demonstrates basic functionality but lacks proper validation, security controls, and REST compliance. These issues introduce risks in data integrity, security, and maintainability.

---

## 🚀 Recommendations

- Enforce authentication validation
- Implement proper HTTP status codes
- Add strict input validation
- Fix REST endpoint design
- Define response contracts in Swagger
- Use proper data types for financial calculations
