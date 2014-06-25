
ocr-test-app
==================
This is a tiny Android project designed to facilite unit testing of tess-two-based OCR.

Getting started

In order to build and develop this project, there are a few pre-requisites:

1) The Android SDK provides the API libraries and developer tools necessary to build, test and debug apps for Android.  Available from http://developer.android.com/sdk/index.html

2) The Android NDK is a toolset that allows you to implement parts of your app using native-code languages such as C and C++.  This is needed to build and test Tesseract.  Available for download from https://developer.android.com/tools/sdk/ndk/index.html

3) The tess-two Tesseract APIs and build files for Android.  Since this needs to be built natively, it is not included in the repository.

4) An appropriate eclipse workspace to work in, created from the Android SDK.

5) A Java 7 compatible JDK (not JRE) set as your JAVA_HOME

Since tess-two binds the native Tesseract code with and Android API, tess-two must be built for your platform.  The procedure below will build tess-two into a library project which your main project can then have a dependency upon.  You can follow the instructions at:

https://github.com/rmtheis/tess-two

But in a nutshell you can change to the root of your workspace and run:

git clone git://github.com/rmtheis/tess-two tess
cd tess
cd tess-two
ANDROID_NDK_HOME/ndk-build
ANDROID_SDK_HOME/sdk/tools/android update project --path . --target android-19
ANDROID_SDK_HOME/eclipse/plugins/org.apache.ant_1.8.4.v201303080030/bin/ant release

You can then import the tess/tess-two project as an existing project in eclipse.  If the relative project workspace references aren't resolved, you can update them to get the project to build.

You can then check out the appropriate projects:

ocr-test-app: A simple Android app that installs the basic OCR requirements 
ocr-test-app-tests: An testing project to run simple OCR scenarios
one-time-pad-external-libraries: A helper project containing third party jars
one-time-pad-library: A Java one-time pad encryption implementation
one-time-pad-library-tests: The tests for the Java one-time pad encryption implementation

to do this you might, for instance:

git clone git@github.com:Sector67/one-time-pad-library.git
git clone git@github.com:Sector67/one-time-pad-library-tests.git
git clone git@github.com:Sector67/ocr-test-app.git
git clone git@github.com:Sector67/ocr-test-app-tests.git
git clone git@github.com:Sector67/one-time-pad-external-libraries.git

You will need to import each of those projects as existing projects into a workspace and ensure any build dependencies in Properties->Android are properly satisfied.  Once that is done, you should be able to run basic OCR scenarios using the Android emulator by running the "ocr-test-app-tests" project as Android Unit Tests using the Android JUnit Test Launcher.  You can also run the one-time-pad-library-tests using the Eclipse JUnit Launcher for a simpler test.

