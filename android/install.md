# Android Installation

## React-Native > `0.60.0` 
If you are using autolinking feature introduced in React-Native `0.60.0` you do not need any additional steps.

## Mapbox Maps SDK

It is possible to set a custom version of the Mapbox SDK


Add the following to your  `android/build.gradle`:

under section `allprojects/repositories`
```
        maven {
            url 'https://api.mapbox.com/downloads/v2/releases/maven'
            authentication {
                basic(BasicAuthentication)
            }
            credentials {
                // Do not change the username below.
                // This should always be `mapbox` (not your username). 
                username = 'mapbox'
                // Use the secret token you stored in gradle.properties as the password
                password = project.properties['MAPBOX_DOWNLOADS_TOKEN'] ?: ""
            }
        }
```

Overwrite mapbox dependencies within your `android/app/build.gradle`:

```
dependencies {
    ...
    implementation 'com.mapbox.mapboxsdk:mapbox-android-sdk:9.6.1'
    implementation 'com.mapbox.mapboxsdk:mapbox-sdk-services:5.6.0'
    implementation 'com.mapbox.mapboxsdk:mapbox-android-plugin-annotation-v9:0.9.0'
    ...
```

Check the current version of the SDK [here](https://docs.mapbox.com/android/maps/guides/).


If you are using version newer versions of the SDK, you will need to authorize your download of the Maps SDK with a secret access token with the DOWNLOADS:READ scope. This [guide](https://docs.mapbox.com/android/maps/guides/install/#configure-credentials) explains how to configure the secret token under section `Configure your secret token`.
