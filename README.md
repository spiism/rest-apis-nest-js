📚NestJS Backend
---

### Installation
Clone the repository and install dependencies:

`npm install`

### Running the Server
`npm run start:dev`

Server will be running at:
http://localhost:3000

# 📘 API Endpoints
## 🔖 Books

#### ➕ Create a New Book
POST /book/new

Creates a new book entry.
Request Body:

``{
"title": "Book 1",
"description": "Book 1 Des",
"author": "Author 1",
"price": 100,
"category": "Adventure"
}``


#### 📚 Get All Books
GET /book
Returns a list of all books.


#### 📄 Get Paginated Books
GET /books?page=2
Returns books from page 2. Adjust the page number as needed.


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


## 👤 Authentication
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





