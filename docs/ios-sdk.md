# Taki iOS SDK

## Installing

- Add Taki SDK to your Podfile:

```ruby
target :yourTarget do
  pod 'TakiSDK', :git => 'https://github.com/indigotech/taki-sdk-ios.git', :tag => '<version>'
end
```

- After a pod install, the SDK will be ready to use.

## Initializing

- Make sure Firebase is configured and you are able to get push notifications
- Import the Taki SDK:

```swift
import TakiSDK
```

- Configure with you authentication data:

```swift
Taki.sharedInstance.configure("<id>", appSecret: "<secret>")
```

- Initialize the Taki SDK passin the push notification token and the user identifier:

```swift
if(Messaging.messaging().fcmToken != nil) {
    Taki.sharedInstance.update("123456", token: Messaging.messaging().fcmToken!)
}
```

## Handling push notifications

- On the method that handles your push notifications, pass the notification, alog with the Firebase authentication

```swift
Taki.sharedInstance.processNotification(userInfo, auth: Auth.auth(), completion: sendPush)
```

The completion method will then be called with the push notification already edited information.