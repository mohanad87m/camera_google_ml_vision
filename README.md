# camera_google_ml_vision

pub package

A Flutter package for iOS and Android to show a preview of the camera and detect things with Google ML Vision.

This version is a copy taken from
flutter_camera_ml_vision

Installation
First, add camera_google_ml_vision as a dependency.

...
dependencies:
  flutter:
    sdk: flutter
  camera_google_ml_vision: 
...

Android
Change the minimum Android sdk version to 21 (or higher) in your android/app/build.gradle file.

minSdkVersion 21
ps: This is due to the dependency on the camera plugin.


 
Usage
1. Example with Barcode
CameraMlVision<List<Barcode>>(
  detector: GoogleVision.instance.barcodeDetector().detectInImage,
  onResult: (List<Barcode> barcodes) {
    if (!mounted || resultSent) {
      return;
    }
    resultSent = true;
    Navigator.of(context).pop<Barcode>(barcodes.first.toString());
  },
)
CameraMlVision is a widget that shows the preview of the camera. It takes a detector as a parameter here we pass the detectInImage method of the BarcodeDetector object. The detector parameter can take all the different CameraMlVision Detector. Here is a list :

CameraMlVision.instance.barcodeDetector().detectInImage
CameraMlVision.instance.cloudLabelDetector().detectInImage
CameraMlVision.instance.faceDetector().processImage
CameraMlVision.instance.labelDetector().detectInImage
CameraMlVision.instance.textRecognizer().processImage
Then when something is detected the onResult callback is called with the data in the parameter of the function.

Exposed functionality from CameraController
We expose some functionality from the CameraController class here a list of these :

value
prepareForVideoRecording
startVideoRecording
stopVideoRecording
takePicture
Getting Started
See the example directory for a complete sample app.

Features and bugs
Please file feature requests and bugs at the issue tracker.

Technical Support
For any technical support, don't hesitate to contact us. Find more information in our website

For now, all the issues with the label support mean that they come out of the scope of the following project. So you can contact us as a support.
