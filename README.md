# FakeAPI

Read-only JSON datasets for frontend development, interface testing and prototypes. GitHub Pages serves each file directly.

## Interactive documentation

[Open Swagger UI](https://shardulaswale.github.io/FakeAPI/) to inspect endpoint schemas and execute GET requests using **Try it out**.

[Download the OpenAPI specification](https://shardulaswale.github.io/FakeAPI/openapi.json). Swagger UI assets use a pinned version from UNPKG.

## Server

Base URL: `https://shardulaswale.github.io/FakeAPI`

Authentication: None. Supported operation: `GET`.

## Endpoints

Each successful request returns a JSON object with a named array, for example `{ "products": [...] }`. Counts describe the current fixtures.

| Method | Path | Response array | Records |
| --- | --- | --- | --- |
| GET | [/users.json](https://shardulaswale.github.io/FakeAPI/users.json) | `users` | 20 |
| GET | [/products.json](https://shardulaswale.github.io/FakeAPI/products.json) | `products` | 30 |
| GET | [/categories.json](https://shardulaswale.github.io/FakeAPI/categories.json) | `categories` | 8 |
| GET | [/orders.json](https://shardulaswale.github.io/FakeAPI/orders.json) | `orders` | 30 |
| GET | [/carts.json](https://shardulaswale.github.io/FakeAPI/carts.json) | `carts` | 15 |
| GET | [/reviews.json](https://shardulaswale.github.io/FakeAPI/reviews.json) | `reviews` | 60 |
| GET | [/posts.json](https://shardulaswale.github.io/FakeAPI/posts.json) | `posts` | 30 |
| GET | [/comments.json](https://shardulaswale.github.io/FakeAPI/comments.json) | `comments` | 60 |
| GET | [/todos.json](https://shardulaswale.github.io/FakeAPI/todos.json) | `todos` | 200 |
| GET | [/employees.json](https://shardulaswale.github.io/FakeAPI/employees.json) | `employees` | 12 |
| GET | [/companies.json](https://shardulaswale.github.io/FakeAPI/companies.json) | `companies` | 6 |
| GET | [/contacts.json](https://shardulaswale.github.io/FakeAPI/contacts.json) | `contacts` | 20 |
| GET | [/addresses.json](https://shardulaswale.github.io/FakeAPI/addresses.json) | `addresses` | 20 |
| GET | [/notifications.json](https://shardulaswale.github.io/FakeAPI/notifications.json) | `notifications` | 40 |
| GET | [/messages.json](https://shardulaswale.github.io/FakeAPI/messages.json) | `messages` | 40 |
| GET | [/events.json](https://shardulaswale.github.io/FakeAPI/events.json) | `events` | 15 |
| GET | [/jobs.json](https://shardulaswale.github.io/FakeAPI/jobs.json) | `jobs` | 18 |
| GET | [/transactions.json](https://shardulaswale.github.io/FakeAPI/transactions.json) | `transactions` | 24 |
| GET | [/tickets.json](https://shardulaswale.github.io/FakeAPI/tickets.json) | `tickets` | 20 |
| GET | [/movies.json](https://shardulaswale.github.io/FakeAPI/movies.json) | `movies` | 15 |
| GET | [/recipes.json](https://shardulaswale.github.io/FakeAPI/recipes.json) | `recipes` | 10 |
| GET | [/weather.json](https://shardulaswale.github.io/FakeAPI/weather.json) | `weather` | 10 |

## Response fields

| Resource | Fields |
| --- | --- |
| `users` | `id`, `name`, `email`, `avatar`, `role` |
| `products` | `id`, `title`, `price`, `currency`, `category`, `categoryId`, `images`, `stock`, `rating` |
| `categories` | `id`, `name`, `slug`, `parentId` |
| `orders` | `id`, `userId`, `items`, `total`, `currency`, `status`, `createdAt` |
| `carts` | `id`, `userId`, `items`, `quantity`, `total`, `currency` |
| `reviews` | `id`, `productId`, `userId`, `rating`, `comment` |
| `posts` | `id`, `userId`, `title`, `body`, `tags`, `createdAt` |
| `comments` | `id`, `postId`, `userId`, `body`, `createdAt` |
| `todos` | id, userId, title, completed |
| `employees` | `id`, `name`, `department`, `jobTitle`, `managerId` |
| `companies` | `id`, `name`, `industry`, `website`, `address` |
| `contacts` | `id`, `name`, `email`, `phone`, `companyId` |
| `addresses` | `id`, `userId`, `street`, `city`, `postcode`, `country` |
| `notifications` | `id`, `userId`, `title`, `message`, `read`, `createdAt` |
| `messages` | `id`, `senderId`, `receiverId`, `body`, `sentAt` |
| `events` | `id`, `title`, `startAt`, `endAt`, `location` |
| `jobs` | `id`, `companyId`, `title`, `location`, `salary`, `skills` |
| `transactions` | `id`, `userId`, `orderId`, `amount`, `currency`, `type`, `status`, `createdAt` |
| `tickets` | `id`, `userId`, `subject`, `priority`, `status` |
| `movies` | `id`, `title`, `genres`, `year`, `poster`, `rating` |
| `recipes` | `id`, `title`, `ingredients`, `steps`, `prepMinutes`, `cookMinutes`, `servings` |
| `weather` | `city`, `temperature`, `temperatureUnit`, `humidity`, `condition`, `observedAt` |

Identifiers and quantities are integers. Prices, amounts and ratings are numbers. Flags such as `completed` and `read` are booleans. Dates use ISO 8601 UTC strings. Money uses GBP. Ratings use a 1–5 scale for products and reviews, and a 1–10 scale for movies.

### Nested objects

| Field | Structure |
| --- | --- |
| `orders[].items[]`, `carts[].items[]` | `productId`, `quantity`, `unitPrice` |
| `companies[].address` | `street`, `city`, `postcode`, `country` |
| `jobs[].salary` | `min`, `max`, `currency`, `period` |
| `products[].images` | Array of image URL strings. |
| `posts[].tags`, `jobs[].skills`, `movies[].genres` | Arrays of strings. |
| `recipes[].ingredients`, `recipes[].steps` | Arrays of strings. |

`parentId` and `managerId` are `null` for top-level categories and the top-level employee. Cart `quantity` is the sum of item quantities; order and cart `total` is the sum of quantity multiplied by unit price.

## Example response

`GET /users.json` returns `200 OK`. Shortened example:

```json
{
  "users": [
    {
      "id": 1,
      "name": "Alex Morgan",
      "email": "user1@example.com",
      "avatar": "https://picsum.photos/seed/fakeapi-avatar-1/640/480",
      "role": "admin"
    }
  ]
}
```

## Request examples

### cURL

```sh
curl https://shardulaswale.github.io/FakeAPI/products.json
```

### JavaScript

```js
const baseUrl = "https://shardulaswale.github.io/FakeAPI";
const response = await fetch(`${baseUrl}/products.json`);

if (!response.ok) {
  throw new Error(`Request failed: ${response.status}`);
}

const { products } = await response.json();
const inStock = products.filter(product => product.stock > 0);
console.log(inStock);
```

## Relationships

- `userId`, `senderId` and `receiverId` refer to `users[].id`.
- `productId` refers to `products[].id`; `categoryId` refers to `categories[].id`.
- `postId` refers to `posts[].id`; `companyId` refers to `companies[].id`.
- `orderId` refers to `orders[].id`.
- `managerId` refers to `employees[].id`; `parentId` refers to `categories[].id`.

Load the related files and join or filter their arrays in your application.

## Behaviour and data notes

- Files are static. POST, PUT, PATCH and DELETE are not supported.
- Query parameters do not provide server-side filtering or pagination. Individual-record routes are not implemented.
- Unknown file paths return a GitHub Pages 404 page rather than a JSON error object.
- The added records are fictional fixtures. Weather is a fixed sample, not live observations; jobs, events and transactions are not real listings or activity.
- Email and company website fields use example domains. Phone fields use UK numbers reserved for fictional use.
- Image URLs provide generic placeholders through Picsum; they do not depict the named people, products or movies.
- The existing 200-record todo dataset is preserved.
- The site root serves interactive Swagger UI. Each dataset remains available at its direct JSON URL.

## Deployment

Publish the `main` branch from the repository root through GitHub Pages. JSON files remain accessible at their direct `.json` URLs when a README is present. Commit fixture changes and allow the Pages deployment to complete.

## Adding endpoints

Add the JSON file, then describe its GET path and response schema in `openapi.json`. Swagger UI reads the specification; new files are not discovered automatically.
