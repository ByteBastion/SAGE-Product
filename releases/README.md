# SAGE Releases

Compiled Android APK binaries are distributed exclusively via **GitHub Releases** (never committed directly to the Git history).

## Latest Release

| Version | Asset | Status | Notes |
| :--- | :--- | :---: | :--- |
| **[v1.0.0](https://github.com/ByteBastion/SAGE-Product/releases/tag/v1.0.0)** | [`SAGE-v1.0.0-android.apk`](https://github.com/ByteBastion/SAGE-Product/releases/download/v1.0.0/SAGE-v1.0.0-android.apk) | **Latest** | Initial public Android release with BYOK Android Keystore API key settings, dual-representation Gemini enrichment, Hybrid RAG, Google Drive sync, and XIAO ESP32-S3 capture support. |

## Verification & Setup
- Requires **Android 8.0+** (API 26+ recommended; Android 10+ for programmatic `WifiNetworkSpecifier` binding).
- No Gemini API keys are bundled in the release APK. Configure your personal key in **Control Agent → Gemini API Key** after installation.
- See the [Android Installation Guide](../docs/android-installation.md) for full walkthrough instructions.

