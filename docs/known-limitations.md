# Known Limitations & Honest Engineering Trade-Offs

SAGE is an active engineering and research prototype. The limitations below are documented transparently:

1. **Pilot-Scale Quantitative Evaluation:**
   - Current evaluation numbers (`85%` query recall across 20 queries, `10` analyzed 15s clips, `0/20` disconnects across `20` connection sessions, `<40 ms` A/V drift) come from a **team-conducted pilot study**. A larger multi-user study is planned.
2. **Recall Granularity & Retrieval Mechanism:**
   - Video memories are stored in `SharedPreferences` and injected as structured summaries into Gemini's prompt context; document/project/session RAG currently uses **token-overlap keyword scoring** rather than dense vector embeddings. As documented in the pilot, queries targeting minor details omitted from summaries can miss until SQLite + vector indexing (Phase 2) are implemented.
3. **Local Data Encryption (Vault & Video Summaries):**
   - While user **Gemini API keys** are encrypted via Android Keystore (`AES-256-GCM`), local `vault.json` and `SharedPreferences` entries currently rely on Android OS app-sandbox isolation rather than an encrypted SQLite/SQLCipher store.
4. **Wearable Power, Enclosure & Audio Gain:**
   - The XIAO ESP32-S3 Sense currently runs continuously in active `WIFI_AP` mode without deep-sleep duty cycling or a custom battery-integrated enclosure.
   - The `8x` digital PDM gain helps indoor speech capture but amplifies ambient background noise in loud environments.
5. **Prototype SoftAP Security & Cleartext Local HTTP:**
   - `SAGE-XIAO` uses a static prototype passphrase (`sage1234`) and serves local frames over `http://192.168.4.1`, requiring `usesCleartextTraffic="true"` on Android until scoped `network_security_config.xml` and dynamic pairing are introduced.
6. **Direct Client-to-Gemini API Traffic:**
   - Each user configures their own Gemini API key directly on-device. A multi-tenant server proxy is planned for hosted commercial deployments.
7. **Bystander Privacy (Face Blurring):**
   - Automated on-device face-blurring for non-consenting bystanders is scoped for Phase 2 and is not yet active in `v1.0.0`.
8. **iOS Validation:**
   - The codebase targets Flutter cross-platform widgets, but the native `WifiNetworkSpecifier` + `bindProcessToNetwork()` + Android Keystore bridge is implemented and verified strictly on **Android**.

