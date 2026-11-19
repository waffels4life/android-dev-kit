# Android Dev Kit

![Platform](https://img.shields.io/badge/platform-Windows-blue?logo=windows)
![Android SDK](https://img.shields.io/badge/Android%20SDK-API%2035-3DDC84?logo=android&logoColor=white)
![Java](https://img.shields.io/badge/JDK-21-orange?logo=openjdk&logoColor=white)
![Gradle](https://img.shields.io/badge/Gradle-8.13-02303A?logo=gradle&logoColor=white)
![Status](https://img.shields.io/badge/status-Active-success)

**Android development tools, ready to download.**

A collection of prebuilt Android development tools and dependencies, distributed through GitHub Actions.

---

## Why this project exists

Setting up an Android development environment shouldn't be a struggle.

Downloading the Android SDK, platform tools, build tools, Gradle distributions, and project dependencies can be time-consuming — especially when access to official download servers is unreliable or restricted.

This project started as a personal solution to that problem.

Instead of repeatedly downloading everything on a local machine, we use GitHub Actions runners to prepare the required tools and publish them as downloadable artifacts.

The result is a convenient distribution point for Android development resources.

## What's available?

The repository currently provides two main packages.

### 1. Android SDK — Windows

A prebuilt Android SDK environment containing:

| Component | Version / Details |
|---|---|
| Android SDK Command-line Tools | Included |
| Android Platform Tools | Included |
| Android SDK Platform | Android 35 |
| Android Build Tools | 35.0.0 |
| Other SDK components | Included where required by the generated SDK |

**Artifact:** `android-sdk-windows`

**Approximate size:** 11.4 GB

### 2. Gradle Dependency Cache — Windows

A preloaded Gradle environment designed to reduce repeated downloads when building Android projects.

| Component | Version |
|---|---|
| JDK used during preparation | Temurin 21 |
| Gradle | 8.13 |
| Android Gradle Plugin | 8.13.2 |

**Artifact:** `harmony-gradle-cache-windows`

This package is intended to help developers avoid downloading the same Gradle distributions and project dependencies repeatedly.

---

## Downloading

All packages are published through GitHub Actions.

**[Open GitHub Actions](https://github.com/waffels4life/android-dev-kit/actions)**

Follow these steps:

1. Open the Actions tab.
2. Select the workflow responsible for the package you need.
3. Open its latest successful workflow run.
4. Scroll down to the Artifacts section.
5. Download the corresponding ZIP archive.
6. Extract the archive to your preferred location.

You don't need to clone the repository or run the workflows yourself to download an existing artifact.

**Important:** GitHub Actions artifacts are temporary. Currently, generated artifacts have a retention period of 7 days. Download them before they expire.

---

## Getting Started

### Step 1 — Install a JDK

The Android SDK package does not replace a Java Development Kit.

Install a compatible JDK separately and configure `JAVA_HOME`.

For the Gradle environment provided here, JDK 21 is the preparation baseline.

### Step 2 — Extract the Android SDK

For example:

```text
D:\Android\SDK\android-sdk-windows
```

Configure the following Windows environment variables:

```text
ANDROID_HOME=D:\Android\SDK\android-sdk-windows
ANDROID_SDK_ROOT=D:\Android\SDK\android-sdk-windows
```

Add the following directories to your `PATH`:

```text
%ANDROID_HOME%\platform-tools
%ANDROID_HOME%\cmdline-tools\latest\bin
```

### Step 3 — Verify the installation

Open PowerShell and run:

```powershell
adb version

sdkmanager --list
```

If both commands execute successfully, the corresponding tools are accessible.

### Step 4 — Configure Gradle

If you downloaded the Gradle cache package, extract its contents into your chosen Gradle User Home, preserving the archive's directory structure.

For example, you can use:

```text
D:\Android\gradle
```

Configure `GRADLE_USER_HOME` to point to that location.

Your Gradle project must also use compatible Gradle and Android Gradle Plugin versions to benefit from the preloaded dependencies.

---

## Limitations

This project is not an official Android distribution or a complete mirror of Google's repositories.

There are some important limitations:

- **Windows-focused:** Current packages are prepared for Windows environments. Linux and macOS distributions are not currently provided.
- **Limited SDK versions:** The currently prepared Android SDK targets API 35 and Build Tools 35.0.0.
- **No Android Studio:** This project provides development tools, not the Android Studio IDE.
- **No guaranteed offline builds:** Some dependencies may not be included in the prepared cache. Projects requiring additional packages may still need internet access.
- **Gradle compatibility:** Cached dependencies are version-specific. Different Gradle or Android Gradle Plugin versions may require additional downloads.
- **Temporary downloads:** GitHub Actions artifacts expire after their configured retention period.
- **No complete repository mirror:** Google's SDK repositories, Maven Central, and other dependency repositories are not mirrored in their entirety.

The goal is to reduce dependency on repeated downloads, not to guarantee a completely offline Android development environment.

---

## Getting Help

If you encounter problems:

1. Check the package versions and compatibility requirements.
2. Make sure environment variables are configured correctly.
3. Check whether the artifact has expired.
4. Open an issue with relevant error messages and environment details.

---

## Disclaimer

Android, Android SDK, Gradle, and related tools are trademarks or products of their respective owners.

This is an independent community project. It is not affiliated with, endorsed by, or officially supported by Google.

All third-party software remains subject to its respective licenses and terms of use.

---

**Built out of necessity. Shared for convenience.**
