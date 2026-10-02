# i can - Online Course Platform

A modern full-stack web application designed for online education, allowing instructors to publish courses and lessons, while enabling students to browse, enroll, learn, and engage through lesson discussions.

---

## 🌟 Key Features

### For Students:
- **Browse & Search Courses**: Explore courses by keyword and category (Machine Learning, Deep Learning, Creative Thinking, Math 0, Math 1, Math 3, Data Science).
- **Course Enrollment**: Single-click enrollment with duplicate prevention.
- **Lesson Learning**: Sequential lesson navigation with detailed text materials.
- **Discussion & Comments**: Add comments on specific lessons, with full edit and delete permissions on own comments.
- **My Enrolled Courses**: Dedicated student dashboard tracking active course enrollments.

### For Instructors:
- **Course Management**: Create, update, and delete courses.
- **Lesson Curriculum (Syllabus)**: Add lessons with custom order, manage lesson content, and delete lessons.
- **Instructor Overview**: Dedicated instructor management showing total enrolled students and syllabus statistics.

### General Platform:
- **Authentication**: JWT-based secure sign in and registration with role assignment (Student / Instructor).
- **Theme Support**: Seamless Dark Mode / Night Mode toggle.
- **Clean UI**: Minimalist, human-designed responsive interface.

---

## 🛠️ Tech Stack

- **Frontend**: React (JavaScript only, no TypeScript, functional components, Hooks)
- **Styling**: Tailwind CSS & Lucide Icons
- **Backend**: Node.js & Express.js (REST API architecture)
- **Database**: MongoDB with Mongoose ODM
- **Authentication**: JSON Web Tokens (JWT) & bcrypt password hashing

---

## 🗄️ Database Models (Mongoose)

1. **User** (`users`):
   - `name`: String
   - `email`: String (unique)
   - `password`: String (hashed)
   - `role`: "student" | "instructor"
   - `createdAt`: Date

2. **Course** (`courses`):
   - `title`: String
   - `description`: String
   - `category`: String
   - `instructor`: ObjectId (ref: 'User')
   - `createdAt`: Date

3. **Lesson** (`lessons`):
   - `title`: String
   - `content`: String
   - `course`: ObjectId (ref: 'Course')
   - `order`: Number
   - `createdAt`: Date

4. **Enrollment** (`enrollments`):
   - `student`: ObjectId (ref: 'User')
   - `course`: ObjectId (ref: 'Course')
   - `enrolledAt`: Date

5. **Comment** (`comments`):
   - `user`: ObjectId (ref: 'User')
   - `lesson`: ObjectId (ref: 'Lesson')
   - `text`: String
   - `createdAt`: Date

---

## 📁 Project Structure

```text
├── backend/
│   ├── config/
│   │   └── db.js               # MongoDB connection
│   ├── models/
│   │   ├── User.js             # User schema
│   │   ├── Course.js           # Course schema
│   │   ├── Lesson.js           # Lesson schema
│   │   ├── Enrollment.js       # Enrollment schema
│   │   └── Comment.js          # Comment schema
│   ├── .env.example
│   ├── package.json
│   └── server.js               # Express application entry point
├── src/
│   ├── data/
│   │   └── initialData.js      # Initial seed & state data
│   ├── App.jsx                 # Main application component
│   ├── index.css               # Global styles & Tailwind
│   └── main.jsx                # Application root mounting
├── index.html
├── metadata.json
└── package.json
```

---

## 🚀 Getting Started

### 1. Install Dependencies
```bash
npm install
```

### 2. Run the Development Server
```bash
npm run dev
```

The application will run locally on `http://localhost:3000`.
