# Guardian AI - Project Status

## 📱 Project Overview

**Guardian AI** is a parental control and privacy protection mobile application for Android. It's a single Android application with role-based logins (Parent and Child) that enables parents to monitor and control child device usage.

## ✅ Completed Modules

### 1. Project Structure & Setup
- ✅ Single Android app module (`:app`) with role-based authentication
- ✅ Java-based implementation (not Kotlin)
- ✅ Package structure organized:
  - `data/model/` - Data models (User, UserRole, QRPairingData)
  - `ui/auth/` - Authentication activities
  - `ui/parent/` - Parent dashboard
  - `ui/child/` - Child dashboard
  - `network/` - Firebase integration services
  - `utils/` - Utility classes (validators, QR generator)
- ✅ Application class (`GuardianAIApplication`) for Firebase initialization

### 2. Dependencies & Build Configuration
- ✅ Firebase BOM configured
  - Firebase Authentication (Email/Password + Anonymous)
  - Firebase Firestore
- ✅ Lifecycle components (ViewModel, LiveData)
- ✅ Material Design Components
- ✅ Biometric Authentication (AndroidX Biometric)
- ✅ ZXing library for QR code generation and scanning
- ✅ View Binding enabled
- ✅ Gradle configuration optimized

### 3. Login Module (COMPLETED ✅)

#### Authentication Features:
- ✅ **Parent Sign-up & Login**
  - Email/Password registration
  - Email verification via link
  - Strong password validation (regex checks)
  - Email format validation
  - Sign-up success screen
  - Login with email verification check

- ✅ **Security & Validation**
  - Email validator with regex
  - Password strength validator (min 8 chars, uppercase, lowercase, number, special char)
  - Input validation and error handling
  - Firebase authentication integration

- ✅ **QR-Handshake Enrollment**
  - QR code generation on parent dashboard
  - QR code scanning on child device
  - Secure password-less pairing via QR scan
  - Automatic child account creation (anonymous auth)
  - Device pairing stored in Firestore
  - Token expiration (10 minutes)
  - Child login info screen with instructions

- ✅ **Biometric App Lock**
  - Biometric authentication support (Fingerprint/FaceID)
  - Integrated in parent dashboard (ready for implementation)

#### UI Screens Implemented:
- ✅ Splash Activity
- ✅ Role Selection Activity (Parent/Child)
- ✅ Login Activity (Parent)
- ✅ Sign Up Activity (Parent only)
- ✅ Sign Up Success Activity
- ✅ Forgot Password Activity
- ✅ Forgot Password Success Activity
- ✅ Email Verification Activity
- ✅ Login Success Activity
- ✅ Child Login Info Activity
- ✅ QR Scan Activity
- ✅ Parent Dashboard Activity
- ✅ Child Dashboard Activity

#### Network Services:
- ✅ `AuthService` - Handles Firebase authentication
  - Parent registration
  - Parent login
  - Password reset
  - Email verification
  - Current user management

- ✅ `QRPairingService` - Handles QR code pairing
  - QR code generation
  - Pairing token creation
  - QR code validation
  - Automatic child account creation
  - Device pairing management

#### Utilities:
- ✅ `EmailValidator` - Email format validation
- ✅ `PasswordValidator` - Password strength validation
- ✅ `QRCodeGenerator` - QR code bitmap generation

### 4. Firebase Integration
- ✅ Firebase Authentication configured
  - Email/Password enabled
  - Anonymous Authentication enabled (for child accounts)
- ✅ Firestore Database configured
  - Security rules set up
  - Collections: `users`, `pairing_tokens`, `device_pairs`
- ✅ Application-level Firebase initialization
- ✅ Error handling for Firebase operations

### 5. Permissions & Manifest
- ✅ Internet permission
- ✅ Network state permission
- ✅ Camera permission (for QR scanning)
- ✅ All activities registered in AndroidManifest
- ✅ Application class registered

## ⏳ Next Steps (To Be Implemented)

### 1. Parent Dashboard Features
- [ ] Biometric lock implementation
- [ ] Child device list/management
- [ ] View child device status
- [ ] Generate/regenerate QR codes
- [ ] Settings screen

### 2. Child Dashboard Features
- [ ] Display pairing status
- [ ] Show parent information
- [ ] Settings screen

### 3. Monitoring & AI Features (Child Device)
- [ ] Background monitoring service
- [ ] App usage tracking
- [ ] Location tracking
- [ ] Sensor data collection
- [ ] Rule enforcement engine
- [ ] AI model integration (TensorFlow Lite)
- [ ] LSTM Autoencoder for anomaly detection
- [ ] Audio keyword detection

### 4. Parent Control Features
- [ ] Real-time child device monitoring
- [ ] Alert management
- [ ] Rule configuration UI
- [ ] Safety rules enforcement
- [ ] Data visualization
- [ ] Remote control commands

### 5. Data Storage
- [ ] Room Database setup (for local storage on child device)
- [ ] Local data models
- [ ] Data synchronization with Firestore

### 6. Testing
- [ ] Unit tests
- [ ] Integration tests
- [ ] UI tests (optional for FYP)

## 📝 Important Notes

### Firebase Setup Required
1. **Authentication Methods:**
   - Email/Password: ✅ Must be enabled
   - Anonymous: ✅ Must be enabled (for child QR pairing)

2. **Firestore Database:**
   - Database must be created
   - Security rules must be configured (see `FIRESTORE_SECURITY_RULES.md`)
   - Collections: `users`, `pairing_tokens`, `device_pairs`

3. **Configuration Files:**
   - `app/google-services.json` must be added (excluded from git)

### Code Style
- **Language**: Java (not Kotlin)
- **Architecture**: MVVM pattern (ready for ViewModels)
- **UI**: Material Design Components
- **Binding**: View Binding (not Data Binding)

### Architecture
- Following MVVM (Model-View-ViewModel) pattern
- Repository pattern ready for data access
- Separation of concerns maintained
- Suitable for FYP academic review

### Permissions
- Camera permission required for QR scanning
- Runtime permission requests implemented for camera
- Internet and network state permissions declared

## 🔧 Development Status

### Current Phase: Login Module ✅ COMPLETE
- All authentication flows working
- QR code pairing functional
- Email verification implemented
- Ready to move to next module

### Next Phase: Dashboard & Monitoring
- Parent dashboard enhancements
- Child monitoring service
- AI integration

## 📚 Resources

- [Firebase Documentation](https://firebase.google.com/docs)
- [Firebase Authentication](https://firebase.google.com/docs/auth)
- [Firestore Documentation](https://firebase.google.com/docs/firestore)
- [ZXing Library](https://github.com/journeyapps/zxing-android-embedded)
- [Android Biometric](https://developer.android.com/training/sign-in/biometric-auth)
- [Material Design Components](https://material.io/components)

## 🐛 Known Issues & Solutions

### Issue: QR Code Not Showing
- **Solution**: Ensure Firestore Database is created and security rules are configured

### Issue: Pairing Failed - PERMISSION_DENIED
- **Solution**: Update Firestore security rules to allow unauthenticated reads of `pairing_tokens`

### Issue: Pairing Failed - Anonymous Auth Restricted
- **Solution**: Enable Anonymous Authentication in Firebase Console

### Issue: Signup/Login Not Working
- **Solution**: 
  1. Enable Email/Password authentication in Firebase Console
  2. Ensure `google-services.json` is in `app/` directory
  3. Check Firebase initialization in `GuardianAIApplication`

## 📋 Setup Checklist for New Developers

1. ✅ Clone repository
2. ⚠️ Add `app/google-services.json` (not in git)
3. ⚠️ Enable Firebase Authentication (Email/Password + Anonymous)
4. ⚠️ Create Firestore Database
5. ⚠️ Configure Firestore Security Rules
6. ✅ Build and run project

---

**Last Updated**: Login Module Complete
**Current Milestone**: ✅ Authentication & QR Pairing Complete
**Next Milestone**: Parent Dashboard Features & Child Monitoring
