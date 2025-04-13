![image](https://github.com/user-attachments/assets/ffffa37b-83b9-41fb-9924-b44abb146823)# 🌟 Android Dependencies Setup Guide

This file provides a clean and readable reference for setting up common Android dependencies using **Version Catalog** (`libs.versions.toml`), **Gradle Kotlin DSL**, required **Plugins**, and optional **Hardcoded Dependencies** for easy switching.

---

## 📈 Plugins

### 🔢 `[versions]`
```toml
kotlin = "1.9.22"
hilt = "2.51.1"
ksp = "2.0.0-1.0.22"
serialization = "1.6.3"
```

### 📦 `[plugins]`
```toml
kotlin-android = { id = "org.jetbrains.kotlin.android", version.ref = "kotlin" }
kotlin-serialization = { id = "org.jetbrains.kotlin.plugin.serialization", version.ref = "kotlin" }
dagger-hilt = { id = "com.google.dagger.hilt.android", version.ref = "hilt" }
ksp = { id = "com.google.devtools.ksp", version.ref = "ksp" }
```

### `build.gradle.kts (plugins section)`
```kotlin
plugins {
    id("com.android.application")
    id("org.jetbrains.kotlin.android")
    id("org.jetbrains.kotlin.plugin.serialization")
    id("com.google.dagger.hilt.android")
    id("com.google.devtools.ksp")
}
```
### 📁'Hardcoded'
```kotlin    
plugins {
    id("com.android.application") version "8.3.1" apply false
    id("com.android.library") version "8.3.1" apply false
    id("org.jetbrains.kotlin.android") version "1.9.22" apply false
    id("org.jetbrains.kotlin.plugin.serialization") version "1.9.22" apply false
    id("com.google.dagger.hilt.android") version "2.51.1" apply false
    id("com.google.devtools.ksp") version "2.0.0-1.0.22" apply false
}
```
## 🏠 Room

### 🔢 `[versions]`
```toml
room = "2.6.1"
roomCompiler = "2.6.1"
```

### 📦 `[libraries]`
```toml
room-runtime = { group = "androidx.room", name = "room-runtime", version.ref = "room" }
room-ktx = { group = "androidx.room", name = "room-ktx", version.ref = "room" }
androidx-room-compiler = { module = "androidx.room:room-compiler", version.ref = "roomCompiler" }
```

### 🧵 `[bundles]`
```toml
room = [
    "room-runtime",
    "room-ktx"
]
```

### `build.gradle.kts`
```kotlin
implementation(libs.room.runtime)
implementation(libs.room.ktx)
ksp(libs.androidx.room.compiler)
```

### 📁 Hardcoded
```kotlin
// Room
implementation("androidx.room:room-runtime:2.6.1")
implementation("androidx.room:room-ktx:2.6.1")
ksp("androidx.room:room-compiler:2.6.1")
```

---

## 💉 Hilt

### 🔢 `[versions]`
```toml
hilt = "2.51.1"
hiltCompiler = "2.51.1"
hiltNavigationCompose = "1.2.0"
```

### 📦 `[libraries]`
```toml
hilt-android = { group = "com.google.dagger", name = "hilt-android", version.ref = "hilt" }
hilt-compiler = { module = "com.google.dagger:hilt-compiler", version.ref = "hiltCompiler" }
androidx-hilt-navigation-compose = { module = "androidx.hilt:hilt-navigation-compose", version.ref = "hiltNavigationCompose" }
```

### 🧵 `[bundles]`
```toml
hilt = [
    "hilt-android",
    "hilt-compiler",
    "androidx-hilt-navigation-compose"
]
```

### `build.gradle.kts`
```kotlin
implementation(libs.hilt.android)
ksp(libs.hilt.compiler)
implementation(libs.androidx.hilt.navigation.compose)
```

### 📁 Hardcoded
```kotlin
// Hilt
implementation("com.google.dagger:hilt-android:2.51.1")
ksp("com.google.dagger:hilt-compiler:2.51.1")
implementation("androidx.hilt:hilt-navigation-compose:1.2.0")
```

---

## 🔗 Retrofit

### 🔢 `[versions]`
```toml
retrofit = "2.9.0"
okhttp = "4.12.0"
serializationConverter = "0.8.0"
```

### 📦 `[libraries]`
```toml
retrofit = { module = "com.squareup.retrofit2:retrofit", version.ref = "retrofit" }
retrofit-serialization = { module = "com.jakewharton.retrofit:retrofit2-kotlinx-serialization-converter", version.ref = "serializationConverter" }
okhttp = { module = "com.squareup.okhttp3:okhttp", version.ref = "okhttp" }
okhttp-logging = { module = "com.squareup.okhttp3:logging-interceptor", version.ref = "okhttp" }
```

### 🧵 `[bundles]`
```toml
retrofit = [
    "retrofit",
    "retrofit-serialization",
    "okhttp",
    "okhttp-logging"
]
```

### `build.gradle.kts`
```kotlin
implementation(libs.bundles.retrofit)
```

### 📁 Hardcoded
```kotlin
// Retrofit
implementation("com.squareup.retrofit2:retrofit:2.9.0")
implementation("com.jakewharton.retrofit:retrofit2-kotlinx-serialization-converter:0.8.0")
implementation("com.squareup.okhttp3:okhttp:4.12.0")
implementation("com.squareup.okhttp3:logging-interceptor:4.12.0")
```

---

## 🌐 Ktor

### 🔢 `[versions]`
```toml
ktor = "2.3.5"
```

### 📦 `[libraries]`
```toml
ktor-client-core = { module = "io.ktor:ktor-client-core", version.ref = "ktor" }
ktor-client-okhttp = { module = "io.ktor:ktor-client-okhttp", version.ref = "ktor" }
ktor-client-content-negotiation = { module = "io.ktor:ktor-client-content-negotiation", version.ref = "ktor" }
ktor-serialization-kotlinx-json = { module = "io.ktor:ktor-serialization-kotlinx-json", version.ref = "ktor" }
ktor-client-logging = { module = "io.ktor:ktor-client-logging", version.ref = "ktor" }
```

### 🧵 `[bundles]`
```toml
ktor = [
    "ktor-client-core",
    "ktor-client-content-negotiation",
    "ktor-client-logging",
    "ktor-serialization-kotlinx-json",
    "ktor-client-okhttp"
]
```

### `build.gradle.kts`
```kotlin
implementation(libs.bundles.ktor)
```

### 📁 Hardcoded
```kotlin
// Ktor core
implementation("io.ktor:ktor-client-core:2.3.5")

// OkHttp engine (Android-specific) 
implementation("io.ktor:ktor-client-okhttp:2.3.5")

// Content negotiation (e.g., for JSON)
implementation("io.ktor:ktor-client-content-negotiation:2.3.5")

// Kotlinx Serialization support
implementation("io.ktor:ktor-serialization-kotlinx-json:2.3.5")

// Optional: Logging
implementation("io.ktor:ktor-client-logging:2.3.5")
```

---

## 🔐 Kotlin Serialization

### 🔢 `[versions]`
```toml
kotlinxSerializationJson = "1.6.3"
```

### 📦 `[libraries]`
```toml
kotlinx-serialization-json = { module = "org.jetbrains.kotlinx:kotlinx-serialization-json", version.ref = "kotlinxSerializationJson" }
```

### `build.gradle.kts`
```kotlin
implementation(libs.kotlinx.serialization.json)
```

### 📁 Hardcoded
```kotlin
// Kotlin Serialization
implementation("org.jetbrains.kotlinx:kotlinx-serialization-json:1.6.3")
```

---

## 🖼️ Coil

### 🔢 `[versions]`
```toml
coil = "2.6.0"
```

### 📦 `[libraries]`
```toml
coil-compose = { module = "io.coil-kt:coil-compose", version.ref = "coil" }
coil-core = { module = "io.coil-kt:coil", version.ref = "coil" }
#if ktor using
#coil-ktor = { module = "io.coil-kt:coil-network-ktor3", version.ref = "coil" }
```

### 🧵 `[bundles]`
```toml
coil = [
    "coil-compose",
    "coil-core",
   # "coil-ktor
]
```

### `build.gradle.kts`
```kotlin
implementation(libs.bundles.coil)
```

### 📁 Hardcoded
```kotlin
// Coil
implementation("io.coil-kt:coil:2.6.0")
implementation("io.coil-kt:coil-compose:2.6.0")

implementation("io.coil-kt:coil-network-ktor3:2.6.0") // Only if you're using Ktor
```
# 🖼️ icons extended
---
implementation("androidx.compose.material:material-icons-extended")

---
Let me know if you'd like to add **Navigation Compose**, **Coroutines**, **WorkManager**, or others!

