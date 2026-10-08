# API Test Cases

This section contains API testing practice completed using Postman and JSONPlaceholder.

## API Under Test

**API:** JSONPlaceholder  
**Base URL:** https://jsonplaceholder.typicode.com

## Test Coverage

### 1. Positive GET Request

**Endpoint:** `GET /users/1`

**Expected Result:**
- Status code is `200`
- Response contains the requested user
- User ID is `1`

**Result:** Passed

---

### 2. Negative GET Request

**Endpoint:** `GET /users/999`

**Expected Result:**
- Status code is `404`
- User does not exist

**Result:** Passed

---

### 3. Missing Fields — POST Request

**Endpoint:** `POST /posts`

**Test Data:**

```json
{
  "title": "QA Test"
}Observed Result:
- Status code: 201
- API returned the submitted title and generated an ID
QA Note: This behavior was documented as an observation because the practice API does not provide a strict contract requiring the other fields.
4. Invalid Data Type — POST Request
Endpoint: POST /posts
Test Data:
{
  "title": "QA Test",
  "body": "Testing invalid data type",
  "userId": "ABC"
}

Observed Result:
- Status code: 201
- API accepted the string value
QA Note: This was treated as a contract observation rather than a confirmed defect because JSONPlaceholder does not enforce a documented integer requirement for userId.
5. Boundary Testing
Valid Boundary:
GET /users/10
Expected:
- Status code 200
- User ID 10
Result: Passed
Outside Boundary:
GET /users/11
Expected:
- Status code 404
- User does not exist
Result: Passed
6. Response Validation
Endpoint: GET /users/1
Validated that the response:
- Returns status code 200
- Contains id
- Contains name
- Contains username
- Contains email
- Returns the user ID as a number
Result: Passed
7. Response Time Validation
Endpoint: GET /users/1
Assertion:
- Response time must be less than 1000ms
Observed response time: Approximately 19ms
Result: Passed
8. Content-Type Validation
Endpoint: GET /users/1
Assertion:
- Response Content-Type contains application/json
Result: Passed
9. POST Response Validation
Endpoint: POST /posts
Test Data:
{
  "title": "QA API Test",
  "body": "Testing POST response validation",
  "userId": 1
}

Expected Result:
- Status code 201
- Response contains a generated id
- Returned userId equals 1
Result: Passed
Postman Automation
Postman tests were created using JavaScript assertions.
Examples of validations included:
- HTTP status codes
- Response fields
- Data types
- Response time
- Content-Type
- POST response values
Collection Variables
The Postman collection uses variables to make requests reusable:
baseUrl = https://jsonplaceholder.typicode.com
userId = 1

Example request:
{{baseUrl}}/users/{{userId}}

Collection Runner
Selected API tests were executed using the Postman Collection Runner.
Latest practice run:
- 13 tests reported as passed
- 0 failed
- 0 skipped
- 0 errors
One request in the run had no assertions, so the 13 passed figure represents Postman's run/test presentation rather than 13 individual assertions.
