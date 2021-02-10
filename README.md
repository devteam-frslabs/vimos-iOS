# Vimos iOS SDK

![version](https://img.shields.io/badge/version-v1.0.0-blue)

The Captus SDK is a set of screens to capture the front and back images of ID documents. It also allows the user to manually verify that the documents are clean and clear. This SDK is useful for IDs that cannot be processed on the mobile and needs server-side processing. 

You can find the release history at [Changelog](CHANGELOG.md)

# Table Of Content

- [Prerequisite](#prerequisite)
- [Requirements](#requirements)
- [Permission](#permission)
- [Installation](#installation)
- [Getting Started](#getting-started)
- [Captus Error Codes](#captus-error-codes)
- [Help](#help)

## Prerequisite

***NOTE : Encryption of CAPTUS SDK Result is under development***

You will need a valid license and Netrc credentials to use the Captus SDK, which can be obtained by contacting support@frslabs.com. 

Once you have the license , follow the below instructions for a successful integration of Captus SDK onto your iOS Application.

## Requirements

- Swift 5.0
- iOS 13.0+

## Installation

### Cocoapods


You can use [CocoaPods](http://cocoapods.org/) to install `captus` by adding it to your `Podfile`:

```ruby
source 'https://gitlab.com/frslabs-public/ios/vimos-ios'
source 'https://github.com/CocoaPods/Specs.git'
platform :ios, '13.0'
target '<Your Target Name>' do
use_frameworks!
pod 'Vimos', ‘1.0.0’
end
```

###### Save/Edit Netrc settings to install custom pod

You will need a valid netrc credentials to install captus from maven, which can be obtained by contacting `support@frslabs.com`. 

1. Create or edit .netrc file under current user's home directory
2. Write the below lines into that file, replace <YOUR_USERNAME> and <YOUR_PASSWORD> with your credentials which is shared through email and save the file.
```ruby
machine vimos-ios.repo.frslabs.space
login <YOUR_USERNAME>
password <YOUR_PASSOWRD>
```
3. In terminal enter below command to install the pod

   pod install or pod update.

4. Connect with physical device to build and run vimos, It will not build/run in simulator due to camera dependency.

To get the full benefits import `vimos` wherever you import UIKit

``` swift
import UIKit
import Vimos
```

## Getting Started

### Swift

1. Invoke Vimos SDK

```swift
    // ...
    
    override func viewDidAppear(_ animated: Bool) {
         let kyc = KycController(delegate: self)
        kyc.modalPresentationStyle = .fullScreen
        kyc.customerLink = "ENTER CUSTOMER LINK"
        kyc.licenceKey   = "ENTER LICENSE KEY"
        present(kyc, animated: false)
      }
    // ...    
```

2. Handling the result and import delegate OCRDelegate

```swift
class YourViewController: UIViewController,OCRDelegate {

   func vimosController(_ callerContoller: KycController, didFinishWithResults results: VimosResults) {
        print("VIMOS : SUCCESS")
    }
    func vimosController(_ callerContoller: KycController, didFailWithError error: Int) {
        print("VIMOS : FAILURE")
    }
  
}
```
   Sets the Captus SDK apiCredentials . Obtain the appropriate api credentials through a REST API call , for details about the REST API, contact `support@frslabs.com`


   ## Help
   For any queries/feedback , contact us at `support@frslabs.com` 
