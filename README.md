# Contact Manager API

A simple RESTful Express API for managing user contacts with authentication (JWT).

## Project Overview
- Backend API built with Node.js, Express and MongoDB.
- Supports user registration and login, and CRUD operations for contacts.

## Tech Stack
- Node.js
- Express
- MongoDB/ Mongoose
- JWT
- bcrypt
- Nodemon
- dotenv

Utilities / Supporting Libraries
- express-async-handler - simplifies async route error handling

## Features
- Secure authentication with JWT
- Protected API routes
- CRUD operations
- Custom error handler
- Modular code structure (controllers, routes, middleware)
- Environment variable management
- MongoDB schema validation

## Repository Structure
- `server.js` — application entry point
- `config/` — `dbConnection.js` (database connection)
- `controllers/` — `contactController.js`, `userController.js`
- `models/` — `contactModel.js`, `userModel.js`
- `routes/` — `contactRoutes.js`, `userRoutes.js`
- `middleware/` — `errorHandler.js`, `validateTokenHandler.js`
- `constants.js` — shared status codes

## Prerequisites
- Node.js (14+ recommended)
- npm
- MongoDB (local or Atlas)

Environment variables
Create a `.env` file in the project root with these variables:

```
CONNECTION_STRING=your_mongo_connection_string
ACCESS_TOKEN_SECRET=your_jwt_secret
PORT=5000
```

## Installation

Open PowerShell in the project folder and run:

```powershell
npm install
```

**Running**

Start in production:

```powershell
node server.js
```

Start in development (live reload):

```powershell
npx nodemon server.js
```

Server will run by default on `http://localhost:5000` unless `PORT` is set.

## API Endpoints (summary)

- **Authentication** (`/api/users`)
	- `POST /api/users/register` — Register a new user. Body: `{ name, email, password }`.
	- `POST /api/users/login` — Login and receive a JWT. Body: `{ email, password }`.

- **Contacts** (`/api/contacts`) — Protected endpoints (require `Authorization: Bearer <token>`)
	- `GET /api/contacts` — List contacts for the authenticated user.
	- `POST /api/contacts` — Create a new contact. Example body: `{ name, email, phone, type }`.
	- `GET /api/contacts/:id` — Get a single contact by id.
	- `PUT /api/contacts/:id` — Update a contact by id.
	- `DELETE /api/contacts/:id` — Delete a contact by id.


## Authentication
- The app uses JWT tokens. Include the token in requests as an `Authorization` header:

```
Authorization: Bearer <token>
```

## Database
- MongoDB connection is handled in `config/dbConnection.js`. Make sure `CONNECTION_STRING` in `.env` is correct.

## Error handling
- Centralized error handling is provided by `middleware/errorHandler.js` and status constants are available in `constants.js`.

## Development tips
- Use Postman or Insomnia to test endpoints.
- Use `npx nodemon server.js` for automatic restarts during development.