# Kinniya Ride Mobile App

A Flutter-based mobile application for the Kinniya Ride platform, providing native Android and iOS apps for passengers, drivers, and administrators.

## Features

### Passenger App
- **User Authentication**: Secure login and registration
- **Location Services**: GPS-based pickup location detection
- **Vehicle Selection**: Choose between bikes and 3-wheelers
- **Ride Booking**: Book rides with estimated fare calculation
- **Ride History**: View past rides and trip details
- **Multi-language Support**: Tamil, Sinhala, and English

### Driver App
- **Driver Dashboard**: Online/offline status management
- **Profile Management**: Vehicle and license information
- **Ride Requests**: Receive and manage ride requests
- **Earnings Tracking**: View ride history and earnings
- **Status Management**: Real-time availability updates

### Admin App
- **System Overview**: Dashboard with key metrics
- **Driver Management**: Approve and manage driver accounts
- **Ride Monitoring**: Track all rides in the system
- **Settings**: Configure fares and system settings

## Technical Architecture

### Frontend (Flutter)
- **Framework**: Flutter 3.10+ with Dart 3.0+
- **State Management**: Provider pattern for state management
- **Navigation**: GoRouter for declarative routing
- **HTTP Client**: Dio for API communication
- **Maps Integration**: Google Maps Flutter for location services
- **Local Storage**: SharedPreferences for app settings

### API Integration
- **Base URL**: Connects to the existing Replit web backend
- **Authentication**: Session-based authentication with the web API
- **Real-time Updates**: HTTP polling for live ride updates
- **Error Handling**: Comprehensive error states and user feedback

### Key Dependencies
```yaml
dependencies:
  flutter: sdk: flutter
  provider: ^6.0.5           # State management
  go_router: ^12.1.3         # Navigation
  dio: ^5.3.2               # HTTP client
  google_maps_flutter: ^2.5.0 # Maps
  location: ^5.0.3          # GPS location
  shared_preferences: ^2.2.2 # Local storage
  intl: ^0.19.0            # Internationalization
```

## Getting Started

### Prerequisites
- Flutter SDK 3.10 or higher
- Android Studio / Xcode for development
- Google Maps API key
- Access to the Kinniya Ride backend API

### Installation

1. **Clone the repository**:
   ```bash
   git clone <repository-url>
   cd mobile
   ```

2. **Install dependencies**:
   ```bash
   flutter pub get
   ```

3. **Configure API endpoint**:
   Update `lib/utils/constants.dart` with your Replit app URL:
   ```dart
   static const String baseUrl = 'https://your-repl-name.replit.app/api';
   ```

4. **Add Google Maps API key**:
   - Android: Update `android/app/src/main/AndroidManifest.xml`
   - iOS: Update `ios/Runner/AppDelegate.swift`

5. **Run the app**:
   ```bash
   flutter run
   ```

## Project Structure

```
mobile/
├── lib/
│   ├── main.dart                 # App entry point
│   ├── models/                   # Data models
│   │   ├── user.dart
│   │   ├── ride.dart
│   │   └── driver.dart
│   ├── providers/                # State management
│   │   ├── auth_provider.dart
│   │   ├── ride_provider.dart
│   │   └── location_provider.dart
│   ├── services/                 # API and external services
│   │   └── api_service.dart
│   ├── screens/                  # UI screens
│   │   ├── auth/
│   │   ├── passenger/
│   │   ├── driver/
│   │   └── admin/
│   ├── widgets/                  # Reusable UI components
│   └── utils/                    # Constants and utilities
│       ├── constants.dart
│       └── theme.dart
├── android/                      # Android-specific code
├── ios/                         # iOS-specific code
└── pubspec.yaml                 # Dependencies and metadata
```

## Configuration

### API Configuration
The app connects to your Replit backend API. Update the base URL in `lib/utils/constants.dart`:

```dart
class AppConstants {
  static const String baseUrl = 'https://your-repl-name.replit.app/api';
  // ... other constants
}
```

### Theme Customization
The app supports role-based theming:
- **Passenger**: Green theme (#22C55E)
- **Driver**: Blue theme (#3B82F6)  
- **Admin**: Purple theme (#6366F1)

Themes are defined in `lib/utils/theme.dart` and automatically applied based on user type.

### Permissions
The app requires the following permissions:
- **Location**: For GPS-based pickup and navigation
- **Internet**: For API communication
- **Camera**: For profile photos and document uploads
- **Phone**: For calling drivers/passengers during rides

## Building for Production

### Android
```bash
flutter build apk --release
# Or for App Bundle
flutter build appbundle --release
```

### iOS
```bash
flutter build ios --release
```

## Testing

Run unit tests:
```bash
flutter test
```

## Deployment

### Android
1. Sign the APK with your keystore
2. Upload to Google Play Console
3. Configure app metadata and screenshots

### iOS
1. Archive the app in Xcode
2. Upload to App Store Connect
3. Submit for App Store review

## Integration with Web Backend

The mobile app is designed to work seamlessly with the existing Kinniya Ride web platform:

- **Shared Database**: Uses the same PostgreSQL database
- **Compatible APIs**: All endpoints work with both web and mobile clients
- **Session Management**: Maintains user sessions across platforms
- **Real-time Sync**: Ride status updates sync between web and mobile

## Localization

The app supports three languages for the Kinniya region:
- **English** (default)
- **Tamil** (primary local language)
- **Sinhala** (national language)

Language files are stored in `assets/lang/` and managed through the `intl` package.

## Support

For technical issues or feature requests, please contact the development team or create an issue in the project repository.