## A) Setup Instructions
**Requirements**
- Postman
- A valid API key from https://crudcrud.com
- Files:
  - `Task 2.postman_collection.json` – the postman collection
  - `employee_data.csv` – the data file for iteration


## B) How to Run the Tests
**Step 1: Import the Collection**
- Open Postman
- Click "Import" and select `Task 2.postman_collection.json`

**Step 2: Update the unique_id Variable**
- Go to the collection "Task 2" > Variables
- Replace the value of the collection variable unique_id with your token from https://crudcrud.com
  - For example: unique_id = 0b968acc306940968b383df8655c8301
  - The full base URL would be: {{base_url}}{{unique_id}} -> https://crudcrud.com/api/0b968acc306940968b383df8655c8301
    
**Step 3: Run the Collection**
- Go to the collection "Task 2"
- Click "Run"
- Select the run sequence
- Upload the csv file through "Test data file"
- Enter a valide iteration number e.g. 2
- Click "Run Task 2"


## C) Design & Approach
**Design Highlights**
- Variables at collection level – no environment needed
- Data-driven tests – using CSV with fields like {{firstName}}, {{email}}, etc.
- Dynamic chaining – employeeId is extracted on POST and reused in GET/PUT/DELETE
- Schema validation – inline schema to verify structure of created employee
- Negative tests – invalid ID, missing fields, incorrect methods or path usage
- Error handling – handling of 400/404/415/405 status codes
- Debugging support – console.log() to inspect payloads

**Test Cases Included**
| Request Name  | Method | Test Type |
| ------------- | ------------- | ------------- |
| Create employee without payload  | POST  | ❌ Negative  |
| Create employee  | POST  | ✅ Positive  |
| Get invalid employee  | Get  | ❌ Negative  |
| Get employee  | Get  | ✅ Positive |
| Update employee with space in path param | PUT  | ❌ Negative |
| Update employee  | PUT  | ✅ Positive  |
| Get updated employee  | GET  | ✅ Validation  |
| Delete employee with missing ID  | DELETE  | ❌ Negative  |
| Delete employee  | DELETE  | ✅ Positive  |
| Get deleted employee  | GET  | ❌ Negative  |


## D) Known Limitations & Areas for Improvement
| Area | Note |
| --- | --- |
| API schema enforcement | crudcrud.com doesn't validate input schemas |
| Token expiry | API key from crudcrud.com is only valid for 24 hours |
| No auth layer | Real-world API scenarios would include token-based auth |
| Business requirement | Real-world API scenarios would introduce more rules on top of the API contract (e.g. dynamic field attribute, dependency) |
| Load testing | 	This suite focuses on functional checks, not performance |
| Reporting | Generate execution reports (e.g. via Newman) |
