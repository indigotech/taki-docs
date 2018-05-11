# Taki Android SDK

## Installing

- Make sure you have configured Firebase Cloud Messaging on your app
- Add the following to yout top-level `build.gradle` file:

```java
allprojects {
   repositories {
       jcenter()
   }
}
```

- Add the followin to your app's `build.gradle` file:

```java
compile 'com.taqtile:taki-sdk-android:<Version Here>'
```

- Add your credentials to you AndroidManifest file:

```xml
<meta-data
    android:name="com.taqtile.takisdk.appId"
    android:value="<id>" />

<meta-data
    android:name="com.taqtile.takisdk.secret"
    android:value="<secret>" />
```

## Initializing

- Import the Taki package:

```kotlin
package com.taqtile.taki
```

- Initiate Taki and associate the pushh notification token to the user:

```kotlin
var taki = Taki.instance
taki.configure(this.baseContext)
taki.update("123456", FirebaseInstanceId.getInstance().getToken() as String
```

## Handling push notifications

- Implement the FirebaseMessagging class:

```kotlin
class NotificationHandler : FirebaseMessagingService() {
```

- Pass the notification to Taki so it'll be able to modify the content and decide if the notification will be shown

```kotlin
override fun onMessageReceived(remoteMessage: RemoteMessage?) {
    Taki.instance.processNotification(remoteMessage, listener)
}
```

- If the notification is to be shown, an event will be emitted with the already eduted push notification, so you can display it accordingly