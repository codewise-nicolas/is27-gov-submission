# Instructions
This repository includes a sample React Native application from https://github.com/bcgov/sample-mobile-app with Github Workflows to build both iOS and Android binaries.
Instructions are provided to get up and running with local development and also using the workflow to generate builds of the app.

---

## Getting Started - Local Development
This project uses a so called bare flow to be able to use react-native to build the binaries locally (and in github workers) instead of using the expo cloud service. 
Building for iOS locally will require a Mac OS machine.
It is assumed your environment is setup for iOS development (Xcode) and/or Android development (Android SDK/Android Studio).

### Initial Run Steps
First Clone/Fork this repository and then follow the instructions in the ORIGINAL_README.md to setup the local development environment.

iOS
- Depending on your setup you may need to run cocoapods install scripts to finish setting up the /ios project. `npx pod-install`
- The first time as part of the initial setup you will need to build and deploy the app to the simulator of choice with a command for example
> `yarn react-native run-ios --simulator "iPhone 8"`

Android
- Android is simpler in that you only need to run the following command once to get the app built and deployed to the sim

> `yarn react-native run-android`

### Subsequent Development
After the initial run steps that build and deploy, you can start using `yarn expo run:ios` or `yarn expo run:android` for regular development.

*IMPORTANT:* Whenever you add/change any native components you will need to re-build and deploy the native app using the `react-native...` command.

---

## Build Process with Github Actions
The project has been setup with a Github Workflow YAML file to make use of Github Actions to build binaries of the app.
It has been setup to run manually via the website or cli. This can be changed to run on push or similar actions as desired.

### Running Github Flow
To run the flow, go to the Github Repository > Actions > 'Build Sample Mobile App for IOS And Android' then click on the drop down "Run workflow", and finally click the green "Run workflow".

### Flow Output/Binaries
Once the flow is complete, you will find the generated binary under the Summary > Artifacts section of the corresponding workflow run results.


The generated .app for iOS can be dragged into an iOS Simulator to run. The generated .aab can be converted to an APK for installation in a simulator with Androids `bundletool` or submitted to the Google Play Store.

### Adaptation to fully automated deployment
As written the workflow generates binaries of the app for iOS and Android as per the Mandatory Task instructions, however to meet the Scoring the flow needs to be augmented to be fully automated from git push to app store deployment. I willl document the extra steps needed to meet this goal.

- The workflow as written would be changed to act on the push event. Depending on how often code is pushed, the action may need to be on a specific label.
- For iOS path, the xcode provisioning profile and signing certificate (password protected) would be included in the repo and the password made part of the Github Secrets so as to not leak them in the repository. The flow would then include xcodebuild commands to archive the project and then push to TestFlight.
- For Android, depending on whether signing is managed locally or by Google Play different approaches can be followed. However, Google is now recommending that developers let Google Play manage signing. Thus the flow would be augmented to sign the aab with a private key (password protected) and the password made part of the Github Secrets (similar to iOS); this is usually handled by the gradle build steps.


---

## Changes from the original project
The original project https://github.com/bcgov/sample-mobile-app was changed to move from a fully managed workflow to a so called bare flow to be able to use react-native to build the binaries locally (and in github workers) instead of using the expo cloud service. Building for iOS locally will require a Mac OS machine.

- `yarn expo eject`