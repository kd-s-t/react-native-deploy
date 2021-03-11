# To Setup React Native  

## To Setup React Native on Windows using Android emulator
Navigate to https://reactnative.dev/docs/environment-setup  
Choose `React Native CLI Quickstart`  
Choose `Windows`  
Choose `Android`   
run `npx react-native init smartLock`  
run `cd smartLock`  
[Optional for designs] run `yarn add react-native-elements react-native-vector-icons react-native-safe-area-context`  
run `npx react-native run-android`  


# To deploy React Native in Android Phone  
## Generate .keystore file  
Navigate to https://reactnative.dev/docs/signed-apk-android  
cd `smartLock/android/app`  
run `keytool -genkeypair -v -keystore react-iot.keystore -alias react-iot-alias -keyalg RSA -keysize 2048 -validity 10000`  
cd `../../`  

## Paste the env variables at the end of the file  
run `vim android/gradle.properties`  
MYAPP_RELEASE_STORE_FILE=react-iot.keystore  
MYAPP_RELEASE_KEY_ALIAS=react-iot-alias  
MYAPP_RELEASE_STORE_PASSWORD=123456  
MYAPP_RELEASE_KEY_PASSWORD=123456  

## Adding signing config to your app's Gradle config  
run `vim ./android/app/build.gradle`  
signingConfigs   
{  
&nbsp;&nbsp;release  
&nbsp;&nbsp;{  
&nbsp;&nbsp;&nbsp;&nbsp;if (project.hasProperty('MYAPP_RELEASE_STORE_FILE'))  
&nbsp;&nbsp;&nbsp;&nbsp;{  
&nbsp;&nbsp;&nbsp;&nbsp;storeFile file(MYAPP_RELEASE_STORE_FILE)  
&nbsp;&nbsp;&nbsp;&nbsp;storePassword MYAPP_RELEASE_STORE_PASSWORD  
&nbsp;&nbsp;&nbsp;&nbsp;keyAlias MYAPP_RELEASE_KEY_ALIAS  
&nbsp;&nbsp;&nbsp;&nbsp;keyPassword MYAPP_RELEASE_KEY_PASSWORD  
&nbsp;&nbsp;&nbsp;&nbsp;}  
&nbsp;&nbsp;}  
}   
buildTypes {  
&nbsp;&nbsp;release {  
&nbsp;&nbsp;&nbsp;&nbsp;...  
&nbsp;&nbsp;&nbsp;&nbsp;signingConfig signingConfigs.release  
&nbsp;&nbsp;}  
}  

## Change app icon  
open in file explore `smartlock\android\app\src\main\res\mipmap-xxxhdpi`  
add your icon with 192 x 192 pixels  

## Change app name
run `vim android/app/src/main/res/values/strings.xml`  
change app_name

## Deploying
run `cd android`  
run `gradlew bundleRelease`  
Check if .apk is available `android\app\build\outputs\apk\release`  
Then upload it in your android mobile phone  
In your phone, double click the APK  
