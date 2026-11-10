## API Selection 

**API Chosen:** Cat Facts (https://alexwohlbruck.github.io/cat-facts/)

**Purpose:** The purpose of Cat Facts API, it is a free public API that returns short facts about cats as JSON.

**Suitable:** This API is suitable because it is free and does not need a API key. It is a simple REST API that returns JSON over GET. Each fact has fields that are easy to shoe in a list and to use. The parameters animal_type and amount give me something to build around.

**Rest Principles:** Each fact is a resource with its own URL. /facts/{factID} is a resource identification. It will only read data from the public API so it only needs the standard GET method. The API is stateless because every request has everything the server needs. The server also does not remember earlier requests. 

---

## Endpoint Mapping 
**Public API:** 

| Verb | Endpoint       | Accepts     | Returns |
|------|----------------|-------------|----------|
| GET  | /facts/random  | animal_type | One fact object, or a list of fact objects |
| GET  | /facts/{factID}| Fact ID in the path | One fact object|

**My Flask backend:** 

| Verb | Endpoint       | Accepts     | Returns |
|------|----------------|-------------|----------|
| GET  | /api/data  | Query: animal_type, amount | JSON list of facts or JSON error |
| POST  | /api/submit | JSON body with form data | JSON confirmation or JSON error |

This follows REST because the URLs name resources instead of actions, and the HTTP verb says what the request does: GET reads data and POST sends new data. Each request is stateless, because the query string or JSON body has everything Flask needs and no session is stored between requests. Responses are returned as JSON with status codes (200, 201, 400, 503) so you can react to the result.

---
## Data Flow Diagram (textual)

```
User open page then click "load facts"
              |
Broswer JS:  fetch GET /api/data?animal_type=cat&amount=5
              |
Flask: requests.get(Cat Facts API /facts/random?)
              |
Cat facts API returns JSON
              |
Flask: checks for errors, returns JSON list (jsonify)
              |
Browser JS: parses JSON, builds list/table rows, adds CSS classes
              |
User sees facts
```
**Fetch API usage:** The page uses asynchronous GET with fetch like async/await. The request header is Accept: application/json. I will check response.ok since fetch does not fail on 4xx or 5xx by itself, then I will call response.json().

**Loading state:** 

**Error handling:**

**Dynamic rendering:**

**Conditional styling:**

---

## Form Handling 

**Fetch API usage:** 

| Field | Control       | Validation     | 
|------|----------------|-------------|
|amount   |Number input   |Required, Number 1-20   | 
|fact_id   |Hidden input   |Required, not empty   | 
|rating   |Radio button 1-5   |Required, one choice only   | 

If validation fails, the page will show a message next to the field and will not send the request.

**Turning the form into JSON:** When a user submits the form, the page will ready the values and build a JSON object with the field names fact_id and rating. The object is then sent to the body of a POST request.

---
## Technology Stack 
The backend is written inside a virtual environment like venv. I will use Flask to build the backend and serve the page with jsonify and request. Also use the request library so the Flask app can call Cat Facts API. The front end will be plain HTML and CSS using fetch. To test the I will use my browser and curl to try GET and POST. Github will be used to store my code and plan.

---
## Implementation Steps 

---
