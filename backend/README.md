# CineVerse Backend

A Node.js/Express REST API for the CineVerse movie review platform. Provides authentication, movie discovery, review management, and sentiment analysis integration.

*Second Year End Project*

## Overview

CineVerse Backend handles:
- User authentication and authorization
- Movie database management with TMDB integration
- Review creation, editing, and deletion
- User profile management
- Image upload with Cloudinary
- Database persistence with MySQL

## Tech Stack

### Core Framework
- **Express.js**: Web framework
- **Node.js**: JavaScript runtime

### Database & ORM
- **MySQL2**: MySQL client
- **Sequelize**: ORM for MySQL

### Authentication & Security
- **JWT**: Token-based authentication
- **bcryptjs**: Password hashing

### File & Cloud Storage
- **Multer**: File upload middleware
- **Cloudinary**: Cloud image storage

### Utilities
- **Axios**: HTTP client for external APIs
- **CORS**: Cross-origin resource sharing
- **Cookie Parser**: Cookie parsing middleware
- **dotenv**: Environment variable management

## Project Structure

```
backend/
├── config/
│   ├── db.js              # Database configuration & connection
│   └── tmdb.js            # TMDB API configuration
├── controllers/           # Business logic layer
│   ├── authController.js  # Authentication endpoints
│   ├── movieController.js # Movie endpoints
│   ├── reviewController.js # Review endpoints
│   └── userController.js  # User endpoints
├── middleware/
│   └── authMiddleware.js  # JWT authentication middleware
├── models/               # Sequelize database models
│   ├── review.js         # Review model
│   └── User.js           # User model
├── routes/              # API routes
│   ├── authRoutes.js     # Auth routes
│   ├── movieRoutes.js    # Movie routes
│   ├── reviewRoutes.js   # Review routes
│   └── userRoutes.js     # User routes
├── lib/
│   ├── cloudinary.js     # Cloudinary integration
│   └── utils.js          # Utility functions
├── server.js            # Express app setup
├── package.json         # Dependencies and scripts
└── README.md            # This file
```

## Installation

1. Clone the repository and navigate to the backend directory:
```bash
cd backend
```

2. Install dependencies:
```bash
npm install
```

3. Create a `.env` file in the root directory:
```env
# Server
PORT=5000
NODE_ENV=development

# Database
DB_HOST=localhost
DB_USER=root
DB_PASSWORD=your_password
DB_NAME=cineverse
DB_PORT=3306

# JWT
JWT_SECRET=your_secret_key_here

# TMDB API
TMDB_API_KEY=your_tmdb_api_key_here
TMDB_BASE_URL=https://api.themoviedb.org/3

# Cloudinary
CLOUDINARY_NAME=your_cloudinary_name
CLOUDINARY_API_KEY=your_api_key
CLOUDINARY_API_SECRET=your_api_secret

# Frontend URL (for CORS)
FRONTEND_URL=http://localhost:5173

# Sentiment Analysis
SENTIMENT_MODEL_PATH=../ML Models/Sentiment Analysis/Sentiment_model.pkl
```

4. Set up MySQL database:
```bash
mysql -u root -p
CREATE DATABASE cineverse;
```

5. Run migrations/sync models:
```bash
npm run dev
# The Sequelize models will sync on startup
```

## Scripts

### Development
Start the development server with auto-reload:
```bash
npm run dev
```
The server runs on `http://localhost:5000`

### Production
Start the production server:
```bash
npm start
```

## Environment Variables

Create a `.env` file in the backend directory:
```env
# Server
PORT=5000
NODE_ENV=development

# Database
DB_HOST=localhost
DB_USER=root
DB_PASSWORD=your_password
DB_NAME=cineverse
DB_PORT=3306

# JWT
JWT_SECRET=your_secret_key_here

# TMDB API
TMDB_API_KEY=your_tmdb_api_key_here
TMDB_BASE_URL=https://api.themoviedb.org/3

# Cloudinary
CLOUDINARY_NAME=your_cloudinary_name
CLOUDINARY_API_KEY=your_api_key
CLOUDINARY_API_SECRET=your_api_secret

# Frontend URL (for CORS)
FRONTEND_URL=http://localhost:5173

# Sentiment Analysis
SENTIMENT_MODEL_PATH=../ML Models/Sentiment Analysis/Sentiment_model.pkl
```

## Database Schema

### User Table
```sql
CREATE TABLE Users (
  id INT AUTO_INCREMENT PRIMARY KEY,
  email VARCHAR(255) UNIQUE NOT NULL,
  fullName VARCHAR(255) NOT NULL,
  password VARCHAR(255) NOT NULL,
  profilePic VARCHAR(255),
  createdAt TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
  updatedAt TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
```

### Review Table
```sql
CREATE TABLE Reviews (
  id INT AUTO_INCREMENT PRIMARY KEY,
  user_id INT NOT NULL,
  tmdb_id INT NOT NULL,
  rating TINYINT NOT NULL,
  review_text TEXT NOT NULL,
  movie_title VARCHAR(255) NOT NULL,
  poster_path VARCHAR(255),
  sentiment DECIMAL(3,2),
  fake DECIMAL(3,2),
  biased DECIMAL(3,2),
  createdAt TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
  updatedAt TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
  FOREIGN KEY (user_id) REFERENCES Users(id)
);
```

## License

This project is part of CineVerse.
