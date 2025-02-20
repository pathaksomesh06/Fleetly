# Azure AD Configuration

## Register an Application with the Microsoft Identity Platform

## Prerequisites

- **Azure Account**: You must have an Azure account with an active subscription.  
- **Permissions**: Your Azure account must be at least a **Cloud Application Administrator**.
- **Tenant Setup**:

## Register an Application

Follow these steps to create the app registration:

1. **Sign in** to the Microsoft Entra admin center as at least a **Cloud Application Administrator**.
2. **Switch Tenants** (if needed):  
   If you have access to multiple tenants, use the **Settings icon** in the top menu to switch to the tenant in which you want to register the application via the **Directories + subscriptions** menu.
3. **Navigate to App Registrations**:  
   Browse to **Identity > Applications > App registrations** and select **New registration**.

   **The app has to be registered as Multi-Tenant App**:
   ![Screenshot 2025-02-13 at 12 39 45](https://github.com/user-attachments/assets/593ef1f1-904b-44c1-b23b-23c3749ec2be)

5. **Enter a Display Name**:  
   - Provide a display name for your application.  
   - This name might be seen by users during sign-in.  
   - You can change the display name at any time, and multiple app registrations can share the same name.  
   - **Note**: The automatically generated **Application (client) ID** uniquely identifies your app, not its display name. Copy the App ID, we will need it later during Intune configuration.
6. **Specify the Sign-In Audience**:  
   Choose who can use the application (sometimes called its sign-in audience).
7. **Configure Redirect URI**:  
   Leave **Redirect URI (optional)** alone for now; you'll configure it in the next section.
8. **Complete Registration**:  
   Select **Register** to complete the initial app registration.
9. **Review the Overview Pane**:  
   Once registration is complete, the Microsoft Entra admin center displays the app registration's **Overview** pane, which shows the **Application (client) ID** (client ID) that uniquely identifies your application.

<img width="1024" alt="Screenshot 2025-02-20 at 21 36 01" src="https://github.com/user-attachments/assets/cc34264a-3b66-4557-863d-67af8b68f47b" />

  
## Add a Redirect URI

A redirect URI is where the Microsoft identity platform sends security tokens after authentication.

`Bundle ID` = `com.irl.Fleetly`
`Redirect URI` = `msauth.com.irl.Fleetly://auth`
<img width="1244" alt="Screenshot 2025-02-20 at 21 37 11" src="https://github.com/user-attachments/assets/1640c54c-2847-4538-96ce-fcd974da31b4" />


## Add a Application ID URI
Add the application ID URI as below:
- Click Application ID URI from the right hand pane
- Add App ID URI
- Verify that application ID URI is automatatically updated 

<img width="1456" alt="Screenshot 2025-02-20 at 21 37 58" src="https://github.com/user-attachments/assets/9e03f252-21d1-46d7-ab4c-514de462756b" />


## In the Manage section, click API permissions

- Click Add a permission.
- The Request API permissions page appears.
 <img width="991" alt="Screenshot 2025-02-20 at 21 39 32" src="https://github.com/user-attachments/assets/fca7a6d2-13b8-477b-92f8-13425936c44f" />

- In the Microsoft APIs section, click Microsoft Graph.
<img width="1504" alt="Screenshot 2025-02-20 at 21 41 06" src="https://github.com/user-attachments/assets/96487a0c-55c3-46a9-92cf-4dfd5ac601f8" />


- Select Delegated permissions as the type of permissions and below permissions
<img width="1453" alt="Screenshot 2025-02-20 at 21 42 07" src="https://github.com/user-attachments/assets/e701453f-bc1a-4b1c-b885-0446bcf08963" />


   - `DeviceManagementManagedDevices.Read.All`
   - `DeviceManagementManagedDevices.ReadWrite.All`
   - `DeviceManagementManagedDevices.PrivilegedOperations.All`
   - `User.Read.All`
   - `Directory.Read.All`
  
![Screenshot 2025-02-13 at 12 49 38](https://github.com/user-attachments/assets/b0b5a088-1810-4f00-812c-92e10198cd9f)

- Navigate back to Manage & click Grant Admin Consent
<img width="970" alt="Screenshot 2025-02-20 at 21 43 10" src="https://github.com/user-attachments/assets/4450d6e5-584b-41ba-a66f-f3fe1af04f03" />


# Intune Configuration
Use app configuration policies in Microsoft Intune to provide custom configuration settings for the app so that it can read the App ID you just created in previous step.

Follow these steps to create a managed devices configuration profile:

- **Sign in** to the Microsoft Intune admin center.
- Navigate to **Apps > Configuration > Create > Managed devices**.
  ![Screenshot 2025-02-13 at 12 59 13](https://github.com/user-attachments/assets/9d7328bc-5cc2-43a3-8009-597f5401ceaa)

- On the **Basics** page, set the following details:
   - **Name**: The name of the profile that appears in the Microsoft Intune admin center.
   - **Description**: The description of the profile that appears in the Microsoft Intune admin center.
   - **Device enrollment type**: This should be set to **Managed devices**.
- **Select iOS/iPadOS as the Platform**.
- Click **Select app** next to **Targeted app**.  
   The **Associated app** pane is displayed.
- In the **Targeted app** pane, choose the **Fleetly** app to associate with the configuration policy, and click **OK**.
  <img width="1321" alt="Screenshot 2025-02-20 at 21 44 55" src="https://github.com/user-attachments/assets/2574933b-0757-481b-85c8-12a9200aa0b2" />

- Click **Next** to display the **Settings** page.
-  In the dropdown box, select the **Configuration settings format** and choose the **Enter XML data** option.
-  Paste the following XML data:
- Assign the profile to all users

```xml
<dict>
    <key>PayloadDescription</key>
    <string>Fleetly Configuration Profile</string>
    <key>PayloadDisplayName</key>
    <string>Fleetly Configuration</string>
    <key>PayloadIdentifier</key>
    <string>com.irl.Fleetly.config1</string>
    <key>PayloadRemovalDisallowed</key>
    <false/>
    <key>PayloadType</key>
    <string>Configuration</string>
    <key>PayloadUUID</key>
    <string>3C03929C-D6CA-41F9-9E4E-3C2227868E11</string>
    <key>PayloadVersion</key>
    <integer>1</integer>
    <key>PayloadContent</key>
    <array>
        <dict>
            <key>PayloadType</key>
            <string>com.apple.app.managed</string>
            <key>PayloadVersion</key>
            <integer>1</integer>
            <key>PayloadIdentifier</key>
            <string>com.irl.Fleetly.managedapp</string>
            <key>PayloadUUID</key>
            <string>CFD75594-390E-47F7-A7E1-F992DEBFF45A</string>
            <key>PayloadEnabled</key>
            <true/>
            <key>PayloadDisplayName</key>
            <string>Fleetly Managed App Config</string>
            <key>BundleIdentifier</key>
            <string>com.irl.Fleetly</string>
            <key>Configuration</key>
            <dict>
                <key>AzureADClientID</key>
                <string>replace with your app id</string>
            </dict>
        </dict>
    </array>
</dict>
![Screenshot 2025-02-13 at 13 01 40](https://github.com/user-attachments/assets/b6176d33-e41d-41cf-96ed-ec18b180a058)
