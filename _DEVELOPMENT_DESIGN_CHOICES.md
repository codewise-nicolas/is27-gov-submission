# Development Process and Design Choices

- Purely for the purpose of this assignment, I decided to create a new repository instead of forking the existing project so that my work for this assignment, while public, would not be easily found via the Github fork history/insights feature.

- As much setup as possible was done locally to get the proper commands to create the Github Workflow. This expedited setup by quickly iterating over commands and parameters to determine the optimal ones for the flow with the least amount of actual Github actions time which is a limited resource for free accounts or can get expensive on paid tiers.

- Tooling such as "act" is used to help test out the workflow locally using docker containers, however this is primarily only helpful for android flows.

- The original sample project relied on the expo tooling to handle development, deployment, and all related tasks but this complicated local build as that tooling uses a cloud based compile system when generating final binaries but I wanted to use only local tooling within the Github workers. The project had expo ejected (converted to a bare project) to allow for react-native cli use for local compilation of the final binaries of the app.

- I chose macos-12 instead of macos-latest for the build steps because currently macos-latest refers to macos-11.
Apple tends to prefer apps be built with the latest version of XCode and that is only available on the latest Mac OS.

- For the assignment I choose a non-colliding bundle ID based on my name: com.nicolasgomez.is27submissionsampleapp. Proper structure of the bundle id (com.*.*) was used to best represent real life use even thought I could have used a one or two tiered bundle id for testing (* or *.*)

- With Xcode 9+ it is not possible (at least I have not found a way) to generate an unsigned/no team IPA file, the resulting generated file for iOS is a .app for the simulator.