# react-native-file-picker
A React Native module that allows you to use native UI to select a file from the device library
Based on [react-native-image-picker](https://github.com/marcshilling/react-native-image-picker)

## Install

### iOS
This component does not currently work on iOS, instead use [react-native-document-picker](https://github.com/Elyx0/react-native-document-picker)

### Android
1. `npm install react-native-file-picker@latest --save`

```gradle
// file: android/settings.gradle
...

include ':react-native-file-picker'
project(':react-native-file-picker').projectDir = new File(settingsDir, '../node_modules/react-native-file-picker/android')
```
```gradle
// file: android/app/build.gradle
...

dependencies {
    ...
    compile project(':react-native-file-picker')
}
```
```xml
<!-- file: android/src/main/AndroidManifest.xml -->
<manifest xmlns:android="http://schemas.android.com/apk/res/android"
    package="com.myApp">

    <uses-permission android:name="android.permission.INTERNET" />

    <!-- add following permissions -->
    <uses-permission android:name="android.permission.CAMERA" />
    <uses-permission android:name="android.permission.WRITE_EXTERNAL_STORAGE"/>
    <uses-feature android:name="android.hardware.camera" android:required="true"/>
    <uses-feature android:name="android.hardware.camera.autofocus" />
    <!-- -->
    ...
```
```java
// file: MainActivity.java
...

import com.filepicker.FilePickerPackage; // import package

public class MainActivity extends ReactActivity {

   /**
   * A list of packages used by the app. If the app uses additional views
   * or modules besides the default ones, add more packages here.
   */
    @Override
    protected List<ReactPackage> getPackages() {
        return Arrays.<ReactPackage>asList(
            new MainReactPackage(),
            new FilePickerPackage() // Add package
        );
    }
...
}

```
## Usage
1. In your React Native javascript code, bring in the native module:

  ```javascript
import FilePickerManager from 'react-native-file-picker';
  ```
2. Use it like so:

  When you want to display the picker:
  ```javascript

  FilePickerManager.showFilePicker((response) => {
    console.log('Response = ', response);

    if (response.didCancel) {
      console.log('User cancelled file picker');
    }
    else if (response.error) {
      console.log('FilePickerManager Error: ', response.error);
    }
    else {
      this.setState({
        file: response
      });
    }
  });
  ```

## News
### Compatible with react-native < 0.40
### Compatible with files from Google Drive
### Index.js added to ease up import
