# Task Manager REST API with Authentication

A simple but solid REST API built with Node.js, Express, and MongoDB. It lets users register, log in, and manage their own tasks — nothing fancy, just clean and functional.

---

## What it does

- Users can create an account and log in
- Passwords are hashed (no plain text storage)
- Login returns a JWT token that's used to access protected routes
- Each user can only see and manage their own tasks
- Tasks can be created, fetched, and deleted

---

## Tech Stack

- **Node.js** + **Express** — server and routing
- **MongoDB** + **Mongoose** — database
- **bcryptjs** — password hashing
- **jsonwebtoken** — authentication
- **Jest** + **Supertest** — testing

---

## Getting Started

### 1. Clone the repo

```bash
git clone https://github.com/yourusername/task-manager-rest-api.git
cd task-manager-rest-api
```

### 2. Install dependencies

```bash
npm install
```

### 3. Set up your environment variables

Create a `.env` file in the root of the project:

```env
PORT=5000
MONGO_URI=your_mongodb_connection_string
JWT_SECRET=your_jwt_secret
```

If you want to run tests, also create a `.env.test` file:

```env
MONGO_URI=your_test_mongodb_connection_string
JWT_SECRET=your_jwt_secret
```

> Use a separate database for testing so your real data doesn't get wiped.

---

## Running the server

```bash
# Development (with auto-restart)
npm run dev

# Production
npm start
```

---

## Running the tests

```bash
npm test
```

Tests cover user registration, login, and all task routes. They run sequentially and clean up after themselves.

---

## API Endpoints

### Auth

| Method | Endpoint | Description |
|--------|------------------|----------------------|
| POST | `/api/auth/register` | Register a new user |
| POST | `/api/auth/login` | Log in and get a token |

### Tasks (requires Authorization header)

| Method | Endpoint | Description |
|--------|-----------------|----------------------|
| GET | `/api/tasks` | Get all your tasks |
| POST | `/api/tasks` | Create a new task |
| DELETE | `/api/tasks/:id` | Delete a task |

For protected routes, pass your token in the request header:

```
Authorization: Bearer your_token_here
```

---

## Project Structure

```
├── src/
│   ├── app.js
│   ├── models/
│   │   ├── User.js
│   │   └── Task.js
│   ├── routes/
│   │   ├── authRoutes.js
│   │   └── taskRoutes.js
│   └── middleware/
│       └── authMiddleware.js
├── tests/
│   ├── auth.test.js
│   ├── tasks.test.js
│   └── setup.js
├── .env.example
├── .gitignore
├── package.json
└── server.js
```

---

## Notes

- Make sure your MongoDB instance is running before starting the server or running tests
- The `.env` and `.env.test` files are intentionally not included in the repo — check `.env.example` for the variables you need
