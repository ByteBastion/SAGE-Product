# Privacy & Security Architecture

## Trust Boundaries & Threat Model

| Asset / Flow | Threat | Mitigation in SAGE v1.0.0 |
| :--- | :--- | :--- |
| **Gemini API Key** | Extraction from public APK (`flutter_assets/.env`) or log leakage | `.env` is excluded from `pubspec.yaml` and public repos. User-entered keys are encrypted via Android Keystore (`AES-256-GCM`), transmitted via `x-goog-api-key` headers, and scrubbed by `ApiKeyService.redact()`. |
| **Google Drive Access** | Over-privileged app reading unrelated user Drive files | Restricted to `drive.file` (files created by SAGE) and `drive.appdata` (hidden app vault folder). |
| **Multi-Account Isolation** | Mixing memories between different signed-in Google users | `UserIdentityService` keys local vault directories (`/sage_memory/<google_id>/vault.json`) by immutable Google Account ID; tombstone lists prevent deleted items from resurfacing on merge. |
| **Wearable Wi-Fi Traffic** | Cellular interception or accidental upload to external servers during capture | Capture runs solely over direct `SAGE-XIAO` local SoftAP bound via `WifiNetworkSpecifier`. Nothing reaches the internet until the phone initiates enrichment/upload. |
| **Temp Recording Integrity** | Loss of video clips on upload failure or crash | `ProcessingService` retains local `.avi` files in `/Download/SAGE` unless `uploadMemoryToDrive()` explicitly returns `true`. |

See [PRIVACY.md](../PRIVACY.md) and [SECURITY.md](../SECURITY.md) for policy terms and disclosure channels.

