

1. Introduction
2. Step 1: Create Google API Project
3. Step 2: Configure 3CX Phone System for Android Push Notifications
4. Step 3: Firewall configuration
5. For 3CX Phone System
6. For Android Phones
“Note: This document applies to 3CX V15. All V15.5 users must follow this procedure.”


**Introduction**
```bash
The 3CX app uses PUSH technology to wake up the smartphone when a call is received. This does not require the user to keep the phone active to be able to receive calls – the phone can be in sleep mode to save battery life.

In order to leverage PUSH technology you need to setup a Google account with PUSH. This step must be performed BEFORE you deploy the 3CX app as the Google API key and project ID are required in order for 3CX to send push requests to the smartphones.
```

**Step 1: Create Google API Project**
```bash
1. Login to your Gmail Account.
2. Follow this link to go to the new Google Developer Console Page: https://console.developers.google.com/project/. Click "Create Project" to create your Google push project.
3. Give your project a name example “3CXPBXPUSH”. Click on "Show advanced options" choose a location that is closest to you and click "Create". Be patient as it will take a few seconds.
4. In the search box on the library page type in "gcm" and press enter.
5. Then click  "Google Cloud Messaging".
6. Click "Enable".
7. Then click "Go to Credentials"
8. Choose "Google Cloud Messaging" from Which API are you using and from the Where will you be calling the API. Then click "What credentials do i need".
9. Click "Restrict" key and choose "IP addresses".
10. Enter the Public IP address of your network that the PBX is behind and press "Save".
11. Your API Key will be generated. Copy it and save it to be placed inside the API Key Text box (3CX Management Console > Settings > 3CXPhone > API Key section). Then click "Done".
12. Click the dropdown menu lines in the top right side of the page and click the "Project settings" button.
13. From the "Project 3CXPBXPUSH" locate the "Project Number". (for example 793510222615). Copy this number and save it so as to place it inside the project number text box within the “3CX Management Console > Settings > 3CXPhone > Push” section.
```

**Step 2: Configure 3CX Phone System for Android Push Notifications**
```bash
1. Login to the 3CX Management console.
2. Navigate to "Settings" > "3CXPhone".
3. Enter the API Key you generated earlier in the API Key field.
4. Enter the Project number in the Project number field.
5. Press "OK".
6. Restart all Android Smartphone apps so they re-provision and take the latest settings.
Note: By default all users are enabled to receive PUSH messages. If you want to disable PUSH for some users, click on "Extensions > edit extension > Phone Provisioning" tab, and uncheck the option "Enable PUSH for Smartphones" under the "Network" section.
```

**Step 3: Firewall configuration**
```bash
For 3CX Phone System

In order to successfully deliver Push messages to Android phones, 3CX Phone System must be allowed to send outbound messages via TCP on port 443 towards “android.googleapis.com” which is the URL for “Google Cloud Messaging” servers.

Important: Normally Inside to Outside traffic is allowed and trusted by a standard firewall. However some company firewalls are very strict and you might need to allow this specific traffic to exit. Do not base the firewall rule on “android.googleapis.com’s” IP Address because when the IP changes PUSH will stop to work.
```
```bash
For Android Phones

In order to receive Push messages within a corporate wifi network, Android Phones must be allowed to connect outbound via TCP port 443 to android.googleapis.com. If 443 is blocked, ports 5228, 5229 and 5230 will be used.

Important: Google does not provide specific IPs, therefore the destination should be set to "any".
```
