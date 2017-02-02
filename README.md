## adambene/react-native-android

For building ReactNative APKs. Latest Java + Node.js + Android SDK.

## Example

### package.json
```json
  "scripts": {
    "build-with-docker": "docker run -t -i -v $(pwd):/workspace -v ~/.gradle/:/root/.gradle/ -w /workspace medicall /bin/sh -c \"cd android && ./gradlew --stacktrace assembleRelease\""
  },
```

### Volumes
Projects directory as workspace and host's .gradle directory.

### APK
APK is built into the usual build directory.
