## API Selection 

**API Chosen:** Cat Facts (https://alexwohlbruck.github.io/cat-facts/)

**Purpose:** The purpose of Cat Facts API, it is a free public API that returns short facts about cats as JSON.

**Suitable:** This API is suitable because it is free and does not need a API key. It is a simple REST API that returns JSON over GET. Each fact has fields that are easy to shoe in a list and to use. The parameters animal_type and amount give me something to build around.

**Rest Principles:** 

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
**Fetch API usage:** 



---
## Form Handling 

---
## Technology Stack

---
## Implementation Steps 

---
