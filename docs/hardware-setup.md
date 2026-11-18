# Hardware Setup Guide (Seeed XIAO ESP32-S3 Sense)

> **Note:** Wearable hardware is **optional** for evaluating the SAGE Android application's AI Recall, Attachment RAG, Memory Vault, and Google Drive features. A GitHub release does **not** expose a physical ESP32 remotely over the internet—the wearable connects directly over short-range local Wi-Fi (`SAGE-XIAO`).

---

## Required Hardware Components
- **Seeed Studio XIAO ESP32-S3 Sense** (includes integrated OV2640 camera expansion board and PDM digital MEMS microphone, 8 MB PSRAM, 8 MB Flash).
- **2.4 GHz Wi-Fi U.FL Antenna** (included with the XIAO ESP32-S3 Sense—**must be attached** for stable Wi-Fi range and frame throughput).
- **USB-C Power Source** (portable USB power bank, smartphone OTG power, or 5V adapter).

---

## Pinout & Firmware Configuration Summary (`v3.0.0`)
- **Camera Interface:** Standard XIAO ESP32-S3 Sense OV2640 parallel pinout (`VGA 640×480`, `PIXFORMAT_JPEG`, double-buffered in PSRAM).
- **PDM Microphone (I2S):** `I2S_WS_PIN = GPIO 42` (CLK), `I2S_SD_PIN = GPIO 41` (DATA), `16 kHz`, 16-bit mono PCM with 8x digital gain and clipping protection.
- **Wireless Access Point:**
  - **SSID:** `SAGE-XIAO`
  - **Default Prototype Passphrase:** `sage1234`
  - **Gateway / Device IP:** `192.168.4.1`
  - **Endpoints:** HTTP `:80` (`/health`, `/status`, `/live_frame`) and raw audio TCP `:81`.

---

## Pairing the Wearable with the Android App
1. **Attach the antenna** to the XIAO ESP32-S3 Sense U.FL connector and power the unit via USB-C.
2. Wait ~2 seconds for `SAGE-XIAO` SoftAP initialization.
3. On your Android phone, ensure **Location Services (GPS)** and **Wi-Fi** are enabled (required by Android OS for `WifiNetworkSpecifier` scanning/pairing).
4. Open **SAGE → Capture** tab and tap **Connect**.
5. Approve the Android system prompt to join `SAGE-XIAO`.
6. Once the status indicator turns **Connected**, the live camera viewfinder appears and you can tap **Start Recording** to capture synchronized `.avi` memory sessions.

> **Using Mobile Data Simultaneously:** Android automatically keeps mobile data active for internet APIs when bound to an internet-less `WifiNetworkSpecifier` network, while SAGE pins local `192.168.4.1` HTTP/TCP traffic exclusively to the `SAGE-XIAO` interface.

