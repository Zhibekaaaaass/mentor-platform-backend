# mentor-platform-backend
```markdown
#  Mentor Request Platform — Backend (Node.js + MySQL)

## 📌 Project Overview

This is the backend for a **Mentor Matching Platform** where students (mentees) can browse mentor-led projects and submit applications. Mentors receive applications via email and can manage incoming requests. The system supports **role-based authentication**, project management, and real-time notifications.

---

##  Tech Stack

- **Backend:** Node.js + Express
- **Database:** MySQL + Sequelize ORM
- **Authentication:** JWT (JSON Web Token)
- **Password Security:** bcrypt.js
- **Email Notifications:** Nodemailer (via Gmail)
- **Frontend:** React (separate repo or `/frontend` folder)

---

##  Features

- ✅ JWT-based user authentication
- ✅ Role-based access: `mentor` and `mentee`
- ✅ User registration and login
- ✅ Mentor projects listing with filtering
- ✅ Request form submission via email
- ✅ Database persistence for requests
- ✅ Viewing user’s own submitted requests
- ✅ Responsive frontend integration
- ✅ Input validation and error handling

---

##  Folder Structure

```

mentor-platform/
├── backend/
│   ├── models/       # Sequelize models (User, Project, Request)
│   ├── routes/       # Auth, Projects, Requests
│   ├── middleware/   # JWT auth middleware
│   ├── utils/        # Email sending via nodemailer
│   └── server.js     # Entry point
├── frontend/         # React client
├── .env.example      # Environment variable template
├── README.md         # This file

```

---

##  API Endpoints

| Method | Endpoint               | Description                          |
|--------|------------------------|--------------------------------------|
| POST   | `/api/auth/register`   | Register a new mentee                |
| POST   | `/api/auth/login`      | Login and receive JWT token          |
| GET    | `/api/projects`        | Get all available projects           |
| GET    | `/api/projects/:id`    | Get detailed project info            |
| POST   | `/api/requests`        | Submit a request to a mentor         |
| GET    | `/api/requests/my`     | View own submitted requests (mentee) |

---

##  Authentication

- All protected routes require a valid JWT token via `x-auth-token` header.
- Middleware `auth.js` decodes token and attaches `req.user`.
- Only mentees can submit requests.
- Passwords are hashed with `bcrypt`.

---

##  Email Notifications

Upon request submission:
- The mentor's email is fetched using `mentorId` from the project.
- A formatted email is sent to the mentor containing:
  - Student’s name
  - Email
  - Phone (optional)
  - Custom message

---

## 🛠 .env Configuration

Create a `.env` file in the `backend` folder based on `.env.example`:

```

PORT=5000
JWT\_SECRET=your\_jwt\_secret\_key
EMAIL\_USER=[your\_gmail@gmail.com](mailto:your_gmail@gmail.com)
EMAIL\_PASS=your\_gmail\_app\_password

````

 **Use App Passwords for Gmail** — not your real password.

---

##  Running Locally

```bash
# Backend
cd backend
npm install
npm start

# Frontend 
cd frontend
npm install
npm start
````

Ensure that MySQL server is running and your database is correctly configured in `backend/config/db.js`.

---

##  Implemented Improvements

| #  | Improvement                                     | Status |
| -- | ----------------------------------------------- | ------ |
| 1  | JWT auth and token verification                 | ✅ Done |
| 2  | Password encryption with bcrypt.js              | ✅ Done |
| 3  | Nodemailer email sending to mentors             | ✅ Done |
| 4  | Filtering projects by tag or name               | ✅ Done |
| 5  | Sequelize associations for User-Project-Request | ✅ Done |
| 6  | Mentee's own request history page               | ✅ Done |
| 7  | Separate request form component                 | ✅ Done |
| 8  | Responsive design and error handling            | ✅ Done |
| 9  | Protected routes using middleware               | ✅ Done |
| 10 | Project details page with dynamic request link  | ✅ Done |

---

##  Project Status

> ✅ **MVP Ready** for final evaluation.
> All 10 planned improvements implemented.
> Clean codebase with clear separation of concerns.

---


##  License

MIT — free to use and modify

```
