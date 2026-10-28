# My AI Agent - Personal AI Assistant (Android / Flutter)

**My AI Agent** is a production-grade personal AI assistant for Android built with Flutter and Dart, backed by a high-performance Node.js / Express backend powered by Google Gemini.

## Highlights
- 🇮🇳 **Deep Multilingual Support**: First-class Hindi (हिंदी), Hinglish, and English support.
- 🎙️ **Voice Conversation Mode**: Real-time speech-to-text dictation and speech-synthesis audio response.
- 💬 **Smart AI Chat**: Powered by `gemini-3.8-flash` with full Markdown, code snippets, syntax styling, copy & share.
- 🎨 **AI Image Generation**: Integrated `gemini-3.1-flash-lite-image` with aspect ratio controls (1:1, 16:9, 9:16).
- 🗄️ **Persistent Chat History**: Complete conversation management (create, search, rename, delete).
- ⚙️ **Comprehensive Settings**: Light/Dark theme, language selector, TTS speech rate, model picker, quota monitoring.
- 📱 **Native Android Architecture**: Package `com.myaiagent.app`, Material 3 design, edge-to-edge layout, and target SDK 34.

## Project Structure
```
flutter_app/
├── android/                   # Native Android wrapper & Gradle scripts
│   ├── app/
│   │   ├── build.gradle       # com.myaiagent.app, SDK 34, Keystore configs
│   │   └── src/main/
│   │       └── AndroidManifest.xml # Permissions (RECORD_AUDIO, INTERNET, etc.)
├── lib/
│   ├── config/                # AppTheme, Colors, FirebaseOptions
│   ├── models/                # Message, Conversation, UserProfile
│   ├── services/              # ApiService, SpeechService, AuthService
│   ├── screens/               # Splash, Onboarding, Chat, Voice, Image, Settings
│   └── main.dart              # Main Flutter application entry point
├── pubspec.yaml               # Flutter dependencies
└── BUILD_APK.md               # Complete APK build & install guide
```
