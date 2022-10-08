# Misc Notes
A list of commands and notes for quick refernece for development tasks.


- To build the AAB android bundle locally, from the android folder run
	- `./gradlew bundleRelease`
	- The bundle will be output to /android/app/build/outputs/bundle/app-release.aab

- To test the Github Workflow locally use
	- https://github.com/nektos/act
	- The default small/medium/large images are not 1:1 to Github, but you can use the act-environments-* to get closer parity.

- Note that with Xcode 9+ it will not allow generation of an unsigned ipa, only of a .app or an app xarchive. It can be signed with a free personal certificate, but an Apple Account is needed for this. For our purposes we generate unsigned .app for the simulator.