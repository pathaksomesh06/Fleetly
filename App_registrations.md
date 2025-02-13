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
 ![Screenshot 2025-02-13 at 12 41 44](https://github.com/user-attachments/assets/879ccddb-b6f4-408e-9161-a62c9f9f30bd)
  
## Add a Redirect URI

A redirect URI is where the Microsoft identity platform sends security tokens after authentication.

`Bundle ID` = `com.irl.MDMaster`
`Redirect URI` = `msauth.com.irl.MDMaster://auth`
![Screenshot 2025-02-13 at 12 42 20](https://github.com/user-attachments/assets/214004cd-01a0-4353-9218-66a59d1fddfd)

## Add a Application ID URI
Add the application ID URI as below:
- Click Application ID URI from the right hand pane
- Add App ID URI
- Verify that application ID URI is automatatically updated 
  ![image](https://github.com/user-attachments/assets/5677a629-2c1c-402b-b978-9a9996ba467f)

<img width="1325" alt="Screenshot 2025-02-13 at 16 27 03" src="https://github.com/user-attachments/assets/d9ff32c7-3198-4e5a-885c-3e920b63dbfc" />
<img width="1004" alt="Screenshot 2025-02-13 at 16 27 11" src="https://github.com/user-attachments/assets/f93afa91-eb5b-4b64-8989-df8f068bd261" />


## In the Manage section, click API permissions

- Click Add a permission.
- The Request API permissions page appears.
  ![Screenshot 2025-02-13 at 12 46 14](https://github.com/user-attachments/assets/b4ab6199-0c02-498a-8810-e6719a1e426b)

- In the Microsoft APIs section, click Microsoft Graph.
  ![Screenshot 2025-02-13 at 12 48 39](https://github.com/user-attachments/assets/abcbc6ab-47a3-402d-8d06-ce533338152d)

- Select Delegated permissions as the type of permissions and below permissions
![Screenshot 2025-02-13 at 12 49 08](https://github.com/user-attachments/assets/f638459a-5b60-47d2-869f-73e88271364e)

    `DeviceManagementManagedDevices.Read.All`
    `DeviceManagementManagedDevices.ReadWrite.All`
    `DeviceManagementManagedDevices.PrivilegedOperations.All`
    `User.Read.All`
    `Directory.Read.All`
  
  ![Screenshot 2025-02-13 at 12 49 38](https://github.com/user-attachments/assets/b0b5a088-1810-4f00-812c-92e10198cd9f)

- Navigate back to Manage & click Grant Admin Consent
![Screenshot 2025-02-13 at 12 51 55](https://github.com/user-attachments/assets/daa00dce-05f8-46d0-a605-00572cc710c8)

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
- In the **Targeted app** pane, choose the **MDMaster** app to associate with the configuration policy, and click **OK**.
  ![Screenshot 2025-02-13 at 13 00 13](https://github.com/user-attachments/assets/947935cf-2813-4e48-9705-00372976eb77)

   ![Screenshot 2025-02-13 at 13 00 44](https://github.com/user-attachments/assets/968c3a3d-9d25-4722-ae93-d4a9385058af)

- Click **Next** to display the **Settings** page.
-  In the dropdown box, select the **Configuration settings format** and choose the **Enter XML data** option.
-  Paste the following XML data:
- Assign the profile to all users

```xml
<dict>
    <key>PayloadDescription</key>
    <string>MDMaster Configuration Profile</string>
    <key>PayloadDisplayName</key>
    <string>MDMaster Configuration</string>
    <key>PayloadIdentifier</key>
    <string>com.irl.MDMaster.config1</string>
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
            <string>com.irl.MDMaster.managedapp</string>
            <key>PayloadUUID</key>
            <string>CFD75594-390E-47F7-A7E1-F992DEBFF45A</string>
            <key>PayloadEnabled</key>
            <true/>
            <key>PayloadDisplayName</key>
            <string>MDMaster Managed App Config</string>
            <key>BundleIdentifier</key>
            <string>com.irl.MDMaster</string>
            <key>Configuration</key>
            <dict>
                <key>AzureADClientID</key>
                <string>replace with your app id</string>
            </dict>
        </dict>
    </array>
</dict>
![Screenshot 2025-02-13 at 13 01 40](https://github.com/user-attachments/assets/b6176d33-e41d-41cf-96ed-ec18b180a058)
