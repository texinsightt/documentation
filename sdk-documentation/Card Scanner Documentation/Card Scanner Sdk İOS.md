# "Newky Card Scanner SDK İOS" by **Newky**
### - What is Newky Card Scanner ?
**Card Scanner is a library made by newky that extracts driver credentials using image processing algorithms.**
**The Card Scanner can be used for many differend tasks.**
- For Registration process
- For comparison operations
- For authentication

## **Usage**
        
##### 1. İnitialize SDK
To use the SDK, you need to initialize it with an API key. The API key is provided by NewkyCardScannerConfig.sharedInstance. 
```swift
func application(_ application: UIApplication, didFinishLaunchingWithOptions launchOptions: [UIApplication.LaunchOptionsKey: Any]?) -> Bool {
    NewkyCardScannerConfig.sharedInstance.configure(withApiKey: "<api_key>")
    return true
}
```
##### 2. Create a Scanner Instance
To create a scanner instance, use the `create` method of the `NewkyScannerViewController` class:
```swift
let controller = NewkyScannerViewController.create(cardType: .driverLicense, country: .tr, side: .front)
```
You can then present the scanner view controller:
```swift
present(controller, animated: true)
```

To track the status of the scanner, implement the `NewkyScannerViewControllerDelegate` protocol in your view controller and set the delegate of the scanner view controller:

```swift
controller.delegate = self
```

You can then implement the following delegate methods to track the status of the scanner:

```swift
func scannerClosed(_ scannerController: NewkyScannerViewController)
func scannerCompletedWithResult(_ scannerController: NewkyScannerViewController, didExtractInformation scannerResult: ScannerExtractResult)
func scannerCompletedWithError(_ scannerController: NewkyScannerViewController, didFailWithError error: NewkyCardScannerError)
```

For example, you can dismiss the scanner view controller and display the extracted information in a label:

```swift
func scannerCompletedWithResult(_ scannerController: NewkyScannerViewController, didExtractInformation scannerResult: ScannerExtractResult) {
    scannerController.dismiss(animated: true)
    // handle scannerResult
}
```

##### Note :
**You can review the design for a sample use case.**

