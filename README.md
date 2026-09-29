# Mark Assistant — Phase 1

An Android AI assistant built on the Gemini Live API, inspired by Mark LV.
Phase 1 covers: first-run setup, secure key storage, real-time voice,
avatar with lip-sync, push-to-talk, model ladder, cloud APK build.

## Get the APK via GitHub Actions (no PC needed)

1. Create a free GitHub account.
2. Create a new **empty** repository, e.g. `mark-assistant`.
3. Upload this entire project. On phone-only: open the repo in the
   GitHub web UI, tap **Add file → Upload files**, and upload the
   folder contents. Keep the folder structure.
4. Push/commit. GitHub Actions runs automatically.
5. Go to **Actions** tab → open the latest **Build APK** run.
6. Scroll to **Artifacts** → download `mark-assistant-debug.zip`.
7. Unzip on your phone → you get `app-debug.apk`.
8. Tap the APK to install. You may need to enable
   **Install unknown apps** for your file manager.

If Actions does not run on its own: **Actions → Build APK → Run workflow**.

## First run on your phone

1. Open the app.
2. Paste your Gemini API key (from https://aistudio.google.com/apikey).
3. Pick a voice.
4. Grant microphone permission when asked.
5. Hold the big button and speak. Release to send. Mark answers.

## Phase 1 status

Working now:
- First-run setup + secure storage (Keystore + EncryptedSharedPreferences)
- Gemini Live API real-time voice (WebSocket, PCM in/out)
- Model ladder with cooldown on failure
- Software-rendered avatar with lip-sync from audio RMS
- Push-to-talk (in-app button)
- Reactive amplitude bar

Coming next phases:
- Global wake word ("Hey Jarvis") via local Vosk/Porcupine
- Overlay push-to-talk (Ctrl+Space equivalent) with SYSTEM_ALERT_WINDOW
- Persistent memory (Room) + memory panel + on-demand lookup
- Device Owner provisioning (ADB once) and admin controls
- AccessibilityService for UI automation, message sending, browser
- MediaProjection screen vision + CameraX webcam
- Web search, weather, news, morning briefing
- Reminders via AlarmManager / WorkManager
- Model ladder expansion to all nine and health metrics
- Remote dashboard via QR pairing
- Auto-start on boot
- Theming from hue wheel
- Session continuity across disconnects
- Plugin system (Kotlin files under plugins/)

## Troubleshooting

- **Gradle fails on first push:** check that `.github/workflows/build.yml`
  is at the repo root and the path is `.github/workflows/build.yml`.
- **APK install blocked:** Settings → Apps → Special access → Install
  unknown apps → allow your file manager / browser.
- **No audio:** confirm mic permission and that the API key is valid.
  Check the `lastText` field on the HUD for the error message.
- **"Connection error":** the model might be unavailable. The ladder
  will move on automatically once you press the button again.