# Changelog

All notable product releases and milestone updates for **SAGE — A Multimodal AI Memory System** are documented in this file.

## [v1.0.0] — 2026-11-18
### Added
- **Initial Public Android Release (`SAGE-v1.0.0-android.apk`):** Published without bundled secrets or `.env` assets.
- **Hardware-Backed API Key Management (Control Agent):** Added **AI & Intelligence → Gemini API Key** configuration sheet backed by Android Keystore (`AES-256-GCM`), supporting live validation, masked display, persistence across app restarts, updates, and deletion with zero key logging.
- **Four-Tab Flutter Application:** Memories library & details view (`human_memory` + `reconstruction_blueprint`), Capture dashboard (live viewfinder + recording controls), Recall Chat (voice STT + text + inline video evidence + attachment RAG), and Control Agent.
- **Wearable Edge Integration (ESP32-S3 Firmware v3.0.0):** Dual-core FreeRTOS capture (`HTTP :80` OV2640 VGA frames + `TCP :81` 16 kHz I2S PDM audio) over private SoftAP `SAGE-XIAO`.
- **Android Native Network Binding & Streaming AVI Muxer:** Kotlin `WifiNetworkSpecifier` + `bindProcessToNetwork()` + native socket proxy paired with Dart `MjpegRecorder` (`00dc`/`01wb` + `idx1` + post-hoc header calibration).
- **User-Owned Google Drive Synchronization:** Least-privilege `drive.file` and `drive.appdata` scopes, delete-after-confirmed-upload safety rule, and tombstone-aware cross-device Memory Vault merges.

