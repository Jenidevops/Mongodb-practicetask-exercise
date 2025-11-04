# MongoDB Practice Task - Full-Stack CRUD API

## 📋 Project Overview
A production-ready RESTful API built with **Express.js** and **MongoDB** that demonstrates enterprise-level database operations, advanced query patterns, and real-world use cases. This project showcases proficiency in backend development, database design, and cloud deployment.

## 💼 Key Highlights for Recruiters
- ✅ **Full CRUD Operations**: Complete Create, Read, Update, Delete implementations with error handling
- ✅ **Advanced MongoDB Queries**: Demonstrates expertise with query operators ($gt, $lt, $in, $and, $or, $exists)
- ✅ **RESTful API Design**: Well-structured endpoints following REST principles
- ✅ **Real-World Use Case**: Functional Library Management System with borrowing/returning logic
- ✅ **Production Deployment**: Live on Vercel with MongoDB Atlas cloud database
- ✅ **Clean Code**: Organized, documented, and maintainable codebase
- ✅ **Modern Stack**: Node.js, Express.js v5, Mongoose ODM, MongoDB Atlas
- ✅ **DevOps Ready**: Environment variables, .gitignore, deployment configuration

## 🎯 Technical Competencies Demonstrated
- Backend API Development with Node.js & Express.js
- MongoDB database design and schema modeling
- Mongoose ODM for data validation and relationships
- Complex database queries and aggregations
- RESTful API architecture and design patterns
- Cloud database integration (MongoDB Atlas)
- Serverless deployment (Vercel)
- Environment configuration and security best practices
- Git version control and GitHub collaboration

## 🏗️ Project Structure
- **Database**: `studentDB` (local) / `library` (production - MongoDB Atlas)
- **Collections**: `students`, `books`
- **Framework**: Express.js with Mongoose ODM
- **Port**: 3000 (local) / Serverless (production)

## 🌐 Live Deployment
**Production URL**: [https://mongodbtask.vercel.app](https://mongodbtask.vercel.app)

Deployed on Vercel with MongoDB Atlas cloud database.

## 🚀 Getting Started

### Prerequisites
- Node.js >= 18.0.0
- MongoDB running locally on port 27017 (for local development)
- MongoDB Atlas account (for production deployment)

### Installation & Setup
```bash
# Install dependencies
npm install

# Start the server
npm start

# Or for development
npm run dev
```

### Access API Documentation
- **Local**: `http://localhost:3000`
- **Production**: `https://mongodbtask.vercel.app`

## 📊 Database Schema

### Student Schema
```javascript
{
  name: String (required),
  age: Number (required),
  course: String (required),
  status: String (default: 'enrolled'),
  enrollmentDate: Date (default: now),
  email: String,
  phone: String
}
```

### Book Schema
```javascript
{
  title: String (required),
  author: String (required),
  isbn: String (unique),
  category: String,
  available: Boolean (default: true),
  borrowedBy: ObjectId (ref: Student),
  borrowDate: Date,
  dueDate: Date
}
```

## 📝 Task Implementation

### ✅ Task 1: Database & Collection Setup
- Created `studentDB` database
- Created `students` and `books` collections
- Established MongoDB connection with proper error handling

### ✅ Task 2: Insert Operations

#### Single Document Insert
```http
POST /students/single
Content-Type: application/json

{
  "name": "John Doe",
  "age": 22,
  "course": "MERN Stack",
  "email": "john@email.com"
}
```

#### Multiple Documents Insert
```http
POST /students/multiple
Content-Type: application/json

[
  {
    "name": "Jane Smith",
    "age": 24,
    "course": "Python Development"
  },
  {
    "name": "Mike Johnson",
    "age": 23,
    "course": "MERN Stack"
  }
]
```

#### Sample Data
```http
POST /students/sample-data
```

### ✅ Task 3: Read Operations

#### Fetch All Students
```http
GET /students
```

#### Filter by Course
```http
GET /students/filter?course=MERN Stack
```

#### MERN Stack Students
```http
GET /students/mern-stack
```

### ✅ Task 4: Update Operations

#### Update Single Student
```http
PUT /students/{studentId}
Content-Type: application/json

{
  "status": "completed",
  "age": 25
}
```

#### Mark Student as Completed
```http
PUT /students/{studentId}/complete
```

#### Bulk Update
```http
PUT /students/bulk
Content-Type: application/json

{
  "filter": { "course": "MERN Stack" },
  "update": { "status": "in-progress" }
}
```

### ✅ Task 5: Delete Operations

#### Delete Single Student
```http
DELETE /students/{studentId}
```

#### Delete by Condition
```http
DELETE /students/by-condition
Content-Type: application/json

{
  "condition": { "status": "dropped" }
}
```

#### Delete All Students (Practice Only!)
```http
DELETE /students/all
```

### ✅ Task 6: Query Operators

#### Age Range ($gt, $lt)
```http
GET /students/age-range?minAge=20&maxAge=25
```

#### Multiple Courses ($in)
```http
GET /students/courses?courses=MERN Stack,Python Development
```

#### Complex Queries ($and, $or, $exists)
```http
GET /students/complex?queryType=and
GET /students/complex?queryType=or
GET /students/complex?queryType=exists
```

#### Advanced Search (Combined Operators)
```http
GET /students/advanced-search
```

### ✅ Task 7: Library System Use Case

#### Library Management Features
- **Book Management**: Add, view, categorize books
- **Borrowing System**: Borrow and return books
- **Student Integration**: Link borrowers with student records
- **Availability Tracking**: Real-time book availability

#### Library API Endpoints

##### Get All Books
```http
GET /library/books
```

##### Add New Book
```http
POST /library/books
Content-Type: application/json

{
  "title": "Clean Code",
  "author": "Robert C. Martin",
  "isbn": "978-0132350884",
  "category": "Programming"
}
```

##### Get Available Books
```http
GET /library/available
```

##### Borrow Book
```http
POST /library/borrow
Content-Type: application/json

{
  "bookId": "book_object_id",
  "studentId": "student_object_id"
}
```

##### Return Book
```http
POST /library/return
Content-Type: application/json

{
  "bookId": "book_object_id"
}
```

##### Books by Category
```http
GET /library/category/Programming
```

##### Add Sample Library Data
```http
POST /library/sample-data
```

## 🔧 Utility Endpoints

### Health Check
```http
GET /health
```

### Database Statistics
```http
GET /stats
```

## 📊 Query Operators Examples

### $gt (Greater Than)
```javascript
{ age: { $gt: 22 } }  // Students older than 22
```

### $lt (Less Than)
```javascript
{ age: { $lt: 25 } }  // Students younger than 25
```

### $in (In Array)
```javascript
{ course: { $in: ["MERN Stack", "Python Development"] } }
```

### $and (Logical AND)
```javascript
{
  $and: [
    { age: { $gte: 22 } },
    { course: "MERN Stack" }
  ]
}
```

### $or (Logical OR)
```javascript
{
  $or: [
    { status: "completed" },
    { age: { $gt: 24 } }
  ]
}
```

### $exists (Field Exists)
```javascript
{ email: { $exists: true, $ne: "" } }
```

## 🧪 Testing the Implementation

### 1. Start the Server
```bash
node index.js
```

### 2. Add Sample Data
```bash
curl -X POST http://localhost:3000/students/sample-data
curl -X POST http://localhost:3000/library/sample-data
```

### 3. Test CRUD Operations
```bash
# Read all students
curl http://localhost:3000/students

# Filter students
curl "http://localhost:3000/students/filter?course=MERN Stack"

# Age range query
curl "http://localhost:3000/students/age-range?minAge=22&maxAge=25"

# Get database stats
curl http://localhost:3000/stats
```

## 🎯 Learning Outcomes

By completing this task, you have:

1. ✅ **Mastered CRUD Operations**: Create, Read, Update, Delete documents
2. ✅ **Query Operators**: Used $gt, $lt, $in, $and, $or, $exists effectively
3. ✅ **Schema Design**: Created proper MongoDB schemas with relationships
4. ✅ **Real-world Application**: Built a functional library management system
5. ✅ **Express Integration**: Combined MongoDB with Express.js REST API
6. ✅ **Error Handling**: Implemented proper error handling and validation
7. ✅ **Data Relationships**: Used population for referenced documents

## 🚀 Production Deployment

### Deployed on Vercel
This application is deployed on Vercel with MongoDB Atlas as the cloud database.

**Live URL**: https://mongodbtask.vercel.app

### Environment Variables
The following environment variables are configured in production:
- `MONGODB_URI`: MongoDB Atlas connection string
- `NODE_ENV`: production
- `PORT`: Auto-configured by Vercel

### Deployment Configuration
- **Platform**: Vercel Serverless Functions
- **Database**: MongoDB Atlas (Cloud)
- **Node Version**: >= 18.0.0
- **Build Command**: Automatic
- **Runtime**: Node.js serverless function

## 🚀 Next Steps & Enhancements

1. ✅ **Production Deployment** - Deployed on Vercel
2. Add authentication and authorization (JWT tokens)
3. Implement pagination for large datasets
4. Add data validation and sanitization
5. Create a frontend interface (React/Next.js)
6. Add API rate limiting and caching
7. Implement search functionality with indexes

## 📚 MongoDB Commands Reference

### Connect to Database
```javascript
use studentDB
```

### View Collections
```javascript
show collections
```

### Basic Queries
```javascript
### Basic Queries
```javascript
// Find all students
db.students.find()

// Find with filter
db.students.find({course: "MERN Stack"})

// Count documents
db.students.countDocuments()

// Create index
db.students.createIndex({email: 1})
```

## 📁 Project Files

```
mongodbtask/
├── index.js              # Main application file with all API routes
├── package.json          # Project dependencies and scripts
├── vercel.json          # Vercel deployment configuration
├── .env                 # Environment variables (local, gitignored)
├── .env.example         # Environment variables template
├── .gitignore           # Git ignore configuration
└── README.md            # Project documentation
```

## 🔐 Security

- Environment variables are stored in `.env` file (not tracked by git)
- MongoDB credentials are secured using environment variables
- Production uses MongoDB Atlas with authentication
- All sensitive data is in `.gitignore`

## 🎉 Project Completion

This MongoDB Practice Task covers all requirements:
- ✅ Database & Collection Setup (studentDB with students and books)
- ✅ Insert Operations (single, multiple, sample data)
- ✅ Read Operations (fetch all, filters, specific queries)
- ✅ Update Operations (single, bulk, status updates)
- ✅ Delete Operations (single, conditional, all)
- ✅ Query Operators ($gt, $lt, $in, $and, $or, $exists)
- ✅ Real-World Use Case (Library Management System)
- ✅ Production Deployment (Vercel + MongoDB Atlas)

**Congratulations!** 🎉 You have successfully completed the MongoDB Basic Practice Task with a comprehensive implementation covering all requirements and real-world use cases, now deployed to production!

---

**Project Name**: MongoDB Practice Task  
**Version**: 1.0.0  
**License**: ISC  
**Deployed**: Vercel (https://mongodbtask.vercel.app)
```
```

---

