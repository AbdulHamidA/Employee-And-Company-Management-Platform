
# 🧾 Employee & Company Management System - Detailed Specification

## 🎯 Purpose

A full-stack web application to:
- Manage employee data (personal, legal, professional)
- Handle company records
- Rent (assign) employees to companies
- Support CV uploads per employee
- Bulk employee creation
- Provide filtered & searchable views for management

---

## 🧱 Technology Stack

| Layer           | Stack                                      |
|------------------|---------------------------------------------|
| **Frontend**     | React (Hooks, Context API), Axios, Tailwind CSS |
| **Backend**      | Node.js, Express.js                        |
| **Database**     | PostgreSQL (via Prisma ORM)                |
| **ORM**          | Prisma                                     |
| **File Uploads** | Multer (for CV PDFs/DOCX)                  |
| **Validation**   | Zod or Joi (optional)                      |
| **Auth (opt)**   | JWT-based admin access (future-ready)      |
| **Deployment**   | Docker, Railway/Render/Vercel              |

---

## 🧾 Data Model

### 🧑‍💼 Employee Table

| Column Name       | Type        | Description                                 |
|-------------------|-------------|---------------------------------------------|
| `id`              | UUID (PK)   | Unique employee ID                          |
| `name`            | TEXT        | Full name                                   |
| `email`           | TEXT        | Unique, contact email                       |
| `mobile`          | TEXT        | Saudi phone number                          |
| `position`        | TEXT        | Job title                                   |
| `salary`          | NUMERIC     | Monthly salary                              |
| `iqama_number`    | TEXT        | Saudi residence ID                          |
| `iqama_expiry`    | DATE        | Iqama expiration date                       |
| `birth_date`      | DATE        | Date of birth                               |
| `city`            | TEXT        | City of residence                           |
| `start_date`      | DATE        | Employment start date                       |
| `transfer_count`  | INTEGER     | Iqama transfer count                        |
| `status`          | TEXT        | Custom status                               |
| `cv_url`          | TEXT        | Path to CV                                  |
| `company_id`      | UUID (FK)   | Assigned company (nullable)                 |
| `is_rented`       | BOOLEAN     | Whether rented                              |
| `interview_date`  | DATE        | Interview date (optional)                   |
| `created_at`      | TIMESTAMP   | Record creation                             |
| `updated_at`      | TIMESTAMP   | Record update                               |

### 🏢 Company Table

| Column Name       | Type        | Description                                 |
|-------------------|-------------|---------------------------------------------|
| `id`              | UUID (PK)   | Unique company ID                           |
| `name`            | TEXT        | Company name                                |
| `industry`        | TEXT        | Sector/industry                             |
| `created_at`      | TIMESTAMP   | Record creation                             |
| `updated_at`      | TIMESTAMP   | Record update                               |

---

## 🔄 Key Features

### 👷 Employee Management

- Add / Edit / Delete employees
- Store personal, legal, professional data
- Upload CV per employee
- Rent / return employee to/from company
- Track Iqama, salary, status, city
- View work status
- Bulk employee import
- View employees by company
- Track timestamps

### 🏢 Company Management

- Add / Edit / Delete companies
- View company info
- View assigned employees
- Restrict delete if employees exist (optional)

---

## 📋 Smart Lists & Filtering

### Employee Views:

- ✅ All Employees
- ✅ Available Employees
- ✅ Rented Employees
- ✅ Filter by Company, City, Position, Status
- ✅ Search by Name, Iqama Number
- ✅ Paginate & Sort Results

---

## 📦 Bulk Import

- Upload Excel/CSV or paste structured JSON
- Auto-map fields
- `/employees/bulk` endpoint
- Upload CVs during or after import

---

## 📁 CV Uploads

- Endpoint: `POST /employees/:id/upload-cv`
- Local storage or cloud
- Save file path as `cv_url`
- UI for preview/download

---

## 🧩 System Architecture

### Backend Clean Architecture

```
server/
├── controllers/
├── services/
├── repositories/
├── routes/
├── middleware/
├── prisma/
└── index.ts
```

### Frontend Modular Architecture

```
client/
├── components/
├── pages/
├── services/
├── context/
├── types/
└── App.tsx
```

---

## 🔐 Optional Enhancements

| Feature                  | Description                                  |
|--------------------------|----------------------------------------------|
| 🔐 Admin Login           | JWT-based access                             |
| 📤 Export CSV/PDF        | Export lists                                 |
| 🧾 Audit Logs            | Log key actions                              |
| ☁️ Cloud Storage         | Store CVs on S3/Drive                        |
| 🔄 Real-time Updates     | WebSockets or polling                        |

---

## ✅ Next Steps

You can now:
- Scaffold backend (Express + Prisma)
- Build React UI with filters & search
- Deploy backend & frontend
