# 🔄 SkillSwap – Peer-to-Peer Skill Exchange Platform

<div align="center">

**A comprehensive full-stack platform enabling users to exchange skills and knowledge without monetary transactions, featuring intelligent matching, swap management, and community-driven learning.**

[![Node.js](https://img.shields.io/badge/Node.js-18+-339933?style=flat&logo=node.js)](https://nodejs.org/)
[![React](https://img.shields.io/badge/React-18+-61DAFB?style=flat&logo=react)](https://reactjs.org/)
[![Express](https://img.shields.io/badge/Express-4.x-000000?style=flat&logo=express)](https://expressjs.com/)
[![MongoDB](https://img.shields.io/badge/MongoDB-Latest-47A248?style=flat&logo=mongodb)](https://www.mongodb.com/)

</div>

---

## 🎯 Problem Statement

In today's knowledge economy, traditional education and skill development often require significant financial investment. Many individuals possess valuable skills but lack access to learning opportunities in other domains. The current system creates barriers to knowledge sharing and personal growth.

**SkillSwap** addresses these challenges by providing:
- **Barter-based skill exchange** eliminating financial barriers to learning
- **Intelligent matching system** connecting users with complementary skills
- **Structured swap management** with request/accept workflows
- **Reputation system** building trust through ratings and feedback
- **Community platform** fostering collaborative learning environments
- **Admin oversight** ensuring quality and safety across the platform

---

## 🚀 Key Features

### 👤 User Profile Management
- **Comprehensive Profiles**: Name, location (optional), profile photo (optional)
- **Skills Offered**: List multiple skills you can teach
- **Skills Wanted**: Specify skills you want to learn
- **Availability Settings**: Define when you're available (weekends, evenings, custom schedules)
- **Privacy Controls**: Toggle between public and private profile visibility
- **Profile Verification**: Build credibility through completed swaps

### 🔍 Skill Discovery & Matching
- **Advanced Search**: Find users by specific skills (e.g., "Photoshop", "Excel", "Guitar")
- **Smart Filtering**: Filter by location, availability, skill level
- **Skill Categories**: Browse organized skill taxonomies
- **Match Recommendations**: AI-suggested matches based on mutual needs
- **Skill Tags**: Granular skill classification for precise matching

### 🤝 Swap Request System
- **Send Requests**: Propose skill exchanges with custom messages
- **Accept/Reject**: Review incoming requests with detailed information
- **Pending Requests**: Track all outgoing and incoming requests
- **Active Swaps**: Monitor ongoing skill exchange sessions
- **Request Deletion**: Cancel pending requests before acceptance
- **Swap History**: Complete record of past exchanges

### ⭐ Ratings & Feedback System
- **Post-Swap Reviews**: Rate and review completed exchanges
- **5-Star Rating System**: Quantitative feedback mechanism
- **Written Testimonials**: Detailed feedback on teaching quality
- **Reputation Scores**: Aggregate ratings visible on profiles
- **Feedback Moderation**: Admin review of inappropriate reviews
- **Trust Indicators**: Verified badges for highly-rated users

### 🛡️ Admin Management Panel
- **Content Moderation**: Review and reject inappropriate skill descriptions
- **User Management**: Ban users violating platform policies
- **Swap Monitoring**: Oversee pending, accepted, and cancelled swaps
- **Platform Announcements**: Send system-wide messages (updates, maintenance alerts)
- **Analytics Dashboard**: Download reports on user activity, feedback logs, swap statistics
- **Dispute Resolution**: Handle conflicts between users

---

## 🏗️ System Architecture

```mermaid
flowchart TB
    subgraph Frontend["Frontend - React"]
        UI[User Interface]
        Router[React Router]
        Components[Components]
        State[State Management]
    end
    
    subgraph Backend["Backend - Node.js + Express"]
        API[REST API Server]
        Auth[Authentication Middleware]
        Routes[Route Controllers]
        Services[Business Logic]
    end
    
    subgraph Database["Database Layer"]
        DB[(MongoDB)]
    end
    
    subgraph External["External Services"]
        Email[Email Service]
        Storage[File Storage]
        Analytics[Analytics Engine]
    end
    
    UI --> Router
    Router --> Components
    Components --> State
    State -->|HTTP Requests| API
    API --> Auth
    Auth --> Routes
    Routes --> Services
    Services --> DB
    Services --> Email
    Services --> Storage
    Services --> Analytics
    
    style Frontend stroke:#333,stroke-width:2px
    style Backend stroke:#333,stroke-width:2px
    style Database stroke:#333,stroke-width:2px
    style External stroke:#333,stroke-width:2px
```

## 🛠️ Tech Stack

### 🎨 Frontend

| Technology                     | Purpose                           |
| ------------------------------ | --------------------------------- |
| **React**                      | UI framework                      |
| **React Router**               | Client-side routing               |
| **Redux / Context API**        | State management                  |
| **Axios**                      | HTTP client for API requests      |
| **Material-UI / Tailwind CSS** | UI components & styling           |
| **Socket.io Client**           | Real-time updates & notifications |

---

### ⚙️ Backend

| Technology               | Purpose                                 |
| ------------------------ | --------------------------------------- |
| **Node.js**              | Runtime environment                     |
| **Express.js**           | Backend web framework                   |
| **MongoDB** | Primary database                        |
| **Mongoose** | ODM / ORM                               |
| **JWT**                  | Authentication & authorization          |
| **Bcrypt**               | Password hashing                        |
| **Nodemailer**           | Email service & notifications           |
| **Socket.io**            | WebSocket server for real-time features |
| **Multer**               | File uploads handling                   |
| **Express Validator**    | Request validation & sanitization       |

---

## 🔧 Installation & Setup

### 📌 Prerequisites

Make sure you have installed:

* **Node.js** (v18 or higher)
* **npm** or **yarn**
* **MongoDB** or **PostgreSQL**
* **Git**
* **Redis** *(optional, for caching & real-time features)*

---

### 1️⃣ Clone the Repository

```bash
git clone https://github.com/jenil1236/OdooHackathon.git
cd OdooHackathon
```

---

### 2️⃣ Backend Setup

```bash
cd Backend

# Install dependencies
npm install

# Create environment file
cp .env.example .env

# Run migrations (only if using SQL database)
npm run migrate

# Seed initial data (optional)
npm run seed

# Start development server
npm run dev
```

**Backend runs on:**
👉 `http://localhost:5000`

---

### 3️⃣ Frontend Setup

```bash
cd Frontend

# Install dependencies
npm install

# Create environment file
cp .env.example .env

# Start development server
npm run dev
```

**Frontend runs on:**
👉 `http://localhost:3000`

---

# 🌍 Environment Variables

---

## ⚙️ Backend `.env`

```env
# Server Configuration
NODE_ENV=development
PORT=5000
API_VERSION=v1

# Database (MongoDB)
MONGODB_URI=mongodb://localhost:27017/skillswap
# OR PostgreSQL
# DATABASE_URL=postgresql://user:password@localhost:5432/skillswap

# Authentication
JWT_SECRET=your_super_secret_jwt_key_change_this_in_production
JWT_EXPIRE=7d
REFRESH_TOKEN_SECRET=your_refresh_token_secret
REFRESH_TOKEN_EXPIRE=30d

# Session
SESSION_SECRET=your_session_secret_key

# CORS
CORS_ORIGIN=http://localhost:3000

# Email Service
EMAIL_HOST=smtp.gmail.com
EMAIL_PORT=587
EMAIL_USER=your_email@gmail.com
EMAIL_PASSWORD=your_app_specific_password
EMAIL_FROM=SkillSwap <noreply@skillswap.com>

# File Upload
MAX_FILE_SIZE=5242880
UPLOAD_PATH=./uploads

# Redis (optional)
REDIS_URL=redis://localhost:6379

# Socket.io
SOCKET_PORT=5001

# Admin Credentials
ADMIN_EMAIL=admin@skillswap.com
ADMIN_PASSWORD=change_this_secure_password
```

---

## 🎨 Frontend `.env`

```env
# API Configuration
VITE_API_URL=http://localhost:5000/api/v1
VITE_SOCKET_URL=http://localhost:5001

# App Configuration
VITE_APP_NAME=SkillSwap
VITE_APP_VERSION=1.0.0

# Feature Flags
VITE_ENABLE_NOTIFICATIONS=true
VITE_ENABLE_ANALYTICS=false
```
---

# 🎨 Key Features Walkthrough

## 👤 1. User Registration & Profile Setup

* Users sign up using **email and password**
* Email verification ensures account authenticity
* Profile setup includes:

  * Skills they **offer**
  * Skills they **want to learn**
  * Optional profile photo upload
  * Availability schedule selection
  * Privacy preferences (public / restricted)

➡️ This onboarding ensures better skill matching and trust within the platform.

---

## 🔎 2. Skill Discovery Flow

* Users search for skills via a **smart search bar**
* Apply filters such as:

  * Location
  * Availability
  * Ratings
* Browse matched user profiles
* View:

  * Detailed skill listings
  * Reviews & ratings
  * Mutual skill compatibility indicators

➡️ Designed to quickly connect users with relevant learning partners.

---

## 🤝 3. Swap Request Process

1. User A finds a profile offering a desired skill
2. Sends a **swap request** with a custom message
3. User B receives:

   * Email notification
   * In-app notification
4. User B reviews requester profile
5. Accepts or rejects the request
6. If accepted:

   * Contact details shared securely
   * Users coordinate the session (online or offline)

➡️ Keeps the platform safe while enabling real collaboration.

---

## ⭐ 4. Post-Swap Feedback System

* After completing a swap, both users are prompted to:

  * Rate the experience (1–5 stars)
  * Write a detailed review
* Reviews appear on user profiles
* Overall rating updates dynamically

➡️ Builds trust, improves recommendations, and encourages quality exchanges.

---

## 🛡 5. Admin Moderation Panel

Admins have tools to maintain platform quality:

* Review reported or flagged content
* Remove inappropriate skill listings
* Suspend or ban policy-violating users
* Publish platform-wide announcements
* Export analytics and usage reports

➡️ Ensures a safe, professional, and scalable ecosystem.

---
Here’s a **polished README-ready version** of both sections — tightened wording, consistent tone, better recruiter appeal, and formatted for GitHub.

---

# 🎯 Why This Project Stands Out

SkillSwap is more than just another CRUD-based web app — it demonstrates real-world product thinking, scalable backend architecture, and user-centric design.

### 🌍 Impact & Concept

* ✅ **Social Impact** — Makes learning accessible by removing financial barriers
* ✅ **Barter Economy Model** — Promotes knowledge exchange instead of transactions
* ✅ **Community-Driven Learning** — Encourages collaboration and peer teaching

### 🧠 Technical Strength

* ✅ **Full-Stack Architecture** — Built using a modern MERN/PERN-style stack
* ✅ **Real-Time Capabilities** — WebSocket-powered notifications & updates
* ✅ **Scalable System Design** — Modular backend with clean separation of concerns
* ✅ **Secure by Design** — JWT auth, password hashing, validation, CORS protection
* ✅ **Production-Oriented Setup** — Environment configs, structured logging, error handling

### 🎨 Product & UX Focus

* ✅ **Intuitive User Experience** — Clean responsive UI with clear workflows
* ✅ **Trust & Reputation System** — Ratings, feedback, and credibility signals
* ✅ **Admin Governance Layer** — Moderation tools, analytics, and platform control

> 💡 **This project showcases enterprise-level thinking:**
> authentication flows, real-time systems, structured APIs, scalable architecture, and community platform design — not just frontend pages and database models.

---

# 📝 Future Enhancements

SkillSwap is designed with extensibility in mind. Planned improvements include:

### 📱 Platform Expansion

* 🚀 **Mobile Apps** — React Native apps for iOS & Android
* 🌐 **Multi-language Support** — global accessibility

### 🤖 Smart Features

* 🧠 **AI Matching Engine** — ML-based compatibility scoring
* 🏅 **Gamification System** — Badges, levels, and achievements
* 📊 **Advanced Analytics Dashboard** — User insights and engagement metrics

### 🎥 Learning Experience Improvements

* 📹 **Built-in Video Calls** — Real-time in-app sessions
* 📅 **Scheduling System** — Calendar integration with booking
* 👥 **Group Swaps** — Multi-user learning sessions
* 🎓 **Skill Verification** — Assessments and certification badges


