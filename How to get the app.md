## How to Re-Sign and Export the IPA from the Distributed .xcarchive

### Download and Unzip the Archive:

1. Download the provided `MDMaster.xcarchive.zip` file.
2. Unzip it to obtain the `MDMaster.xcarchive` folder.

### Open Xcode Organizer:

1. Launch Xcode.
2. Go to **Window > Organizer**.
3. If your archive does not appear automatically, drag and drop the unzipped `MDMaster.xcarchive` folder into the Organizer window.

### Export the IPA:

1. In Organizer, select `MDMaster.xcarchive` and click the **Export…** button.
2. Choose the export option that suits your distribution method:
   - **Save for Ad Hoc Deployment** (for registered devices)
   - **Save for Enterprise Deployment**
3. Click **Next** and then **Export**.
4. During the export process, Xcode will prompt you to select your signing certificate and provisioning profile. Choose the ones associated with your account.
5. Xcode will generate an IPA file, which you can then install on your devices.

### Testing the IPA:

After exporting, you can install the IPA on your device using:
- Xcode
- Apple Configurator
- A Mobile Device Management (MDM) solution.
