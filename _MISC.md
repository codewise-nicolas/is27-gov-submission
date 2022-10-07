# Misc Notes
A list of commands and notes for quick refernece for development tasks.


- To build the AAB android bundle, from the android folder
	- `./gradlew bundleRelease`
	- It will be output to /android/app/build/outputs/bundle/app-release.aab

- To test the Github Workflow locally use
	- https://github.com/nektos/act
	- The default small/medium/large images are not 1:1 to Github, but you can use the act-environments-* to get closer parity.