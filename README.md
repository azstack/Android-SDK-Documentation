# 1. Quick Start
AZStack is the communication platform which provides SDK, API to add chatting, calling features to the third-party mobile applications or websites.
This Quick Start guide will help you run a sample project powered by AZStack as fast as possible. To run the sample project, you will need Android Studio installed.

```
1. Clone sample project from git hub: https://github.com/azstack/Android-SDK-Sample-Project.git
2. Open and run in Android Studio
```

# 2. Setup and installation
To integerate AZStack SDK to your application, you need to create an AZStack account. If you do not have an AZStack account, sign up here: http://developer.azstack.co. After creating your account successfully, you need create a project. When a project is created, AZStack provides you an application ID (appId) and a RSA key pair (public key is used on your application, private key is used on your server).

![AZStack create account](http://azstack.com/docs/static/azstack_create_account.png "AZStack create account")

AZStack SDK is built and designed to be used with Android Studio. The following instructions will help you to integrate AZStack into your application:
### 2.1. Adding AAR
Copy AZStack-version.aar (download from https://developers.azstack.co) to libs folder at the app level.
Navigate to build.gradle file at the app level and adding the following lines:
```
repositories {
        flatDir {
            dirs 'libs'
        }
}

dependencies {
    compile(name: 'AZStackSDK-version', ext: 'aar')
	compile 'com.android.support:appcompat-v7:23.1.1'
	compile 'com.google.android.gms:play-services-maps:8.4.0'
    compile 'com.google.android.gms:play-services-gcm:8.4.0'
    compile 'com.google.android.gms:play-services-location:8.4.0'
    compile 'com.google.android.gms:play-services-plus:8.4.0'
}
```

![Add AAR lib](http://azstack.com/docs/static/android_add_lib.png "Add AAR lib")

### 2.2. AndroidManifest.xml
#### Set up permissions and references
The AZStack SDK requires some permissions and references (activities, gcm receivers, google map api key...) from your app's AndroidManifest.xml file. These permissions allow the SDK to monitor network state and receive Google Cloud Messaging messages... Below is an example with a com.example package; replace with your own package when merging with your own manifest.
```
<?xml version="1.0" encoding="utf-8"?>
<manifest xmlns:android="http://schemas.android.com/apk/res/android"
    package="com.example"
    android:versionCode="1"
    android:versionName="1.0" >

    <uses-sdk
        android:minSdkVersion="10"
        android:targetSdkVersion="21" />

	<!-- AZStack permissions -->
	
    <uses-permission android:name="android.permission.READ_PHONE_STATE" />
    <uses-permission android:name="com.azstack.sample.permission.MAPS_RECEIVE" />
    <uses-permission android:name="android.permission.INTERNET" />
    <uses-permission android:name="android.permission.READ_EXTERNAL_STORAGE" />
    <uses-permission android:name="android.permission.WRITE_EXTERNAL_STORAGE" />
    <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
    <uses-permission android:name="android.permission.CAMERA" />
    <uses-permission android:name="android.permission.VIBRATE" />
    <uses-permission android:name="android.permission.RECORD_AUDIO" />
    <uses-permission android:name="android.permission.MODIFY_AUDIO_SETTINGS" />
    <uses-permission android:name="android.permission.ACCESS_FINE_LOCATION" />
    <uses-permission android:name="android.permission.ACCESS_COARSE_LOCATION" />
    <uses-permission android:name="android.permission.DISABLE_KEYGUARD" />
    <uses-permission android:name="com.google.android.providers.gsf.permission.READ_GSERVICES" />
    <uses-permission android:name="android.permission.ACCESS_WIFI_STATE" />
    <uses-permission android:name="android.permission.GET_TASKS" />
	
	<!-- AZStack permissions -->

	<!-- AZStack activities-->
	
    <application
        android:allowBackup="true"
        android:icon="@drawable/ic_launcher"
        android:label="@string/app_name">
        <activity
            android:name="com.azstack.activity.ChatActivity"
            android:configChanges="keyboard|keyboardHidden|orientation|screenLayout|uiMode|screenSize|smallestScreenSize"
            android:launchMode="singleTask"
            android:screenOrientation="portrait"
            android:theme="@style/AzStackTheme.Light"
            android:windowSoftInputMode="stateHidden|adjustResize" />
        <activity
            android:name="com.azstack.activity.ChatGroupActivity"
            android:configChanges="keyboardHidden|orientation|screenSize"
            android:launchMode="singleTask"
            android:screenOrientation="portrait"
            android:theme="@style/AzStackTheme.Light"
            android:windowSoftInputMode="stateHidden|adjustResize" />
        <activity
            android:name="com.azstack.activity.FreeCallActivity"
            android:configChanges="keyboardHidden|orientation|screenSize"
            android:screenOrientation="portrait"
            android:theme="@style/AzStackTheme.Light" />
        <activity
            android:name="com.azstack.activity.IncomingCallActivity"
            android:configChanges="keyboardHidden|orientation|screenSize"
            android:screenOrientation="portrait"
            android:theme="@style/AzStackTheme.Light" />
        <activity
            android:name="com.azstack.activity.ViewPhotoActivity"
            android:configChanges="keyboardHidden|orientation|screenSize"
            android:screenOrientation="portrait"
            android:theme="@style/Theme.AppCompat.NoActionBar" />
        <activity
            android:name="com.azstack.activity.ReviewPhotoActivity"
            android:configChanges="keyboardHidden|orientation|screenSize"
            android:screenOrientation="portrait"
            android:theme="@style/Theme.AppCompat.NoActionBar" />
        <activity
            android:name="com.azstack.activity.ConversationActivity"
            android:configChanges="keyboardHidden|orientation|screenSize"
            android:screenOrientation="portrait"
            android:theme="@style/AzStackTheme.Light" />
        <activity
            android:name="com.azstack.activity.GroupListActivity"
            android:configChanges="keyboardHidden|orientation|screenSize"
            android:screenOrientation="portrait"
            android:theme="@style/AzStackTheme.Light" />
        <activity
            android:name="com.azstack.activity.GroupInfoActivity"
            android:configChanges="keyboardHidden|orientation|screenSize"
            android:screenOrientation="portrait"
            android:theme="@style/AzStackTheme.Light" />
        <activity
            android:name="com.azstack.activity.SendLocationActivity"
            android:screenOrientation="portrait"
            android:theme="@style/AzStackTheme.Light" />
        <activity
            android:name="com.azstack.activity.ShowLocationActivity"
            android:screenOrientation="portrait"
            android:theme="@style/AzStackTheme.Light" />
        <activity
            android:name="com.azstack.activity.ForwardActivity"
            android:screenOrientation="portrait"
            android:theme="@style/AzStackTheme.Light" />
        <activity
            android:name="com.azstack.activity.FileExplorerActivity"
            android:configChanges="keyboardHidden|orientation|screenSize"
            android:screenOrientation="portrait"
            android:theme="@style/AzStackTheme.Light"
            android:windowSoftInputMode="stateHidden|adjustResize" />
        <activity
            android:name="com.azstack.activity.GunDrawActivity"
            android:screenOrientation="portrait"
            android:theme="@android:style/Theme.Translucent.NoTitleBar" />
        <activity
            android:name="com.azstack.activity.GunGGalleryActivity"
            android:screenOrientation="portrait"
            android:theme="@style/AzStackTheme.Light" />
        <activity
            android:name="com.azstack.activity.GunGDirectoryActivity"
            android:screenOrientation="portrait"
            android:theme="@style/AzStackTheme.Light" />
        <activity
            android:name="com.azstack.activity.SelectContactChatGroupActivity"
            android:screenOrientation="portrait"
            android:theme="@style/AzStackTheme.Light" />
		<activity
            android:name="com.azstack.activity.StickerDetailActivity"
            android:screenOrientation="portrait"
            android:theme="@style/AzStackTheme.Light"></activity>
        <activity
            android:name="com.azstack.activity.StickerListActivity"
            android:screenOrientation="portrait"
            android:theme="@style/AzStackTheme.Light"></activity>
		
		<!-- AZStack activities-->

		<!-- AZStack meta-data-->
		
        <meta-data
            android:name="com.google.android.maps.v2.API_KEY"
            android:value="AIzaSyDuqAE6o4Uj45SVyQstieg00BxxSA8ICAI" />
        <meta-data
            android:name="com.google.android.gms.version"
            android:value="@integer/google_play_services_version" />
			
		<!-- AZStack meta-data-->
    </application>
	
</manifest>
```

#### Set up Google Maps API key
AZStack SDK has sending location function which using Google Maps Android API. It's required to set up Google Map API key. Refer to the following link: https://developers.google.com/maps/documentation/android-api/signup to get your own api key and replace it in AndroidManifest.

# 3. Connecting
### 3.1 Instantiate
Each application must register with AZStack for 1 appID, 1 RSA key pair (public key is used on your application, private key is used on your server). For example: 
```
String appId = "26870527d2ac628002dda81be54217cf";   
String publicKey = "MIIBIjANBgkqhkiG9w0BAQEFAAOCAQ8AMIIBCgKCAQEAq9s407QkMiZkXF0juCGj ti6iWUDzqEmP+Urs3+g2zOf+rbIAZVZItS5a4BZlv3Dux3Xnmhrz240OZMBO1cNc poEQNij1duZlpJY8BJiptlrj3C+K/PSp0ijllnckwvYYpApm3RxC8ITvpmY3IZTr RKloC/XoRe39p68ARtxXKKW5I/YYxFucY91b6AEOUNaqMFEdLzpO/Dgccaxoc+N1 SMfZOKue7aH0ZQIksLN7OQGVoiuf9wR2iSz3+FA+mMzRIP+lDxI4JE42Vvn1sYmM CY1GkkWUSzdQsfgnAIvnbepM2E4/95yMdRPP/k2Qdq9ja/mwEMTfA0yPUZ7Liywo ZwIDAQAB"
```

The AZStack SDK has a primary interface AzStackClient for interacting with AZStack service. You have to initialize AzStackClient object in onCreate() method of your Application or your main Activity.. Only once instance of AzStackClient should be instantiated and used all time:
```
AzStackClient azStackClient = AzStackClient.newInstance(Context context,String appId,String publicKey);
```

### 3.2 Listeners
The AZStack SDK uses listener pattern to push specific events to your application. You must register 2 listeners AzStackConnectListener, AzStackUserListener when initialize AzStackClient object.
```
azStackClient.registerConnectionListenter(AzStackConnectListener instance)
azStackClient.registerUserListener(AzStackUserListener instance)
```

### 3.3 Connect and authenticate
In order to a user to chat or call, you must authenticate them first. AZStack will accept any unique String as a User ID (UIDs, email addresses, phone numbers, usernames, etc), which we call as azStackUserId. So you can use any new or existing User Management system.
The process is described in the following model:

![AZStack init and authentication](http://azstack.com/docs/static/Android_Connect_Authenticate.png "AZStack init and authentication")

#### Step 0
Go to http://developer.azstack.com/
```
	a. Create project
	b. Generate keys
	c. Update Authentication URL which used to authenticate user between AZStack and your backend.
```

#### Step 1
Initialize SDK with your appID, public key as described in 3.1

#### Step 2
Call  azStackClient.connect(String azStackUserId, String userCredentials, String name) method to start connecting, autheticating process
```
azStackClient.connect(String azStackUserId, String userCredentials, String name);

Parameter: 	azStackUserId: your user id on your system, as described above
			userCredentials: can be your password, token on your system. AZStack will not use this information. It's forwared to your server to authenticate your user.
			name: optional, used to display on push notification.
```

You must register AzStackConnectListener for listening connection,authentication events such as: connected, disconnected, connect failed...
```
azStackClient.registerConnectionListenter(new AzStackConnectListener() {

			@Override
			public void onConnectionError(AzStackClient client,
					AzStackException e) {
				// Connect or authenticate unsuccessfully
			}

			@Override
			public void onConnectionDisconnected(AzStackClient client) {
				// Disconnected from AZStack service
			}

			@Override
			public void onConnectionConnected(AzStackClient client) {
				// Connect and authenticate successfully, can start chatting, calling from here
			}
		});
```

### Step 3
After calling connect method, AZStack SDK will encrypt the following string:
```
{"azStackUserID":"...", "userCredentials":"..."}
```
using RSA 2048 algorithm with your public key. The Identity Token is returned and will be sent to AZStack server.

#### Step 4
AZStack decrypts Identity Token using RSA 2048 algorithm with the private key generated at step 0. Then AZStack will use the public key generated at step 0 to encrypt the following string:
```
{"azStackUserID":"...", "userCredentials":"...", "timestamp": ..., "appId":"...", "code":"..."}
```
"code" is generated as below:
```
md5(appId + "_" + timestamp + "_" + secret_code)
```
The encryption process returns Authentication Token. AZStack will send the Authentication Token to your server via Authentication URL (updated at step 0).

#### Step 5
On your server side, you need decrypt Authentication Token receiving from AZStack server to get the "code". Compare "code" with the following string:
```
md5(appId + "_" + timestamp + "_" + secret_code)
```
If they are the same, execute authentication with azStackUserID and userCredentials on your backend. Please see sample code writing in PHP here: https://github.com/azstack/Backend-example/blob/master/php/azstack_authentication.php

### 3.4 AzStackUserListener
AzStackUserListener must to be registered when initialize AzStackClient object. It's used to get basic information of app's user such as: name, avatar... to display on chat, call screen.

```
azStackClient.registerUserListener(new AzStackUserListener() {

            @Override
            public void getUserInfo(List<String> azStackUserIds, int purpose) {
                // This code implemention is only for testing purpose
                // When going into production, you have to implement your own
                // web service to get your app's user info
				try {
                    JSONArray arrayContact = new JSONArray();
                    for (String azStackUserId : azStackUserIds) {
                        JSONObject ob = new JSONObject();
                        ob.put("azStackUserId", azStackUserId);
                        ob.put("name", name);
                        ob.put("avatar", avatar);
                        arrayContact.put(ob);
                    }
                    AzStackClient.getInstance().getUserInfoComplete(arrayContact, purpose);
                } catch (Exception e) {
                    e.printStackTrace();
                }
            }

            @Override
            public void viewUserInfo(String appUserId) {

            }

            @Override
            public JSONArray getListFriend() {
				// This code implemention is only for testing purpose
                // When going into production, you have to implement your own
                // web service to get list user info
				JSONArray jsonArray = getListUserInfo();
                return jsonArray;
            }
        });
```

In the getUserInfo(List<String> azStackUserIds, int purpose) method, you need return users'information (including azStackUserId, name, avatar) equivalent to the list azStackUserIds via JSONArray. At the end of this medthod, you must call azStackClient.getUserInfoComplete(arrayContact, purpose) method. These information will be displayed on chat, call screen. You can check the sample for more detail how to implement this method.

# 4. API
### 4.1 Chat with a user
```
azStackClient.startChat(Context context, String azStackUserId, String name, String avatar);

Parameter: 	context: The context to start chat, required
			azStackUserId: identifier of app’s user, required
			name: name of app’s user, default “No name”, optional
			avatar: avatar of app’s user, optional
```

### 4.2 Call to a user
```
azStackClient.startCall(Context context, String azStackUserId, String name, String avatar);

Parameter: 	context: The context to start call, required
			azStackUserId: identifier of app’s user, required
			name: name of app’s user, default “No name”, optional
			avatar: avatar of app’s user, optional
```

### 4.3 Create a chat group
```
azStackClient.createGroup(Context context);

Parameter: 	context: The context to create group, required
```
When creating a new group chat, the app navigates to select users screen. To make this screen work fine, you must implement the method getListFriend() of AzStackUserListener when initialize AZStack service. 
In getListFriend() method, the information of users (who you want to add to the group) is returned via JSONArray object. You can check the sample for more detail how to implement this method.

### 4.4 Update user's information
Update your info for push notification

```
azStackClient.updateMyInfo(newName);
```

### 4.5 Chat history
To show chat history, you can call this method

```
azStackClient.viewChatHistory(Context context);
```

or use AzConversationFragment in your application.
Important: if you use AzConversationFragment in your application, you must initialize AZStackClient object before using.

### 4.6 Disconnect
Disconnect from AZStack server

```
azStackClient.disconnect();
```

### 4.7 Logout
Disconnect from AZStack server and clear all cached data on client

```
azStackClient.logout();
```

# 5. Push notification
### 5.1 Set up Google Cloud Messaging on Web

Go to the Google Developer Console(https://console.developers.google.com/) and click Create a project
![AZStack GCM](http://azstack.com/docs/static/gcm/1.png "AZStack GCM")
Select the newly project and note the numeric Project number. This number is used for initializing AZStack SDK.
![AZStack GCM](http://azstack.com/docs/static/gcm/2.png "AZStack GCM")
Under API Manager, make sure that Google Cloud Messaging API is enabled. To do so, on the left menu navigate to API Manager -> Google APIs -> Mobile APIs, find Google Cloud Messaging and enable it.
![AZStack GCM](http://azstack.com/docs/static/gcm/3.png "AZStack GCM")
Next, you must create new Server API key under API Manager -> Credentials -> Add Credentials
![AZStack GCM](http://azstack.com/docs/static/gcm/4.png "AZStack GCM")
Choose Server key from popup
![AZStack GCM](http://azstack.com/docs/static/gcm/5.png "AZStack GCM")
Type 0.0.0.0/0 in the IP addresses field and Create
![AZStack GCM](http://azstack.com/docs/static/gcm/6.png "AZStack GCM")
Note the alphanumeric API Key. You will need to input this key into the AZStack Dashboard.
![AZStack GCM](http://azstack.com/docs/static/gcm/7.png "AZStack GCM")

### 5.2 Set up Google Cloud Messaging in AZStack Dashboard
Go to your project's Dashboard, choose Push -> Configure for Android -> Add credentials. Enter the Server API key(which created in 5.1), project package name.
### 5.3 Set up Google Cloud Messaging in client code
First, following this link https://developers.google.com/cloud-messaging/android/start to get configuration file google-services.json.

Copy google-services.json file into the app/ directory of your Android Studio project.

Instantiate AzStackClient with your sender id via Options object. The sender id is the Project number which created in 5.1.
```
AzOptions azOptions = new AzOptions ();
azOptions.setGoogleCloudMessagingId(senderId);			
AzStackClient azStackClient = AzStackClient.newInstance(this, appId, publicKey, userCredentials, azOptions);
```

You have to declare some permissions for push notification in AndroidManifest.xml
```
<permission android:name="{your package name}.permission.C2D_MESSAGE"
    android:protectionLevel="signature" />
<uses-permission android:name="{your package name}.permission.C2D_MESSAGE" />
<uses-permission android:name="com.google.android.c2dm.permission.RECEIVE" />
<uses-permission android:name="android.permission.GET_ACCOUNTS" />
<uses-permission android:name="android.permission.WAKE_LOCK" />
```

Add receivers and services to AndroidManifest.xml. Note that you must create your own gcm listener service extends GcmListenerService to receive push message.
```
<!-- [START gcm_receiver] -->
<receiver
    android:name="com.google.android.gms.gcm.GcmReceiver"
    android:exported="true"
    android:permission="com.google.android.c2dm.permission.SEND" >
    <intent-filter>
        <action android:name="com.google.android.c2dm.intent.RECEIVE" />
        <category android:name="{your package name}" />
    </intent-filter>
</receiver>
<!-- [END gcm_receiver] -->

<!-- [START gcm_service] -->
<service
    android:name="{your package}.MyGcmListenerService"
    android:exported="false" >
    <intent-filter>
        <action android:name="com.google.android.c2dm.intent.RECEIVE" />
    </intent-filter>
</service>
<service
    android:name="com.azstack.AzStackInstanceIDListenerService"
    android:exported="false" >
    <intent-filter>
        <action android:name="com.google.android.gms.iid.InstanceID" />
    </intent-filter>
</service>
<service
    android:name="com.azstack.RegistrationIntentService"
    android:exported="false" />
<!-- [END gcm_service] -->
```

Finally, create your own service extends GcmListenerService:
```
public class MyGcmListenerService extends GcmListenerService {

    @Override
    public void onMessageReceived(String from, Bundle data) {
        // Implement connect AZStack service here
		AzStackClient.getInstance().showNotification(this, data);
    }
}
```

In onMessageReceived method, you need connect to AZStack service as described in #3 and call AzStackClient.getInstance().showNotification(context, data) method.

# 6. UI customization
AZStack SDK allows developers to change some basic attributes of chat, call screen via AzUI object.

```
AzUI azUI = AzUI.getInstance();
```

### 6.1 Change the color of the actionbar, call background:

```
azUI.setHeaderColor(0xff4caf50);
```

### 6.2 Change the notification icon:

```
azUI.setNotificationIcon(R.mipmap.your_icon);
```

These methods need to be called only once time when you initialize AZStack SDK