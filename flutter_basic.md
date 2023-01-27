---

marp: true
theme: gaia
paginate: true
backgroundColor: #fff
Date: 2023-1-25
MetaDescription: Basics of flutter 3.0

---

# Basics of Flutter 3.0  
![bg 90%](https://www.mycloudpa.com/assets/img/logo.png)

---

# 1 - Create a new Flutter project

To create a new Flutter project, you can use the command line or an IDE like Android Studio or Visual Studio Code.

### A - Create a new Flutter project with the command line

To create a new Flutter project with the command line, run the following command in a terminal window:

```bash
$ flutter create <name_of_your_project>
```

---

### B - Create a new Flutter project with Android Studio

To create a new Flutter project with Android Studio, follow these steps:

1. Open Android Studio and click on **Start a new Flutter project**.

2. Select **Flutter Application** and click on **Next**.

3. Enter the name of your project and click on **Next**.

4. Select the location of your project and click on **Finish**.

---

### C - Create a new Flutter project with Visual Studio Code

To create a new Flutter project with Visual Studio Code, follow these steps:

1. Open Visual Studio Code and click on **Create a new Flutter project**.

2. Select **Flutter Application** and click on **Next**.

3. Enter the name of your project and click on **Next**.

4. Select the location of your project and click on **Finish**.

---

# 2 - Run your Flutter project

To run your Flutter project, you can use the command line or an IDE like Android Studio or Visual Studio Code.

### A - Run your Flutter project with the command line

To run your Flutter project, identify the device you want to run your project by running the following command in a terminal window:

```bash
$ flutter devices
```

---

```bash
5 connected devices:

Chrome (web) • chrome • web-javascript • Google Chrome 90.0.4430.212
Web Server (web) • web-server • web-javascript • Flutter Tools
iPhone 12 Pro Max (mobile) • 00008020-000C2E1E0A0A802E • ios • com.apple.CoreSimulator.
Samsung Galaxy S21 (mobile) • 4d005d0c0d0d0d0d • android-arm64 • Android 11 (API 30)
macOS (desktop) • macos • darwin-x64 • Mac OS X 10.15.7 19H524 darwin-x64
```

if you don't have any device connected, you can use the web server to run your project. To do this, run the following command in a terminal window:

```bash
$ flutter run -d web-server --web-port=8080 --web-hostname=localhost
```

On the next page it's exemple to run your project on ios simulator :

---

![bg 90%](gif/run_ios.gif)

---

Sometimes you need to run your project on a specific device. To do this, run the following command in a terminal window:

```bash
$ flutter run -d <device_id>
```

And to finish, you can run your project on all devices connected by running the following command in a terminal window:

```bash
$ flutter run -d all
```

Don't forget the command to be sure your device is available, to see the list of available devices is allow by flutter :

```bash
$ flutter config -h 
```
---

# 3 - Debug your Flutter project 

To debug your Flutter project, you can use the command line or an IDE like Android Studio or Visual Studio Code.

### A - Debug your Flutter project with the command line

To debug your Flutter project, run the following command in a terminal window:

```bash
$ flutter run -d <device_id> --verbose
```

---

### B - Debug your Flutter project with Android Studio

To debug your Flutter project with Android Studio, follow these steps:

1. Open Android Studio and click on **Open an existing Android Studio project**.

2. Select your project and click on **OK**.

3. Click on **Run** and select **Run 'main.dart'**.

4. Select the device you want to run your project and click on **OK**.

---

### C - Debug your Flutter project with Visual Studio Code

To debug your Flutter project with Visual Studio Code, follow these steps:

1. Open Visual Studio Code and click on **Open folder**.

2. Select your project and click on **Select Folder**.

3. Click on **Run** and select **Start Debugging**.

4. Select the device you want to run your project and click on **OK**.

---
### D - UI and code debug 

One the two next pages, it's exemple to debug your project, for the first page we focus on the UI and for the second page we focus on the code like the value of a variable, the state of a widget or a function.

You can also open the **Widget Inspector** by running the following command in a terminal window:

```bash
$ flutter run -d <device_id> --verbose --dart-define=FLUTTER_INSPECTOR=true
```

or press **v** on your keyboard when your project is running.

---
![bg 90%](gif/debug_step_by_step.gif)


---

# 4 - Architecture of a Flutter project 

When you create develop a Flutter project you need to know the architecture of a Flutter project. But you going to write in some files like : 
- **lib/main.dart** : in this file you will write the main function of your project, you can also refactor your code in some files and import them in this file.
- **pubspec.yaml** : in this file you will write the dependencies of your project or fonts, images, etc... , you can update the dependencies by running the following command in a terminal window : 

---

```bash
$ flutter pub get
```
- **android/app/src/main/AndroidManifest.xml** : you will write the configuration and the permissions of your project (access to the camera, access to the microphone, etc...).
<!-- for ios  -->
- **ios/Runner/Info.plist** : you will write the configuration and the permissions of your project (access to the camera, access to the microphone, etc...).
- **lib/** : in this folder you will write the code of your project, you can create some folders to organize your code.

---

This is the details of architecture of a Flutter project on a MAC OS :

```bash
<name_of_your_project>
├── .dart_tool # contains the files generated by the Dart tool
├── android  # contains the Android project
├── build  # contains the files generated by the Flutter tool
├── ios  # contains the iOS project
├── lib  # contains the source code of your project
├── linux  # contains the Linux project
├── macos # contains the macOS project
├── test # contains the test files of your project 
├── web  # contains the web project 
├── windows # contains the Windows project 
├── analysis_options.yaml # contains the options for the Dart analyzer 
├── pubspec.lock # contains the versions of the dependencies of your project 
├── pubspec.yaml # contains the dependencies of your project 
├── README.md # contains the description of your project 
```
---

# 5 - Build your Flutter project

 To build your Flutter project, you can use the command line or an IDE like Android Studio or Visual Studio Code.

 - To build your Flutter project for **Windows**, run the following command in a terminal window:

```bash
$ flutter build windows-desktop
```

- To build your project for **Linux** device :
```bash
$ flutter build linux-desktop
```
--- 

- To build your Flutter project for **Mac OS** device without signing, run the following command in a terminal window:


```bash
$ flutter build macos-desktop
```

- To build your Flutter project for **Android** device, run the following command in a terminal window:

```bash
$ flutter build apk
```


- To build your Flutter project for **web**, run the following command in a terminal window:

```bash
$ flutter build web
```

--- 

- To build your Flutter project for **iOS** device is more complicated, you need to have a Mac OS device and you need to have a developer account, you can follow this [link](https://flutter.dev/docs/deployment/ios) to build your project for iOS device. But you can generate a **.ipa** file to test your project on a real device, run the following command in a terminal window:

```bash
$ flutter build ios --release --no-codesign
```
Now to launch the the **.ipa** file in your device, run the following command in a terminal window:

```bash
$ flutter install
```
---

If you have an error which said you can't launch it because the app is not signed, you need to build the project with Xcode, to do this, follow these steps:

1. In Visual Studio Code, right-click on **ios** and select **Open in Xcode**.

2. In Xcode, click on **Runner** and select **Runner** in the **TARGETS** section.

3. In the **Signing & Capabilities** section, select your team. If you don't have a team, you can create one.

4. Click on the run button to build and run your project. But if you disconnect your device, you can't run your project. So you can build your project by clicking on the **Profile** button.

---

5. Now in your phone, go to **Settings** and select **General**.

6. Select **Device Management** and select your team.

7. Click on **Trust**.

8. Now you can run your project on your device.

In the next page you have a video to show you how to build your Flutter project for iOS device. the first part is to build the project with Xcode and the second part is to run the project on a real device.

If you have any questions, you can go to the [Flutter Community](https://flutter.dev/community) page or you can go on the documentation of Flutter [here](https://flutter.dev/docs).

---

![bg 90%](gif/build_ios.gif)

---

![bg 90%](gif/run_ios_device.gif)




