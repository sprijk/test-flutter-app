# Managing Assets, Icons, and Build Processes in Android and Flutter Apps

## Flutter Apps

### Adding and Using Assets like SVG and PNG

- **pubspec.yaml**: Assets in Flutter are specified in the `pubspec.yaml` file under the `flutter/assets` section.
- **Usage**: To use an image named `example.png`, specify it in `pubspec.yaml` and use it in your code with `Image.asset('assets/example.png')`. For SVGs, you will need a package like `flutter_svg`.

### App Logo/Icon

For **Android**:
Open the `AndroidManifest.xml` file located at `android/app/src/main/AndroidManifest.xml`, and look for the <application> tag. Within this tag, you'll see an attribute called `android:icon`. You can set this attribute to reference the icon file you want to use. The icon file should be placed in the `android/app/src/main/res/mipmap-*` directories.

For **iOS**:
Open the `Info.plist` file located at `ios/Runner/Info.plist`. Inside this file, you'll find an entry for `CFBundleIcons` or `CFBundleIconFiles`, and you can specify the icon files there. The icon files should be added to the `ios/Runner/Assets.xcassets` directory.

Make sure to include the appropriate icon sizes for different devices and resolutions as required by each platform. After making changes to these files, you may need to rebuild your app to see the updated icon on your device.

#### Using a library (haven't tested)

- **Location & Tool**: Use the `flutter_launcher_icons` package specified in `pubspec.yaml` and configure it with your icon paths.
- **Usage**: Run `flutter pub get` and then `flutter pub run flutter_launcher_icons:main` to generate app icons.

### Splash Screen Icon

For **Android**:

The launch_background.xml file is located in the `res/drawable` directory under `android/app/src/main` in your Flutter project. This XML file defines the splash screen appearance for Android devices.

For **iOS**:

For iOS, the splash screen is typically defined either in `LaunchScreen.storyboard` or `LaunchScreen.xib`. These files are located in the `ios/Runner` directory of your Flutter project. They are used to define the launch screen layout for iOS devices.

- **Libraries**: Use packages like [flutter_native_splash](https://pub.dev/packages/flutter_native_splash) to easily configure and generate a native splash screen for both iOS and Android. Specify configurations in `pubspec.yaml` and follow the instructions on the package's page.

### Signing the Built Version for Google Play Store

1. **Create a Keystore**: As with Android, use Keytool to generate a keystore.
2. **Configure Signing**: Edit or create the `<app>/android/key.properties` file with your keystore details and reference it in `<app>/android/app/build.gradle`.
3. **Build a Release**: Run `flutter build apk` or `flutter build appbundle` with the `--release` flag.

### Building for Testing on a Real Device

1. **Enable Developer Options** on your device: Go to Settings > About phone and tap `Build number` seven times.
2. **Enable USB Debugging** in Developer Options.
3. **Connect Device** to your development machine via USB.
4. **Select Device** in your terminal, run `flutter devices` and see if the phone is in the list. If not, repeat the previous steps.
5. **Execute** in your terminal, run `flutter run`. If you are running an emulator, you'll be asked to select the device you want to run your application on by selecting it with a number. Select the one corresponding to the real device.

### Installing Dependencies

- **pubspec.yaml**: Add your dependencies under the `dependencies` section in `pubspec.yaml` and run `flutter pub get` to install them.

### Signing the Built Version for Google Play Store

1. **Generate a Keystore**: Use the Keytool utility (included with the JDK) to create a keystore and a key.
2. **Configure Gradle**: Specify the keystore and key details in your app's `build.gradle` file inside the `android` block.
3. **Build Signed APK or AAB**: Use your IDE or Gradle to build a signed APK or Android App Bundle (AAB) for release.

