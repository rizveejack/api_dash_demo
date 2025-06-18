
# 🧠 Simple Login/Register — Backend Setup

This is the backend service for the Simple Login/Register. It handles user authentication, and protected connects to a PostgreSQL database — all managed using Docker and Docker Compose.

---

## 📦 Prerequisites

Make sure you have the following installed:

- [Docker](https://docs.docker.com/get-docker/)
- [Docker Compose](https://docs.docker.com/compose/)

---

## ⚙️ Installation & Setup

### ✅ 1. Install Docker

If Docker is not installed on your system, follow the installation guide:

👉 https://docs.docker.com/get-docker/

---

### 🔍 2. Check Docker Installation

Verify Docker is installed correctly:

```bash
docker --version
```

Expected output:

```bash
Docker version 24.0.2, build cb74dfc
```

---

### 🚀 3. Run Docker Compose

Use the following command to build and run all services:

```bash
docker compose up --build
```

Or To run in the background (detached mode):

```bash
docker compose up -d --build
```

This will:

- Start the API server on `http://localhost:5000`
- Set up PostgreSQL database
- Launch Adminer UI at `http://localhost:5000/db`

---

## 🔌 API Endpoints

Base URL: `http://localhost:5000`

---

### ➕ Register

**POST** `/register`  
Create a new user.

```json
{
  "name": "Al kut",
  "email": "c@foo.bar",
  "password": "12345",
  "role": "USER"
}
```

---

### 🔐 Login

**POST** `/login`  
Log in with user credentials.

```json
{
  "email": "c@foo.bar",
  "password": "12345"
}
```

---

### 🚪 Logout

**POST** `/logout`  
Log out the currently authenticated user.

_No body required._

---

### 📊 Dashboard

**GET** `/dashboard`  
Returns user-specific dashboard data. May require authentication.

---

## 🔐 Using Axios with Session-based Authentication

Since this project uses **session-based login**, you must include `withCredentials: true` in your frontend HTTP requests. This ensures cookies (containing the session ID) are sent and received properly.

### ✅ Example: Axios Login Request

```js
import axios from 'axios';

axios.post('http://localhost:5000/login', {
  email: 'c@foo.bar',
  password: '12345'
}, {
  withCredentials: true // ⚠️ required for session to work
}).then(response => {
  console.log('Login successful:', response.data);
}).catch(error => {
  console.error('Login failed:', error.response.data);
});
```
---

## 🗄️ Database Admin Panel

You can visually inspect and interact with the database via Adminer.

- **URL:** [http://localhost:5000/db](http://localhost:5000/db)

### 🧾 Database Credentials

| Field       | Value       |
|-------------|-------------|
| **System**  | PostgreSQL  |
| **Server**  | `db`        |
| **Username**| `user`      |
| **Password**| `password`  |
| **Database**| `mydatabase`|

---

## 🛠️ Tech Stack

- **Backend:** Node.js, Express
- **ORM:** Prisma
- **Database:** PostgreSQL
- **Containerization:** Docker, Docker Compose
- **Admin Panel:** Adminer

---

## 📄 License

This project is licensed under the [MIT License](LICENSE).

Feel free to clone, modify, and use it in your own projects.

---