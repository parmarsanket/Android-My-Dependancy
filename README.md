# 🚀 Complete Android Dependencies Guide (Interview & Production Ready)

> **Quick Setup Reference** - Copy → Paste → Build 🚀  
> No Version Catalog • Hardcoded versions • Always up-to-date • Interview optimized

---

## 📋 Table of Contents

1. [Project Setup](#project-setup)
2. [Core Dependencies](#core-dependencies)
3. [Jetpack Compose](#jetpack-compose)
4. [Navigation](#navigation)
5. [Dependency Injection](#dependency-injection)
6. [Database](#database)
7. [Networking](#networking)
8. [Image Loading](#image-loading)
9. [Async & Background](#async--background)
10. [PDF & Documents](#pdf--documents)
11. [Camera & Media](#camera--media)
12. [Storage & Preferences](#storage--preferences)
13. [Security](#security)
14. [Testing](#testing)
15. [Debug Tools](#debug-tools)
16. [Minimal Setups](#minimal-setups)

---

## 📦 Project Setup

### Project Level `build.gradle.kts`

```kotlin
plugins {
    id("com.android.application") version "8.7.3" apply false
    id("com.android.library") version "8.7.3" apply false
    id("org.jetbrains.kotlin.android") version "2.1.0" apply false
    id("org.jetbrains.kotlin.plugin.compose") version "2.1.0" apply false
    id("org.jetbrains.kotlin.plugin.serialization") version "2.1.0" apply false
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
    id("org.jetbrains.kotlin.plugin.serialization")
    id("com.google.devtools.ksp")
    id("com.google.dagger.hilt.android") // For Hilt DI
}
```

### Android Configuration

```kotlin
android {
    namespace = "com.example.app"
    compileSdk = 35

    defaultConfig {
        applicationId = "com.example.app"
        minSdk = 24
        targetSdk = 35
        versionCode = 1
        versionName = "1.0"
        
        testInstrumentationRunner = "androidx.test.runner.AndroidJUnitRunner"
        vectorDrawables {
            useSupportLibrary = true
        }
    }

    buildTypes {
        release {
            isMinifyEnabled = true
            proguardFiles(
                getDefaultProguardFile("proguard-android-optimize.txt"),
                "proguard-rules.pro"
            )
        }
    }

    compileOptions {
        sourceCompatibility = JavaVersion.VERSION_17
        targetCompatibility = JavaVersion.VERSION_17
    }

    kotlinOptions {
        jvmTarget = "17"
    }

    buildFeatures {
        compose = true
        buildConfig = true
    }

    packaging {
        resources {
            excludes += "/META-INF/{AL2.0,LGPL2.1}"
        }
    }
}
```

---

## 📚 Core Dependencies

### Essential Android Core

```kotlin
dependencies {
    // Core Android
    implementation("androidx.core:core-ktx:1.15.0")
    implementation("androidx.appcompat:appcompat:1.7.0")
    implementation("androidx.fragment:fragment-ktx:1.8.5")
    implementation("androidx.activity:activity-ktx:1.9.3")
    
    // Lifecycle
    implementation("androidx.lifecycle:lifecycle-runtime-ktx:2.8.7")
    implementation("androidx.lifecycle:lifecycle-viewmodel-ktx:2.8.7")
    implementation("androidx.lifecycle:lifecycle-livedata-ktx:2.8.7")
    implementation("androidx.lifecycle:lifecycle-viewmodel-compose:2.8.7")
    implementation("androidx.lifecycle:lifecycle-runtime-compose:2.8.7")
    
    // Kotlin Coroutines
    implementation("org.jetbrains.kotlinx:kotlinx-coroutines-core:1.9.0")
    implementation("org.jetbrains.kotlinx:kotlinx-coroutines-android:1.9.0")
    
    // Splash Screen
    implementation("androidx.core:core-splashscreen:1.0.1")
}
```

---

## 🎨 Jetpack Compose

### Complete Compose Stack

```kotlin
// Compose BOM (Bill of Materials)
implementation(platform("androidx.compose:compose-bom:2024.12.01"))

// Core Compose
implementation("androidx.compose.ui:ui")
implementation("androidx.compose.ui:ui-graphics")
implementation("androidx.compose.ui:ui-tooling-preview")
implementation("androidx.compose.foundation:foundation")

// Material Design 3
implementation("androidx.compose.material3:material3")
implementation("androidx.compose.material3:material3-window-size-class")

// Material Icons
implementation("androidx.compose.material:material-icons-core")
implementation("androidx.compose.material:material-icons-extended")

// Activity & ViewModel
implementation("androidx.activity:activity-compose:1.9.3")
implementation("androidx.lifecycle:lifecycle-viewmodel-compose:2.8.7")
implementation("androidx.lifecycle:lifecycle-runtime-compose:2.8.7")

// Google Fonts
implementation("androidx.compose.ui:ui-text-google-fonts")

// Animation
implementation("androidx.compose.animation:animation")
implementation("androidx.compose.animation:animation-core")
implementation("androidx.compose.animation:animation-graphics")

// Compose Runtime
implementation("androidx.compose.runtime:runtime")
implementation("androidx.compose.runtime:runtime-livedata")
```

---

## 🧭 Navigation

### Navigation Compose

```kotlin
// Navigation for Compose
implementation("androidx.navigation:navigation-compose:2.8.5")
implementation("androidx.navigation:navigation-fragment-ktx:2.8.5")
implementation("androidx.navigation:navigation-ui-ktx:2.8.5")

// Type-safe navigation (Optional - requires serialization plugin)
implementation("org.jetbrains.kotlinx:kotlinx-serialization-json:1.7.3")
```

### Navigation 3 (Latest - Alpha)

```kotlin
// Navigation 3 - Next Generation
implementation("androidx.navigation3:navigation3-runtime:1.0.0")
implementation("androidx.navigation3:navigation3-ui:1.0.0")
```

---

## 💉 Dependency Injection

### Option 1: Hilt (Recommended by Google)

```kotlin
// Hilt
implementation("com.google.dagger:hilt-android:2.54")
ksp("com.google.dagger:hilt-android-compiler:2.54")

// Hilt Navigation Compose
implementation("androidx.hilt:hilt-navigation-compose:1.2.0")

// Hilt Work Manager (if using WorkManager)
implementation("androidx.hilt:hilt-work:1.2.0")
ksp("androidx.hilt:hilt-compiler:1.2.0")
```

### Option 2: Koin (Lightweight Alternative)

```kotlin
// Koin Core
implementation("io.insert-koin:koin-core:4.1.1")
implementation("io.insert-koin:koin-android:4.1.1")

// Koin Compose
implementation("io.insert-koin:koin-androidx-compose:4.1.1")
implementation("io.insert-koin:koin-androidx-compose-navigation:4.1.1")

// Koin WorkManager
implementation("io.insert-koin:koin-androidx-workmanager:4.1.1")
```

### Option 3: Dagger (Manual Setup)

```kotlin
// Dagger
implementation("com.google.dagger:dagger:2.54")
ksp("com.google.dagger:dagger-compiler:2.54")
```

---

## 🗄️ Database

### Room Database (Complete Setup)

```kotlin
// Room
implementation("androidx.room:room-runtime:2.6.1")
implementation("androidx.room:room-ktx:2.6.1")
ksp("androidx.room:room-compiler:2.6.1")

// Room Paging (if using Paging 3)
implementation("androidx.room:room-paging:2.6.1")

// Room Testing
testImplementation("androidx.room:room-testing:2.6.1")
```

### DataStore (Modern SharedPreferences Alternative)

```kotlin
// Preferences DataStore
implementation("androidx.datastore:datastore-preferences:1.1.1")

// Proto DataStore (type-safe)
implementation("androidx.datastore:datastore:1.1.1")
```

---

## 🌐 Networking

### Retrofit + OkHttp (REST APIs)

```kotlin
// Retrofit
implementation("com.squareup.retrofit2:retrofit:2.11.0")
implementation("com.squareup.retrofit2:converter-gson:2.11.0")
implementation("com.squareup.retrofit2:converter-moshi:2.11.0") // Alternative to Gson

// OkHttp
implementation("com.squareup.okhttp3:okhttp:4.12.0")
implementation("com.squareup.okhttp3:logging-interceptor:4.12.0")

// Moshi (JSON parser - alternative to Gson)
implementation("com.squareup.moshi:moshi:1.15.1")
implementation("com.squareup.moshi:moshi-kotlin:1.15.1")
ksp("com.squareup.moshi:moshi-kotlin-codegen:1.15.1")
```

### Ktor (Kotlin-first Alternative)

```kotlin
// Ktor Client
implementation("io.ktor:ktor-client-core:3.0.2")
implementation("io.ktor:ktor-client-android:3.0.2")
implementation("io.ktor:ktor-client-serialization:3.0.2")
implementation("io.ktor:ktor-client-logging:3.0.2")
implementation("io.ktor:ktor-client-content-negotiation:3.0.2")
implementation("io.ktor:ktor-serialization-kotlinx-json:3.0.2")
```

### Gson & Serialization

```kotlin
// Gson (JSON library)
implementation("com.google.code.gson:gson:2.11.0")

// Kotlin Serialization (Recommended)
implementation("org.jetbrains.kotlinx:kotlinx-serialization-core:1.7.3")
implementation("org.jetbrains.kotlinx:kotlinx-serialization-json:1.7.3")
```

---

## 🖼️ Image Loading

### Coil (Recommended for Compose)

```kotlin
// Coil 3.x - Multiplatform
implementation("io.coil-kt.coil3:coil-compose:3.0.4")
implementation("io.coil-kt.coil3:coil-network-okhttp:3.0.4")
implementation("io.coil-kt.coil3:coil-gif:3.0.4")
implementation("io.coil-kt.coil3:coil-svg:3.0.4")
```

### Glide (Alternative)

```kotlin
// Glide
implementation("com.github.bumptech.glide:glide:4.16.0")
ksp("com.github.bumptech.glide:ksp:4.16.0")

// Glide for Compose
implementation("com.github.bumptech.glide:compose:1.0.0-beta01")
```

---

## ⚡ Async & Background

### WorkManager (Background Tasks)

```kotlin
// WorkManager
implementation("androidx.work:work-runtime-ktx:2.10.0")

// WorkManager Testing
androidTestImplementation("androidx.work:work-testing:2.10.0")
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

### Document File (SAF - Storage Access Framework)

```kotlin
// Document File
implementation("androidx.documentfile:documentfile:1.1.0")
```

### Zoom Gestures

```kotlin
// Telephoto - Zoomable images
implementation("me.saket.telephoto:zoomable:0.18.0")
implementation("me.saket.telephoto:zoomable-image-coil:0.18.0")
```

---

## 📷 Camera & Media

### CameraX

```kotlin
// CameraX
implementation("androidx.camera:camera-core:1.4.1")
implementation("androidx.camera:camera-camera2:1.4.1")
implementation("androidx.camera:camera-lifecycle:1.4.1")
implementation("androidx.camera:camera-view:1.4.1")
implementation("androidx.camera:camera-extensions:1.4.1")
```

### ExoPlayer (Media Playback)

```kotlin
// ExoPlayer
implementation("androidx.media3:media3-exoplayer:1.5.0")
implementation("androidx.media3:media3-ui:1.5.0")
implementation("androidx.media3:media3-common:1.5.0")
```

### Permissions

```kotlin
// Accompanist Permissions (for Compose)
implementation("com.google.accompanist:accompanist-permissions:0.36.0")
```

---

## 💾 Storage & Preferences

### DataStore (Modern Solution)

```kotlin
// DataStore Preferences
implementation("androidx.datastore:datastore-preferences:1.1.1")
implementation("androidx.datastore:datastore-preferences-core:1.1.1")
```

### Security Crypto

```kotlin
// Security Library
implementation("androidx.security:security-crypto:1.1.0-alpha06")
implementation("androidx.security:security-crypto-ktx:1.1.0-alpha06")
```

---

## 🔐 Security

### Biometric Authentication

```kotlin
// Biometric
implementation("androidx.biometric:biometric:1.4.0-alpha02")
implementation("androidx.biometric:biometric-ktx:1.4.0-alpha02")
```

### Security Crypto

```kotlin
// Encrypted SharedPreferences & Files
implementation("androidx.security:security-crypto:1.1.0-alpha06")
implementation("androidx.security:security-crypto-ktx:1.1.0-alpha06")
```

---

## 🧪 Testing

### Unit Testing

```kotlin
// JUnit
testImplementation("junit:junit:4.13.2")
testImplementation("org.jetbrains.kotlinx:kotlinx-coroutines-test:1.9.0")

// Mockito / MockK
testImplementation("org.mockito:mockito-core:5.14.2")
testImplementation("org.mockito.kotlin:mockito-kotlin:5.4.0")
testImplementation("io.mockk:mockk:1.13.14")

// Truth (Assertions)
testImplementation("com.google.truth:truth:1.4.4")

// Turbine (Flow testing)
testImplementation("app.cash.turbine:turbine:1.2.0")
```

### Android Instrumentation Testing

```kotlin
// Android Test
androidTestImplementation("androidx.test.ext:junit:1.2.1")
androidTestImplementation("androidx.test.espresso:espresso-core:3.6.1")
androidTestImplementation("androidx.test:runner:1.6.2")
androidTestImplementation("androidx.test:rules:1.6.1")

// Compose UI Tests
androidTestImplementation(platform("androidx.compose:compose-bom:2024.12.01"))
androidTestImplementation("androidx.compose.ui:ui-test-junit4")
androidTestImplementation("androidx.navigation:navigation-testing:2.8.5")

// Hilt Testing
androidTestImplementation("com.google.dagger:hilt-android-testing:2.54")
kspAndroidTest("com.google.dagger:hilt-android-compiler:2.54")
```

---

## 🛠 Debug Tools

### Development & Debugging

```kotlin
// Compose Tooling
debugImplementation("androidx.compose.ui:ui-tooling")
debugImplementation("androidx.compose.ui:ui-test-manifest")

// LeakCanary (Memory Leak Detection)
debugImplementation("com.squareup.leakcanary:leakcanary-android:3.0-beta-1")

// Timber (Logging)
implementation("com.jakewharton.timber:timber:5.0.1")

// Chucker (Network Inspector)
debugImplementation("com.github.chuckerteam.chucker:library:4.1.0")
releaseImplementation("com.github.chuckerteam.chucker:library-no-op:4.1.0")
```

---

## ⚡ Minimal Setups

### Interview Speed Setup (5 Minutes)

```kotlin
dependencies {
    // Core
    implementation("androidx.core:core-ktx:1.15.0")
    implementation("androidx.lifecycle:lifecycle-runtime-ktx:2.8.7")
    
    // Compose
    implementation(platform("androidx.compose:compose-bom:2024.12.01"))
    implementation("androidx.compose.ui:ui")
    implementation("androidx.compose.material3:material3")
    implementation("androidx.activity:activity-compose:1.9.3")
    
    // Navigation
    implementation("androidx.navigation:navigation-compose:2.8.5")
    
    // DI (Koin - faster setup)
    implementation("io.insert-koin:koin-androidx-compose:4.1.1")
    
    // Room
    implementation("androidx.room:room-ktx:2.6.1")
    ksp("androidx.room:room-compiler:2.6.1")
    
    // Coil
    implementation("io.coil-kt.coil3:coil-compose:3.0.4")
    
    // Testing
    testImplementation("junit:junit:4.13.2")
    androidTestImplementation("androidx.compose.ui:ui-test-junit4")
}
```

### MVVM Clean Architecture Setup

```kotlin
dependencies {
    // Core Android
    implementation("androidx.core:core-ktx:1.15.0")
    implementation("androidx.lifecycle:lifecycle-viewmodel-ktx:2.8.7")
    implementation("androidx.lifecycle:lifecycle-runtime-ktx:2.8.7")
    
    // Compose
    implementation(platform("androidx.compose:compose-bom:2024.12.01"))
    implementation("androidx.compose.ui:ui")
    implementation("androidx.compose.material3:material3")
    implementation("androidx.activity:activity-compose:1.9.3")
    implementation("androidx.lifecycle:lifecycle-viewmodel-compose:2.8.7")
    
    // Navigation
    implementation("androidx.navigation:navigation-compose:2.8.5")
    
    // Hilt (DI)
    implementation("com.google.dagger:hilt-android:2.54")
    ksp("com.google.dagger:hilt-android-compiler:2.54")
    implementation("androidx.hilt:hilt-navigation-compose:1.2.0")
    
    // Room (Local DB)
    implementation("androidx.room:room-ktx:2.6.1")
    ksp("androidx.room:room-compiler:2.6.1")
    
    // Retrofit (Network)
    implementation("com.squareup.retrofit2:retrofit:2.11.0")
    implementation("com.squareup.retrofit2:converter-gson:2.11.0")
    implementation("com.squareup.okhttp3:logging-interceptor:4.12.0")
    
    // Coroutines
    implementation("org.jetbrains.kotlinx:kotlinx-coroutines-android:1.9.0")
    
    // Coil (Images)
    implementation("io.coil-kt.coil3:coil-compose:3.0.4")
    
    // Timber (Logging)
    implementation("com.jakewharton.timber:timber:5.0.1")
}
```

### Full Production App Setup

```kotlin
dependencies {
    // Core
    implementation("androidx.core:core-ktx:1.15.0")
    implementation("androidx.appcompat:appcompat:1.7.0")
    implementation("androidx.lifecycle:lifecycle-runtime-ktx:2.8.7")
    implementation("androidx.lifecycle:lifecycle-viewmodel-ktx:2.8.7")
    
    // Compose
    implementation(platform("androidx.compose:compose-bom:2024.12.01"))
    implementation("androidx.compose.ui:ui")
    implementation("androidx.compose.material3:material3")
    implementation("androidx.compose.material:material-icons-extended")
    implementation("androidx.activity:activity-compose:1.9.3")
    implementation("androidx.lifecycle:lifecycle-viewmodel-compose:2.8.7")
    implementation("androidx.lifecycle:lifecycle-runtime-compose:2.8.7")
    
    // Navigation
    implementation("androidx.navigation:navigation-compose:2.8.5")
    
    // Hilt
    implementation("com.google.dagger:hilt-android:2.54")
    ksp("com.google.dagger:hilt-android-compiler:2.54")
    implementation("androidx.hilt:hilt-navigation-compose:1.2.0")
    implementation("androidx.hilt:hilt-work:1.2.0")
    ksp("androidx.hilt:hilt-compiler:1.2.0")
    
    // Room
    implementation("androidx.room:room-runtime:2.6.1")
    implementation("androidx.room:room-ktx:2.6.1")
    ksp("androidx.room:room-compiler:2.6.1")
    
    // DataStore
    implementation("androidx.datastore:datastore-preferences:1.1.1")
    
    // Retrofit + OkHttp
    implementation("com.squareup.retrofit2:retrofit:2.11.0")
    implementation("com.squareup.retrofit2:converter-gson:2.11.0")
    implementation("com.squareup.okhttp3:okhttp:4.12.0")
    implementation("com.squareup.okhttp3:logging-interceptor:4.12.0")
    
    // Coroutines
    implementation("org.jetbrains.kotlinx:kotlinx-coroutines-core:1.9.0")
    implementation("org.jetbrains.kotlinx:kotlinx-coroutines-android:1.9.0")
    
    // Serialization
    implementation("org.jetbrains.kotlinx:kotlinx-serialization-json:1.7.3")
    
    // Coil
    implementation("io.coil-kt.coil3:coil-compose:3.0.4")
    implementation("io.coil-kt.coil3:coil-network-okhttp:3.0.4")
    
    // WorkManager
    implementation("androidx.work:work-runtime-ktx:2.10.0")
    
    // Paging
    implementation("androidx.paging:paging-runtime-ktx:3.3.5")
    implementation("androidx.paging:paging-compose:3.3.5")
    
    // Security
    implementation("androidx.security:security-crypto:1.1.0-alpha06")
    implementation("androidx.biometric:biometric-ktx:1.4.0-alpha02")
    
    // Splash Screen
    implementation("androidx.core:core-splashscreen:1.0.1")
    
    // Timber
    implementation("com.jakewharton.timber:timber:5.0.1")
    
    // Testing
    testImplementation("junit:junit:4.13.2")
    testImplementation("org.jetbrains.kotlinx:kotlinx-coroutines-test:1.9.0")
    testImplementation("io.mockk:mockk:1.13.14")
    testImplementation("com.google.truth:truth:1.4.4")
    testImplementation("app.cash.turbine:turbine:1.2.0")
    
    androidTestImplementation("androidx.test.ext:junit:1.2.1")
    androidTestImplementation("androidx.test.espresso:espresso-core:3.6.1")
    androidTestImplementation(platform("androidx.compose:compose-bom:2024.12.01"))
    androidTestImplementation("androidx.compose.ui:ui-test-junit4")
    androidTestImplementation("com.google.dagger:hilt-android-testing:2.54")
    kspAndroidTest("com.google.dagger:hilt-android-compiler:2.54")
    
    debugImplementation("androidx.compose.ui:ui-tooling")
    debugImplementation("androidx.compose.ui:ui-test-manifest")
    debugImplementation("com.squareup.leakcanary:leakcanary-android:3.0-beta-1")
    debugImplementation("com.github.chuckerteam.chucker:library:4.1.0")
    releaseImplementation("com.github.chuckerteam.chucker:library-no-op:4.1.0")
}
```

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

