## adambene/react-native-android
Docker image for building ReactNative APKs. Latest Java + Node.js + Android SDK.

## GitHub
[github.com/adambene/react-native-android](https://github.com/adambene/react-native-android)

## DockerHub
[hub.docker.com/r/adambene/react-native-android](https://hub.docker.com/r/adambene/react-native-android/)

## Example

### Command Line
Build a React Native project for Android from the command line.

```bash
cd my-project/

docker run -t -i \
  -v $(pwd):/workspace \
  -v ~/.gradle/:/home/user/.gradle/ \
  -w /workspace \
  -e LOCAL_USER_ID=`id -u $USER` \
  adambene/react-native-android \
  /bin/sh -c "cd android && ./gradlew --stacktrace assembleRelease"
```

### package.json & npm
Build a React Native project for Android with `npm`.

```json
  "scripts": {
    "build-with-docker-debug": "docker run -t -i -v $(pwd):/workspace -v ~/.gradle/:/home/user/.gradle/ -w /workspace -e LOCAL_USER_ID=`id -u $USER` adambene/react-native-android /bin/sh -c \"cd android && ./gradlew --stacktrace assembleDebug\"",
    "build-with-docker-release": "docker run -t -i -v $(pwd):/workspace -v ~/.gradle/:/home/user/.gradle/ -w /workspace -e LOCAL_USER_ID=`id -u $USER` adambene/react-native-android /bin/sh -c \"cd android && ./gradlew --stacktrace assembleRelease\""
  },
```

```bash
npm run build-with-docker-debug
npm run build-with-docker-release
```

## More
The container runs the command with username `user` and user id `LOCAL_USER_ID`. This is important to avoid permission problems. The built files are owned by `user` not the root.

### Volumes
Projects directory as workspace and host's `~/.gradle/` directory is needed.

### APK
Debug and release APK are built into the usual build directory `android/app/build/outputs/apk/`.

### Customizations
You can override the following defaults either in your Dockerfile or command line using `-e`.

```bash
ENV ANDROID_COMPONENTS platform-tools,build-tools-23.0.1,build-tools-23.0.3,android-23
ENV GOOGLE_COMPONENTS extra-android-m2repository,extra-google-m2repository,extra-google-google_play_services,extra-google-gcm
```
