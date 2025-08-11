# isar_flutter_libs (Modified Version)

This is a **modified version** of the [`isar_flutter_libs`](https://isar.dev) Flutter plugin.  
It includes fixes for two common issues that occurred when building Flutter apps with the original package.

---

## 🔧 What Was Fixed

### 1. Namespace Not Declared
Some Android Gradle builds failed because the `namespace` property was missing in the Android `build.gradle` file.  
**Fix:** Added a valid `namespace` declaration to the plugin.

---

### 2. `error: resource android:attr/lStar not found`
When building on older Android SDK versions, the following error occurred:

**Cause:** The `lStar` attribute is only available in newer Android versions.  
**Fix:** Removed/replaced the attribute with a backward-compatible alternative.

---

## 🚀 How to Use

In your `pubspec.yaml`, replace the existing `isar_flutter_libs` dependency with this:

```yaml
isar_flutter_libs:
  git:
    url: https://github.com/HijbullahMahmud/isar_flutter_libs.git
    ref: master

# 1. Delete lock files
rm pubspec.lock
rm ios/Podfile.lock

# 2. Get dependencies
flutter pub get

# 3. Rebuild iOS Pods
cd ios
pod install
cd ..

# 4. Clean and build
flutter clean
flutter build apk   # For Android
flutter build ios   # For iOS
