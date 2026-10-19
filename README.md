<div align="center">

# 📋 Smart Workflow & Task Organizer API

**A REST API for project management: create projects, add and assign tasks, and track their status. Built with Express, Prisma and PostgreSQL.**

![Node.js](https://img.shields.io/badge/Node.js-339933?logo=nodedotjs&logoColor=white)
![Express](https://img.shields.io/badge/Express-000000?logo=express&logoColor=white)
![Prisma](https://img.shields.io/badge/Prisma-2D3748?logo=prisma&logoColor=white)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4169E1?logo=postgresql&logoColor=white)
![JWT](https://img.shields.io/badge/JWT-auth-000000?logo=jsonwebtokens&logoColor=white)

</div>

---

## ✨ Features

- **Users**: register and log in (JWT, bcrypt), plus list, update and delete
- **Projects**: create, list, get and delete, with status `PLANNED` · `ONGOING` · `COMPLETED`
- **Tasks**:
  - Add tasks to a project and assign them to a user
  - Update and delete tasks
  - Status: `TODO` · `IN_PROGRESS` · `DONE`
- **Filtering**: list tasks by `status` and/or `assignedUserId`
- **Type-safe database access** with the Prisma ORM, UUID primary keys and versioned **migrations**
- Request logging with **morgan**, plus CORS

## 🗃️ Data model

```mermaid
erDiagram
    USER ||--o{ PROJECT : owns
    PROJECT ||--o{ TASK : contains
    USER ||--o{ TASK : "assigned to"
    PROJECT { string name string description Status status }
    TASK { string title string description TaskStatus status }
```

## 📡 API

| Method | Endpoint | Description |
|:---:|---|---|
| `POST` | `/users/register` · `/users/login` | Auth |
| `GET` · `PUT` · `DELETE` | `/users` · `/users/:id` | Manage users |
| `POST` · `GET` | `/projects` | Create or list projects |
| `GET` · `DELETE` | `/projects/:id` | Get or delete a project |
| `POST` · `GET` | `/projects/:projectId/tasks` | Add or list a project's tasks |
| `PUT` · `DELETE` | `/tasks/:taskId` | Update or delete a task |
| `GET` | `/tasks?status=TODO&assignedUserId=<uuid>` | Filter tasks |

Protected routes expect `Authorization: Bearer <token>`.

## 🚀 Run locally

```bash
git clone https://github.com/mayurvij22/Smart-Workflow-and-Task-Organizer.git
cd Smart-Workflow-and-Task-Organizer
npm install
```

`.env`:

```env
DATABASE_URL=postgresql://user:password@localhost:5432/taskmanager
JWT_SECRET=a-long-random-string
PORT=3000
```

```bash
npx prisma migrate deploy   # create tables
npm start
```

## 🛠️ Tech stack

Node.js · Express · Prisma ORM · PostgreSQL · JWT · bcryptjs · morgan

---

<div align="center">

Made by **[Mayur Patil](https://github.com/mayurvij22)**

</div>
