Commands to install and start ionic 

npm install -g cordova ionic

Create one using 
ionic start myApp 

or clone an existing one

git clone ....myApp.git

Move to the project directory

cd myApp

Add needed platform

ionic platform add ios or android

Build the application for the platform

ionic build ios ( This needs Xcode to be installed)

Start the emulator

ionic emulate ios (This needs ios-sim to be installed, install using npm install -g ios-sim)

Time to see it realtime, You can use ionicview to see your app in action, ionicview is available on itunes and google play store

ionic upload ( Give your ionicview credentials to start viewing it)
