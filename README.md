THIS WORK IS UNDERGOING

# Online Mechanic Finder & Assistance App

A comprehensive Flutter application with Node.js backend for connecting users with mechanics and tow services.

## 🚀 Features

### User Features
- ✅ Firebase Authentication (Login/Register)
- ✅ Select vehicle type (2W/4W)
- ✅ Choose issue category (tyre, battery, engine, tow)
- ✅ View nearby mechanics with filtering
- ✅ Filter mechanics by expertise
- ✅ Time slot matching (only shows available mechanics)
- ✅ Call, chat, or video call mechanics
- ✅ Tow service with phone numbers only
- ✅ Beautiful British-style professional UI

### Mechanic Features
- ✅ Firebase Authentication (Login/Register)
- ✅ Set expertise (multiple selections)
- ✅ Upload shop image
- ✅ Toggle availability (Online/Offline)
- ✅ Set daily time slots
- ✅ Accept jobs
- ✅ View user details

### Tow Shops
- ✅ Simple panel
- ✅ Show only phone numbers

## 📁 Project Structure

```
├── lib/
│   ├── config/
│   │   ├── theme.dart          # App theme & colors
│   │   └── api_config.dart     # API endpoints
│   ├── controllers/
│   │   ├── auth_controller.dart
│   │   ├── mechanic_controller.dart
│   │   └── booking_controller.dart
│   ├── models/
│   │   ├── user_model.dart
│   │   ├── mechanic_model.dart
│   │   ├── problem_model.dart
│   │   └── tow_company_model.dart
│   ├── screens/
│   │   ├── auth/
│   │   │   ├── user_registration_screen.dart
│   │   │   └── mechanic_registration_screen.dart
│   │   ├── home/
│   │   ├── problems/
│   │   ├── mechanics/
│   │   │   ├── mechanic_dashboard_screen.dart
│   │   │   ├── mechanic_jobs_screen.dart
│   │   │   └── mechanic_job_details_screen.dart
│   │   ├── tow/
│   │   ├── profile/
│   │   └── video_call/
│   ├── services/
│   │   ├── firebase_auth_service.dart
│   │   ├── firebase_storage_service.dart
│   │   ├── api_service.dart
│   │   ├── user_service.dart
│   │   ├── mechanic_service.dart
│   │   └── notification_service.dart
│   └── widgets/
│
└── backend/
    ├── config/
    │   └── database.js
    ├── models/
    │   ├── User.js
    │   └── Mechanic.js
    ├── routes/
    │   ├── users.js
    │   ├── mechanics.js
    │   ├── bookings.js
    │   ├── towCompanies.js
    │   └── notifications.js
    ├── middleware/
    │   └── auth.js
    ├── database/
    │   └── schema.sql
    ├── server.js
    └── package.json
```

## 🎨 Design

### Colors
- **Royal Blue**: `#0050FF`
- **Pure White**: `#FFFFFF`
- **Dark Navy**: `#001B44`

### Style
- Clean, modern British professional design
- Large icons and graphics for easy understanding
- Rounded cards with professional spacing

## 🔧 Setup Instructions

### Flutter App Setup

1. **Install Dependencies**
   ```bash
   flutter pub get
   ```

2. **Firebase Setup**
   - Create a Firebase project
   - Add Android/iOS apps to Firebase
   - Download `google-services.json` (Android) and `GoogleService-Info.plist` (iOS)
   - Place them in the appropriate directories

3. **Configure API Base URL**
   - Update `lib/config/api_config.dart` with your backend URL

4. **Run the App**
   ```bash
   flutter run
   ```

### Backend Setup

1. **Install Dependencies**
   ```bash
   cd backend
   npm install
   ```

2. **Database Setup**
   - Create MySQL database
   - Run `backend/database/schema.sql` to create tables
   - Update `.env` file with database credentials

3. **Firebase Admin Setup**
   - Get Firebase Admin SDK credentials
   - Update `.env` file with Firebase credentials

4. **Environment Variables**
   ```bash
   cp .env.example .env
   # Edit .env with your credentials
   ```

5. **Run Server**
   ```bash
   npm start        # Production
   npm run dev      # Development (with nodemon)
   ```

## 📱 API Endpoints

### Users
- `POST /api/users` - Create user profile
- `GET /api/users/:id` - Get user profile
- `PUT /api/users/:id` - Update user profile
- `GET /api/users/:id/bookings` - Get user bookings

### Mechanics
- `POST /api/mechanics` - Create mechanic profile
- `GET /api/mechanics/:id` - Get mechanic profile
- `PUT /api/mechanics/:id` - Update mechanic profile
- `PUT /api/mechanics/:id/availability` - Toggle availability
- `GET /api/mechanics/search` - Search mechanics
- `GET /api/mechanics/:id/bookings` - Get mechanic bookings

### Bookings
- `POST /api/bookings` - Create booking
- `GET /api/bookings/:id` - Get booking details
- `POST /api/bookings/:id/accept` - Accept booking

### Tow Companies
- `GET /api/tow-companies` - Get all tow companies
- `GET /api/tow-companies/:id` - Get tow company details

### Notifications
- `POST /api/notifications/token` - Save FCM token
- `POST /api/notifications/send` - Send notification

## 🔐 Authentication

The app uses Firebase Authentication for user authentication. All API requests require a Bearer token in the Authorization header:

```
Authorization: Bearer <firebase-id-token>
```

## 📦 Dependencies

### Flutter
- `firebase_core`, `firebase_auth`, `firebase_storage`, `firebase_messaging`
- `get` (State management)
- `dio` (HTTP client)
- `image_picker` (Image selection)
- `geolocator` (Location services)

### Backend
- `express` (Web framework)
- `mysql2` (Database)
- `firebase-admin` (Firebase Admin SDK)
- `jsonwebtoken` (JWT tokens)
- `cors`, `helmet`, `morgan` (Security & logging)

## 🚧 Next Steps

1. Complete Firebase configuration
2. Set up backend server
3. Configure database
4. Test all features
5. Deploy to production

## 📝 License

This project is licensed under the MIT License.

