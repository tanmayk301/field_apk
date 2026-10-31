# Field Force Connect — Native Android APK Build Guide (`com.fieldforce.connect`)

This package contains the **complete Native Android (Flutter) source project** and **automated GitHub Actions Cloud APK Compiler** for **Field Force Connect**.

---

## Option 1: 1-Click Free Cloud APK Build via GitHub (No Android Studio Needed — Takes ~2 Minutes)

Because Android OS requires `.apk` binaries to be compiled by the official Android Gradle / SDK toolchain and cryptographically signed (V1+V2 JAR/APK signature), this package includes a pre-configured GitHub Actions cloud compiler (`.github/workflows/build-android-apk.yml`).

### Steps:
1. Create a free repository on [github.com/new](https://github.com/new) (e.g., `field-force-connect-apk`).
2. Extract this ZIP file (`Field-Force-Connect-Android-Source.zip`) and upload its contents (`mobile_app/` and `.github/`) to your GitHub repository.
3. Click the **Actions** tab in your GitHub repository:
   - GitHub Actions will automatically spin up an Ubuntu runner with **Java 17 + Android SDK + Flutter**, compile the native Android project, sign `Field-Force-Connect.apk`, and publish it under **Releases** (`latest-apk`) as well as **Workflow Artifacts**.
4. Download **`Field-Force-Connect.apk`** from the **Releases** section directly onto your Android phone and install it!

---

## Option 2: Local Build on Your PC / Laptop (Flutter CLI / Android Studio)

If you have Flutter SDK and Android Studio installed on your computer:

```bash
cd mobile_app
flutter create . --project-name field_force_connect --org com.fieldforce --platforms android
flutter pub get
flutter build apk --release
```

Your signed native Android APK will be generated at:
`mobile_app/build/app/outputs/flutter-apk/app-release.apk`

---

## Pre-Configured Backend Connection

- **Package ID**: `com.fieldforce.connect`
- **Google Sheet ID**: `1HJXVPi8bs1pbaibq5_AdP04mbwngTouv`
- **Apps Script Web App URL**: `https://script.google.com/macros/s/AKfycby6cWKwVXVOdTZd9Nr561X7_nF9NXEr3vVi3bn3KVn5dfPw6lslfZdcT_xH8TjuWgrB/exec`
- **Included Features**:
  - Explicit **Start Activity** button (locks GPS & start timestamp) and **Complete & Finish Activity** button.
  - Automatic routing to separate Google Sheet tabs (`Distributor_Visits`, `Retailer_Visits`, `Farmer_Visits`, `Product_Demonstrations`, `Farmer_Meetings`, `Field_Days`).
  - Native Camera photo capture with automatic upload to Google Drive (`Photo_URLs` column).
  - Order Booking with `Unit_Price`, `Order_Value`, and live Dispatch Tracking (`Transporter_Name`, `Tracking_Number`).
