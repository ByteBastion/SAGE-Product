# Privacy Policy & Data Custody Architecture — SAGE

**Last Updated:** November 18, 2026

SAGE is designed around **user-owned storage** and **explicit user control**. No developer-operated central database stores your recorded videos, voice queries, or personal memory vaults.

## 1. What Data Is Processed
- **Wearable Capture Sessions (Optional Hardware):** Video frames (`640×480` JPEG) and mono audio (`16 kHz` PCM) captured strictly while you initiate a recording session with your paired XIAO ESP32-S3 Sense device.
- **Memory Vault & Chat Context:** User-confirmed profile preferences, active project notes, conversation summaries, and uploaded chat attachments (images, PDFs, DOCX, code/text files).
- **Gemini API Key:** Entered voluntarily by you in Control Agent to access the Google Gemini API directly from your device.

## 2. Where Your Data Lives
1. **Wearable Unit:** Buffers only live streaming frames in volatile memory; no footage is uploaded directly by the wearable to the internet.
2. **Your Android Device:** Temporary `.avi` clips are cached in `/Download/SAGE` until processed. Your personal Memory Vault (`vault.json`) and attachments reside in your app's user-partitioned local directory, and your Gemini API key is encrypted inside Android Keystore (`AES-256-GCM`).
3. **Your Google Drive Account:** When connected, recorded `.avi` files and structured AI JSON summaries are uploaded directly to `/SAGE/YYYY-MM-DD/` in your own Google Drive (`drive.file` scope), and cross-device Memory Vault backups are stored in your private hidden `appDataFolder` (`drive.appdata` scope).

## 3. Third-Party AI Processing
- Video clips (during enrichment), Recall queries, and selected chat context/attachments are transmitted directly over HTTPS to Google's Gemini API (`generativelanguage.googleapis.com`) using your own API key via the `x-goog-api-key` header.
- Please review [Google's Gemini API Terms](https://ai.google.dev/gemini-api/terms) regarding how Google handles API requests under your API key tier.

## 4. Deletion & Right to Be Forgotten
- **Temporary Clips:** Deleted automatically from local device storage **only after** Google Drive confirms a successful upload.
- **API Key:** Can be permanently deleted at any time via **Control Agent → Gemini API Key → Remove Saved Key**.
- **Memory Vault:** Can be purged completely inside **Control Agent → Memory Vault → Clear All Saved Memory**, and cloud backups can be deleted directly from your Google Drive.

## 5. Known Privacy Limitations (Current v1.0.0)
- Local `vault.json` and `SharedPreferences` video summaries rely on Android app-sandbox isolation and are not yet wrapped in an additional database encryption layer (SQLCipher/SQLite migration planned).
- Automated on-device face-blurring for non-consenting bystanders is a planned Phase 2 feature; users are responsible for recording consent in accordance with local laws.

