# Android Installation & Quick-Start Guide

> **No Hardware Required for Evaluation:** You can install the APK and test Recall Chat, Persistent Memory Vault, Document/Image Analysis, and Google Drive synchronization immediately on any compatible Android phone without owning the ESP32-S3 wearable.

---

## System Requirements
- **OS:** Android 8.0 (API 26) or newer *(Android 10+ required for programmatic `WifiNetworkSpecifier` wearable pairing)*.
- **Internet Access:** Required for Gemini API calls and Google Drive synchronization.
- **Google Gemini API Key:** Obtain a free or paid key from [Google AI Studio](https://aistudio.google.com/apikey).

---

## Step 1: Download & Install the APK
1. Download **`SAGE-v1.0.0-android.apk`** from the [v1.0.0 GitHub Release](https://github.com/ByteBastion/SAGE-Product/releases/tag/v1.0.0).
2. Open the downloaded `.apk` file on your Android device.
3. When prompted, allow **Install unknown apps** for your browser or file manager, then tap **Install**.

---

## Step 2: Configure Your Gemini API Key (One-Time Setup)
Public builds of SAGE ship with **zero embedded API keys**.
1. Launch **SAGE**.
2. Tap the **You** tab (bottom-right) to open **Control Agent**.
3. Under **AI & Intelligence**, tap **Gemini API Key**.
4. Paste your Gemini API key and tap **Save & Verify Key**.
   - SAGE verifies the key against the Gemini API and encrypts it on-device using **Android Keystore (AES-256-GCM)**.
   - Your key persists across app restarts—you only need to enter it once.
   - You can update or remove the saved key at any time from the same screen.

---

## Step 3: Connect Google Drive *(Optional)*
1. In **Control Agent**, scroll to **Storage & Backup → Google Drive**.
2. Tap **Connect** and sign in with your Google account.
3. SAGE requests only least-privilege scopes (`drive.file` and `drive.appdata`) to manage `/SAGE/` folders and sync your Memory Vault across devices.

---

## Step 4: Test Capabilities Immediately (Without Hardware)
- Open the **Recall** tab and ask general questions, attach a PDF/DOCX/image to analyze, or tell SAGE preferences/project details to watch it automatically build your **Memory Vault** (inspectable under **Control Agent** / **Vault**).
- If you own a XIAO ESP32-S3 Sense flashed with SAGE firmware, follow the [Hardware Setup Guide](hardware-setup.md) to pair and capture live moments.

