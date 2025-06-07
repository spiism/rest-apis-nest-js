# 📚NestJS Backend
---
## Installation & Running
### Installation
Clone the repository and install dependencies:

`npm install`

### Running the Server
`npm run start:dev`

Server will be running at:
http://localhost:3000

## 📘 API Endpoints
### 🔖 Books

#### ➕ Create a New Book
POST /book/new

Creates a new book entry.
**Note:** This route is protected by `@UseGuards(AuthGuard())`, so you **must** provide a valid JWT token in the Authorization header to access it.
Request Body:

```json
{
"title": "Book 1",
"description": "Book 1 Des",
"author": "Author 1",
"price": 100,
"category": "Adventure"
}
```


#### 📚 Get All Books
GET /book
Returns a list of all books.


#### 📄 Get Paginated Books
GET /books?page=2
Returns books from page 2. Adjust the page number as needed.

#### 📄 Get Paginated Books with Keyword Search
**GET** `/books?keyword=book 1&page=1`

Fetches books that match the keyword "book 1" and returns results from page 1.

- `keyword` (optional query param): Filter books by keyword in title, description, author, etc.
- `page` (optional query param): Page number for pagination (default is 1).

**Example Request:**
`GET http://localhost:3000/books?keyword=book%201&page=1`
**Response**
```json
[
  {
    "_id": "6744270f6f78877095d023a2",
    "title": "Book 1",
    "description": "Book 1 Des",
    "author": "Author 1",
    "price": 100,
    "category": "Advanture",
    "createdAt": "2024-11-25T07:28:15.481Z",
    "updatedAt": "2024-11-25T07:28:15.481Z",
    "__v": 0
  }
]
```

#### 📖 Get a Single Book by ID
GET /books/:id
Example:
`GET /books/674544cb6a7cce6efae4987855`

#### ✏️ Update a Book
PUT /books/:id
Update a book’s information.
Request Body Example:
`{
  "title": "yay"
}`
Example:
`PUT /books/674268d9afcc75a61752eea5`


#### ❌ Delete a Book
DELETE /books/:id
Deletes a book by its ID.
Example:
`DELETE /books/674268d9afcc75a61752eea5`


### 👤 Authentication
#### 📝 Sign Up
POST /auth/signup
Registers a new user.
Request Body:
`{
  "name": "michael",
  "email": "michael@gmail.com",
  "password": "123456"
}`


#### 🔐 Log In
POST /auth/login
Authenticates a user.
Request Body:
`{
  "email": "michael@gmail.com",
  "password": "123456"
}`





