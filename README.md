CometChat Android Chat Tutorial: One-2-One/ Group Chat

    Best for: Use cases where users jump directly into a chat — no list, just the conversation.
    
    Highlights:
    Opens a specific user/group chat.
    Great for support, direct messages, or onboarding.
    Lightweight with minimal UI.
    Full-screen, focused chat experience.
    Easily launched using user/group ID or object.
1. Create a CometChat Account

       -Go to https://app.cometchat.com/signup.
       -Register on CometChat's dashboard 
2. Create App on CometChat Dashboard

       -After logging in, go to the CometChat Dashboard
       -Click on + Add App     
       -give your app a name.
       -Click Create App.
3. Get Credentials

       -Navigate to Application
       -Then select the Credentials section and copy these:
             App ID
             Auth Key
             Region
       You'll need them in your Android project.
4. Install Dependencies
    a. Add the CometChat Repository
        In your build.gradle (Project):

        allprojects {
            repositories {
                google()
                mavenCentral()
                maven { url 'https://dl.cloudsmith.io/public/cometchat/cometchat-pro-android/maven/' }
            }
        }
    b. Add the CometChat Dependency
      In build.gradle (App):
         
          dependencies {
              implementation(libs.cometchat.ui.kit)
          
              // (Optional) Include if using voice/video calling features
              implementation(libs.cometchat.calls.sdk)
          }    
      Inside libs.versions.toml,
      
        [versions]
        cometchat-ui-kit = "5.0.2"
        cometchat-calls-sdk = "4.1.0"
    
        [libraries]
        cometchat-ui-kit = { module = "com.cometchat:chat-uikit-android", version.ref = "cometchat-ui-kit" }
        cometchat-calls-sdk = { module = "com.cometchat:calls-sdk-android", version.ref = "cometchat-calls-sdk" } 
5. Initialize CometChat UI Kit  

       -The UI Kit is initialized in `MainActivity.java` using `UIKitSettings`.
       -Initialization requires your `App ID`, `Region`, and `Auth Key`.  
6. User Authentication

       -After initialization, the app logs in a user by their UID.
       -To authenticate a user in CometChat, you need the UID (unique user ID). There are two main options for getting this UID:
        
       a. Pre-generated test users:
           cometchat-uid-1 
           cometchat-uid-2 
           cometchat-uid-3  
           cometchat-uid-4  
           cometchat-uid-5
   
       b. Or create users:
       create your own users via CometChat Dashboard,CometChat SDK method or via API.

       -Use the provided MainActivity code to initialize CometChat UI Kit and perform user login.
       -Replace appID, region, and authKey with your own credentials.
       -Use one of the pre-generated test UIDs or create your own users.   
7. Build the Chat Experience

       -Stitch the Components: Conversation + Message View
       -Key Components
           Chat Header : Displays user/group name, profile image, and status.
           Message List : Shows chat history and new messages.
           Message Composer : Allows users to send messages, media, and reactions.
       -Integration Steps:
           a. Setup the Messages Layout
           b.Setup the MessageActivity
8. Customise
    
           Set Up Global Theme
           -To customize component styling across your application in one place, you need to set up the CometChat Theme.
           -Use the CometChatTheme.DayNight style, which is built on Theme.MaterialComponents.DayNight.NoActionBar.
           -Apply the Theme
           -Set CometChatTheme.DayNight as the parent theme for your application in the themes.xml file.
     themes.xml
    
        <style name="YourAppParentTheme" parent="CometChatTheme.DayNight"/>
     AndroidManifest.xml   
    
           <application
            android:theme="@style/YourAppParentTheme"
            ...
            ...
        >
    
        </application>
9. Run the App   

