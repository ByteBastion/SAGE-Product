# Product Overview — SAGE

**SAGE (Smriti Adaptive Guardian Engine)** is a multimodal personal memory assistant built to bridge continuous edge sensing with conversational recall.

## Who SAGE Is Built For
1. **Cognitive Accessibility & Memory Support:** Provides individuals experiencing memory challenges with a calm, chronological, plain-language narrative (`human_memory`) and immediate video playback of their day.
2. **Students & Researchers:** Captures lectures and lab demos via a lightweight wearable and lets students query details later (e.g., *"What did the lecturer explain in the third session?"*).
3. **Engineers & Everyday Users:** Tracks misplaced items, meeting commitments, and project notes—combining recorded video memory with persistent project/document RAG inside a single app.

## Four-Tab Application Experience

| Tab | Primary Purpose | What Works Without Wearable? |
| :--- | :--- | :--- |
| **Memories** | Browse chronological captured memories, play synchronized `.avi` recordings in-app via `media_kit`, inspect transcripts, and read both **Human Memory** and **Reconstruction Blueprint** views. | Yes (plays previously synced Drive memories) |
| **Capture** | Discover and bind directly to the `SAGE-XIAO` wearable AP, inspect the live `640×480` MJPEG viewfinder, and start/stop synchronized recording sessions. | Requires `SAGE-XIAO` wearable |
| **Recall** | Conversational AI chat powered by Gemini + Hybrid RAG across video memories, persistent profile/project vaults, and attached images/PDFs/DOCX/code files. Supports voice input via `speech_to_text`. | **Yes (100% standalone)** |
| **You (Control Agent)** | Configure your Gemini API key (encrypted via Android Keystore), link/switch your Google Drive account, inspect `Uploaded` vs. `Pending` counts, trigger manual sync, and manage the **Personal Memory Vault**. | **Yes (100% standalone)** |

