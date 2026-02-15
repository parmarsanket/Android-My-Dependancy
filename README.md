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
    id("com.google.devtools.ksp") version "2.1.0-1.0.29" apply false
    id("com.google.dagger.hilt.android") version "2.54" apply false
}
```

### App Level `build.gradle.kts` - Plugins

```kotlin
plugins {
    id("com.android.application")
    id("org.jetbrains.kotlin.android")
    id("org.jetbrains.kotlin.plugin.compose")
    id("com.google.devtools.ksp")
    id("com.google.dagger.hilt.android") // For Hilt DI
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

### Retrofit + OkHttp (Minimal)

```kotlin
// Retrofit - Essential only
implementation("com.squareup.retrofit2:retrofit:2.11.0")
implementation("com.squareup.retrofit2:converter-gson:2.11.0")
implementation("com.squareup.okhttp3:okhttp:4.12.0")
```

### Moshi (JSON Parser - No Serialization Plugin Required)

```kotlin
// Moshi - Alternative to Gson
implementation("com.squareup.moshi:moshi:1.15.1")
implementation("com.squareup.moshi:moshi-kotlin:1.15.1")
ksp("com.squareup.moshi:moshi-kotlin-codegen:1.15.1")

// Use with Retrofit
implementation("com.squareup.retrofit2:converter-moshi:2.11.0")
```

### Kotlin Serialization (If Needed)

```kotlin
// Add plugin in app level build.gradle.kts
// id("org.jetbrains.kotlin.plugin.serialization")

// Serialization - Only if type-safe navigation or Ktor needed
implementation("org.jetbrains.kotlinx:kotlinx-serialization-json:1.7.3")
```

### Gson (Simple Alternative)

```kotlin
// Gson - Lightweight JSON
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
✅ **Network** - `retrofit` + `okhttp`  
✅ **JSON** - `gson` or `moshi`  
✅ **Images** - `coil-compose` or `glide`  
✅ **Async** - `coroutines-android`  
✅ **Testing** - `junit`, `mockk`, `espresso`

---

## 💡 Quick Tips

### Dependency Combinations

**Networking Option 1: Retrofit + Gson**
```kotlin
implementation("com.squareup.retrofit2:retrofit:2.11.0")
implementation("com.squareup.retrofit2:converter-gson:2.11.0")
implementation("com.google.code.gson:gson:2.11.0")
```

**Networking Option 2: Retrofit + Moshi (No Serialization Plugin)**
```kotlin
implementation("com.squareup.retrofit2:retrofit:2.11.0")
implementation("com.squareup.retrofit2:converter-moshi:2.11.0")
implementation("com.squareup.moshi:moshi:1.15.1")
implementation("com.squareup.moshi:moshi-kotlin:1.15.1")
ksp("com.squareup.moshi:moshi-kotlin-codegen:1.15.1")
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

