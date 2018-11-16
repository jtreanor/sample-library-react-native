# sample-library-react-native

This is a simple React Native project that demonstrates an issue with building Android libraries on React Native `0.57.5`.

## Issue

Any Android React Native project which uses `apply plugin: "com.android.library"` currently fails to build. The problem is that [a recent change](https://github.com/facebook/react-native/pull/20526) to `react.gradle` now uses `android.applicationVariants` when configuring the project. This is not present for library projects, so it fails.

## Usage

1. Clone this repository
2. Run `yarn install`
3. Run `cd android && ./gradlew build`

You will see this error similar to this:

```
FAILURE: Build failed with an exception.

* Where:
Script '/Users/james/src/SampleLibrary/node_modules/react-native/react.gradle' line: 15

* What went wrong:
A problem occurred configuring project ':app'.
> Could not get unknown property 'applicationVariants' for object of type com.android.build.gradle.LibraryExtension.

* Try:
Run with --stacktrace option to get the stack trace. Run with --info or --debug option to get more log output. Run with --scan to get full insights.

* Get more help at https://help.gradle.org

BUILD FAILED in 0s
```
