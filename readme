# MDMaster - An Intune Management iOS Application

MDMaster is a powerful iOS application designed for IT administrators to manage and monitor devices enrolled in Microsoft Intune. With an intuitive interface and comprehensive feature set, it provides seamless device management capabilities on the go.

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

- Built with SwiftUI
- Platform-specific device icons
- Visual compliance indicators
- Relative time formatting
- Pull-to-refresh support
- Responsive loading states
- User-friendly error handling
- Intuitive navigation

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
- `Directory.Read.All`
- `Directory.ReadWrite.All`

### Info.plist Configuration

```xml
<key>AzureADClientID</key>
<string>YOUR_CLIENT_ID</string>
<key>AzureADTenantID</key>
<string>YOUR_TENANT_ID</string>
```

## Usage

1. Launch MDMaster
2. Sign in with your Azure AD credentials
3. Select device platform (iOS, macOS, Windows, etc.)
4. View and manage your devices
5. Perform remote actions as needed

## Architecture

### Design Pattern
- MVVM (Model-View-ViewModel)

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

- Remote management actions limited to macOS devices
- Beta Graph API endpoints in use
- Single active session support
- Manual refresh required for real-time updates

## Upcoming Features

### Extended Device Support

- iOS/iPadOS remote management
- Windows device actions
- Android device management

### Enhanced Capabilities

- Bulk device actions
- Custom device grouping
- Compliance policy management
- App deployment
- Configuration profiles
- Device templates

### Additional Features

- Offline mode
- Push notifications
- Advanced filtering
- Data export
- Audit logging
- Custom dashboards

### Technical Improvements

- Background refresh
- Enhanced error handling
- Performance optimization
- Security enhancements

## License

This project is licensed under the MIT License.


## Contact

Somesh Pathak - [@someshpathak](https://github.com/someshpathak)

Project Link: [https://github.com/someshpathak/MDMaster](https://github.com/someshpathak/MDMaster)

---

Made with ❤️ by Somesh Pathak  
© 2025 MDMaster. All rights reserved.

