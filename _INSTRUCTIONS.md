# Instructions
This repository includes a sample React Native application from https://github.com/bcgov/sample-mobile-app with Github Workflows to build both iOS and Android binaries.


---

## Getting Started - Local Development
This project uses a so called bare flow to be able to use react-native to build the binaries locally (and in github workers) instead of using the expo cloud service. 
Building for iOS locally will require a Mac OS machine.
It is assumed your environment is setup for iOS development (Xcode) and/or Android development (Android SDK/Android Studio).

### Steps
>First Clone/Fork this repository and then follow the instructions in the ORIGINAL_README.md to setup the local development environment.
>
>
>iOS
>- Depending on your setup you may need to run cocoapods install scripts to finish setting up the /ios project
>- The first time you will need to build and deploy the app to the simulator of choice, for example
>`yarn react-native run-ios --simulator "iPhone 8"`
>
>Android
>- Android is simpler in that you only need to run to get the app built and deployed to the sim
>`yarn react-native run-android`


After this initial build and deploy, you can go back to using `yarn expo ...` for development.

*Note:* Whenever you add/change any native components you will need to re-build and deploy the native app using the react-native command.

---

## Build Process with Github Actions
The project has been setup with a Github Workflow YAML file to make use of Github Actions to build binaries of the app.
It has been setup to run manually via the website or cli. This can be changed to run on push or similar actions as desired.

To run the flow, manually go to the Github Repository > Actions > Build Sample Mobile App for IOS And Android then click on the drop down "Run workflow", and finally click the green "Run workflow".

Once the flow is complete, you will find the generated binary under the Artifacts section of the corresponding job.


---

## Changes from the original project
The original project https://github.com/bcgov/sample-mobile-app was changed to move from a fully managed workflow to a so called bare flow to be able to use react-native to build the binaries locally (and in github workers) instead of using the expo cloud service. Building for iOS locally will require a Mac OS machine.

- `yarn expo eject`