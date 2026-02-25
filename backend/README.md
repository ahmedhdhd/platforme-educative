# Educational Interactive Platform - Backend

This is the backend API for the Educational Interactive Platform built with the MERN stack.

## 📁 Project Structure

```
backend/
├── src/
│   ├── config/
│   │   └── database.js          # MongoDB connection configuration
│   ├── controllers/             # Route controllers (to be implemented)
│   ├── middleware/
│   │   ├── asyncHandler.js      # Async error handling middleware
│   │   └── errorHandler.js      # Custom error handling
│   ├── models/                  # Mongoose models
│   │   ├── User.js             # User accounts and authentication
│   │   ├── Course.js           # Course content and structure
│   │   ├── Lesson.js           # Individual lessons
│   │   ├── Category.js         # Course categories
│   │   ├── Enrollment.js       # Course enrollments
│   │   ├── Quiz.js             # Assessments and quizzes
│   │   ├── Progress.js         # User progress tracking
│   │   └── Notification.js     # User notifications
│   ├── routes/
│   │   ├── auth.js             # Authentication routes
│   │   ├── courses.js          # Course management routes
│   │   └── users.js            # User management routes
│   ├── utils/                  # Utility functions (to be implemented)
│   └── server.js               # Main server file
├── .env                        # Environment variables
├── MODELS.md                   # Detailed models documentation
├── USECASE.puml                # Use case diagram (PlantUML)
├── CLASS_DIAGRAM.puml          # Class diagram (PlantUML)
├── DIAGRAMS.md                 # Diagrams documentation
├── package.json                # Project dependencies and scripts
```

## 🚀 Getting Started

### Prerequisites

- Node.js (v14 or higher)
- MongoDB (local or Atlas)
- npm or yarn

### Installation

1. **Navigate to the backend directory:**
   ```bash
   cd backend
   ```

2. **Install dependencies:**
   ```bash
   npm install
   ```

3. **Create environment file:**
   ```bash
   cp .env.example .env
   ```

4. **Configure your environment variables in `.env`:**
   ```env
   PORT=5000
   NODE_ENV=development
   MONGODB_URI=mongodb://localhost:27017/educative-platform
   JWT_SECRET=your-super-secret-jwt-key
   CLIENT_URL=http://localhost:5173
   ```

### Running the Application

**Development mode (with auto-reload):**
```bash
npm run dev
```

**Production mode:**
```bash
npm start
```

The server will start on `http://localhost:5000` (or your configured PORT).

## 🛠️ API Endpoints

### Authentication Routes (`/api/auth`)
- `POST /api/auth/register` - Register a new user
- `POST /api/auth/login` - Login user
- `GET /api/auth/me` - Get current user profile

### Course Routes (`/api/courses`)
- `GET /api/courses` - Get all courses
- `GET /api/courses/:id` - Get single course
- `POST /api/courses` - Create new course
- `PUT /api/courses/:id` - Update course
- `DELETE /api/courses/:id` - Delete course

### User Routes (`/api/users`)
- `GET /api/users` - Get all users
- `GET /api/users/:id` - Get user by ID
- `PUT /api/users/:id` - Update user
- `DELETE /api/users/:id` - Delete user

### Health Check
- `GET /api/health` - Check if API is running

## 📦 Dependencies

### Production Dependencies
- `express` - Web framework
- `mongoose` - MongoDB object modeling
- `cors` - Cross-origin resource sharing
- `dotenv` - Environment variables management

### Development Dependencies
- `nodemon` - Auto-restart server during development

## 🔧 Development

### Adding New Features

1. **Create a new route file** in `src/routes/`
2. **Create controller functions** in `src/controllers/`
3. **Add Mongoose models** in `src/models/` (if needed)
4. **Register the route** in `src/server.js`

### Example: Adding a new route

1. Create `src/routes/lessons.js`:
```javascript
const express = require('express');
const router = express.Router();
const asyncHandler = require('../middleware/asyncHandler');

router.get('/', asyncHandler(async (req, res) => {
  res.status(200).json({
    success: true,
    message: 'Lessons fetched successfully',
    data: []
  });
}));

module.exports = router;
```

2. Register in `src/server.js`:
```javascript
const lessonRoutes = require('./routes/lessons');
app.use('/api/lessons', lessonRoutes);
```

## 🛡️ Error Handling

The backend includes comprehensive error handling:
- Async error wrapper middleware
- Custom AppError class
- Mongoose error handling
- Global error handler

## 📊 Database

### Local MongoDB Setup
1. Install MongoDB locally
2. Start MongoDB service
3. Update `MONGODB_URI` in `.env`

### MongoDB Atlas (Cloud)
1. Create account at [MongoDB Atlas](https://www.mongodb.com/cloud/atlas)
2. Create a cluster
3. Get connection string
4. Update `MONGODB_URI` in `.env`

## 🔒 Security Features (To be implemented)

- JWT authentication
- Password hashing
- Input validation
- Rate limiting
- CORS configuration
- Security headers

## 📝 Next Steps

1. **Implement Mongoose models** for Users, Courses, Lessons, etc.
2. **Add authentication logic** with JWT
3. **Implement controller functions** for business logic
4. **Add input validation** using express-validator
5. **Set up file upload** for course materials
6. **Add pagination** for large datasets
7. **Implement logging** with winston
8. **Add unit tests** with Jest

## 🤝 Contributing

1. Fork the repository
2. Create your feature branch
3. Commit your changes
4. Push to the branch
5. Open a pull request

## 📄 License

This project is licensed under the ISC License.

## 🆘 Troubleshooting

### Common Issues

**MongoDB Connection Error:**
- Check if MongoDB is running
- Verify `MONGODB_URI` in `.env`
- Ensure network connectivity for Atlas

**Port Already in Use:**
- Change `PORT` in `.env`
- Kill the process using the port

**CORS Error:**
- Check `CLIENT_URL` in `.env`
- Verify frontend is running on correct port

## 📞 Support

For issues and questions, please open an issue in the repository.