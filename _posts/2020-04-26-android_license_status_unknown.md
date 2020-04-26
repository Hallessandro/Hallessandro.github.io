---
layout: post
title: "#18 - How to solve the problem of Android License in Flutter"
author: "Hallessandro D´villa"
categories: programming, flutter, android
tags: [programming, flutter, android]
image: coverPosts/flutter-logo-sharing.png
header-img: "flutter-logo-sharing.png"
---

Hello folks, in this post I will show how I deal with the problem android license status unknown presented by the Flutter when the flutter doctor runs. 

First things first, this is the problem: 

```bash
λ flutter doctor
Doctor summary (to see all details, run flutter doctor -v):
[√] Flutter (Channel stable, v1.12.13+hotfix.9, on Microsoft Windows [versÃ£o 10.0.18363.778], locale pt-BR)
[!] Android toolchain - develop for Android devices (Android SDK version 29.0.3)
    X Android license status unknown.
      Try re-installing or updating your Android SDK Manager.
      See https://developer.android.com/studio/#downloads or visit https://flutter.dev/setup/#android-setup for detailed instructions.
[!] Android Studio (version 3.6)
    X Flutter plugin not installed; this adds Flutter specific functionality.
    X Dart plugin not installed; this adds Dart specific functionality.
[√] VS Code (version 1.44.2)
[√] Connected device (1 available)

! Doctor found issues in 2 categories.
```

In theory to solve that, we just need to run the command **flutter doctor --android-licenses**, but when do this, another error message will be presented: 

```bash
Android sdkmanager tool not found (C:\Users\hdjes\AppData\Local\Android\sdk\tools\bin\sdkmanager).
Try re-installing or updating your Android SDK,
visit https://flutter.dev/setup/#android-setup for detailed instructions.
```

This problem occurs because the the android sdk tool has been renamed to android sdk command-line tools, which is located in: 
```
(C:\Users\hdjes\AppData/Local/Android/Sdk/cmdline-tools/latest/bin
```

So the Flutter is trying to finding something that don't exists anymore in that directory, to solve this we need to install the skd tool, for this, open Android Studio, go to Configure -> SDK Manager -> SDK Tools -> Uncheck Hide Obsolete Packages, and you'll see Android SDK Tools (Obsolete) 26.1.1, now just install this package. 

After that we can run **flutter doctor --android-licenses** again, but this time no problem should be found and several licenses will be shown to you, and you basically accept them if you agree.

After this we can run **flutter doctor** again but this time without any error. :D