# "Newky Face Scanner SDK İOS "  by **Newky**
### What is Newky Face Scanner ?
**Face Scanner, made by newky, scans users' faces with image processing algorithms. Comparisons or recordings can be made with the scan results.**
**You can do the following operations with face sdk.**
- For Registration process
- For comparison operations
- For authentication
- For verification 
 

## Usage
##### 1.İnitialize SDK
To initialize the SDK, add the following code to your `AppDelegate`:

```swift
NewkyFaceConfig.sharedInstance.configure(withApiKey: "<api-key>")
```

Replace `"<api-key>"` with your own API key.


##### a. Register
To create an instance register screen of the SDK, use the following code:

```swift
let vc = StepController.create(state: .registerWithPhoto, userId: UUID().uuidString)
```

The `StepState` enumeration is used to register a user by person. It has two possible meanings:

-   `registerWithPhoto`: Indicates that the user needs to register using a driver's license photo.
-   `register`: Indicates that the user needs to register without a photo, only using a face scanner.
##### b. Recognition

To create an instance of `FaceRecognitionController`, use the following code:

```swift
let vc = FaceRecognitionController.create(userId: userId)
```

Replace `userId` with the ID of the user.

##### Delegate methods

To implement the delegate methods for face recognition, use the following code:

```swift
extension FirstViewController: FaceRegisterControllerDelegate, FaceRecognitionControllerDelegate {
    
    func faceRecognitionControllerLoginFail(_ controller: NewkyFace.FaceRecognitionController, withErrorText errorText: String) {
        // handle error
    }
    
    func faceRecognitionControllerLoginSuccess(_ controller: NewkyFace.FaceRecognitionController) {
        // handle success recognition result
    }
}
```

##### Note:
**You can review the designs for sample usage scenarios.**
