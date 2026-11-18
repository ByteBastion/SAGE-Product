# Implementation Overview

This document summarizes the engineering scope and verified subsystems built across **SAGE** without disclosing proprietary source code (`ByteBastion/SAGE-Core`).

## Engineering Footprint
- **Mobile Application (Flutter / Dart):** ~17,500+ lines of Dart across 33 feature-first modules (`core/models`, `core/services`, `core/providers`, `core/theme`, `core/widgets`, and `features/home`), backed by 29 integrated dependencies.
- **Android Native Layer (Kotlin):** ~760 lines in `MainActivity.kt` implementing `MethodChannel` / `EventChannel` bridges for `WifiNetworkSpecifier` binding, native `Network.openConnection()` HTTP transport, external storage management, and hardware-backed Android Keystore AES-256-GCM encryption.
- **Wearable Firmware (C++ / Arduino / FreeRTOS):** Modular PlatformIO codebase (`v3.0.0`) partitioning HTTP frame streaming (Core 1) and continuous I2S audio acquisition (Core 0) on the Seeed XIAO ESP32-S3 Sense.

## Core Engineering Subsystems
1. **Self-Healing Wearable Link:** 6-second `/health` polling with an 8-miss (`~48 s`) disconnect threshold and automatic socket client reset (`XiaoHttpClient.reset()`) when Android rebinds to `SAGE-XIAO`.
2. **Real-Time Client-Side AVI Muxer:** Streams variable-rate MJPEG frames and fixed-rate 16 kHz PCM samples directly to disk (`RandomAccessFile`) to stay well within Android mobile memory constraints while writing standard `idx1` indices.
3. **Resilient Multi-Model AI Client:** Implements a prioritized Gemini model fallback chain with retry/backoff on HTTP `429` and `503` responses, strict JSON fence stripping, and resilient fallback replies.
4. **Tombstone-Aware Multi-User Memory Vault:** Partitioned per authenticated Google Subject ID (`google_<accountId>`) so user data never leaks across accounts, with deletion tombstones preventing erased facts or sessions from being resurrected during Drive `appDataFolder` sync.
5. **Automated Verification:** 26 automated Flutter unit and integration tests covering attachment extraction, RAG context budgeting, tombstone cloud merges, Android Keystore key persistence/redaction, and live Gemini API round-trips.

