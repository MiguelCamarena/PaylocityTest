# UI Defects Report

---

## Defect 1: Login – Favicon.ico returns error after login

### Description
The `favicon.ico` resource fails to load after user login.

### Steps to Reproduce
1. Go to the application  
2. Login with valid credentials  
3. Open browser DevTools → Network tab  
4. Locate the `favicon.ico` request  

### Actual Result
- Status Code: 403 Forbidden  

### Expected Result
- Favicon should load successfully (200 OK)  
- No errors should be present in the Network tab  

---

## Defect 2: Login – Invalid credentials show incorrect error

### Description
When using invalid credentials, the system does not display a proper authentication error message.

### Steps to Reproduce
1. Go to the application  
2. Attempt login using invalid credentials  

### Actual Result
- Browser shows a generic error page (HTTP error / unexpected behavior)  
- No clear validation message is displayed  

### Expected Result
- System should display a clear message such as:  
  "Invalid username or password"  

---

## Defect 3: Login – User can access data without valid authentication

### Description
The application allows users to access data without valid authentication using browser navigation.

### Steps to Reproduce
1. Login with valid credentials  
2. Logout  
3. Attempt login with invalid credentials (e.g., user1 / pass1)  
4. Error appears ("Esta página no funciona")  
5. Click browser Back button  

### Actual Result
- User is able to see application data without valid login  

### Expected Result
- User should not be able to access any data without valid authentication  
- System should redirect to login page or block access  

---

## Defect 4: Employee Creation – No validation for empty or negative values

### Description
The system allows creating employees with empty fields and negative values without displaying any validation error.

### Steps to Reproduce
1. Login with valid credentials  
2. Add a new employee  
3. Enter:
   - Empty fields  
   - Negative values (e.g., dependents = -1)  

### Actual Result
- No error message is displayed  

### Expected Result
- System should validate inputs  
- Error message should be displayed for invalid data  

---

## Defect 5: Employee Creation – No validation for maximum field length

### Description
The system does not enforce maximum character limits in input fields.

### Steps to Reproduce
1. Login with valid credentials  
2. Add a new employee  
3. Enter values exceeding maximum allowed characters  

### Actual Result
- No error message is displayed  

### Expected Result
- System should enforce maximum length validation  
- Error message should be shown  

---

## Defect 6: Employee Table – Incorrect row ordering

### Description
New employees are not added at the end of the table after re-login.

### Steps to Reproduce
1. Login with valid credentials  
2. Add more than 5 employees  
3. Logout and login again  
4. Add a new employee  

### Actual Result
- New employee is not added at the end of the table  

### Expected Result
- New employee should be appended at the end of the table  

---

## Defect 7: Employee Update – No confirmation message displayed

### Description
No confirmation message is displayed after updating an employee.

### Steps to Reproduce
1. Login with valid credentials  
2. Add a new employee  
3. Close and reopen the employee list  
4. Edit the employee and save changes  

### Actual Result
- No update confirmation message appears  

### Expected Result
- A success/update message should be displayed  

---

## Defect 8: UI Layout – Dependents label misalignment

### Description
The "Dependents" label breaks the layout when maximum input length is used.

### Steps to Reproduce
1. Login with valid credentials  
2. Add a new employee  
3. Enter maximum allowed characters in input fields  

### Actual Result
- "Dependents" label overflows or becomes misaligned  

### Expected Result
- UI should remain aligned and responsive  

---
