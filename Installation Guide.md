## Recommended: VPP Distribution

1. Purchase MDMaster through Apple Business Manager/Apple School Manager
2. Distribute via your MDM solution
3. Configure the required MDM settings:

```xml
<key>com.apple.configuration.managed</key>
<dict>
    <key>AzureADClientID</key>
    <string>YOUR_CLIENT_ID</string>
</dict>
```

### Alternative: App Store Installation:

1. Download MDMaster from the App Store
2. Deploy configuration profile through your MDM with:

```xml
<key>com.apple.configuration.managed</key>
<dict>
    <key>AzureADClientID</key>
    <string>YOUR_CLIENT_ID</string>
</dict>
```
### Note: App requires MDM configuration to function. Installation without proper MDM configuration will result in limited functionality.
