# 📘 Multi-Role Learning Platform

A role-based e-learning system with dedicated dashboards for Admin, Teacher, and Student roles. Built with React (frontend) and Express.js (backend), supporting secure media uploads, one-time payments, and AI-powered course recommendations.

---

## 🗂 Folder Structure

- /client → React frontend
- /server → Node.js backend

---

## 🧰 Tech Stack

| Layer        | Stack                             |
|--------------|------------------------------------|
| Frontend     | React.js, Tailwind CSS             |
| Backend      | Node.js, Express.js                |
| Database     | MongoDB with Mongoose              |
| File Upload  | Multer + Cloudinary (Required)     |
| Auth         | JWT + Role-based Middleware        |
| AI           | NLP chatbot for recommendations    |

---

## 📥 Local Development Setup

1. Clone the repo:

```bash
git clone https://github.com/your-repo/your-project.git
cd your-project


Configure Environment:

Copy and modify the .env files using sample.env format in both server and client (as needed):

In /server directory:

cp sample.env .env


Required .env variables:

.env (backend)

PORT=8080
MONGO_URI=mongodb://localhost:27017/your-db-name
JWT_SECRET=your_jwt_secret_key

# Required for Cloudinary upload
CLOUDINARY_CLOUD_NAME=your_cloud_name
CLOUDINARY_API_KEY=your_cloudinary_api_key
CLOUDINARY_API_SECRET=your_cloudinary_api_secret


Install dependencies and run:


cd server
npm install
npm run dev


Frontend:

cd client
npm install
npm run dev


Access the frontend at https://iit-e-learning.pages.dev/
Backend API base URL:https://e-learning-server-vqj4.onrender.com/

👥 User Roles & Flow
🧑‍💼 Admin

Add teachers and students using /add-member

Each admin has isolated users and courses

Shares credentials with added users

👨‍🏫 Teacher

Create and manage courses

Add/update lectures (video/PDF/quiz)

Publish/unpublish or delete content

View enrolled students and their progress

🧑‍🎓 Student

Search, filter, and enroll in published courses

Pay once to unlock content

View videos, download materials, submit feedback

Use chatbot for course recommendations

📁 Backend API Overview
Base URL: http://localhost:8080/api/v1

🔐 /user

Method	Endpoint	Description
POST	/register	Register a new user
POST	/login	Login with credentials
GET	/logout	Logout current user
POST	/add-member	Admin adds teacher/student
GET	/getMembers	Admin views own users
GET	/profile	Get logged-in user's profile
GET	/getprofiledata	Detailed profile info
PUT	/profile/update	Update profile with image
DELETE	/delete/:userId	Delete a user (admin only)
📚 /courses

Method	Endpoint	Description
POST	/	Create a new course
GET	/published-courses	View all published courses
GET	/	Get creator's own courses
GET	/search	Search by name/language/domain
GET	/:courseId	Get a course by ID
PUT	/:courseId	Edit course info
PATCH	/:courseId	Publish or unpublish a course
POST	/:courseId/lecture	Add a lecture to course
GET	/:courseId/lecture	List lectures in a course
POST	/:courseId/lecture/:lectureId	Edit a lecture
DELETE	/lecture/:lectureId	Delete a lecture
GET	/lecture/:lectureId	Get a lecture
💳 /purchase

Method	Endpoint	Description
POST	/checkout/create-checkout-session	Start Stripe payment session
GET	/course/:courseId/detail-with-status	Course access with purchase check
GET	/	Get list of purchased courses
📺 /media

Method	Endpoint	Description
POST	/upload-video	Upload video/file to Cloudinary
Form data required: key = file

📈 /progress

Method	Endpoint	Description
GET	/:courseId	Get user’s course progress
POST	/:courseId/lecture/:lectureId/view	Mark lecture as completed
POST	/:courseId/complete	Mark course completed
POST	/:courseId/incomplete	Mark course incomplete
📌 Notes
Cloudinary credentials are required to upload and access course media.

Admins have isolated scopes — no overlap in user/course data.

Course data (lectures, PDFs, etc.) is only visible to enrolled students.

