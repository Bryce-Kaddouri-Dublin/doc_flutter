---

marp: true
theme: gaia
paginate: true
backgroundColor: #fff
Date: 2023-1-25
MetaDescription: Install flutter on Windows, Mac OS and Linux

---
# Process to install flutter on Windows, Linux and mac OS
![bg 90%](https://www.mycloudpa.com/assets/img/logo.png)

---

# What is Flutter ? 

Flutter is a mobile app SDK for building high-performance, high-fidelity, apps for iOS and Android, from a single codebase. Flutter works with existing code, is used by developers and organizations around the world, and is free and open source.

Flutter is Google’s UI toolkit for building beautiful, natively compiled applications for mobile, web, and desktop like Linux, Mac OS, and Windows.

---

# Why Flutter ? 

Flutter allows you to build beautiful native apps on iOS and Android from a single codebase. It’s fast, expressive, flexible, and reactive. Flutter also includes a rich set of fully-customizable widgets, along with APIs for 2D, animation, gestures, effects, and more.

So with Flutter you can build a native app for both iOS and Android with a single codebase. This is a huge time saver  and money saver. Flutter allows you to focus on building your app instead of maintaining two separate codebases.

---

# 1 - Installation of Flutter
### A - Windows Installation

**1.** Requirements

In order to install Flutter on Windows, you have to install git 2.x and , if you already have it, you can skip this step. Else to install Git, yo can just download it with this link below: [Download Git](https://objects.githubusercontent.com/github-production-release-asset-2e65be/23216272/9f52f8e4-769e-4307-88b1-eea7ab1f05ca?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAIWNJYAX4CSVEH53A%2F20230123%2Fus-east-1%2Fs3%2Faws4_request&X-Amz-Date=20230123T154209Z&X-Amz-Expires=300&X-Amz-Signature=34ede7527cba1e982b9cc497d491b38b63f29f0da54f0dcd7cc3b0db692abd23&X-Amz-SignedHeaders=host&actor_id=106662991&key_id=0&repo_id=23216272&response-content-disposition=attachment%3B%20filename%3DGit-2.39.1-64-bit.exe&response-content-type=application%2Foctet-stream
)
After you have downloaded it, execute the setup. When the installation is finished, open a new Windows Command Prompt and try to run the git command that allows you to know the version of git. 

---

**2.** Get the Flutter SDK

Download the Flutter SDK from the [Flutter SDK archive](https://storage.googleapis.com/flutter_infra/releases/stable/windows/flutter_windows_2.5.3-stable.zip) and unzip it to the directory where you want to install Flutter (for example, `C:\src\flutter`).
Be sure to put the Flutter directory in a standard path (for example, in `C:\src`), not in a directory like `C:\Users\<username>\Downloads` that requires elevated privileges to access.

After that you have to add the Flutter tool to your path. Open the Windows Control Panel, type `path` in the search box, and select **Edit the system environment variables**. The **System Properties** window appears. Click **Environment Variables**. In the section **System**

---
**variables**, find the **Path** variable and select it. Click **Edit**. If the **Path** environment variable doesn't exist, click **New**.

Add the full path to the Flutter tool (`C:\src\flutter\bin`) using the semicolon character (`;`) as a separator from the existing values. Click **OK** to save the change. Close any open terminal windows so that the new environment variables can take effect.

To be sure that the Flutter tool is available in your terminal window, run the following command:

```bash
C:\> flutter --version
```
---
**3.** Confirm that your development environment is set up correctly

To confirm that your development environment is set up correctly, run the following command:

```bash
C:\> flutter doctor
```

```bash
Doctor summary (to see all details, run flutter doctor -v):
[√] Flutter (Channel stable, 2.5.3, on Microsoft Windows [Version 10.0.19043.1288], locale en-US)
[√] Android toolchain - develop for Android devices (Android SDK version 31.0.0)
[√] Chrome - develop for the web
[√] Android Studio (version 2020.3)
[√] VS Code (version 1.63.2)
[√] Connected device (2 available)

• No issues found!
```

---

**4.** resolve some issues found by the doctor command 

**A)** If you get the error message `Android license status unknown` when you run the flutter doctor command, run the following command to accept the Android SDK licenses:

```bash
C:\> flutter doctor --android-licenses
```

**B)** If you get the error message `Unable to locate Android SDK` when you run the flutter doctor command, run the following command to update the location of the Android SDK:

```bash
C:\> flutter config --android-sdk <path_to_android_sdk>
```

---

**5.** configure your IDE (Android Studio or VS Code)

**A)** Android Studio

1. Start Android Studio.
2. Select **Configure > Plugins** from the menu.
3. Select the **Marketplace** tab, search for Flutter, and install the Flutter and Dart plugins.
4. Click **Yes** when you are prompted to install the Dart SDK.
5. Click **Restart** when prompted.

---

**B)** VS Code

1. Start VS Code.
2. Select **View > Command Palette** from the menu.
3. Select **Install Extensions**.
4. Search for Flutter and install the Flutter and Dart plugins.
5. Click **Reload** when prompted.

The Flutter and Dart plugins provide code completion, along with visual and structural editing support, for Flutter development.

---

### B - Mac Os Installation

**1.** Requirements

In order to install Flutter on Mac Os, you have to install git 2.x and , if you already have it, you can skip this step. Else to install Xcode, because it includes the necessary command line tools and Git. You can download it from the Mac App Store.

After Xcode is installed, open a terminal window and run the following command to confirm that Xcode is installed correctly and that the `xcode-select` command line tool is functional:

```bash
$ xcode-select --install
```

---

if you get the following message, you are ready to continue:

```bash
xcode-select: error: command line tools are already installed, use "Software Update" in System Settings to install updates
```
 That means Xcode is installed and the `xcode-select` command line tool is functional.

**2.** Get the Flutter SDK

 If you have an Intel Mac download the zip file of the SDK with this link : [Flutter SDK archive](https://storage.googleapis.com/flutter_infra_release/releases/stable/macos/flutter_macos_3.3.10-stable.zip)   

If you have an Apple Silicon Mac download the zip file of the SDK with this link : [Flutter SDK archive](https://storage.googleapis.com/flutter_infra_release/releases/stable/macos/flutter_macos_arm64_3.3.10-stable.zip)

---

When your download is finish extract the zip file in a folder which don't need elevated privileges and contains no spaces or special characters with this command : 
    
For Intel Mac : 

```bash
$ unzip ~/Downloads/flutter_macos_3.3.10-stable.zip 
```

For Apple Silicon Mac : 

```bash
$ unzip ~/Downloads/flutter_macos_arm64_3.3.10-stable.zip
```


---

After that, update your PATH in order to execute the flutter command. To do this you need to determine what shell you are using run the command  in your terminal window: 

```bash
$ echo $SHELL
```

For bash  shell create or edit the rc file by running this command :

```bash
$ nano $HOME/.bashrc
```

For Z shell create or edit the rc file with this following command :

```bash
$ nano $HOME/.zshrc
```

---

In this file paste this following line in your file : 

```bash
export PATH="$PATH:[PATH_OF_FLUTTER_GIT_DIRECTORY]/bin"
```

Now, change the flutter directory by the location of your flutter SDK. for example, My SDK’s location is “/Users/brycekaddouri/devflutter/flutter”, so I replace “PATH_OF_FLUTTER_GIT_DIRECTORY” by my SDK’s location and save your file.
In a new terminal window run the command to be sure flutter are correctly installed:
    
```bash
$ flutter doctor
```

---

make sure the licence agreement is signed by either opening Xcode by running the commande :

```bash
$ sudo xcodebuild -license
```
You can set up your editor like Visual Studio Code or Android Studio in the same way as on Windows.

---

### C - Linux Installation

**1.** Requirements

First of all your operating system must be 64-bit. To check your operating system type, run the following command in a terminal window:

```bash
$ uname -m
```

On Linux you need to be sure this librairies are installed : 

---

<!-- markdown list with 2 columns: 1st column is the package name, 2nd column is the package description -->
| Package | Description |
| ------- | ----------- |
| bash | GNU Bourne-Again SHell |
| curl | Command line tool for transferring data with URL syntax |
| file | Determine file type |
| git 2.x | Distributed version control system |
| mkdir | Make directories |
| rm | Remove files or directories |
| unzip | De-archiver for .zip files |
| which | Locate a command |

---

| Package | Description |
| ------- | ----------- |
| xz-utils | XZ-format compression utilities |
| zip | Archiver for .zip files |
| libglu1-mesa | Mesa OpenGL utility library (GLU) (on Ubuntu or Debian) |

make sure you have installed the following shared libraries :
- libgtk-3-dev (on Ubuntu or Debian)
- mesa-libGLU (on Fedora, CentOS, or RHEL)

---

**2.** Get the Flutter SDK

To install Flutter manually on Linux, you need to download the SDK archive by clicking on this link : [Flutter SDK archive](https://storage.googleapis.com/flutter_infra_release/releases/stable/linux/flutter_linux_3.3.10-stable.tar.xz)

When your download is finish extract the zip file in a folder which don't need elevated privileges and contains no spaces or special characters with this command : 

```bash
$ tar xf ~/Downloads/flutter_linux_3.3.10-stable.tar.xz 
```

Now you need to update your PATH in order to execute t he flutter command. To do this you can use the same method as on Mac Os.

---
**3.** Confirm that your development environment is set up correctly

To confirm that your development environment is set up correctly, run the following command in a terminal window:

```bash
$ flutter doctor
```

```bash
Doctor summary (to see all details, run flutter doctor -v):
[✓] Flutter (Channel stable, 3.3.10, on Linux, locale en_US.UTF-8)
[✓] Android toolchain - develop for Android devices (Android SDK version 30.0.3)
[✓] Chrome - develop for the web
[✓] Android Studio (version 4.1)
[✓] VS Code (version 1.55.2)
[✓] Connected device (2 available)

• No issues found!
```

---

### D - Chrome OS installation

To install flutter on Chrome OS, you need to install the Linux terminal app from the Chrome Web Store. After that make sure you have the same packages as on Linux (refer to the Linux installation ([here](#c---linux-installation)) for more details). 

The only change is that you need to download the SDK archive by clicking on this link : [Flutter SDK archive](https://storage.googleapis.com/flutter_infra_release/releases/stable/linux/flutter_linux_3.7.0-stable.tar.xz)

To extract the archive, run the following command in a terminal window:

```bash
$ tar xf ~/Downloads/flutter_linux_3.7.0-stable.tar.xz 
```

---

# 2 - Setup mobile devices for development

### A - Android devices

To set up your Android device for development, you need to enable developer options and USB debugging and USB debugging (Security settings) on your device.

To Activate developer options and USB debugging, on your device, go to Build number option :

---


 | Device | Setting |
| ------- | ----------- |
| Google Pixel | Settings > About phone > Build number |
| Samsung Galaxy S8 and later | Settings > About phone > Software information > Build number |
| LG G6 and later | Settings > About phone > Software information > Build number | 
| HTC U11 and later | Settings > About > Software information > More > Build number or Settings > System > About phone > More > Build number |

---

When you have find the Build number option, tap it seven times to enable developer options. Then go back to the Settings menu and you will see the Developer options entry. Find the USB debugging option and enable it. 
After that make sure your devices is connected to your computer with a USB cable and run the following command in a terminal window:

```bash
$ flutter devices
```

```bash
2 connected devices:

SM G973F (mobile) • R58M30X1Z7V • android-arm64 • Android 11 (API 30)
Chrome (web)      • chrome      • web-javascript • Google Chrome 90.0.4430.212
```

---

<!-- crop gif in markdown -->

![bg 90% ](gif/debugusb.gif)


---

### B - iOS devices

To launch Flutter apps on an iOS device, you need a **Mac** with **Xcode** installed. To install Xcode, open the Mac App Store and search for Xcode. Then click Get to download and install Xcode.

After that, you need to **enable developer mode** on your device. To do this, go to **Settings** > **General** > **Device Management** and tap your developer team. Then tap Trust to confirm.


#   d o c _ f l u t t e r  
 