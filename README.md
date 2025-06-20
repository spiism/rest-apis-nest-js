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

### Running Docker in Dev
`docker-compose --profile dev up -d`

Server will be running at:
http://localhost:3000

### Running Docker in Prod
`docker-compose --profile prod up -d --build`

Server will be running at:
http://localhost:8080

## 📘 API Endpoints
### 🔖 Books

#### ➕ Create a New Book
POST /book/new
> **Note:** This route is protected by `@UseGuards(AuthGuard())`. You **must** provide a valid JWT token in the `Authorization` header to access it.

Creates a new book entry.
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
> **Note:** This route is protected by `@UseGuards(AuthGuard())`. You **must** provide a valid JWT token in the `Authorization` header to access it.

Update a book’s information.
Request Body Example:
`{
  "title": "yay"
}`
Example:
`PUT /books/674268d9afcc75a61752eea5`


#### ❌ Delete a Book
DELETE /books/:id
> **Note:** This route is protected by `@UseGuards(AuthGuard())`. You **must** provide a valid JWT token in the `Authorization` header to access it.

Deletes a book by its ID.
Example:
`DELETE /books/674268d9afcc75a61752eea5`


#### ✏️ Upload image files to a Book
PUT /books/upload/:id

This endpoint allows you to upload one or more image files to a specific book by its ID.

Path Parameters:
:id — The ID of the book you want to upload images to.

Request Body:
- Content-Type: multipart/form-data
- Field name: files
- Type: File  (supports multiple files from the backend)

Example Request:
`PUT /books/upload/674544c86a7cce6efae49876`
Form Data:
- Key:    files
- Value:  [Choose file(s)]


### 👤 Authentication
#### 📝 Sign Up
POST /auth/signup
Registers a new user.
Request Body:
```json
{
  "name": "michael",
  "email": "michael@gmail.com",
  "password": "T9v#zLq3!mB@X1eF"
}
```

#### 📝 Sign Up with role
POST /auth/signup
Registers a new user.


> ⚠️ **Note:** The `role` field is only allowed during testing or development to create the initial admin user.  
> In production, role assignment should be restricted and handled by authorized admin users only.
> 
Request Body:
```json
{
  "name": "michael_admin",
  "email": "michael_admin@gmail.com",
  "password": "T9v#zLq3!mB@X1eF",
  "role": ["user", "admin"]
}
```


#### 🔐 Log In
POST /auth/login
Authenticates a user.
Request Body:
```json
{
  "email": "michael@gmail.com",
  "password": "T9v#zLq3!mB@X1eF"
}
```





