# CineVerse 🎬

A full-stack movie review platform with AI-powered sentiment analysis. Discover movies, write reviews, and get intelligent insights about review sentiments.

*Second Year End Project*

**Live Application:** [https://cineverse-iig9.onrender.com/](https://cineverse-iig9.onrender.com/)

---

## 📋 Table of Contents

- [Project Overview](#project-overview)
- [Tech Stack](#tech-stack)
- [Project Structure](#project-structure)
- [Quick Start](#quick-start)
- [Installation & Setup](#installation--setup)
- [Environment Variables](#environment-variables)
- [Running the Application](#running-the-application)
- [Key Features](#key-features)
- [ML Models](#ml-models)
- [Database Schema](#database-schema)
- [Team](#team)
- [License](#license)

---

## 🎯 Project Overview

CineVerse is a full-stack web application that allows movie enthusiasts to discover, review, and discuss films. It combines:

- **Movie Discovery**: Search and explore thousands of movies powered by TMDB API
- **User Reviews**: Write, edit, and manage detailed movie reviews with star ratings
- **Sentiment Analysis**: AI-powered analysis of review content to detect sentiment
- **User Profiles**: Personalized user accounts with profile management and review history
- **Social Features**: View reviews from other users, track popular movies and trends

### Key Goals

✅ Provide an intuitive movie discovery platform  
✅ Enable meaningful user engagement through reviews  
✅ Leverage ML for content analysis  
✅ Ensure scalability and performance  
✅ Maintain data security and user privacy

---

## 💻 Tech Stack

### Frontend
- **React** - UI Library
- **Vite** - Build Tool & Dev Server
- **React Router** - Client-side Routing
- **Zustand** - State Management
- **Axios** - HTTP Client
- **Tailwind CSS** - Styling
- **Framer Motion** - Animations

### Backend
- **Node.js** - Runtime
- **Express.js** - Web Framework
- **Sequelize** - ORM
- **MySQL** - Database
- **JWT** - Authentication
- **bcryptjs** - Password Hashing
- **Cloudinary** - Image Storage

### ML/Python
- **Flask** - API Framework
- **scikit-learn** - ML Algorithms
- **pandas** - Data Processing
- **NumPy** - Numerical Computing
- **spaCy** - NLP Processing

### External APIs
- **TMDB API** - Movie Data Source
- **Cloudinary** - Image Hosting

---

## 📁 Project Structure

```
CineVerse/
│
├── frontend/                          # React + Vite Application
│   ├── src/
│   │   ├── components/                # Reusable React components
│   │   ├── pages/                     # Page-level components (Home, MovieDetail, etc.)
│   │   ├── store/                     # Zustand stores (auth, movie, review)
│   │   ├── services/                  # API service layer
│   │   ├── assets/                    # Images and static files
│   │   ├── App.jsx                    # Main app component with routes
│   │   ├── main.jsx                   # Entry point
│   │   └── index.css                  # Global styles
│   ├── vite.config.js                 # Vite configuration
│   ├── tailwind.config.js             # Tailwind CSS configuration
│   ├── package.json                   # Dependencies
│   ├── README.md                      # Frontend documentation
│   └── index.html                     # HTML template
│
├── backend/                           # Node.js + Express API
│   ├── config/
│   │   ├── db.js                      # MySQL/Sequelize configuration
│   │   └── tmdb.js                    # TMDB API configuration
│   ├── controllers/                   # Business logic
│   │   ├── authController.js          # Authentication logic
│   │   ├── movieController.js         # Movie API logic
│   │   ├── reviewController.js        # Review API logic
│   │   └── userController.js          # User API logic
│   ├── models/                        # Sequelize Models
│   │   ├── User.js                    # User model
│   │   └── review.js                  # Review model
│   ├── routes/                        # API Routes
│   │   ├── authRoutes.js              # Auth endpoints
│   │   ├── movieRoutes.js             # Movie endpoints
│   │   ├── reviewRoutes.js            # Review endpoints
│   │   └── userRoutes.js              # User endpoints
│   ├── middleware/
│   │   └── authMiddleware.js          # JWT authentication middleware
│   ├── lib/
│   │   ├── cloudinary.js              # Cloudinary integration
│   │   └── utils.js                   # Utility functions
│   ├── server.js                      # Express app setup
│   ├── package.json                   # Dependencies
│   ├── README.md                      # Backend documentation
│   └── .env.example                   # Environment variables template
│
├── ML Models/                         # Machine Learning Models
│   ├── Flask API/
│   │   ├── app.py                     # Flask application
│   │   ├── resources/
│   │   │   ├── Sentiment_model.py     # Sentiment analysis model
│   │   │   ├── Hate_speech_model.py   # Hate speech detection model
│   │   │   └── models/                # Trained model files
│   │   ├── requirements.txt           # Python dependencies
│   │   └── README.md                  # ML API documentation
│   │
│   └── Sentiment Analysis/
│       ├── Sentiment.ipynb            # Training notebook
│       ├── data/
│       │   └── review.csv             # Training dataset
│       ├── Sentiment_model.pkl        # Trained model
│       ├── requirements.txt           # Dependencies
│       └── README.md                  # Model documentation
│
└── README.md                          # This file (Root README)
```

---

## 🚀 Quick Start

### Prerequisites
- **Node.js** v16+ and npm
- **Python** 3.8+ and pip
- **MySQL** 5.7+ (or MariaDB)
- **Git**

### 1 Minute Setup
```bash
# Clone repository
git clone https://github.com/Nikhil-vaishnav-17/CineVerse.git
cd CineVerse

# Frontend
cd frontend
npm install
npm run dev

# Backend (in new terminal)
cd backend
npm install
npm run dev

# ML Models (in new terminal)
cd "ML Models/Flask API"
pip install -r requirements.txt
python app.py
```

---

## 📦 Installation & Setup

### Backend Setup

#### 1. Prerequisites
```bash
# Create MySQL Database
mysql -u root -p
CREATE DATABASE cineverse;
EXIT;
```

#### 2. Install Dependencies
```bash
cd backend
npm install
```

#### 3. Environment Configuration
Create `.env` file in backend directory:
```env
# Server Configuration
PORT=5000
NODE_ENV=development

# Database Configuration
DB_HOST=localhost
DB_USER=root
DB_PASSWORD=your_mysql_password
DB_NAME=cineverse
DB_PORT=3306

# JWT Configuration
JWT_SECRET=your_very_secret_jwt_key_here

# TMDB API Configuration
TMDB_API_KEY=your_tmdb_api_key
TMDB_BASE_URL=https://api.themoviedb.org/3

# Cloudinary Configuration
CLOUDINARY_CLOUD_NAME=your_cloudinary_name
CLOUDINARY_API_KEY=your_cloudinary_key
CLOUDINARY_API_SECRET=your_cloudinary_secret

# CORS Configuration
FRONTEND_URL=http://localhost:5173
```

#### 4. Start Backend
```bash
npm run dev
```
Backend runs on `http://localhost:5000`

---

### Frontend Setup

#### 1. Install Dependencies
```bash
cd frontend
npm install
```

#### 2. Environment Configuration
Create `.env` or `.env.local`:
```env
VITE_API_URL=http://localhost:5000/api
VITE_API_BASE_URL=http://localhost:5000/api
```

#### 3. Start Development Server
```bash
npm run dev
```
Frontend available at `http://localhost:5173`

#### 4. Build for Production
```bash
npm run build
```

---

### ML Models (Flask API) Setup

#### 1. Navigate to ML API Directory
```bash
cd "ML Models/Flask API"
```

#### 2. Create Virtual Environment (Optional but Recommended)
```bash
python -m venv venv

# Activate
# On macOS/Linux:
source venv/bin/activate

# On Windows:
venv\Scripts\activate
```

#### 3. Install Dependencies
```bash
pip install -r requirements.txt
python -m spacy download en_core_web_sm
```

#### 4. Start Flask Server
```bash
python app.py
```
Flask API runs on `http://localhost:5000` (Note: Change port if backend is on 5000)

---

## 🔐 Environment Variables

### Backend (.env)
```env
# Essential for production
JWT_SECRET=super_secret_key_with_at_least_32_chars
DB_PASSWORD=strong_mysql_password
TMDB_API_KEY=your_actual_tmdb_key
CLOUDINARY_API_SECRET=your_cloudinary_secret

# Standard setup
PORT=5000
NODE_ENV=production
DB_HOST=localhost
DB_USER=root
DB_NAME=cineverse
DB_PORT=3306
TMDB_BASE_URL=https://api.themoviedb.org/3
CLOUDINARY_CLOUD_NAME=your_name
CLOUDINARY_API_KEY=your_key
FRONTEND_URL=https://yourdomain.com
```

### Frontend (.env or .env.local)
```env
VITE_API_URL=https://your-backend-api.com/api
VITE_API_BASE_URL=https://your-backend-api.com/api
```

---

## ▶️ Running the Application

### Development Mode

**Terminal 1 - Backend**
```bash
cd backend
npm run dev
# Runs on http://localhost:5000
```

**Terminal 2 - Frontend**
```bash
cd frontend
npm run dev
# Runs on http://localhost:5173
```

**Terminal 3 - ML API** (Optional)
```bash
cd "ML Models/Flask API"
python app.py
# Runs on http://localhost:5000 (adjust port if needed)
```

### Production Mode

**Backend**
```bash
cd backend
npm start
```

**Frontend**
```bash
cd frontend
npm run build
npm run preview
# For deployment, copy dist/ folder to your hosting
```

---

## ✨ Key Features

### 🎬 Movie Discovery
- Search movies by title in real-time
- Browse trending movies (top 10)
- Filter by genre and release year range
- Detailed movie information pages
- Movie ratings and descriptions from TMDB

### 👤 User Management
- User registration with email and password
- Secure login with JWT authentication
- Profile management with avatar upload
- Account deletion capability
- Password hashing with bcryptjs

### ⭐ Review System
- Write detailed movie reviews
- Rate movies on 1-10 scale
- Edit and delete reviews
- View all reviews for a movie
- User-specific review history
- Automatic timestamp tracking

### 🤖 AI-Powered Analysis
- **Sentiment Analysis**: Classify review sentiment as positive/negative
- Confidence scores for predictions
- Real-time processing

### 📊 Analytics & Insights
- Review analysis dashboard
- Aggregate sentiment metrics
- Popular reviews section
- User statistics

### 🎨 User Experience
- Responsive design (mobile/tablet/desktop)
- Smooth animations with Framer Motion
- Loading states and error handling
- Optimized performance

---

## 🧠 ML Models

### Sentiment Analysis Model
- **Algorithm**: Logistic Regression
- **Feature Extraction**: TF-IDF Vectorizer
  - Max features: 50,000
  - N-gram range: 1-2 (unigrams and bigrams)
  - Min document frequency: 2
  - Max document frequency: 95%
- **Additional Features**: Star ratings (weight: 0.0048)
- **Preprocessing**: Lemmatization, stopword removal, text cleaning
- **Output**: Positive/Negative classification with confidence score

### Hate Speech Detection Model
- **Algorithm**: Text Classification
- **Feature**: TF-IDF vectors
- **Output**: Hate/Not Hate classification with confidence

### Model Training
- **Data**: IMDB movie reviews dataset
- **Training**: Jupyter notebook in `ML Models/Sentiment Analysis/Sentiment.ipynb`
- **Evaluation**: Accuracy, F1-score, classification reports
- **Serialization**: Pickle format for easy loading

For detailed model documentation, see [Sentiment Analysis README](ML%20Models/Sentiment%20Analysis/README.md).

---

## 🗄️ Database Schema

### User Table
```sql
CREATE TABLE Users (
  id INT AUTO_INCREMENT PRIMARY KEY,
  email VARCHAR(255) UNIQUE NOT NULL,
  fullName VARCHAR(255) NOT NULL,
  password VARCHAR(255) NOT NULL,
  profilePic VARCHAR(255),
  createdAt TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
  updatedAt TIMESTAMP DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP
);
```

### Review Table
```sql
CREATE TABLE Reviews (
  id INT AUTO_INCREMENT PRIMARY KEY,
  user_id INT NOT NULL,
  tmdb_id INT NOT NULL,
  rating TINYINT NOT NULL (1-10),
  review_text TEXT NOT NULL,
  movie_title VARCHAR(255) NOT NULL,
  poster_path VARCHAR(255),
  sentiment DECIMAL(3,2),
  fake DECIMAL(3,2),
  biased DECIMAL(3,2),
  createdAt TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
  updatedAt TIMESTAMP DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP,
  FOREIGN KEY (user_id) REFERENCES Users(id)
);
```

---

## � Live Links

| Service | URL |
|---------|-----|
| **Application** | [https://cineverse-iig9.onrender.com/](https://cineverse-iig9.onrender.com/) |
| **GitHub Repo** | https://github.com/Nikhil-vaishnav-17/CineVerse |

---

## 📚 Documentation

- [Frontend Documentation](frontend/README.md)
- [Backend Documentation](backend/README.md)
- [ML Models Documentation](ML%20Models/Sentiment%20Analysis/README.md)

---

## 📝 License

This project is licensed under the ISC License - see the file below for details.

```
ISC License

Copyright (c) 2024 CineVerse Team

Permission to use, copy, modify, and/or distribute this software for any purpose with or without fee is hereby granted, provided that the above copyright notice and this permission notice appear in all copies.
```

---

## 👥 Team

- **UI/UX**: Nikhil Jangid
- **ML Components**: Nikhil Vaishnav, Neelam Nagar
- **Web Development**: Neeraj Prajapat

### Special Thanks
- TMDB for movie data API
- Cloudinary for image hosting
- Render for hosting platform
- Open source community

---

## �️ Future Enhancements

- [ ] Dark mode support
- [ ] Social sharing features
- [ ] Review comments and discussions
- [ ] User following/followers system
- [ ] Advanced filtering and sorting
- [ ] Watchlist functionality
- [ ] Mobile app support

---

**Made with ❤️ by the CineVerse Team**

Last Updated: March 28, 2024
