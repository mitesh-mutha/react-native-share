﻿# react-native-share [![npm version](https://badge.fury.io/js/react-native-share.svg)](http://badge.fury.io/js/react-native-share)
Share Social , Sending Simple Data to Other Apps

## Getting started

### Mostly automatic install
1. `npm install rnpm --global`
2. `npm install react-native-share --save`
3. `rnpm link react-native-share`

### Manual install

#### iOS

1. `npm install react-native-share --save`
2. In XCode, in the project navigator, right click `Libraries` ➜ `Add Files to [your project's name]`
3. Go to `node_modules` ➜ `react-native-share` and add `RNShare.xcodeproj`
4. In XCode, in the project navigator, select your project. Add `libRNShare.a` to your project's `Build Phases` ➜ `Link Binary With Libraries`
5. Run your project (`Cmd+R`)

#### Android

1. `npm install react-native-share --save`
2. Open up `android/app/src/main/java/[...]/MainActivity.java`
  - Add `import cl.json.RNSharePackage;` to the imports at the top of the file
  - Add `new RNSharePackage()` to the list returned by the `getPackages()` method
3. Append the following lines to `android/settings.gradle`:
  	```
  	include ':react-native-share'
  	project(':react-native-share').projectDir = new File(rootProject.projectDir, 	'../node_modules/react-native-share/android')
  	```
4. Insert the following lines inside the dependencies block in `android/app/build.gradle`:

    	```
        compile project(':react-native-share')
    	```

#### Windows
[Read it! :D](https://github.com/ReactWindows/react-native)

1. `npm install react-native-share --save`
2. In Visual Studio add the `RNShare.sln` in `node_modules/react-native-share/windows/RNShare.sln` folder to their solution, reference from their app.
2. Open up your `MainPage.cs` app
  - Add `using Cl.Json.RNShare;` to the usings at the top of the file
  - Add `new RNSharePackage()` to the `List<IReactPackage>` returned by the `Packages` method


## Usage

```javascript
import React, {
  AppRegistry,
  Component,
  StyleSheet,
  Text,
  View,
  TouchableHighlight
} from 'react-native';
import Share from 'react-native-share';

class Example extends Component {
  onShare() {
    Share.open({
      share_subject: "email subject",
      share_text: "Hola mundo",
      share_URL: "http://google.cl",
      title: "Share Link"
    },(e) => {
      console.log(e);
    });
  }
  render() {
    return (
      <View style={styles.container}>
        <Text style={styles.welcome}>
          Welcome to React Native!
        </Text>
        <Text style={styles.instructions}>
          To get started, edit index.ios.js
        </Text>
        <Text style={styles.instructions}>
          Press Cmd+R to reload,{'\n'}
          Cmd+D or shake for dev menu
        </Text>
        <TouchableHighlight onPress={this.onShare}>
          <Text style={styles.instructions}>
            Social Share
          </Text>
        </TouchableHighlight>
      </View>
    );
  }
}

const styles = StyleSheet.create({
  container: {
    flex: 1,
    justifyContent: 'center',
    alignItems: 'center',
    backgroundColor: '#F5FCFF',
  },
  welcome: {
    fontSize: 20,
    textAlign: 'center',
    margin: 10,
  },
  instructions: {
    textAlign: 'center',
    color: '#333333',
    marginBottom: 5,
  },
});

AppRegistry.registerComponent('Example', () => Example);
```

NOTE: If both share_text and share_url are provided share_url will be concatenated to the end of share_text to form the body of the message. If only one is provided it will be used

#### Android Image Share
Sharing of images with caption is possible in Android. You have to provide the absolute full path of the image in options as "share_image_path".

For example, "/storage/emulated/0/image.jpg" <- is the absolute full path of the image to be shared. You provide that as the input for "share_image_path". 

The caption works in the way similar to text share.

NOTE: Ensure that the image is in a shared location and not in the app's private data area. It won't share otherwise.

## how it looks:
![Demo Android](/assets/android.png)
![Demo iOS](/assets/ios.png)
![Demo Windows](/assets/windows.png)
