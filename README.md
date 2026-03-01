# 🚀 Android Dependencies Guide (Interview & Production Ready)

> **Quick Setup Reference** - Copy → Paste → Build 🚀  
> No Version Catalog • Hardcoded versions • Interview optimized

---

## 📋 Table of Contents

1. [Project Setup](#project-setup)
2. [Navigation](#navigation)
3. [Dependency Injection](#dependency-injection)
4. [Database](#database)
5. [Networking](#networking)
6. [Image Loading](#image-loading)
7. [Async & Background](#async--background)
8. [PDF & Documents](#pdf--documents)
9. [Camera & Media](#camera--media)
10. [Storage & Preferences](#storage--preferences)
11. [Security](#security)
12. [Testing](#testing)

---

## 📦 Project Setup

### Project Level `build.gradle.kts`

```kotlin
plugins {
    id("com.android.application") version "8.7.3" apply false
    id("com.android.library") version "8.7.3" apply false
    id("org.jetbrains.kotlin.android") version "2.1.0" apply false
    id("org.jetbrains.kotlin.plugin.compose") version "2.1.0" apply false
    id("org.jetbrains.kotlin.plugin.serialization") version "2.3.10" apply false
    id("com.google.devtools.ksp") version "2.3.5" apply false    
    id("com.google.dagger.hilt.android") version "2.54" apply false
    id("com.google.gms.google-services") version "4.4.2" apply false
}
```

### App Level `build.gradle.kts` - Plugins

```kotlin
plugins {
    id("com.android.application")
    id("org.jetbrains.kotlin.android")
    id("org.jetbrains.kotlin.plugin.compose")
    id("org.jetbrains.kotlin.plugin.serialization")
    id("com.google.devtools.ksp")
    id("com.google.dagger.hilt.android") // For Hilt DI
    id("com.google.gms.google-services") // For Firebase
}
```

---

## 🧭 Navigation

### Navigation Compose

```kotlin
// Navigation for Compose
implementation("androidx.navigation:navigation-compose:2.8.5")
```

### Navigation 3 (Latest - Alpha)

```kotlin
// Navigation 3 - Next Generation
implementation("androidx.navigation3:navigation3-runtime:1.0.0")
implementation("androidx.navigation3:navigation3-ui:1.0.0")
```
## Viewmodel 
 ```
//nav2 for
implementation("androidx.lifecycle:lifecycle-viewmodel-compose:2.8.7")
//nav3
implementation("org.jetbrains.androidx.lifecycle:lifecycle-viewmodel-navigation3:2.10.0-alpha07")
```
## Icon exteanted

### In Build
```
implementation("androidx.compose.material:material-icons-extended:1.7.8")
```
### feather Icons
```
    implementation("br.com.devsrsouza.compose.icons:feather:1.1.1")
```
###  tabler Icons
    ```
    implementation("br.com.devsrsouza.compose.icons:tabler-icons:1.1.1")
    ```
---

## 💉 Dependency Injection

### Dagger Hilt (Recommended)

```kotlin
// Hilt - Essential only
implementation("com.google.dagger:hilt-android:2.54")
ksp("com.google.dagger:hilt-android-compiler:2.54")
implementation("androidx.hilt:hilt-navigation-compose:1.2.0")
```

### Koin (Lightweight Alternative)

```kotlin
// Koin - Essential only
implementation("io.insert-koin:koin-android:4.1.1")
implementation("io.insert-koin:koin-androidx-compose:4.1.1")
```

---

## 🗄️ Database

### Room Database

```kotlin
// Room - Essential
implementation("androidx.room:room-runtime:2.6.1")
implementation("androidx.room:room-ktx:2.6.1")
ksp("androidx.room:room-compiler:2.6.1")
```

### DataStore (Modern Preferences)

```kotlin
// DataStore
implementation("androidx.datastore:datastore-preferences:1.1.1")
```

---

## 🌐 Networking

### Retrofit + Kotlinx Serialization (Recommended)

```kotlin
// Retrofit
implementation("com.squareup.retrofit2:retrofit:2.11.0")
implementation("com.jakewharton.retrofit:retrofit2-kotlinx-serialization-converter:1.0.0")
implementation("com.squareup.okhttp3:okhttp:4.12.0")
implementation("com.squareup.okhttp3:logging-interceptor:4.12.0")

// Kotlinx Serialization
implementation("org.jetbrains.kotlinx:kotlinx-serialization-json:1.7.3")
```

### Gson Alternative (If Needed)

```kotlin
// Retrofit + Gson
implementation("com.squareup.retrofit2:retrofit:2.11.0")
implementation("com.squareup.retrofit2:converter-gson:2.11.0")
implementation("com.google.code.gson:gson:2.11.0")
```

---

## 🖼️ Image Loading

### Coil (Recommended for Compose)

```kotlin
// Coil - Essential
implementation("io.coil-kt.coil3:coil-compose:3.0.4")
implementation("io.coil-kt.coil3:coil-network-okhttp:3.0.4")
```

### Glide (Alternative)

```kotlin
// Glide - Essential
implementation("com.github.bumptech.glide:glide:4.16.0")
ksp("com.github.bumptech.glide:ksp:4.16.0")
implementation("com.github.bumptech.glide:compose:1.0.0-beta01")
```

---

## ⚡ Async & Background

### WorkManager (Background Tasks)

```kotlin
// WorkManager
implementation("androidx.work:work-runtime-ktx:2.10.0")
```

### Paging 3 (Pagination)

```kotlin
// Paging 3
implementation("androidx.paging:paging-runtime-ktx:3.3.5")
implementation("androidx.paging:paging-compose:3.3.5")
```

---

## 📄 PDF & Documents

### AndroidX PDF Viewer (Official)

```kotlin
// PDF Viewer
implementation("androidx.pdf:pdf-viewer:1.0.0-alpha12")
implementation("androidx.pdf:pdf-compose:1.0.0-alpha12")
implementation("androidx.pdf:pdf-document-service:1.0.0-alpha12")
```

### Document File (SAF)

```kotlin
// Document File
implementation("androidx.documentfile:documentfile:1.1.0")
```

### Zoom Gestures

```kotlin
// Telephoto - Zoomable
implementation("me.saket.telephoto:zoomable:0.18.0")
```

---

## 🔥 Firebase

### Firebase Core (BOM - Bill of Materials)

```kotlin
// Firebase BOM - Manages all Firebase versions
implementation(platform("com.google.firebase:firebase-bom:33.7.0"))
```

### Firebase Analytics

```kotlin
// Firebase Analytics
implementation("com.google.firebase:firebase-analytics")
```

### Firebase Authentication

```kotlin
// Firebase Auth
implementation("com.google.firebase:firebase-auth")

// Google Sign-In
implementation("com.google.android.gms:play-services-auth:21.3.0")
```

### Firebase Firestore (Cloud Database)

```kotlin
// Firestore
implementation("com.google.firebase:firebase-firestore")
```

### Firebase Realtime Database

```kotlin
// Realtime Database
implementation("com.google.firebase:firebase-database")
```

### Firebase Cloud Storage

```kotlin
// Cloud Storage
implementation("com.google.firebase:firebase-storage")
```

### Firebase Cloud Messaging (FCM - Push Notifications)

```kotlin
// FCM
implementation("com.google.firebase:firebase-messaging")
```

### Firebase Crashlytics

```kotlin
// Crashlytics - Add plugin: id("com.google.firebase.crashlytics")
implementation("com.google.firebase:firebase-crashlytics")
```

### Firebase Remote Config

```kotlin
// Remote Config
implementation("com.google.firebase:firebase-config")
```

### Firebase Dynamic Links

```kotlin
// Dynamic Links
implementation("com.google.firebase:firebase-dynamic-links")
```

---

## 📷 Camera & Media

### CameraX

```kotlin
// CameraX - Essential
implementation("androidx.camera:camera-core:1.4.1")
implementation("androidx.camera:camera-camera2:1.4.1")
implementation("androidx.camera:camera-lifecycle:1.4.1")
implementation("androidx.camera:camera-view:1.4.1")
```

### ExoPlayer (Media Playback)

```kotlin
// ExoPlayer - Essential
implementation("androidx.media3:media3-exoplayer:1.5.0")
implementation("androidx.media3:media3-ui:1.5.0")
```

### Permissions (Compose)

```kotlin
// Accompanist Permissions
implementation("com.google.accompanist:accompanist-permissions:0.36.0")
```

---

## 💾 Storage & Preferences

### DataStore

```kotlin
// DataStore
implementation("androidx.datastore:datastore-preferences:1.1.1")
```

### Security Crypto

```kotlin
// Security - Encrypted Storage
implementation("androidx.security:security-crypto:1.1.0-alpha06")
```

---

## 🔐 Security

### Biometric Authentication

```kotlin
// Biometric
implementation("androidx.biometric:biometric-ktx:1.4.0-alpha02")
```

### Security Crypto

```kotlin
// Encrypted SharedPreferences & Files
implementation("androidx.security:security-crypto:1.1.0-alpha06")
```

---

## 🎨 UI & Animation

### Lottie (Animations)

```kotlin
// Lottie - JSON Animations
implementation("com.airbnb.android:lottie-compose:6.6.2")
```

### Splash Screen

```kotlin
// Splash Screen API
implementation("androidx.core:core-splashscreen:1.0.1")
```

### Accompanist (Compose Utilities)

```kotlin
// System UI Controller
implementation("com.google.accompanist:accompanist-systemuicontroller:0.36.0")

// Pager (ViewPager for Compose)
implementation("com.google.accompanist:accompanist-pager:0.36.0")
implementation("com.google.accompanist:accompanist-pager-indicators:0.36.0")

// Swipe Refresh
implementation("com.google.accompanist:accompanist-swiperefresh:0.36.0")
```

---

## 🧪 Testing

### Unit Testing

```kotlin
// JUnit
testImplementation("junit:junit:4.13.2")
testImplementation("org.jetbrains.kotlinx:kotlinx-coroutines-test:1.9.0")

// MockK
testImplementation("io.mockk:mockk:1.13.14")

// Truth (Assertions)
testImplementation("com.google.truth:truth:1.4.4")
```

### Android Instrumentation Testing

```kotlin
// Android Test
androidTestImplementation("androidx.test.ext:junit:1.2.1")
androidTestImplementation("androidx.test.espresso:espresso-core:3.6.1")

// Compose UI Tests
androidTestImplementation("androidx.compose.ui:ui-test-junit4")

// Hilt Testing
androidTestImplementation("com.google.dagger:hilt-android-testing:2.54")
kspAndroidTest("com.google.dagger:hilt-android-compiler:2.54")
```

---

## 🎯 Interview Essentials Checklist

### Must-Know Dependencies:

✅ **Navigation** - `navigation-compose`  
✅ **DI** - `hilt-android` or `koin-android`  
✅ **Database** - `room-ktx`  
✅ **Network** - `retrofit` + `kotlinx-serialization`  
✅ **Images** - `coil-compose`  
✅ **Firebase** - `firebase-auth`, `firebase-firestore`, `firebase-storage`  
✅ **Async** - `coroutines-android`, `workmanager`  
✅ **UI** - `lottie-compose`, `accompanist`  
✅ **Testing** - `junit`, `mockk`, `espresso`

---

## 💡 Quick Tips

### Essential Interview Setup

**Minimal Interview Starter (5 min setup)**
```kotlin
// DI
implementation("io.insert-koin:koin-androidx-compose:4.1.1")

// Room
implementation("androidx.room:room-ktx:2.6.1")
ksp("androidx.room:room-compiler:2.6.1")

// Retrofit + Serialization
implementation("com.squareup.retrofit2:retrofit:2.11.0")
implementation("com.jakewharton.retrofit:retrofit2-kotlinx-serialization-converter:1.0.0")
implementation("org.jetbrains.kotlinx:kotlinx-serialization-json:1.7.3")

// Coil
implementation("io.coil-kt.coil3:coil-compose:3.0.4")
```

**Firebase Starter**
```kotlin
implementation(platform("com.google.firebase:firebase-bom:33.7.0"))
implementation("com.google.firebase:firebase-auth")
implementation("com.google.firebase:firebase-firestore")
implementation("com.google.firebase:firebase-analytics")
```

### Build Optimization
```kotlin
// gradle.properties
org.gradle.jvmargs=-Xmx4096m
org.gradle.parallel=true
org.gradle.caching=true
android.useAndroidX=true
```

---

## 📌 Notes

- **Minimal setup** for faster interview preparation
- **No serialization plugin** required for Moshi
- **Essential dependencies only** - no bloat
- **KSP** preferred over kapt

---

**Last Updated:** February 2026  
**Optimized for:** Fast Interview Setup & Production Apps

---

> 💡 **Quick Tip:** Copy only what you need - avoid adding unnecessary dependencies!

---

## 🎯 Interview Checklist

### Must-Know for Interviews:

✅ **Core Libraries:**
- Jetpack Compose (UI)
- ViewModel & LiveData/StateFlow
- Navigation Component
- Lifecycle

✅ **Architecture:**
- MVVM / MVI
- Clean Architecture
- Repository Pattern
- Use Cases

✅ **Dependency Injection:**
- Hilt (preferred) or Koin
- Module setup
- Injection types

✅ **Database:**
- Room (DAO, Entity, Database)
- Migrations
- Type Converters

✅ **Networking:**
- Retrofit + OkHttp
- Coroutines for async
- Error handling

✅ **Async:**
- Kotlin Coroutines
- Flow & StateFlow
- WorkManager for background

✅ **Testing:**
- JUnit for unit tests
- MockK/Mockito for mocking
- Compose UI tests

---

## 💡 Pro Tips

### Version Consistency
- Always use BOM for Compose dependencies
- Match Kotlin version with KSP version
- Keep lifecycle libraries at same version

### Build Optimization
```kotlin
// Add to gradle.properties
org.gradle.jvmargs=-Xmx4096m
org.gradle.parallel=true
org.gradle.caching=true
kotlin.code.style=official
kotlin.daemon.jvmargs=-Xmx4096m
android.useAndroidX=true
android.enableJetifier=false
```

### Common Configurations
```kotlin
// Kotlin options
kotlinOptions {
    jvmTarget = "17"
    freeCompilerArgs += listOf(
        "-opt-in=kotlin.RequiresOptIn",
        "-opt-in=kotlinx.coroutines.ExperimentalCoroutinesApi",
        "-opt-in=androidx.compose.material3.ExperimentalMaterial3Api"
    )
}
```

---

## 🚀 Quick Start Commands

### Clean Build
```bash
./gradlew clean
./gradlew build
```

### Install Debug
```bash
./gradlew installDebug
```

### Run Tests
```bash
./gradlew test
./gradlew connectedAndroidTest
```

---

## 📌 Notes

- **Always check official docs** for latest versions
- **Use stable versions** for production apps
- **Alpha/Beta versions** are fine for interviews/demos
- **KSP is preferred** over kapt (faster build times)
- **Compose BOM** manages compatibility automatically

---

## 🔗 Useful Links

- [Android Developers](https://developer.android.com)
- [Jetpack Compose](https://developer.android.com/jetpack/compose)
- [Kotlin Docs](https://kotlinlang.org/docs)
- [Maven Repository](https://mvnrepository.com)

---

**Last Updated:** February 2026  
**Maintained for:** Interview Preparation & Production Apps

---

> 💡 **Quick Tip:** Bookmark this file and keep it in every Android project for instant reference!

