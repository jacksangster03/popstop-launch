# App Plan — POPSTOP

## 1. App Overview

POPSTOP is a cross-platform mobile app for people who keep turning microwave popcorn into charcoal. During cooking, the app uses the phone microphone to detect the timing between pops and estimate when the user should stop the microwave. It gives a loud visual, audio, and vibration alert; it does not control the microwave. V1 focuses on one job: start listening, detect the slowdown, and tell the user to stop.

Technical assumptions for this plan: Codex will build the app with React Native, Expo, and TypeScript for iOS and Android. Audio analysis runs on-device, no account is required, and raw microphone audio is neither saved nor uploaded.

## 2. Key Components

- First-run onboarding that explains the product, safe use, phone placement, and on-device audio processing.
- Microphone permission request with clear fallback instructions when permission is denied.
- Listening session controller with start, cancel, elapsed-time, and active-state controls.
- Real-time audio input module that extracts signal features without retaining recordings.
- Pop detector that separates likely pops from steady microwave noise.
- Stop estimator based on the recent intervals between detected pops, with configurable thresholds for testing.
- Three-part stop alert: full-screen message, sound, and vibration.
- “Couldn’t hear enough pops” state instead of pretending the result is reliable.
- Local settings for sound, vibration, permission status, safety acknowledgment, and optional diagnostics.
- Privacy and safety screens available without starting a session.

Helpful additions that remain small enough for v1:

- A pre-session microphone check.
- A visible confidence indicator using plain labels: “Listening,” “Hearing pops,” or “Too noisy.”
- Local, anonymous session diagnostics containing event timestamps and outcomes, never raw audio.

## 3. App Structure

- **Welcome:** states the benefit and starts onboarding.
- **How It Works:** explains phone placement, microphone use, and user responsibility.
- **Permission:** requests microphone access and explains how to restore denied access.
- **Ready:** primary home screen with one “Start Listening” action.
- **Listening:** shows elapsed time, detected activity, status, and cancel control.
- **Stop Now:** interrupts the listening view with the stop alert.
- **Session Result:** lets the user mark the alert as too early, right, or too late.
- **Settings:** controls sound, vibration, privacy details, safety guidance, and diagnostics.

Navigation flow: first launch moves from Welcome → How It Works → Permission → Ready. Later launches open Ready. Starting a session moves Ready → Listening. A reliable stop estimate triggers Stop Now → Session Result. Cancellation returns to Ready. Weak or unusable audio opens an explanation and returns to Ready. Settings is reachable from Ready and Session Result.

## 4. User Interface

**Welcome:** cream background, oversized black headline, red accent, short two-line explanation, CSS-style popcorn artwork, and a fixed yellow “Show Me How” button.

**How It Works:** three vertically stacked cards: place phone safely nearby, start the microwave and app, stop when alerted. Include a safety note that the user must stay nearby and operate the microwave.

**Permission:** microphone illustration, one-paragraph privacy explanation, “Allow Microphone” button, and secondary “Not Now” action. If denied, replace the main action with “Open Settings.”

**Ready:** compact POPSTOP logo at top, settings icon, large central popcorn graphic, one sentence of placement guidance, and a dominant circular “Start Listening” button. Show “Audio stays on this phone” below it.

**Listening:** prevent screen sleep. Show an animated waveform, elapsed time, current state label, detected-pop pulse, and a large outlined “Cancel” button. Keep information readable from several feet away.

**Stop Now:** red full-screen takeover with “STOP THE MICROWAVE” in high-contrast type, repeating vibration, repeating alert sound, and one large “I Stopped It” button. Do not dismiss automatically.

**Session Result:** three large feedback buttons: “Too Early,” “Good Call,” and “Too Late.” State that feedback is stored only on the device.

**Settings:** grouped rows for alert sound, vibration, replay onboarding, privacy, safety, diagnostics export/delete, and app version.

## 5. Backend Requirements

V1 does not require a backend. On-device processing reduces latency, works without internet, and avoids uploading household audio.

Store the following locally:

- `onboardingComplete`: boolean
- `safetyAcknowledgedAt`: ISO timestamp
- `alertSoundEnabled`: boolean
- `vibrationEnabled`: boolean
- `diagnosticsEnabled`: boolean
- Session records: generated ID, start/end timestamps, detected-pop timestamps, stop-trigger timestamp, noise-quality label, cancellation/error code, and optional user rating

Never store raw audio. Provide a “Delete Local Data” action. If diagnostics export is enabled, generate a JSON file only after a deliberate user action.

## 6. APIs and Libraries

- **React Native + TypeScript:** shared iOS and Android interface and application logic.
- **Expo development build:** project setup, native builds, permissions, haptics, audio playback, screen-awake behavior, and app configuration.
- **Native audio input bridge:** access low-latency microphone sample buffers needed for real-time signal analysis. Confirm the selected Expo-compatible module with a short technical spike before building the full interface.
- **React Navigation:** typed screen flow and modal presentation.
- **AsyncStorage:** settings and small session records.
- **Jest + React Native Testing Library:** logic and component tests.

No cloud AI API is needed for v1. The initial detector should use explainable signal rules and interval analysis so thresholds can be tested and adjusted.

## 7. Testing Strategy

Unit-test pop-event classification, interval calculations, stop thresholds, low-confidence outcomes, session state transitions, and local-data deletion. Component tests cover permission states, disabled start actions, cancel confirmation, persistent Stop Now alert, and accessibility labels.

Integration tests must verify microphone permission → listening → simulated pop stream → stop alert, plus denied permission, interruption by a phone call, backgrounding, audio-device changes, and no-audio conditions.

User acceptance scenarios:

- A first-time user understands placement and starts a session in under 45 seconds.
- The app never starts listening before microphone permission is granted.
- A known test recording triggers the expected state changes within agreed tolerances.
- Continuous microwave hum without pops does not trigger a confident stop alert.
- The stop alert is visible, audible, and vibrating when those settings are enabled.
- Canceling ends microphone use immediately.
- No raw audio file exists after a completed or canceled session.
- iOS and Android layouts remain usable at large text sizes.

Real-world validation must cover multiple microwave models, popcorn brands, phone distances, kitchens, and background-noise conditions before public performance claims are made.

## 8. Platform-Specific Considerations

Codex should work in small, reviewable slices: scaffold, permissions, audio spike, detector tests, session state machine, interface, alerts, then device validation. Keep detector logic independent from React components so recorded sample data can test it without running the full app.

Use Expo development builds rather than assuming the standard preview client exposes the required real-time audio data. Place native-platform changes behind one typed audio-service interface. Document all run, test, build, and device-permission commands in the repository README.

Match the launch page with cream, yellow, red, pink, near-black, heavy borders, offset shadows, and bold typography. Respect reduced-motion settings, maintain WCAG AA contrast, use 48×48-point minimum touch targets, and keep safety controls visually stronger than decorative elements.

## 9. Out of Scope for v1

- Automatic microwave control or smart-microwave integration
- User accounts, cloud sync, or social features
- Raw audio recording or cloud audio processing
- Personalized machine-learning models
- Popcorn purchasing, subscriptions, or delivery
- Session leaderboards, streaks, or achievements
- Apple Watch, Wear OS, smart-speaker, or desktop apps
- Guaranteed doneness, safety, or burn prevention
- Localization beyond English

## 10. Definition of Done

- A new user can install the app, understand safe placement, grant permission, and begin listening.
- The app processes microphone input locally and stores no raw audio.
- Tested pop sequences move the app through listening, detected-pop, slowdown, and stop-alert states.
- Low-quality audio produces an honest error state rather than a confident alert.
- The user receives a persistent visual, audible, and vibration stop alert.
- Canceling or completing a session releases the microphone immediately.
- The primary journey passes automated tests and real-device tests on one current iPhone and one current Android phone.
- Privacy, safety, settings, and local-data deletion are complete and readable.
