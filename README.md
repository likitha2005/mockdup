# mockdup

**MockDup** is a full-stack mock API builder that lets users create mock RESTful endpoints with realistic fake data using [Faker.js](https://fakerjs.dev/). Inspired by platforms like MockAPI.io, it allows you to:
- Sign up / log in securely
- Create multiple mock API **projects**
- Add **resources** to projects with custom fields (e.g. `name`, `email`, `country`, etc.)
- Instantly generate mock data
- Access RESTful endpoints for your mock data (e.g. `/api/us/people`)

---

## 🌐 Tech Stack

**Frontend**  
- HTML, CSS, JavaScript  
- Token-based authentication  
- Dynamic dashboard interface  

**Backend (Node.js + Express)**  
- REST API  
- JWT Authentication  
- Faker.js for data generation  
- MySQL database (via `mysql2`)

---

## 📁 Folder Structure

mockdup/
├── backend/
│ ├── routes/
│ │ ├── auth.js
│ │ ├── projects.js
│ │ └── resources.js
│ ├── middleware/
│ │ └── verifyToken.js
│ ├── config/
│ │ └── db.js
│ ├── index.js
│ └── .env
└── frontend/
├── index.html
├── styles.css
└── script.js


---

## 🛠 Setup Instructions

### 1. Clone the repository

```bash
git clone https://github.com/yourusername/mockdup.git
cd mockdup
2. Install Backend Dependencies
bash
Copy
Edit
cd backend
npm install
3. Setup .env file in /backend
env
Copy
Edit
PORT=3000
JWT_SECRET=your_jwt_secret
DB_HOST=localhost
DB_USER=root
DB_PASSWORD=your_mysql_password
DB_NAME=mockdup
4. Create MySQL Tables
sql
Copy
Edit
CREATE DATABASE IF NOT EXISTS mockdup;

USE mockdup;

CREATE TABLE users (
  id INT AUTO_INCREMENT PRIMARY KEY,
  name VARCHAR(100),
  email VARCHAR(100) UNIQUE,
  password VARCHAR(255)
);

CREATE TABLE projects (
  id INT AUTO_INCREMENT PRIMARY KEY,
  user_id INT,
  name VARCHAR(100),
  prefix VARCHAR(50),
  created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

CREATE TABLE resources (
  id INT AUTO_INCREMENT PRIMARY KEY,
  project_id INT,
  name VARCHAR(100),
  count INT DEFAULT 10
);

CREATE TABLE fields (
  id INT AUTO_INCREMENT PRIMARY KEY,
  resource_id INT,
  name VARCHAR(100),
  type VARCHAR(50)
);
5. Run the Backend Server
bash
Copy
Edit
node index.js
# Server running at http://localhost:3000
🧪 API Examples
✅ Login
http
Copy
Edit
POST /api/auth/login
json
Copy
Edit
{
  "email": "admin@mockdup.io",
  "password": "Admin@123"
}
📁 Create a Project
http
Copy
Edit
POST /api/projects
Authorization: Bearer <token>
json
Copy
Edit
{
  "name": "People API",
  "prefix": "people"
}
📦 Create a Resource
http
Copy
Edit
POST /api/resources
Authorization: Bearer <token>
json
Copy
Edit
{
  "projectId": 5,
  "name": "users",
  "fields": [
    { "name": "name", "type": "name" },
    { "name": "email", "type": "email" },
    { "name": "country", "type": "country" }
  ],
  "count": 15
}
🔄 Fetch Resource Data
http
Copy
Edit
GET /api/people/users
Response:

json
Copy
Edit
[
  {
    "name": "John Doe",
    "email": "john@example.com",
    "country": "USA"
  },
  ...
]
🎯 Features
 JWT Auth with user accounts

 Project creation with prefix-based URL mapping

 Dynamic mock data via Faker

 Fully RESTful endpoints

 Easy-to-use dashboard UI

✨ Future Enhancements
✅ Editable resource schemas

⏳ Support PUT/POST/DELETE on mocks

⏳ Pagination, sorting, filtering

⏳ Export project config as JSON

⏳ Deploy to mockdup.io

💡 Credits
Faker.js

MySQL

Built with ❤️ by Likitha @ 2025

📬 Contact
Email: likitha@example.com
