#SNS Mobile Push and Mobile Analytics Sample

This sample demonstrates how you would track user engagement for the mobile push notifications using [Amazon Cognito](http://aws.amazon.com/cognito/), [Amazon SNS Mobile Push](http://aws.amazon.com/sns/), and [Amazon Mobile Analytics](http://aws.amazon.com/mobileanalytics/).

##Requirements

* Xcode 5 and later
* iOS 7 and later
* Before moving forward, follow [Getting Started with Apple Push Notification Service](http://docs.aws.amazon.com/sns/latest/dg/mobile-push-apns.html) and [Using Amazon SNS Mobile Push](http://docs.aws.amazon.com/sns/latest/dg/mobile-push-send.html) and configure Amazon SNS Mobile Push properly.

##Setting up CocoaPods

1. The AWS Mobile SDK for iOS is available through [CocoaPods](http://cocoapods.org). If you have not installed CocoaPods, install CocoaPods by running the command:

		sudo gem install cocoapods
		pod setup

1. In your project directory, create a text file named **Podfile** and add the following lines:

        source 'https://github.com/CocoaPods/Specs.git'
        
        pod 'AWSSNS'
        
1. Then run the following command:
	
		pod install

##Getting Started

1. Import the service headers in the bridging header in `AppDelegate.m`.

		#import <AWSSNS/AWSSNS.h>

1. In the [Amazon Cognito console](https://console.aws.amazon.com/cognito/), use Amazon Cognito to create a new identity pool. Obtain the `PoolID` constant. Make sure the [role](https://console.aws.amazon.com/iam/home?region=us-east-1#roles) has appropriate permissions for Amazon SNS Mobile Push and Amazon Mobile Analytics. Use Amazon Mobile Analytics to create an app, and obtain the `AppId` constant.

1. Open `Constants.m` and update the following lines with the appropriate constants:

        AWSRegionType const CognitoRegionType = AWSRegionUnknown; // e.g. AWSRegionUSEast1
        AWSRegionType const DefaultServiceRegionType = AWSRegionUnknown; // e.g. AWSRegionUSEast1
        NSString *const CognitoIdentityPoolId = @"YourCognitoIdentityPoolId";
        NSString *const SNSPlatformApplicationArn = @"YourSNSPlatformApplicationArn";
        NSString *const MobileAnalyticsAppId = @"YourMobileAnalyticsAppId";
