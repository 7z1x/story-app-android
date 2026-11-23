<h1 align="center">Aplikasi-Story</h1>

<p align="center">
  Android app to browse, post, and upload stories with location -- built with Kotlin, Retrofit, MVVM, and DataStore.<br>
  <strong><a href="#usage">Explore Aplikasi-Story usage &#187;</a></strong>
  <br><br>
  <a href="https://github.com/7z1x/Aplikasi-Story/issues/new?labels=bug">Report bug</a>
  &#183;
  <a href="https://github.com/7z1x/Aplikasi-Story/issues/new?labels=enhancement">Request feature</a>
  &#183;
  <a href="https://github.com/7z1x/Aplikasi-Story">Repository</a>
</p>

<p align="center">
  <a href="https://kotlinlang.org/"><img src="https://img.shields.io/badge/Kotlin-1.9-purple?logo=kotlin&logoColor=white" alt="Kotlin"></a>
  <a href="https://developer.android.com/"><img src="https://img.shields.io/badge/Android-SDK%2034-green?logo=android&logoColor=white" alt="Android"></a>
  <a href="https://square.github.io/retrofit/"><img src="https://img.shields.io/badge/API-Retrofit-blue" alt="Retrofit"></a>
  <a href="https://developer.android.com/topic/libraries/architecture/viewmodel"><img src="https://img.shields.io/badge/Arch-MVVM-orange" alt="MVVM"></a>
  <a href="https://airbnb.io/lottie/"><img src="https://img.shields.io/badge/Animation-Lottie-00BFFF" alt="Lottie"></a>
</p>

---

## Overview

**Aplikasi-Story** is an Android application for browsing, posting, and uploading user
stories (with optional location) to the Dicoding Story API. It is built with **Kotlin**,
follows the **MVVM** architecture using **ViewModel + LiveData**, persists sessions with
**DataStore Preferences**, and includes a polished onboarding flow with **Lottie**
animations and multi-language support (Indonesian, Javanese, English).

### How it works

1. **Welcome** -- `WelcomeActivity` shows an animated onboarding screen (Lottie).
2. **Auth** -- `LoginActivity` / `SignupActivity` authenticate against the Story API;
   the session token is stored in **DataStore Preferences** via `UserPreference`.
3. **Main feed** -- `MainActivity` lists stories in a RecyclerView (`ListAdapter`), fed by
   `MainViewModel` + `UserRepository`.
4. **Upload** -- `UploadActivity` lets the user pick/capture a photo, attach location, and
   post it; `ExifInterface` handles image rotation.
5. **Detail** -- `DetailActivity` shows the full story (image, description, location).
6. **Settings** -- `SettingActivity` handles locale switching and session logout.

---

## Requirements

- **Android Studio** (Giraffe or newer)
- **JDK 17**
- **Android SDK 34** (minSdk 21, targetSdk 33)

| Package | Purpose |
|---|---|
| [Retrofit 2](https://square.github.io/retrofit/) + Gson | Story API networking |
| [Glide](https://github.com/bumptech/glide) | Image loading |
| [OkHttp Logging Interceptor](https://square.github.io/okhttp/) | Network debugging |
| [DataStore Preferences](https://developer.android.com/topic/libraries/architecture/datastore) | Session storage |
| [Lifecycle ViewModel + LiveData](https://developer.android.com/jetpack/androidx/releases/lifecycle) | MVVM state |
| [ExifInterface](https://developer.android.com/reference/androidx/exifinterface/ExifInterface) | Image rotation handling |
| [Lottie](https://airbnb.io/lottie/) | Onboarding animations |

---

## Installing

```bash
git clone https://github.com/7z1x/Aplikasi-Story.git
cd Aplikasi-Story
```

Open the project in **Android Studio**, let Gradle sync, then run on an emulator or device:

```bash
./gradlew assembleDebug
```

The app targets the Dicoding Story API at `https://story-api.dicoding.dev/v1/`
(configured in `app/build.gradle.kts` as `BASE_URL`).

---

## Usage

1. **Welcome** -- launch the app and watch the Lottie onboarding animation.
2. **Register / Login** -- create an account or sign in; your session is persisted across launches.
3. **Browse stories** -- the main feed lists all stories in a RecyclerView.
4. **Upload a story** -- tap the add button, capture or pick a photo, optionally attach
   location, and post.
5. **View detail** -- tap any story to see the full image and description.
6. **Settings** -- switch the app language (Indonesian / Javanese / English) or log out.

---

## Acknowledgements

Built as a Dicoding *Android Intermediate* submission using
[Retrofit](https://square.github.io/retrofit/),
[Android Jetpack](https://developer.android.com/jetpack),
[DataStore](https://developer.android.com/topic/libraries/architecture/datastore), and
[Lottie](https://airbnb.io/lottie/). Story data comes from the Dicoding Story API.
