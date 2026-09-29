# Phase 2 — Wake Word + Overlay

## New in this phase

- Offline "Hey Jarvis" wake word (Vosk, no cloud)
- Microphone foreground service that keeps listening in the background
- Draggable floating push-to-talk button over other apps
- Auto-sleep after 2 minutes of silence
- Instant local acknowledgment before a task starts
- Persistent notification showing the current state

## Before you build

1. Download `vosk-model-small-en-us-0.15` from
   https://alphacephei.com/vosk/models
2. Unzip it.
3. Put the folder in `app/src/main/assets/vosk-model-small-en-us-0.15/`
   (loose files, not a zip).

Without the model folder the app will compile but the wake service will
fail to load and stop itself.

## First run after Phase 2

1. Open the app → paste API key → pick voice → Start.
2. Grant microphone permission.
3. Grant notification permission (Android 13+).
4. Grant "Display over other apps" permission when prompted.
5. The floating button appears.
6. Say "Hey Jarvis" — the notification changes to "Listening…".
7. Or hold the floating button anywhere and talk.

## Permissions used

- RECORD_AUDIO — wake word + live voice
- FOREGROUND_SERVICE + FOREGROUND_SERVICE_MICROPHONE — background mic
- POST_NOTIFICATIONS — foreground service notification (Android 13+)
- SYSTEM_ALERT_WINDOW — floating push-to-talk button
- RECEIVE_BOOT_COMPLETED — reserved for Phase 9

## What still does not exist

- Memory (Phase 3)
- Device Owner provisioning (Phase 4)
- Accessibility automation (Phase 5)
- Vision (Phase 6)
- Web search / weather / news (Phase 7)
- Reminders / proactive (Phase 8)
- Remote dashboard (Phase 9)
- Plugin system (Phase 10)
- Full nine-model ladder (Phase 11)