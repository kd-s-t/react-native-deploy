Navigate to https://reactnative.dev/docs/environment-setup  
Choose React Native CLI Quickstart  
Choose Windows 
Choose Android  
npx react-native init smartLock

[Optional for designs] yarn add react-native-elements react-native-vector-icons react-native-safe-area-context  



## To deploy React Native  
keytool -genkeypair -v -keystore reactIot.keystore -alias my-key-alias -keyalg RSA -keysize 2048 -validity 10000  

## cp reactIot ./android/app  

## vim ./android/gradle.properties
MYAPP_RELEASE_STORE_FILE=reactIot.keystore  
MYAPP_RELEASE_KEY_ALIAS=reactIot  
MYAPP_RELEASE_STORE_PASSWORD=  
MYAPP_RELEASE_KEY_PASSWORD=  

## vim ./android/app/build.gradle
signingConfigs
{
    release
    {
        if (project.hasProperty('MYAPP_RELEASE_STORE_FILE'))
        {
            storeFile file(MYAPP_RELEASE_STORE_FILE)
            storePassword MYAPP_RELEASE_STORE_PASSWORD
            keyAlias MYAPP_RELEASE_KEY_ALIAS
            keyPassword MYAPP_RELEASE_KEY_PASSWORD
        }
    }
}

## To change app icon
cd android\app\src\main\res\mipmap-xxxhdpi
add your icon with 192 x 192 pixels

## To change app name
vim android/app/src/main/res/values/strings.xml  

## cd android
## gradlew bundleRelease

Check if .apk is available android\app\build\outputs\apk\release
Then upload it in your android mobile phone
In your phone, double click the APK
