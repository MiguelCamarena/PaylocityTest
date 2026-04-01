# API Defects Report

---

## API-01: DELETE – Deleting the same resource twice returns incorrect status

### Description
The DELETE endpoint does not validate whether the resource exists before attempting deletion.

### Steps to Reproduce
1. Delete an existing employee using:
   DELETE /api/Employees/{id}
2. Repeat the DELETE request with the same ID

### Actual Result
- API returns 200 OK

### Expected Result
- API should return 404 Not Found for a non-existing resource

---

## API-02: GET – Using deleted ID still returns 200

### Description
The API allows retrieval of a deleted resource and still returns a success response.

### Steps to Reproduce
1. Delete an employee
2. Perform GET using the same ID

### Actual Result
- API returns 200 OK

### Expected Result
- API should return 404 Not Found

---

## API-03: PUT – Endpoint is not REST compliant

### Description
The PUT endpoint does not follow RESTful design principles because it does not include the resource identifier in the URL.

### Steps to Reproduce
1. Send a PUT request to:
   PUT /api/Employees
2. Include employee ID in the request body

### Actual Result
- The endpoint updates the resource without specifying the ID in the URL
- The resource being updated is ambiguous

### Expected Result
- Endpoint should follow REST standards:
  PUT /api/Employees/{id}
- Resource must be explicitly defined in the path

---

## POSSIBLE ISSUE API-04: Employee salary can be modified without business validation

### Description
The API allows modifying the salary field without enforcing business rules.

### Steps to Reproduce
1. Create or update an employee
2. Set salary to any arbitrary value

### Actual Result
- Salary accepts any value

### Expected Result
- Salary should follow business rules or be restricted
- Validation should be enforced

---

## POSSIBLE ISSUE API-05: CORS misconfiguration 

### Description
The API appears to have CORS configuration issues, preventing requests from browser-based tools such as Swagger UI.

### Steps to Reproduce
1. Open Swagger UI or browser client
2. Execute any request

### Actual Result
- Requests fail with “Failed to fetch”
- Cross-origin requests are blocked

### Expected Result
- Proper CORS headers should be configured (e.g., Access-Control-Allow-Origin)
- Requests should be allowed from valid clients

---

## API-06: Missing response contract in Swagger

### Description
The API specification does not define response schemas.

### Steps to Reproduce
1. Open Swagger documentation
2. Inspect any endpoint response definition

### Actual Result
- Response only shows:
  "200": { "description": "Success" }

### Expected Result
- API should define full response schema including:
  - Fields
  - Data types
  - Required attributes

---

## API-07: Dependants field accepts invalid data type

### Description
The API accepts a string value for the dependants field, even though it is defined as an integer.

### Steps to Reproduce
1. Send a POST or PUT request to /api/Employees
2. Use this payload:

{
  "firstName": "Test",
  "lastName": "User",
  "username": "testuser",
  "dependants": "5"
}

### Actual Result
- Request is accepted
- API processes "5" as valid input

### Expected Result
- API should reject the request
- Return 400 Bad Request
- Validation error indicating invalid data type

---
