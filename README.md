# 🚀 Android Hardcoded Dependencies Guide (Interview Ready)

This file provides **clean hardcoded Gradle dependencies** without Version Catalog.
Useful for:

* Interviews
* New projects
* Quick setup
* When Version Catalog is not allowed

Includes modern Android stack:

* Jetpack Compose
* Navigation 3
* PDF Viewer (AndroidX official)
* Room Database
* Koin Dependency Injection
* Coil Image loading
* Serialization
* Zoom gestures

---

# 📦 Project Level `build.gradle.kts`

```kotlin
plugins {
    id("com.android.application") version "8.13.2" apply false
    id("com.android.library") version "8.13.2" apply false
    id("org.jetbrains.kotlin.android") version "2.3.0" apply false
    id("org.jetbrains.kotlin.plugin.compose") version "2.3.0" apply false
    id("org.jetbrains.kotlin.plugin.serialization") version "2.3.0" apply false
    id("com.google.devtools.ksp") version "2.3.0-1.0.30" apply false
}
```

---

# 📱 App Level `build.gradle.kts`

```kotlin
plugins {

    id("com.android.application")

    id("org.jetbrains.kotlin.android")

    id("org.jetbrains.kotlin.plugin.compose")

    id("org.jetbrains.kotlin.plugin.serialization")

    id("com.google.devtools.ksp")

}
```

---

# ⚙️ Android Configuration

```kotlin
android {

    namespace = "com.example.app"

    compileSdk = 36

    defaultConfig {

        applicationId = "com.example.app"

        minSdk = 24

        targetSdk = 36

        versionCode = 1

        versionName = "1.0"

    }

    buildFeatures {
        compose = true
    }

}
```

---

# 📚 Core Android Dependencies

```kotlin
implementation("androidx.core:core-ktx:1.17.0")

implementation("androidx.fragment:fragment-ktx:1.8.9")

implementation("androidx.lifecycle:lifecycle-runtime-ktx:2.10.0")

implementation("androidx.lifecycle:lifecycle-viewmodel-compose:2.10.0")
```

---

# 🎨 Jetpack Compose

```kotlin
implementation(platform("androidx.compose:compose-bom:2025.12.01"))

implementation("androidx.compose.ui:ui")

implementation("androidx.compose.ui:ui-graphics")

implementation("androidx.compose.foundation:foundation:1.10.0")

implementation("androidx.compose.material3:material3:1.5.0-alpha11")

implementation("androidx.activity:activity-compose:1.12.2")

implementation("androidx.compose.ui:ui-text-google-fonts:1.10.0")

implementation("androidx.compose.animation:animation:1.10.0")

implementation("androidx.compose.animation:animation-core:1.10.0")
```

---

# 🧭 Navigation

## Navigation Compose

```kotlin
implementation("androidx.navigation:navigation-compose:2.9.6")
```

## Navigation 3 (Latest)

```kotlin
implementation("androidx.navigation3:navigation3-runtime:1.0.0")

implementation("androidx.navigation3:navigation3-ui:1.0.0")

implementation("org.jetbrains.androidx.lifecycle:lifecycle-viewmodel-navigation3:2.10.0-alpha07")
```

---

# 📄 PDF Viewer (AndroidX Official)

```kotlin
implementation("androidx.pdf:pdf-viewer:1.0.0-alpha12")

implementation("androidx.pdf:pdf-compose:1.0.0-alpha12")

implementation("androidx.pdf:pdf-document-service:1.0.0-alpha12")
```

---

# 🖼️ Image Loading (Coil)

```kotlin
implementation("io.coil-kt.coil3:coil-compose:3.3.0")
```

---

# 🔍 Zoom Gesture Support

```kotlin
implementation("me.saket.telephoto:zoomable:0.18.0")
```

---

# 🗄️ Room Database

```kotlin
implementation("androidx.room:room-runtime:2.8.4")

implementation("androidx.room:room-ktx:2.8.4")

ksp("androidx.room:room-compiler:2.8.4")
```

---

# 💉 Dependency Injection (Koin)

```kotlin
implementation("io.insert-koin:koin-core:4.1.1")

implementation("io.insert-koin:koin-android:4.1.1")

implementation("io.insert-koin:koin-androidx-compose:4.1.1")
```

---

# 🔐 Serialization

```kotlin
implementation("org.jetbrains.kotlinx:kotlinx-serialization-core:1.9.0")

implementation("org.jetbrains.kotlinx:kotlinx-serialization-json:1.9.0")
```

---

# 📁 File Access

```kotlin
implementation("androidx.documentfile:documentfile:1.1.0")
```

---

# 🧪 Testing

```kotlin
testImplementation("junit:junit:4.13.2")

androidTestImplementation("androidx.test.ext:junit:1.3.0")

androidTestImplementation("androidx.test.espresso:espresso-core:3.7.0")

androidTestImplementation(platform("androidx.compose:compose-bom:2025.12.01"))

androidTestImplementation("androidx.compose.ui:ui-test-junit4")
```

---

# 🛠 Debug Tools

```kotlin
debugImplementation("androidx.compose.ui:ui-tooling")

debugImplementation("androidx.compose.ui:ui-test-manifest")
```

---

# ❌ Removed (Add only if needed)

These libraries are NOT included but can be added if required:

Retrofit
OkHttp
Hilt
Ktor
Coil-Ktor
Fragment PDF Viewer
Version Catalog

---

# ✅ Minimal Setup (Ultra Fast)

If interviewer asks minimal dependencies:

```kotlin
implementation("androidx.core:core-ktx:1.17.0")

implementation("androidx.compose.material3:material3")

implementation("androidx.navigation3:navigation3-runtime:1.0.0")

implementation("androidx.pdf:pdf-compose:1.0.0-alpha12")

implementation("io.coil-kt.coil3:coil-compose:3.3.0")
```

---

# 🎯 Interview Tip

Most important dependencies interviewers expect:

* Compose
* ViewModel
* Navigation
* Room
* DI (Hilt or Koin)
* Coil / Glide
* Coroutines
* Serialization

---

# ✅ Ready for Production Apps

Supports:

* Modern Compose UI
* Clean Architecture
* MVVM
* Navigation 3
* PDF Viewer
* Offline storage
* Dependency Injection

---

**Copy → Paste → Run 🚀**
