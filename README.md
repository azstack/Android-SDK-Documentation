# 1. Quick Start
AZStack is the full-stack building block for communications.
This Quick Start guide will help you run a sample project powered by AZStack as fast as possible. To run the sample project, you will need Android Studio installed

```
1. Clone sample project from git hub: 
https://github.com/azstack/Android-SDK-Sample-Project.git
2. Open and run in Android Studio
```

# 2. Settup and installation
To integerate AZStack SDK to your application, you need to create an AZStack account. If you do not have an AZStack account, sign up here(coming soon) or get account from AZStack team.
When you create account successfully, AZStack provide you an application ID(appId) to be used in your application(client) and a RSA public key to be used on server side
AZStack SDK is built and designed to be used with Android Studio. The following instructions will help you to integrate AZStack into your application:
### 2.1. Adding AAR
Copy AZStack.aar to libs folder at the app level
Navigate to build.gradle file at the app level and adding the following lines:
```
repositories {
        flatDir {
            dirs 'libs'
        }
}

dependencies {
    compile(name: 'AZStackSDK', ext: 'aar')
}
```

### 2.2. AndroidManifest.xml
The AZStack SDK requires some permissions and references from your app's AndroidManifest.xml file. These permissions allow the SDK to monitor network state and receive Google Cloud Messaging messages. Below is an example with a com.example package; replace with your own package when merging with your own manifest.
```
<?xml version="1.0" encoding="utf-8"?>
<manifest xmlns:android="http://schemas.android.com/apk/res/android"
    package="com.example"
    android:versionCode="1"
    android:versionName="1.0" >

    <uses-sdk
        android:minSdkVersion="10"
        android:targetSdkVersion="21" />

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

    <application
        android:allowBackup="true"
        android:icon="@drawable/ic_launcher"
        android:label="@string/app_name">
        <activity
            android:name="com.azstack.activity.ChatActivity"
            android:configChanges="keyboardHidden|orientation|screenSize"
            android:launchMode="singleTask"
            android:screenOrientation="portrait"
            android:theme="@android:style/Theme.Translucent.NoTitleBar"
            android:windowSoftInputMode="stateHidden|adjustResize" >
        </activity>
        <activity
            android:name="com.azstack.activity.ChatGroupActivity"
            android:configChanges="keyboardHidden|orientation|screenSize"
            android:launchMode="singleTask"
            android:screenOrientation="portrait"
            android:theme="@android:style/Theme.Translucent.NoTitleBar"
            android:windowSoftInputMode="stateHidden|adjustResize" >
        </activity>
        <activity
            android:name="com.azstack.activity.FreeCallActivity"
            android:theme="@android:style/Theme.Translucent.NoTitleBar" >
        </activity>
        <activity
            android:name="com.azstack.activity.IncomingCallActivity"
            android:theme="@android:style/Theme.Translucent.NoTitleBar" >
        </activity>
        <activity
            android:name="com.azstack.activity.RecentDetailActivity"
            android:theme="@android:style/Theme.Translucent.NoTitleBar" >
        </activity>
        <activity
            android:name="com.azstack.activity.ViewPhotoActivity"
            android:theme="@android:style/Theme.Translucent.NoTitleBar" >
        </activity>
        <activity
            android:name="com.azstack.activity.ReviewPhotoActivity"
            android:theme="@android:style/Theme.Translucent.NoTitleBar" >
        </activity>
        <activity
            android:name="com.azstack.activity.ConversationActivity"
            android:theme="@android:style/Theme.Translucent.NoTitleBar" >
        </activity>
        <activity
            android:name="com.azstack.activity.GroupListActivity"
            android:theme="@android:style/Theme.Translucent.NoTitleBar" >
        </activity>
        <activity
            android:name="com.azstack.activity.GroupInfoActivity"
            android:theme="@android:style/Theme.Translucent.NoTitleBar" >
        </activity>
        <activity
            android:name="com.azstack.activity.GalleryRootActivity"
            android:theme="@android:style/Theme.Translucent.NoTitleBar" >
        </activity>
        <activity
            android:name="com.azstack.activity.GalleryDirectoryActivity"
            android:theme="@android:style/Theme.Translucent.NoTitleBar" >
        </activity>
        <activity
            android:name="com.azstack.activity.SendLocationActivity"
            android:theme="@android:style/Theme.Translucent.NoTitleBar" >
        </activity>
        <activity
            android:name="com.azstack.activity.ShowLocationActivity"
            android:theme="@android:style/Theme.Translucent.NoTitleBar" >
        </activity>
        <activity
            android:name="com.azstack.activity.CropImageActivity"
            android:theme="@android:style/Theme.Translucent.NoTitleBar" >
        </activity>
        <activity
            android:name="com.azstack.activity.ListStickerActivity"
            android:theme="@android:style/Theme.Translucent.NoTitleBar" >
        </activity>
        <activity
            android:name="com.azstack.activity.StickerDetailActivity"
            android:theme="@android:style/Theme.Translucent.NoTitleBar" >
        </activity>
        <activity
            android:name="com.azstack.activity.ForwardActivity"
            android:theme="@android:style/Theme.Translucent.NoTitleBar" >
        </activity>
        <activity
            android:name="com.azstack.activity.ChooseMultiContactActivity"
            android:theme="@android:style/Theme.Translucent.NoTitleBar" >
        </activity>
        <activity
            android:name="com.azstack.activity.FileExplorerActivity"
            android:theme="@android:style/Theme.Translucent.NoTitleBar" >
        </activity>
        <activity
            android:name="com.azstack.activity.ChooseOneContactChatActivity"
            android:theme="@android:style/Theme.Translucent.NoTitleBar" >
        </activity>
        <activity
            android:name="com.azstack.activity.ChooseOneContactActivity"
            android:theme="@android:style/Theme.Translucent.NoTitleBar" >
        </activity>
        <activity
            android:name="com.azstack.activity.ChatSlidingMenu"
            android:theme="@android:style/Theme.Translucent.NoTitleBar" >
        </activity>
        <activity
            android:name="com.azstack.activity.GunDrawActivity"
            android:theme="@android:style/Theme.Translucent.NoTitleBar" >
        </activity>
        <activity
            android:name="com.azstack.activity.GunGGalleryActivity"
            android:theme="@android:style/Theme.Translucent.NoTitleBar" >
        </activity>
        <activity
            android:name="com.azstack.activity.GunGDirectoryActivity"
            android:theme="@android:style/Theme.Translucent.NoTitleBar" >
        </activity>

        <meta-data
            android:name="com.google.android.maps.v2.API_KEY"
            android:value="AIzaSyDuqAE6o4Uj45SVyQstieg00BxxSA8ICAI" />
        <meta-data
            android:name="com.google.android.gms.version"
            android:value="@integer/google_play_services_version" />
    </application>
	
</manifest>
```

# 3. Connecting
### 3.1 Instantiate
Each application must register with AZStack for 1 appID. For example: 
```
String appId = "26870527d2ac628002dda81be54217cf";   
```

The AZStack SDK has a primary interface AzStackClient for interacting with AZStack service. You have to initialize AzStackClient object in onCreate() method of your Application or your main Activity. Only once instance of AzStackClient should be instantiated and used all time:
```
AzStackClient azStackClient = AzStackClient.newInstance(context, appId);
```

### 3.2 Listeners
The AZStack SDK uses listener pattern to push specific events to your application. You need register 3 listeners AzStackConnectListener, AzStackAuthenticateListener, AzStackContactListener.
```
azStackClient.registerConnectionListenter(AzStackConnectListener instance)
azStackClient.registerAuthenticateListenter(AzStackAuthenticateListener instance)
azStackClient.registerContactListener(AzStackContactListener instance)
```

### 3.3 Connect and authenticate
In order for a user to chat or call, you must authenticate them first. AZStack will accept any unique String as a User ID (UIDs, email addresses, phone numbers, usernames, etc), so you can use any new or existing User Management system. As part of the Authentication process, you will need to set up a Web Service which generates a unique Identity Token for each user on request
You should start authentication process after AZStack SDK connectes successfully. The process is described in the following model:

![AZStack init and authentication](http://azstack.com/docs/static/AndroidAuthentication_3.png "AZStack init and authentication")

#### Connect AZStack Server
```
azStackClient.connect();
```

You can register AzStackConnectListener for listening connect events such as: connected, disconnected, connect failed...
```
azStackClient.registerConnectionListenter(new AzStackConnectListener() {

			@Override
			public void onConnectionError(AzStackClient client,
					AzStackException e) {
				//Connect to AZStack Server fail 
			}

			@Override
			public void onConnectionDisconnected(AzStackClient client) {
				//Disconnect AZStack Server
			}

			@Override
			public void onConnectionConnected(AzStackClient client) {
				// Called when connect to AZStack server successfully
				// You should start authentication here
				if (!AzStackClient.getInstance().isAuthenticated()) {
					AzStackClient.getInstance().authenticate();
				}
			}
		});
```
#### Authenticate
Once connected, AZStack requires every users to be authenticated before they can send, receive message or make, receive a call. To authenticate, call AzStackClient.getInstance().authenticate() method in AzStackConnectListener.onConnectionConnected() like above instruction.

```
azStackClient.registerAuthenticateListenter(new AzStackAuthenticateListener() {

			@Override
			public void onDeauthenticated(AzStackClient client) {
			}

			@Override
			public void onAuthenticationError(AzStackClient client, 
						AzStackException e) {
			}
			

			@Override
			public void onAuthenticationChallenge(AzStackClient client, 
						String nonce) {
				//CODE goes here. Post the nonce to your backend. Generate and return                 //an Identity Token
				String authenToken = getToken(azStackUserID, nonce);
						
				//after get authenToken, you must call this method
				azStackClient.answerAuthenticationChallenge(authenToken);
			}

			@Override
			public void onAuthenticated(AzStackClient client, String arg1) {
			}
		});
```
Once the authenticate method is called, the onAuthenticationChallenge() callback executes with the nonce in the AzStackAuthenticateListener. You must setup your own Web Service to validate a user's credentials and create an Identity Token.
That Identity Token is returned to your app, and then passed on to the AZStack server. If the Identity Token is valid, the Authentication process will complete.For more information about configuring your own Authentication Web Service check out the Web Service Authentication Guide

#### Web Service Authentication Guide
On authentication web service, you need to generate authentication token to return to the app. 

Authentication token is generated by encrypting the following information:
```
{
	"azStackUserID" : azStackUserID, identifier Of app'user.
	"nonce" : nonce
}
```
using RSA publicKey generated in step 1. You can refer to https://github.com/azstack/Backend-example/blob/master/gen_token_test.php for sample code.

### 3.4 AzStackContactListener
AzStackContactListener need to be registered when initialize AzStackClient object. It's used to get basic information of app's user such as: name, avatar... to display on chat, call screen.

```
azStackClient.registerContactListener(new AzStackContactListener() {
            @Override
            public void getUserInfo(String azStackUserId) {
                // This code implemention is only for testing purpose
                // When going into production, you have to implement your own
                // web service to get your app's user info
                AzContact user = Utils.getUserInfo(azStackUserId);
                azStackClient.getUserInfoComplete(user);
            }

            @Override
            public void viewContactInfo(String azStackUserId) {

            }
        });
```

### 3.4 Push notification
If you need push notification for your app, instantiate AzStackClient with GCM sender id via Options object:
```
AzOptions azOptions = new AzOptions ();
azOptions.setGoogleCloudMessagingId(appId);			
AzStackClient azStackClient = AzStackClient.newInstance(this, appId, azOptions);
```

You have to declare some permissions for push notification in AndroidManifest.xml
```
<permission android:name="com.mypackage.permission.C2D_MESSAGE"
    android:protectionLevel="signature" />
<uses-permission android:name="com.bchat.permission.C2D_MESSAGE" />
<uses-permission android:name="com.google.android.c2dm.permission.RECEIVE" />
<uses-permission android:name="android.permission.GET_ACCOUNTS" />
<uses-permission android:name="android.permission.WAKE_LOCK" />
```

Add receivers and services to AndroidManifest.xml
```
<!-- [START gcm_receiver] -->
<receiver
    android:name="com.google.android.gms.gcm.GcmReceiver"
    android:exported="true"
    android:permission="com.google.android.c2dm.permission.SEND" >
    <intent-filter>
        <action android:name="com.google.android.c2dm.intent.RECEIVE" />
        <category android:name="com.mypackage" />
    </intent-filter>
</receiver>
<!-- [END gcm_receiver] -->

<!-- [START gcm_service] -->
<service
    android:name=".MyGcmListenerService"
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
    }
}
```

### 3.5 Start chat
```
azStackClient.startChat(azStackUserId, name, avatar);

Parameter: 	azStackUserId: identifier of app’s user, required
			name: name of app’s user, default “No name”, optional
			avatar: avatar of app’s user, optional
```

### 3.6 Start call
```
azStackClient.startCall(azStackUserId, name, avatar);

Parameter: 	azStackUserId: identifier of app’s user, required
			name: name of app’s user, default “No name”, optional
			avatar: avatar of app’s user, optional
```

### 3.7 Disconnect
```
azStackClient.disconnect();
```
