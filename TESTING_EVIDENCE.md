# RESTful API Testing Evidence

**Testing Client:** Postman
**Base URL:** `http://localhost:3000`

### 1. GET /api/resources (Initial State)
* **Method:** GET
* **Endpoint:** `/api/resources`
* **Status Return:** 200 OK
* **Expected Result:** Returned the initial in-memory JSON array of tracked elements, verifying the dataset containing `id: 1` ("Test Task") and `id: 2` ("Code Structure Review").

### 2. GET /api/resources/:id
* **Method:** GET
* **Endpoint:** `/api/resources/1`
* **Status Return:** 200 OK 
* **Expected Result:** Successfully isolated and returned the single JSON object for ID 1.

### 3. POST /api/resources
* **Method:** POST
* **Endpoint:** `/api/resources`
* **Payload:** `{ "name": "New Test Item", "status": "Pending" }`
* **Status Return:** 201 Created
* **Expected Result:** Appended a unique tracking ID (`id: 3`) and returned the newly created object.

### 4. PUT /api/resources/:id
* **Method:** PUT
* **Endpoint:** `/api/resources/1`
* **Payload:** `{ "name": "Refactored Task", "status": "Completed" }`
* **Status Return:** 200 OK
* **Expected Result:** Safely overwrote the specific fields for `id: 1` and returned the updated object.

### 5. DELETE /api/resources/:id
* **Method:** DELETE
* **Endpoint:** `/api/resources/2`
* **Status Return:** 200 OK
* **Expected Result:** Successfully spliced the target item out of the tracking array and returned the confirmation message `"Resource 2 successfully deleted."`.

### 6. GET /api/resources (Checking Changes)
* **Method:** GET
* **Endpoint:** `/api/resources`
* **Status Return:** 200 OK
* **Expected Result:** Returned the modified in-memory JSON array, confirming that `id: 1` was updated, `id: 2` was deleted, and `id: 3` was added.