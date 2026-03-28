# CineVerse Frontend

A modern, responsive React-based web application for discovering movies, writing reviews, and analyzing sentiment patterns in movie reviews. Built with Vite, Tailwind CSS, and modern React patterns.

## Overview

CineVerse Frontend is a feature-rich single-page application that provides users with:
- Movie discovery and search functionality
- Detailed movie information and reviews
- User authentication and profiles
- Review writing and editing capabilities
- Review sentiment analysis
- Responsive design for all devices

## Tech Stack

### Core Framework
- **React** (v19.1.1): UI library with modern hooks
- **React Router** (v7.9.1): Client-side routing
- **Vite** (v7.1.6): Fast build tool and development server

### State Management & API
- **Zustand** (v5.0.8): Lightweight state management
- **Axios** (v1.12.2): HTTP client for API requests

### Styling & UI
- **Tailwind CSS** (v3.4.17): Utility-first CSS framework
- **PostCSS** (v8.5.6): CSS transformations
- **Tailwind Scrollbar Hide** (v4.0.0): Custom scrollbar styling

### Animations & Icons
- **Framer Motion** (v12.23.16): Smooth animations and transitions
- **Lucide React** (v0.544.0): Modern icon library
- **React Icons** (v5.5.0): Popular icon sets
- **React Scroll** (v1.9.3): Smooth scrolling

### UI Components
- **React Range** (v1.10.0): Range slider component

### Development Tools
- **ESLint**: Code quality and consistency
- **Autoprefixer**: CSS vendor prefixing

## Project Structure

```
frontend/
├── public/                 # Static assets
├── src/
│   ├── assets/             # Images, fonts, media files
│   ├── components/         # Reusable React components
│   │   ├── ConfirmationModal.jsx
│   │   ├── EditReview.jsx
│   │   ├── Footer.jsx
│   │   ├── Header.jsx
│   │   ├── MovieDetailLoading.jsx
│   │   ├── ProtectedRoute.jsx
│   │   ├── ReviewForm.jsx
│   │   ├── SearchedMovies.jsx
│   │   └── StarRating.jsx
│   ├── pages/              # Page-level components
│   │   ├── Auth/
│   │   │   ├── Login.jsx
│   │   │   └── Signup.jsx
│   │   ├── Home/
│   │   │   └── Home.jsx
│   │   ├── MovieDetail/
│   │   │   └── MovieDetail.jsx
│   │   ├── Profile/
│   │   │   └── Profile.jsx
│   │   ├── ReviewAnalysis/
│   │   │   └── ReviewAnalysis.jsx
│   │   └── WriteReview/
│   │       └── WriteReview.jsx
│   ├── services/           # API service layer
│   │   └── api.js          # Axios instance and API calls
│   ├── store/              # Zustand stores
│   │   ├── authStore.js    # Authentication state
│   │   ├── movieStore.js   # Movie data state
│   │   └── reviewStore.js  # Review data state
│   ├── App.jsx             # Main app component with routes
│   ├── App.css             # App-level styles
│   ├── index.css           # Global styles
│   └── main.jsx            # React entry point
├── index.html              # HTML template
├── tailwind.config.js      # Tailwind configuration
├── postcss.config.js       # PostCSS configuration
├── eslint.config.js        # ESLint configuration
├── vite.config.js          # Vite configuration
├── package.json            # Dependencies and scripts
└── README.md               # This file
```

## Installation

1. Clone the repository and navigate to the frontend directory:
```bash
cd frontend
```

2. Install dependencies:
```bash
npm install
```

3. Create a `.env` file with backend API configuration:
```env
VITE_API_BASE_URL=http://localhost:5000
```

## Scripts

### Development
Start the development server with hot module replacement:
```bash
npm run dev
```
The app will be available at `http://localhost:5173`

### Build
Create an optimized production build:
```bash
npm run build
```

### Preview
Preview the production build locally:
```bash
npm run preview
```

### Linting
Check code quality and style:
```bash
npm run lint
```

## Key Features

### Authentication
- User signup with validation
- User login with JWT tokens
- Protected routes for authenticated users
- User profile management
- Account deletion

### Movie Discovery
- Browse all movies from TMDB
- Search movies by title
- Filter and sort functionality
- Detailed movie information pages
- Movie recommendations

### Reviews
- Write detailed reviews with star ratings
- Edit existing reviews
- View all reviews for a movie
- Delete reviews
- Star ratings on reviews

### Sentiment Analysis
- Real-time sentiment analysis of reviews
- Confidence scores for predictions
- Review analysis dashboard
- Aggregate sentiment metrics

### User Experience
- Responsive design for mobile/tablet/desktop
- Smooth animations with Framer Motion
- Loading states and error handling
- Toast notifications
- Optimized performance

## API Integration

The frontend communicates with the backend API at `http://localhost:5000/api/`. 

### Main API Endpoints

**Authentication:**
- `POST /auth/signup` - Register new user
- `POST /auth/login` - User login
- `POST /auth/logout` - User logout
- `GET /auth/check` - Verify authentication
- `PUT /auth/update-profile` - Update user profile
- `POST /auth/delete-account` - Delete account

**Movies:**
- `GET /movies` - Get all movies
- `GET /movies/:id` - Get movie details
- `GET /movies/search?q=query` - Search movies

**Reviews:**
- `GET /reviews` - Get all reviews
- `GET /reviews/:id` - Get review details
- `POST /reviews` - Create new review
- `PUT /reviews/:id` - Update review
- `DELETE /reviews/:id` - Delete review

**Users:**
- `GET /users/:id` - Get user profile
- `GET /users/:id/reviews` - Get user's reviews

## State Management (Zustand)

### AuthStore
Manages user authentication state:
- `authUser`: Current authenticated user
- `login(credentials)`: Login user
- `signup(data)`: Register user
- `logout()`: Logout user
- `loadUser()`: Load user from session

### MovieStore
Manages movie data:
- `movies`: List of all movies
- `movieDetails`: Current movie details
- `fetchMovies()`: Fetch all movies
- `fetchMovieById(id)`: Get movie details
- `searchMovies(query)`: Search movies

### ReviewStore
Manages review data:
- `reviews`: List of reviews
- `createReview(data)`: Create new review
- `updateReview(id, data)`: Update review
- `deleteReview(id)`: Delete review
- `fetchReviews()`: Fetch all reviews

## Component Overview

### Page Components
- **Home**: Landing page with movie grid and search
- **MovieDetail**: Detailed movie page with reviews
- **Login**: User login form
- **Signup**: User registration form
- **WriteReview**: Review creation form
- **Profile**: User profile and settings
- **ReviewAnalysis**: Sentiment analysis dashboard
- **EditReview**: Review editing interface

### Reusable Components
- **Header**: Navigation bar
- **Footer**: Footer section
- **ProtectedRoute**: Authentication wrapper
- **StarRating**: 5-star rating selector
- **ReviewForm**: Reusable review input form
- **EditReview**: Review editing component
- **ConfirmationModal**: Confirmation dialog
- **MovieDetailLoading**: Loading skeleton
- **SearchedMovies**: Search results display

## Styling

The frontend uses Tailwind CSS for styling with custom configurations:

### Customization
Edit `tailwind.config.js` to customize:
- Color scheme
- Typography
- Spacing
- Responsive breakpoints

### Global Styles
- `index.css`: Base styles and Tailwind directives
- `App.css`: Component-specific styles

## Environment Variables

Create a `.env.local` file for local development:

```env
# Backend API
VITE_API_BASE_URL=http://localhost:5000

# Optional: Third-party services
VITE_TMDB_API_KEY=your_key_here
```

## Performance Optimization

- **Code Splitting**: Lazy loading with React Router
- **Bundle Analysis**: Monitor with Vite's build analysis
- **Image Optimization**: Optimized images in assets
- **Memoization**: React.memo for expensive components
- **State Optimization**: Minimal state updates

## Browser Support

- Chrome (latest)
- Firefox (latest)
- Safari (latest)
- Edge (latest)

## Development Workflow

1. Create feature branches from `main`
2. Run `npm run dev` for development
3. Run `npm run lint` to check code quality
4. Test features in browser
5. Submit pull request

## Troubleshooting

### Port 5173 already in use
```bash
npm run dev -- --port 5174
```

### API connection issues
- Ensure backend is running on `http://localhost:5000`
- Check `VITE_API_BASE_URL` in `.env`
- Verify CORS configuration in backend

### Style not applying
- Rebuild Tailwind: `npm run build`
- Check class names match Tailwind conventions
- Clear browser cache

### State not updating
- Verify Zustand store is properly exported
- Check dependencies array in useEffect hooks
- Use browser React DevTools extension

## Build for Production

```bash
# Create optimized build
npm run build

# Preview production build
npm run preview

# Deploy to hosting service
# Copy dist/ folder to your hosting provider
```

## Future Enhancements

- [ ] Dark mode support
- [ ] Social sharing features
- [ ] Review comments and discussions
- [ ] User following/followers system
- [ ] Advanced filtering and sorting
- [ ] Movie ratings and recommendations
- [ ] Watchlist functionality
- [ ] Push notifications
- [ ] Progressive Web App (PWA) support

## Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## License

This project is part of CineVerse.

## Support

For issues and questions, please open an issue in the repository or contact the development team.
