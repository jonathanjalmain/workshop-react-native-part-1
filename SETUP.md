# Setup

## OpenWeather API

In order to use the OpenWeather API, you must have an API Key.

1. Go to [OpenWeather](https://openweathermap.org/) and create an account / sign in
2. Go to your ***My API keys*** section
3. Give a name to your key and click on ***Generate***

Keep the web page since you will need to use the key later in your code.

## Expo Snack

### Workspace

You will develop the whole application through Expo Snack in the browser

1. Go to [Expo](https://expo.dev/accounts/ccchristiant) and create an account / sign in
2. Go to your dashboard and go to the ***Snacks*** sub-section
3. Click on ***New Snack***
4. Click on ***Save*** and name your snack "RN-WeatherApp"

### Smartphone linking

What you want to do first is to fetch the user's (in this case, you, obviously) coordinates (latitude, longitude) to display the weather at their location.

To get this information, we need to use a smartphone, whether an IOS or Android device.

1. On your Expo Snack preview (right side of the screen), click on ***My Device***
2. Download **Expo Go** and your device through the AppStore / Google Play Store depending on your case
3. Scan the QR Code
    - **IOS**: scan with your camera application and click on the popup
    - **Android**: scan it directly with Expo Go

Now that you have the preview directly on your device, close the web preview by clicking on the ***Preview*** toggle.

### Dependencies

Make sure your package.json looks like this:

    {
        "dependencies": {
        "expo-constants": "~13.2.4",
        "@expo/vector-icons": "^13.0.0",
        "react-native-paper": "4.9.2",
        "axios": "^1.3.3"
        "date-fns": "^2.29.3"
        "expo-location": "^15.0.1"
    }

## App.js

Make sure your App.js looks like this:

    import * as React from 'react';
    import { Text, View, StyleSheet } from 'react-native';
    import Constants from 'expo-constants';
                                   [d
    export default function AppO
       return С
        <View style={styles.container}>
          /View>
      );
    const styles = StyleSheet.createC{
       container: {
        flex: 1,
        justifyContent: 'center',
         paddingTop: Constants. statusBarHeight,
        backgroundColor: '#ecf0f1',
         padding: 8,
      له
    });

**[Let's start coding !](README.md#step-1---fetch-the-users-coordinates)**