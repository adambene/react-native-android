## adambene/react-native-android
Docker image for building ReactNative APKs. Latest Java + Node.js + Android SDK.

## GitHub
[github.com/adambene/react-native-android](https://github.com/adambene/react-native-android)

## Example

### package.json
```json
  "scripts": {
    "build-with-docker-debug": "docker run -t -i -v $(pwd):/workspace -v ~/.gradle/:/root/.gradle/ -w /workspace adambene/react-native-android /bin/sh -c \"cd android && ./gradlew --stacktrace assembleRelease\"",
    "build-with-docker-release": "docker run -t -i -v $(pwd):/workspace -v ~/.gradle/:/root/.gradle/ -w /workspace adambene/react-native-android /bin/sh -c \"cd android && ./gradlew --stacktrace assembleRelease\""
  },
```

### Command Line
```bash
npm run build-with-docker-debug
npm run build-with-docker-release
```

### Volumes
Projects directory as workspace and host's .gradle directory.

### APK
APK is built into the usual build directory.

### Customizations

You can override the following defaults either in your Dockerfile or command line using `-e`.

```bash
ENV ANDROID_COMPONENTS platform-tools,build-tools-23.0.1,build-tools-23.0.3,android-23
ENV GOOGLE_COMPONENTS extra-android-m2repository,extra-google-m2repository,extra-google-google_play_services,extra-google-gcm
```
