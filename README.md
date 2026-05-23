# jmeAndroidNatives

Android native libraries used by jMonkeyEngine.

This project is extracted from the old `jme3-android-native` module so the Android natives can have their own build and release cycle. The published Maven artifact intentionally keeps the existing artifact id:

```groovy
implementation "org.jmonkeyengine:jme3-android-native:<version>"
```

`./gradlew assemble` builds the native libraries from source and packages them into an Android AAR. An Android SDK, Android NDK, and CMake must be available.

Native build targets are configured in `gradle.properties`:

```properties
androidAbis = arm64-v8a,x86_64
androidPlatform = android-21
```

Non-release builds use `baseVersion` from `gradle.properties` with `-SNAPSHOT` appended. GitHub release jobs pass `-PreleaseVersion` from the release tag.

The JNI headers in `src/native/headers` are the ABI contract with `jme3-android`.
