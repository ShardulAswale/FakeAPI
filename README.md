# FakeAPI

Static JSON data for frontend development, prototypes and HTTP fetch examples. GitHub Pages serves the files directly.

## Server

Base URL: `https://shardulaswale.github.io/FakeAPI`

No authentication is required.

## Endpoints

| Method | Path | Description |
| --- | --- | --- |
| GET | [/todos.json](https://shardulaswale.github.io/FakeAPI/todos.json) | Retrieve all 200 todo records. |

### GET /todos.json

**Parameters:** None.

**Successful response:** `200 OK`, JSON object containing a `todos` array.

Response example, shortened to one record:

```json
{
  "todos": [
    {
      "userId": 1,
      "id": 1,
      "title": "delectus aut autem",
      "completed": false
    }
  ]
}
```

### Response schema

| Field | Type | Description |
| --- | --- | --- |
| todos | array of Todo | Complete todo collection. |
| todos[].id | integer | Todo identifier. |
| todos[].userId | integer | User identifier associated with the todo. |
| todos[].title | string | Task description. |
| todos[].completed | boolean | Whether the task is complete. |

## Request examples

### cURL

```sh
curl https://shardulaswale.github.io/FakeAPI/todos.json
```

### JavaScript

```js
const response = await fetch(
  "https://shardulaswale.github.io/FakeAPI/todos.json"
);

if (!response.ok) {
  throw new Error(`Request failed: ${response.status}`);
}

const { todos } = await response.json();
console.log(todos);
```

## Behaviour

- Read-only static data; POST, PUT, PATCH and DELETE operations are not supported.
- No server-side filtering, pagination or individual-record routes. Filter the downloaded array in your application.
- Unknown file paths return a GitHub Pages 404 page, not a JSON error response.
- Dataset changes are made by committing the JSON file and allowing GitHub Pages to redeploy.
- This README documents the endpoints. It does not provide interactive Swagger UI.

## Deployment

Publish the `main` branch from the repository root through GitHub Pages. Data remains accessible at its direct `.json` URL when a README is present.
