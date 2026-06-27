# 🌱 Eco Commute Tracker

A native mobile application for UTM students to track eco-friendly commutes and earn rewards while promoting sustainable transportation.

## 📱 Overview

**Eco Commute Tracker** gamifies sustainable commuting by:
- Tracking user distance via geolocation
- Awarding points based on transport mode (walking, cycling, bus, carpooling)
- Converting points to UTM Merit Points or campus rewards
- Running an eco-friendly shop for used book exchanges with sustainability bonuses

## 🎨 Theme & Branding

- **Primary Color**: UTM Dark Red (#8B0000)
- **Secondary Color**: Crimson (#DC143C)
- **Accent**: Gold (#FFD700) for points/achievements
- **Logo**: Eco Commute branding integrated throughout

## 🚀 Getting Started

### Prerequisites

- Node.js (v16 or higher)
- npm or yarn
- Expo CLI: `npm install -g expo-cli`
- Firebase account (for backend)

### Installation

1. **Clone/Navigate to project**:
   ```bash
   cd eco-commute-tracker
   ```

2. **Install dependencies**:
   ```bash
   npm install
   ```

3. **Configure Firebase**:
   - Create a Firebase project at https://console.firebase.google.com
   - Get your Firebase config (API keys, etc.)
   - Update `.env` file with your credentials:
     ```
     EXPO_PUBLIC_FIREBASE_API_KEY=your_api_key
     EXPO_PUBLIC_FIREBASE_AUTH_DOMAIN=your_auth_domain
     EXPO_PUBLIC_FIREBASE_PROJECT_ID=your_project_id
     EXPO_PUBLIC_FIREBASE_STORAGE_BUCKET=your_storage_bucket
     EXPO_PUBLIC_FIREBASE_MESSAGING_SENDER_ID=your_sender_id
     EXPO_PUBLIC_FIREBASE_APP_ID=your_app_id
     ```

4. **Start the app**:
   ```bash
   npm start
   ```

5. **Run on your device**:
   - **iOS**: `npm run ios` (requires Mac)
   - **Android**: `npm run android`
   - **Expo Go**: Scan QR code with Expo Go app

## 📚 Project Structure

```
src/
├── App.tsx                      # Main app entry point
├── theme/                       # Design system
│   ├── colors.ts               # UTM color palette
│   ├── typography.ts           # Font scales
│   └── spacing.ts              # Spacing & shadows
├── services/                    # Business logic
│   ├── FirebaseService.ts      # Firebase setup
│   ├── AuthService.ts          # Authentication
│   ├── LocationService.ts      # GPS tracking (Phase 3)
│   └── PointsService.ts        # Points calculations (Phase 2)
├── context/                     # React Context state
│   ├── AuthContext.tsx         # Auth state
│   └── UserContext.tsx         # User data (Phase 2)
├── screens/                     # Screen components
│   ├── auth/                   # Login/Register
│   ├── main/                   # Dashboard/Rewards/Shop
│   └── trip/                   # Trip tracking
└── components/
    └── Navigation/             # Navigation stacks
```

## 🔐 Authentication

### Signup Flow
1. User enters: name, email, phone, password
2. Firebase creates account
3. User profile created in Firestore
4. Points balance initialized to 0

### Login Flow
1. User enters: email, password
2. Firebase authenticates
3. Auth state restored from persistence
4. Navigate to home dashboard

### Features
- ✅ Email/password authentication
- ✅ Input validation (email format, password strength)
- ✅ Error handling with user-friendly messages
- ✅ Show/hide password toggle
- ✅ Forgot password option
- ✅ Secure token management

## 💡 Points System

### Point Multipliers
- **Walking**: 100 points/km
- **Cycling**: 100 points/km
- **Public Bus**: 75 points/km
- **Carpooling**: 50 points/km

### Reward Conversions
1. **Merit Points**: 100 Eco-points = 10 Merit Points
2. **Vouchers**: Campus cafe/restaurant discounts
3. **Eco-Shop**: Used books with 10% bonus on purchase

### 10% Sustainability Bonus
When purchasing a book:
- Bonus calculated on EXISTING balance (before purchase)
- Formula: `new_balance = balance - book_cost + (balance × 0.10)`
- Example: 150 points - 50 (book) + 15 (bonus) = 115 points

## 🗺️ Navigation Structure

```
Root Navigator
├── Auth Stack (not logged in)
│   ├── Login Screen
│   └── Register Screen
└── Main Tab Navigator (logged in)
    ├── Home Stack
    │   ├── Home (Dashboard)
    │   └── Start Trip
    ├── Rewards Screen
    ├── Shop Screen
    └── Profile Screen
```

## 📋 Development Phases

### Phase 1: ✅ COMPLETE
- Expo project setup
- Firebase configuration
- Authentication system
- Login/Register UI
- Navigation structure
- UTM theme implementation

### Phase 2: ⏳ IN PROGRESS
- Firestore database schema
- Points engine & Cloud Functions
- Geolocation service
- Trip tracking UI

### Phase 3: 🔜 NEXT
- Rewards dashboard
- Merit points converter
- Voucher redemption
- Eco-friendly shop marketplace
- Profile management

### Phase 4: 🔜 LATER
- Testing & QA
- Performance optimization
- Deployment to App Stores

## 🔧 Configuration

### Environment Variables
Create a `.env` file from `.env.example`:

```bash
cp .env.example .env
```

Then update with your Firebase credentials.

### Firebase Setup

1. **Firestore Database**
   - Enable Firestore
   - Collections: users, books, orders, vouchers, etc.
   - Security rules configured for user privacy

2. **Authentication**
   - Enable Email/Password auth
   - Enable Google OAuth (optional)

3. **Cloud Storage**
   - For profile pictures and book images

4. **Cloud Functions**
   - Points calculation
   - Merit points conversion
   - Book purchase processing

## 🎯 Key Features

### Current (Phase 1)
- ✅ User authentication
- ✅ Sign up/login screens
- ✅ Auth state persistence
- ✅ UTM-themed UI
- ✅ Navigation structure

### In Development (Phase 2)
- 🔄 Firestore collections
- 🔄 Points calculation engine
- 🔄 Geolocation tracking
- 🔄 Trip summaries

### Coming Soon (Phase 3)
- 📅 Rewards dashboard
- 📅 Merit conversion
- 📅 Voucher redemption
- 📅 Book marketplace

## 📱 Screen List

| Screen | Status | Purpose |
|--------|--------|---------|
| Login | ✅ Complete | User authentication |
| Register | ✅ Complete | New account creation |
| Home | ✅ Complete | Dashboard with points |
| Start Trip | 🔄 In Progress | Trip mode selection |
| Trip Tracking | 🔄 In Progress | Real-time GPS tracking |
| Trip Summary | 🔄 In Progress | Trip results & points earned |
| Rewards | ⏳ Planned | Conversion & redemption options |
| Shop | ⏳ Planned | Book marketplace |
| Profile | ⏳ Planned | User profile & settings |

## 🧪 Testing

```bash
# Run tests
npm test

# Run tests in watch mode
npm run test:watch
```

## 🚀 Deployment

### Staging
```bash
npm run build:staging
```

### Production
```bash
npm run build:production
eas submit
```

## 📖 Documentation

- [Requirements](/.kiro/specs/eco-commute-tracker/requirements.md)
- [Design](/.kiro/specs/eco-commute-tracker/design.md)
- [Tasks](/.kiro/specs/eco-commute-tracker/tasks.md)

## 🤝 Contributing

1. Create a feature branch
2. Make your changes
3. Submit a pull request

## 📝 License

Private project for UTM

## 🆘 Troubleshooting

### npm/npx not found
- Install Node.js from https://nodejs.org
- Restart your terminal after installation

### Firebase connection errors
- Verify `.env` credentials are correct
- Check Firebase console for any errors
- Ensure Firestore is enabled in your project

### Location permissions
- iOS: Check Info.plist for location permissions
- Android: Check AndroidManifest.xml permissions

## 📞 Support

For issues or questions, contact the development team.

---

**Happy commuting! 🚴‍♀️🚶‍♂️🚌**
