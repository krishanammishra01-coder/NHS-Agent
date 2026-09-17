# 🏥 Digital_Hospital

## Next-Generation Smart Healthcare SaaS & AI Assistant Platform

Digital_Hospital is a full-stack healthcare management platform designed to connect patients, doctors, administrators, and pharmacy services through a single web application.

The platform combines healthcare management features with an AI-powered assistant to improve appointment booking, patient support, clinical record management, billing, and pharmacy operations.

---

## 📌 Project Overview

Healthcare providers often face challenges such as:

- Long appointment booking procedures
- Fragmented patient records
- Manual prescription and billing management
- Difficulty managing doctor schedules
- Pharmacy stock mismatches
- Limited access to basic healthcare guidance
- Lack of centralized administrative analytics

Digital_Hospital provides a unified digital solution that simplifies healthcare operations and improves the patient experience.

---

## 🎯 Project Objectives

- Provide an easy-to-use patient healthcare portal
- Simplify doctor appointment scheduling
- Manage patient records and clinical notes digitally
- Provide AI-based healthcare guidance
- Manage prescriptions, invoices, and payments
- Track pharmacy inventory
- Support role-based access for different users
- Improve hospital administration through analytics
- Maintain secure and reliable data handling

---

## 🌟 Key Features

### 👨‍⚕️ Admin and Clinical Management

- Admin dashboard
- Doctor registration and management
- Department management
- Doctor availability and slot management
- Appointment approval and rescheduling
- Patient registry
- Electronic medical records
- Clinical notes and prescription management
- Billing and payment tracking
- Pharmacy inventory management
- Low-stock medicine alerts
- Financial and patient analytics

---

### 🩺 Patient Portal

- Patient registration and login
- Secure JWT-based authentication
- Doctor and department browsing
- Online appointment booking
- Appointment status tracking
- Digital prescription viewing
- Invoice and payment history
- Personal clinical journal
- Symptom and health-note recording
- Pharmacy medicine browsing
- AI healthcare assistant

---

### 🤖 AI Healthcare Assistant

Digital_Hospital includes an AI-powered healthcare assistant using the Google Gemini API.

#### AI Capabilities

- Answers questions about the platform
- Explains how to book appointments
- Helps users find prescriptions and invoices
- Provides general health information
- Supports basic symptom reporting
- Provides navigation assistance
- Responds conversationally to user queries

#### AI Safety Guardrails

The AI assistant:

- Does not diagnose diseases
- Does not prescribe medicines
- Does not make definitive medical claims
- Advises users to consult qualified healthcare professionals
- Displays medical safety disclaimers when required
- Supports fallback demo mode when the API key is unavailable

---

## 🛡️ Security Features

- JWT-based authentication
- Role-based access control
- Password hashing using Bcrypt
- Secure HTTP headers using Helmet
- API rate limiting
- Authentication request limiting
- Centralized error handling
- Validation error handling
- Invalid ObjectId handling
- Duplicate key error handling
- Protection against exposing internal server errors
- Secure environment variable configuration

---

## 💳 Payment and Inventory Transaction Handling

Digital_Hospital uses MongoDB multi-document transactions to maintain data consistency during payment and pharmacy operations.

### Transaction Workflow

1. Patient initiates checkout
2. A database session and transaction are started
3. The bill status is verified
4. The payment amount is validated
5. Medicine stock availability is checked
6. Payment record is created
7. Bill status is updated to `Paid`
8. Medicine stock is reduced
9. The transaction is committed

If any validation fails, the transaction is aborted and the changes are rolled back.

This helps reduce:

- Duplicate payments
- Incorrect bill settlements
- Medicine stock mismatches
- Race conditions during concurrent checkouts

---

## 🏗️ System Architecture

```text
+-------------------------------------------------------------+
|                        CLIENT LAYER                         |
|                                                             |
| React 19 + Tailwind CSS + Recharts + Axios                  |
+-----------------------------+-------------------------------+
                              |
                              |
                       HTTP / HTTPS
                        JWT Authentication
                              |
                              |
+-----------------------------v-------------------------------+
|                       BACKEND LAYER                         |
|                                                             |
| Node.js + Express 5 REST API                               |
| Helmet Security + Rate Limiting + JWT                      |
+----------------------+----------------------+---------------+
                       |                      |
                       |                      |
        +--------------v-----------+  +-------v----------------+
        |     AI SERVICE           |  |    DATABASE SERVICE    |
        |                          |  |                       |
        | Google Gemini API        |  | MongoDB Atlas          |
        | AI Healthcare Assistant  |  | Mongoose ODM           |
        +--------------------------+  | Transactions           |
                                      +-----------------------+

📂 Project Structure
Digital_Hospital/
│
├── Digital_Hospital_Backend/
│   ├── controllers/
│   │   ├── aiController.js
│   │   ├── authController.js
│   │   ├── appointmentController.js
│   │   ├── billController.js
│   │   └── medicineController.js
│   │
│   ├── models/
│   ├── routes/
│   ├── middleware/
│   ├── config/
│   ├── scripts/
│   ├── server.js
│   ├── package.json
│   └── .env
│
├── Digital_Hospital_frontend/
│   ├── src/
│   │   ├── components/
│   │   ├── pages/
│   │   ├── assets/
│   │   ├── services/
│   │   ├── context/
│   │   └── App.jsx
│   │
│   ├── public/
│   ├── package.json
│   └── .env
│
└── README.md
⚠️ Medical Safety Disclaimer

Digital_Hospital is an academic and software engineering project.

The AI assistant provides general information and platform guidance only. It is not a replacement for professional medical advice, diagnosis, or treatment.

Users should consult qualified healthcare professionals for medical concerns and emergencies.

📄 License

This project is intended for educational and academic purposes.

You may add your preferred open-source license here, such as the MIT License.

❤️ Project Credits

Digital_Hospital: A full-stack healthcare management and AI assistant platform developed as a internship completion project.

Built with React, Node.js, Express, MongoDB, and Google Gemini AI.