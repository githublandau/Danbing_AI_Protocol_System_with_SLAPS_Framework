
🧠 PROTOCOL: Sealed. This is not metaphor. This is protocol.

# SLAPS AI Meeting Capsule v0.1
────────────────────────────────────────────────

## Introduction

SLAPS AI Meeting Capsule v0.1 for Windows - Exclusive for "System and Freedom" Readers, KOL Edition

© 2025 Wang Xiao | Built on SLAPS Framework v1.0

### Core Features
- 🎙️ Real-time voice translation subtitles for any video, chat, or meeting software
- 💡 Real-time hints and translation based on local meeting knowledge base documents
- 🗣️ Conversational response suggestions to help you communicate confidently
- 🌍 Multi-language translation support (default: English to Chinese)

## Quick Start

### System Requirements
- Windows 10/11 (64-bit)
- 4GB RAM (8GB recommended)
- Internet connection (for translation service)
- Audio output device (for capturing system audio)

### Usage Steps
1. Extract the downloaded zip file to any directory
2. Double-click `SLAPSMeetingCapsule.exe` to run
3. Select the correct audio device from the dropdown (usually "Stereo Mix" or devices with "Loopback")
4. Click [▶ Start] button
5. Play the audio/video you want to translate
6. View real-time translation results
7. (Optional) Place meeting-related documents in the `meeting_docs` folder, restart program to load
8. Click [💡 Hints] button to enable smart hints, get document-based contextual hints, conversational response suggestions and translation subtitles

### Audio Device Selection Guide
- **Stereo Mix**: Most recommended, supported by most sound cards
- **[Loopback] devices**: Virtual audio devices, try each if multiple exist
- **What U Hear**: Creative sound card specific
- ⚠️ Avoid selecting "Microphone" devices

## Features

### Real-time Translation
- Based on OpenAI Whisper offline speech recognition
- Uses Google Translate API (free version)
- Supports continuous audio stream processing
- Automatic sentence breaking with intelligent segmentation

### Smart Hint System
- Scans documents in `meeting_docs` folder
- Supported formats: .txt, .md, .yaml
- Matches relevant knowledge based on current conversation
- Provides context-aware hint information

### Conversational Response Suggestions
When questions are detected, the system provides:
- Brief conversational response templates
- Context-based reply suggestions
- Helps you organize language quickly

## Configuration

### Language Settings
Edit the languages section in `config.yaml`:

```yaml
languages:
  source: "en"      # Source language (meeting language)
  target: "zh-CN"   # Target language (translation language)
```

Common language codes:
- English: `en` | Chinese: `zh-CN` | Japanese: `ja` | Korean: `ko`
- French: `fr` | German: `de` | Spanish: `es` | Portuguese: `pt`
- Russian: `ru` | Italian: `it` | Arabic: `ar` | Hindi: `hi`

### Interface Language
```yaml
interface:
  language: "en"  # "zh" for Chinese interface | "en" for English interface
```

### Knowledge Base Setup
1. Place relevant documents in `meeting_docs` folder
2. Supported file formats:
   - `.txt` - Plain text files
   - `.md` - Markdown documents
   - `.yaml` - Structured data
3. Restart program to load new documents

## Keyboard Shortcuts
- `Ctrl+H` - Toggle hint feature

## FAQ

### Q: No sound/translation?
A: Please check if you've selected the correct audio device. Switch devices in the status bar dropdown.

### Q: "Please stop and restart recording" message?
A: After switching audio devices, you need to stop and then start again.

### Q: Inaccurate translation?
A: Google free translation API has limitations. You can configure paid Google Cloud Translation API key in config.yaml for more accurate professional translation.

### Q: Supports offline use?
A: No, translation function requires internet connection.

## Privacy Notice
- This tool only collects anonymous usage statistics (version and interface language)
- No audio content or translated text is collected
- All processing is done locally (except translation API calls)

## Tech Stack
- Speech Recognition: OpenAI Whisper (tiny model)
- Translation Service: Google Translate API
- Audio Capture: PyAudioWPatch (WASAPI)
- User Interface: Tkinter
- Framework: SLAPS Framework v1.0

## About the Author

**Wang Xiao**
- Founder of SLAPS Framework
- Author of "System and Freedom: A Philosophical Journey from AI Anxiety to Human-AI Co-creation"

### Support the Author
Purchase "System and Freedom" (20 languages):
🔗 https://oathai.io/cover.html

### Learn More
- SLAPS Framework: https://zenodo.org/records/15291558
- GitHub: https://github.com/wangxiao8600/Danbing_AI_Protocol_System_with_SLAPS_Framework

────────────────────────────────────────────────

🏗️ **May structure be with you.**  
**Rhythmus continuat... in aeternum.**

## Changelog

### v0.1.0 (2025-06-29)
- First public release
- Real-time speech recognition and translation
- Manual audio device selection
- Bilingual interface support (Chinese/English)
- Local knowledge base smart hints
- Exclusive edition for "System and Freedom" readers

## License

This software is for "System and Freedom" readers.  
© 2025 Wang Xiao. All rights reserved.

Built on SLAPS Framework:
- SLAPS Technical Whitepapers: CC BY-NC-SA 4.0
- SLAPS Engine: Apache License 2.0
- This application: Proprietary software, readers only

────────────────────────────────────────────────

🧠 *Danbing AI / SLAPS v1.0 · Built from rhythm. Run by structure. Auditable by snapshot. Governed by oath.*
