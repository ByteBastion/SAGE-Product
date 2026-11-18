# Key Engineering Decisions

Every technology choice in SAGE addresses a specific embedded, mobile, or multimodal constraint:

| Decision | Chosen Approach | Why Alternatives Were Rejected |
| :--- | :--- | :--- |
| **On-Device Capture vs. Cloud Streaming** | Local Wi-Fi SoftAP (`SAGE-XIAO`) + asynchronous phone upload | Streaming video continuously over cellular/BLE drains wearable battery quickly and fails offline. |
| **Client-Side RIFF/AVI Muxing vs. On-Chip MP4** | Stream raw JPEG (`:80`) + PCM (`:81`) to Android and mux `MjpegRecorder` with `idx1` + header rewrite | ESP32-S3 lacks hardware H.264/AAC encoders and 8 MB PSRAM fragments under on-chip container muxing; post-hoc header rewrite eliminates A/V drift (`<40 ms`). |
| **Native Kotlin Socket Proxy vs. Pure Dart HTTP** | `MainActivity.kt` `bindProcessToNetwork()` + `Network.openConnection()` | Android silently routes `dart:io` sockets over cellular when Wi-Fi has no internet; native `Network.openConnection()` guarantees traffic reaches `192.168.4.1`. |
| **Dual-Representation Prompting vs. Raw Transcripts** | Single Gemini File API JSON call generating `human_memory` + `reconstruction_blueprint` | Transcripts alone lose visual context, off-camera sounds, and spatial details; dual output serves both accessibility readers and structured search. |
| **User-Owned Google Drive vs. Central Backend DB** | OAuth 2.0 (`drive.file` + `drive.appdata`) directly from phone | Gives users full data ownership and zero-vendor cloud lock-in without operating expensive video storage infrastructure. |
| **BYOK Android Keystore vs. Bundled `.env` Key** | User enters personal key in Control Agent, encrypted via Android Keystore (`AES-256-GCM`) | Embedding a developer API key inside a public `.apk` allows trivial extraction via unzipping; Keystore keeps user keys hardware-backed and secret-free in releases. |
| **Transactional Delete-After-Confirm** | Keep `.avi` in `/Download/SAGE` until Drive confirms upload | Prevents silent memory loss when cellular or Wi-Fi connections drop mid-upload. |

