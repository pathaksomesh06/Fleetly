# Fleetly - An Intune Management iOS Application

Fleetly is a powerful iOS application designed for IT administrators to manage and monitor devices enrolled in Microsoft Intune. With an intuitive interface and comprehensive feature set, it provides seamless device management capabilities on the go.

## Table of Contents

- [Features](#features)
- [Screenshots](#screenshots)
- [Requirements](#requirements)
- [Installation](#installation)
- [Configuration](#configuration)
- [Usage](#usage)
- [Architecture](#architecture)

## Features

### Authentication & Security

- Microsoft Azure AD authentication with MSAL integration
- Multi-tenant authentication support
- Automatic token refresh and session management
- Secure keychain credential storage
- SSO (Single Sign-On) capability
- Enhanced security with biometric authentication

### Device Management

- Real-time device inventory management
- Cross-platform device support:
  - iOS/iPadOS
  - macOS
  - Windows
  - Android
  - Linux

- Comprehensive device details:
  - Compliance status
  - Management state
  - Enrollment information
  - OS version
  - Last sync timestamp
  - User assignment

### Remote Management Actions

Currently supported for macOS:

- Device synchronization
- Remote restart
- Remote shutdown
- Remote lock
- Passcode removal
- Device retirement
- Device wipe
- Device deletion

### Search & Organization

- Real-time device search functionality
- Filter devices by:
  - Device name
  - Model
  - Manufacturer
  - Platform
  - Compliance status

### Modern UI/UX
I
- Built with SwiftUI
- Platform-specific device icons
- Visual compliance indicators
- Relative time formatting
- Pull-to-refresh support
- Responsive loading states
- User-friendly error handling
- Intuitive navigation
- Dark mode support

## Screenshots
![Simulator Screenshot - iPad Pro 13-inch (M4) - 2025-02-12 at 22 01 09](https://github.com/user-attachments/assets/de774094-e563-4260-a1ca-934daeff5f38)
![Simulator Screenshot - iPad Pro 13-inch (M4) - 2025-02-12 at 22 01 12](https://github.com/user-attachments/assets/0ddd7433-d94c-4b8d-8d5c-8338248fa24a)
![Simulator Screenshot - iPad Pro 13-inch (M4) - 2025-02-12 at 22 01 16](https://github.com/user-attachments/assets/6662d355-d9dd-4335-a056-9a7797f798fd)
![Simulator Screenshot - iPad Pro 13-inch (M4) - 2025-02-12 at 22 01 19](https://github.com/user-attachments/assets/7e9610a1-305e-4f5f-aa3e-519d40673fcf)
![Simulator Screenshot - iPhone 16 Pro Max - 2025-02-12 at 22 03 45](https://github.com/user-attachments/assets/eacfa157-c4f2-4058-ac31-bfc5bc0705b1)
![Simulator Screenshot - iPhone 16 Pro Max - 2025-02-12 at 22 03 49](https://github.com/user-attachments/assets/92fe3ed6-0036-4261-bd02-5a854d1853fa)
![Simulator Screenshot - iPhone 16 Pro Max - 2025-02-12 at 22 03 52](https://github.com/user-attachments/assets/c6fb4c6e-5ba9-4730-9b8f-5303326d589d)
![Simulator Screenshot - iPhone 16 Pro Max - 2025-02-12 at 22 03 56](https://github.com/user-attachments/assets/9cefcef1-4ec9-4dc2-b633-c3021542bdf5)


## Requirements

- iOS 15.0 or later
- Valid Microsoft Intune license
- Azure AD account with proper permissions
- Internet connectivity
- Xcode 14.0+ (for development)

## Configuration

### Azure AD Permissions

Required Graph API permissions:

- `DeviceManagementManagedDevices.Read.All`
- `DeviceManagementManagedDevices.ReadWrite.All`

### MDM Configuration

The app requires deployment through your organization's Mobile Device Management (MDM) system with the following configuration:
```xml
<key>com.apple.configuration.managed</key>
<dict>
    <key>AzureADClientID</key>
    <string>YOUR_CLIENT_ID</string>
</dict>
```

## Usage

1. Launch Fleetly
2. Sign in with your Azure AD credentials
3. Select device platform (iOS, macOS, Windows, etc.)
4. View and manage your devices
5. Perform remote actions as needed

## Architecture

### Design Pattern
- MVVM (Model-View-ViewModel)
- Clean Architecture principles

### UI Framework
- SwiftUI

### Authentication
- MSAL (Microsoft Authentication Library)

### API Integration
- Microsoft Graph API

### Concurrency
- Async/await

### Dependencies
- None (No third-party libraries except MSAL)

### Key Components

- **MSALManager**: Handles authentication
- **GraphAPI**: Manages API communications
- **DeviceManager**: Coordinates device operations
- **CryptoManager**: Manages security operations
- **KeychainService**: Handles secure storage

## Current Limitations

- Remote management actions limited to macOS and iOs/iPadOS devices
- Single active session support
- Manual refresh required for real-time updates

## Upcoming Features

### Extended Device Support

- iOS/iPadOS remote management
- Windows device action support
- Android device management
- Bulk device actions
- Configuration profiles management
- Push notifications for device events
- Advanced audit logging
- Custom dashboards

### Enhanced Capabilities

- Bulk device actions
- Custom device grouping
- Compliance policy management
- App deployment
- Configuration profiles
- Device templates

### Technical Improvements

- Background refresh
- Enhanced error handling
- Performance optimization
- Security enhancements

## License

This project is licensed under the MIT License.


## Contact

Somesh Pathak - [@pathaksomesh06](https://github.com/pathaksomesh06)

---

Made with ❤️ by Somesh Pathak  
© 2025 Fleetly. All rights reserved.

