<h1 align="center">Aplikasi-Story</h1>

<p align="center">
  Android app to browse, post, and upload stories with location â€” built with Kotlin, Retrofit, MVVM, and DataStore.<br>
  <strong><a href="#usage">Explore Aplikasi-Story usage Â»</a></strong>
  <br><br>
  <a href="https://github.com/7z1x/Aplikasi-Story/issues/new?labels=bug">Report bug</a>
  Â·
  <a href="https://github.com/7z1x/Aplikasi-Story/issues/new?labels=enhancement">Request feature</a>
  Â·
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

1. **Welcome** â€” `WelcomeActivity` shows an animated onboarding screen (Lottie).
2. **Auth** â€” `LoginActivity` / `SignupActivity` authenticate against the Story API;
   the session token is stored in **DataStore Preferences** via `UserPreference`.
3. **Main feed** â€” `MainActivity` lists stories in a RecyclerView (`ListAdapter`), fed by
   `MainViewModel` + `UserRepository`.
4. **Upload** â€” `UploadActivity` lets the user pick/capture a photo, attach location, and
   post it; `ExifInterface` handles image rotation.
5. **Detail** â€” `DetailActivity` shows the full story (image, description, location).
6. **Settings** â€” `SettingActivity` handles locale switching and session logout.

---

## Files

- **[README.md](README.md)** â€” the file you are currently reading.
- **[app/build.gradle.kts](app/build.gradle.kts)** â€” module config, dependencies, and `BASE_URL` build config.
- **app/src/main/java/com/dicoding/picodiploma/loginwithanimation/**
  - `data/` â€” `Result.kt`, `UserModel.kt`, `UserRepository.kt`.
  - `data/pref/` â€” `LocalDataStore.kt`, `UserPreference.kt` (DataStore session).
  - `data/response/` â€” `LoginResponse`, `RegisterResponse`, `StoryResponse`, `UploadStoryResponse`.
  - `data/retrofit/` â€” `ApiConfig.kt`, `ApiService.kt`.
  - `di/Injection.kt` â€” manual DI for repository.
  - `adapter/ListAdapter.kt` â€” RecyclerView adapter for stories.
  - `view/welcome/WelcomeActivity.kt` â€” Lottie onboarding.
  - `view/login/` â€” `LoginActivity.kt`, `LoginViewModel.kt`.
  - `view/signup/` â€” `SignupActivity.kt`, `SignUpViewModel.kt`.
  - `view/main/` â€” `MainActivity.kt`, `MainViewModel.kt`.
  - `view/upload/` â€” `UploadActivity.kt`, `UploadViewModel.kt`.
  - `view/detail/DetailActivity.kt` â€” story detail screen.
  - `view/setting/` â€” `SettingActivity.kt`, `SettingViewModel.kt`.
  - `view/mybtnEdt/` â€” custom `MyButton`, `MyEditEmail`, `MyEditPass` views.
  - `view/utils/` â€” `Utils.kt`, `ViewModelFactory.kt`.
- **app/src/main/res/layout/** â€” XML layouts (`activity_main`, `activity_login`,
  `activity_signup`, `activity_upload`, `activity_detail`, `activity_setting`,
  `activity_welcome`, `item_layout`).
- **app/src/main/res/values/** â€” `strings.xml`, `colors.xml`, `themes.xml`, `style.xml`.
- **app/src/main/res/values-in/ & values-jv/** â€” Indonesian & Javanese localization.
- **app/src/main/assets/language.json** & **animasi/animation_language.json** â€” Lottie assets.
- **gambar/** â€” onboarding background images.

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

1. **Welcome** â€” launch the app and watch the Lottie onboarding animation.
2. **Register / Login** â€” create an account or sign in; your session is persisted across launches.
3. **Browse stories** â€” the main feed lists all stories in a RecyclerView.
4. **Upload a story** â€” tap the add button, capture or pick a photo, optionally attach
   location, and post.
5. **View detail** â€” tap any story to see the full image and description.
6. **Settings** â€” switch the app language (Indonesian / Javanese / English) or log out.

---

## Acknowledgements

Built as a Dicoding *Android Intermediate* submission using
[Retrofit](https://square.github.io/retrofit/),
[Android Jetpack](https://developer.android.com/jetpack),
[DataStore](https://developer.android.com/topic/libraries/architecture/datastore), and
[Lottie](https://airbnb.io/lottie/). Story data comes from the Dicoding Story API.
