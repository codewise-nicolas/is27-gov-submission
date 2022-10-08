# Design Choices

As much setup as possible was done locally to get the proper commands to create the Github Workflow. This expedited setup by quickly iterating over commands and parameters to determine the optimal ones for the flow with the least amount of actual Github actions time which is a limited resource for free or can get expensive on paid tiers.

Tooling such as "act" is used to help test out the workflow locally using docker containers, however this is only helpful for android.

The original sample project relied on expo to handle development but this complicated local build as that tooling uses a cloud based compile system but I wanted to make it local to the Github workers. The project had expo ejected (converted to a bare project) for local compilation.

I chose macos-12 instead of macos-latest for the build steps because currently macos-latest refers to macos-11.
Apple tends to prefer apps be built with the latest version of XCode and that is only available on the latest Mac OS.

For the assignment I choose a non-colliding bundle ID based on my name: com.nicolasgomez.is27submissionsampleapp. Proper structure of the bundle id (com.*.*) was used to best represent real life use even thought I could have used a one or two tiered bundle id for testing (* or *.*)

With Xcode 9+ it is not possible (at least I have not found a way) to generate an unsigned/no team IPA file, the resulting generated file for iOS is a .app for the simulator.