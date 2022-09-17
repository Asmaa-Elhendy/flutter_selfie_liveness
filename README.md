# selfie_liveness

A new Flutter Plugin for detecting liveness.




## Using


The plugin is very easy to use. to use the plugin  just call a single functions that returns the file/image path of the captured user. 


```dart
import 'package:selfie_liveness/selfie_liveness.dart';


//and call and await the function to return imagePath of the captured user
  SelfieLiveness.detectLiveness(
                      poweredBy: "",
                      assetLogo: "assets/raven_logo_white.png",
                      msgselfieCapture:
                          "Place your face inside the oval shaped panel",
                      msgBlinkEye: "Blink your eyes to capture");;

 
```


## IOS Requirements

update your ios/Runner/info.plist

```
<key>NSCameraUsageDescription</key>
<string>Allow Camera Permission</string>
<key>NSPhotoLibraryUsageDescription</key>
<string>Alllow photo library to store your captured image</string>


```

and ios/Podfile to

```
platform :ios, '13.0'

and run the command 'pod install'

```

 


## Example


```dart
import 'package:flutter/material.dart';
import 'dart:io';
import 'package:selfie_liveness/selfie_liveness.dart';

void main() {
  runApp(ElatechLiveliness());
}

class ElatechLiveliness extends StatefulWidget {
  @override
  State<StatefulWidget> createState() {
    return _ElatechLiveliness();
  }
}

class _ElatechLiveliness extends State<ElatechLiveliness> {
  String value = "";
//asset image required
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      home: Scaffold(
        body: SizedBox(
          width: double.infinity,
          child: Column(mainAxisAlignment: MainAxisAlignment.center, children: [
            value != ""
                ? Image.file(new File(value), key: UniqueKey())
                : const SizedBox(),
            Text("Press The Button To Take Photo"),
            ElevatedButton(
                onPressed: () async {
                  value = await SelfieLiveness.detectLiveness(
                      poweredBy: "",
                      assetLogo: "assets/raven_logo_white.png",
                      msgselfieCapture:
                          "Place your face inside the oval shaped panel",
                      msgBlinkEye: "Blink your eyes to capture");
                  setState(() {});
                },
                child: const Text("Detect Liveness"))
          ]),
        ),
      ),
    );
  }
 
}

```

