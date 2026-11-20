# SAGE Releases

Compiled Android APK binaries are distributed exclusively via **GitHub Releases** (never committed directly to the Git history).

## Latest Release

| Version | Asset | Status | Notes |
| :--- | :--- | :---: | :--- |
| **[v1.0.1](https://github.com/ByteBastion/SAGE-Product/releases/tag/v1.0.1)** | [`SAGE-v1.0.1-android.apk`](https://github.com/ByteBastion/SAGE-Product/releases/download/v1.0.1/SAGE-v1.0.1-android.apk) | **Latest** | Release (`61.2 MB`) with AI-generated visual card thumbnails grounded in recorded scenes, permanent Google Drive memory alignment, 2-year calendar navigation across all previous months, active Gemini model routing, and post-hoc AVI muxer stability. |
| **[v1.0.0](https://github.com/ByteBastion/SAGE-Product/releases/tag/v1.0.0)** | [`SAGE-v1.0.0-android.apk`](https://github.com/ByteBastion/SAGE-Product/releases/download/v1.0.0/SAGE-v1.0.0-android.apk) | Previous | Initial public Android release (`94.3 MB`) built with Dart symbol obfuscation, Android R8 minification, BYOK Android Keystore API key settings, dual-representation Gemini enrichment, Hybrid RAG, Google Drive sync, and XIAO ESP32-S3 capture support. |

## Verification & Setup
- **APK SHA-256 (v1.0.1):** `DAC26EA81DE7DA0B1A8C48371EF86AE5AD9C1D2FEA7B5C21667694B16EB0E5D3`
- **APK SHA-256 (v1.0.0):** `C6A8630137E0116D3E184C07FF46FE2DAB868620168A6EB4FD157D86FD2F6E77`
- Requires **Android 8.0+** (API 26+ recommended; Android 10+ for programmatic `WifiNetworkSpecifier` binding).
- No Gemini API keys are bundled in the release APK. Configure your personal key in **Control Agent → Gemini API Key** after installation.
- See the [Android Installation Guide](../docs/android-installation.md) for full walkthrough instructions.

