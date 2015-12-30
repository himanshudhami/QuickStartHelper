#**_Commands to install and start ionic_** 

####Install cordova and ionic, Install XCode if you want to build for ios
_npm install -g cordova ionic_

####Create one using

_ionic start myApp_ 

####or clone an existing one

_git clone ....myApp.git_

####Move to the project directory

_cd myApp_

####Add required platform

_ionic platform add **ios** or **android**_

####Build the application for the platform

_ionic build ios_ (This needs Xcode to be installed)

####Start the emulator

_ionic emulate ios_ (This needs ios-sim to be installed, install using npm install -g ios-sim)

#####Time to see it realtime, You can use _ionicview_ to see your app in action, ionicview is available on itunes and google play store

_ionic upload_ ( Give your ionicview credentials to start viewing it)

####Step 2: Building and Signing your Android Release

We will need to build a digital signed Android release APK file to distribute your app on Google Play Store or other app distribution channels. (Your will need to pre-install Android SDK before moving to this step)

Add Android platform support in your app if you have not done so. Inside your app root folder, type in terminal: $ ionic platform add android

Create your digital signed key $ keytool -genkey -v -keystore my-release-key.keystore -alias alias_name -keyalg RSA -keysize 2048 -validity 10000 Follow the on screen instruction to type in your password and information. Please save this key in a safe location. You will need it again when you sign a new build and release an update.

Build an release version of your app $ ionic build --release android It will generate an android-release-unsigned.apk file under your platform/android/build/output/apk path. Copy the apk file into your app root folder so you do not need to type in the path.

Sign your release build apk. $ jarsigner -verbose -sigalg SHA1withRSA -digestalg SHA1 -keystore my-release-key.keystore android-release-unsigned.apk alias_name

Align your build with zipalign tool for android build tool. $ [Your Android SDK path]/build-tools/[Newest version number]/zipalign -v 4 android-release-unsigned.apk myapp-signed.apk If you keep getting command not find error, You can also just navigate to your android sdk folder, find the zipalign tool under build-tools, version number and drag the folder into your terminal to get the absolute path.
