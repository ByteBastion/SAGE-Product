# Security Policy

## Architectural Security Controls in SAGE v1.0.0
1. **Zero Embedded Secrets in Public Releases:** No `.env` files, Gemini API keys, Google OAuth `client_secret` tokens, or private signing keystores are bundled inside `SAGE-v1.0.0-android.apk` or committed to public repositories.
2. **Hardware-Backed API Key Storage:** User-entered Gemini API keys are encrypted via Android Keystore (`AES/GCM/NoPadding`, 256-bit key alias) and stored in private app `SharedPreferences`.
3. **Header-Based API Authentication & Log Redaction:** Gemini API calls authenticate via the `x-goog-api-key` HTTP header rather than URL query parameters, and exception/debug formatters sanitize keys before emitting diagnostics.
4. **Least-Privilege Google Drive OAuth Scopes:** SAGE requests only `drive.file` (access restricted to files/folders created by SAGE) and `drive.appdata` (private hidden app data folder)—never full-drive read/write access.
5. **Process-Bound Wearable Networking:** Android `WifiNetworkSpecifier` + `ConnectivityManager.bindProcessToNetwork()` isolates local HTTP/TCP communication (`192.168.4.1`) to the `SAGE-XIAO` wireless link without leaking local frames over cellular interfaces.

## Known Security & Prototype Constraints
- **Prototype Wearable SoftAP Credentials:** The local `SAGE-XIAO` SoftAP uses a default prototype WPA2 passphrase (`sage1234`) over short-range 2.4 GHz Wi-Fi. Users should power off the wearable when not actively recording.
- **Cleartext Local HTTP to `192.168.4.1`:** `usesCleartextTraffic="true"` is currently enabled in the Android manifest to communicate with the microcontroller's local HTTP server (`http://192.168.4.1`). Scoped `network_security_config.xml` restricting cleartext exclusively to `192.168.4.1` is scheduled for the next hardening release.
- **Direct Client-to-Gemini Requests:** Until a multi-tenant backend proxy is deployed, the Android client communicates directly with Gemini using the user's encrypted on-device key.

## Reporting a Vulnerability
If you discover a security issue in `SAGE-Product` or `SAGE-v1.0.0-android.apk`, please **do not** disclose it in a public GitHub issue. Open a private GitHub Security Advisory on `ByteBastion/SAGE-Product` or contact the maintainer directly via [ByteBastion](https://github.com/ByteBastion).

