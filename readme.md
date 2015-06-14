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
