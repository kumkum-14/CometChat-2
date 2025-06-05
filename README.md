Building an Android Chat App with CometChat UI Kit

Description

This repository provides an Android sample app that demonstrates integrating CometChat’s UI Kit for one-to-one and group chat functionality.

It features:

    -Real-time messaging with session persistence
    -A compact, full-screen UI
    -Seamless navigation using Activities (can be extended to Fragments or Jetpack Navigation)
    -Lightweight, responsive, and optimized for mobile devices.

Features

        -One-to-One & Group Chats
        -Real-Time Messaging with session persistence
        -Compact UI with conversations & messages
        -Activity-based navigation
        -Lightweight & mobile responsive design

Getting Started

1️. Create a CometChat Account

    -Visit the CometChat Dashboard:
    
        https://app.cometchat.com/signup
    -Register or log in to access the Dashboard.

2. Create an App on CometChat Dashboard

        -In the Dashboard, click + Add App.
        -Enter a name for your app and click Create App.
        -Navigate to Application → Credentials and copy the following values:
                App ID
                Auth Key
                Region
        Store these values securely; you will reference them in your Android project configuration.

3. Install Dependencies

        -All dependency declarations and version catalogs are managed with Gradle.
        -Project-level Build Configuration
            Open build.gradle.kts to verify that mavenCentral() and the CometChat Maven repository are included under allprojects → repositories.
        -App-level Build Configuration
            Open app/build.gradle.kts and confirm the following dependencies:
                
            com.cometchat:chat-uikit-android (CometChat UI Kit)
            com.cometchat:calls-sdk-android (CometChat Calls SDK; optional if you want voice/video features)
                
        -For exact versions, refer to the version catalog in gradle/libs.versions.toml.
        -Sync Your Project
            In Android Studio, click Sync Now after making changes to Gradle files. This ensures the CometChat SDKs are downloaded.

4. Initialize CometChat UI Kit

        -Open the application class file MainActivity.java.
        -Replace the placeholder values for App ID, Region, and Auth Key with the credentials you copied from the Dashboard.
        -Verify that CometChat.init(…) is invoked in the onCreate() method so the SDK initializes before any UI is rendered.
        
5. User Authentication

        -Open the main activity file MainActivity.java.
        -Review the login logic, which calls CometChat.login(uid, authKey, …).
        -You can use pre-generated test UIDs (e.g., cometchat-uid-1, cometchat-uid-2) or create your own users via the Dashboard, the SDK, or the REST API.
        -Confirm that the Auth Key placeholder has been replaced with your own value.

6. Build the Chat Experience

        -Message View Layout
        
        -Inspect the layout files in app/src/main/res/layout/:
                
                -Activity_message.xml( Single chat messages)
                -Message Activity
                -See app/src/main/java/com/example/cometchatdemo2/MessageActivity.java to understand how the CometChat UI Kit fragment is loaded.
            
        -Key Components
        
            Chat Header: Displays user/group name, profile image, and status.
            Message List: Shows chat history and incoming messages.
            Message Composer: Allows users to send text, media, and reactions.
        
        -Integration Steps
        
            i. Set up message layouts (handled internally by the UI Kit)
            ii. Configure MessageActivity.java
            iii. Verify navigation between activities and fragments

7. Customize Theme

       -To apply a global theme that matches CometChat’s styling, open app/src/main/res/values/themes.xml.
       -Ensure your root theme is set to inherit from CometChatTheme.DayNight:
    
               <style name="AppTheme" parent="CometChatTheme.DayNight" />
    
        -Open AndroidManifest.xml and confirm that <application> uses @style/AppTheme as its android:theme.

8. Run the App 
    
        -Connect an Android device or start an emulator.
        -In Android Studio, click Run > Run ‘app’ or use the toolbar ▶ icon.
        -The Message View interface should load.
        -Open a second instance or a separate device, log in with a different UID, and send a message to verify real-time delivery.

10. Troubleshooting 

        -Problem: SDK not initializing
         Check: Correct App ID, Region, and Auth Key
        
        -Problem: Gradle sync fails
         Check: libs.versions.toml for correct versions
        
        -Problem: Login fails
         Check: Ensure UID exists in CometChat (via dashboard or API)

Repository Structure

    cometchatdemo2/
    ├── app/
    │   ├── src/
    │   │   ├── main/
    │   │   │   ├── java/com/example/cometchatdemo2/
    │   │   │   │   ├── MainActivity.kt
    │   │   │   │   └── MessageActivity.kt
    │   │   │   ├── res/
    │   │   │   │   ├── layout/
    │   │   │   │   │   ├── activity_main.xml
    │   │   │   │   │   ├── activity_message.xml
    │   │   │   │   └── values/themes.xml
    │   │   │   └── AndroidManifest.xml
    ├── gradle/libs.versions.toml
    ├── build.gradle.kts
    ├── settings.gradle.kts
    └── README.md




