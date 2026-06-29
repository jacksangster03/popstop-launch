# POPSTOP Project Context

## What I'm Building

POPSTOP is a popcorn brand with a companion mobile app for people who regularly burn microwave popcorn.

While the microwave runs, the app uses the phone microphone to listen to the timing between pops. It estimates when the popcorn is ready and alerts the user to stop the microwave.

The app does not control or turn off the microwave. The user must stop the microwave after receiving the alert.

The smallest useful v1 should:

- Let the user start a listening session.
- Request and explain microphone permission.
- Listen to the popcorn's popping pattern.
- Estimate when the user should stop the microwave.
- Give a clear visual, audible, and vibration alert.
- Let the user stop or cancel a session.
- Explain that results vary by popcorn, microwave, room noise, and phone placement.

The launch website has one primary goal: get visitors to download the app.

## Audience

The primary audience is people aged 15–45 who regularly burn microwave popcorn.

They want:

- A simple way to know when their popcorn is ready.
- Less smoke and fewer burnt kernels.
- No extra kitchen hardware.
- A fast explanation without technical jargon.

Likely concerns include:

- Whether the app can hear the pops over the microwave.
- Whether microphone audio is recorded or uploaded.
- Whether the app works with their microwave and popcorn brand.
- Whether the alert will be noticeable.

## Product Positioning

The problem is not that people cannot use a timer. Fixed microwave instructions are guesses because microwaves, popcorn bags, and conditions vary.

POPSTOP listens to what is happening instead of trusting a fixed cook time.

Core message:

> Stop guessing. Stop burning popcorn.

Messaging order:

1. Microwave popcorn burns easily.
2. POPSTOP listens to the popping pattern.
3. The app tells the user when to stop.
4. The result is fewer burnt kernels and less smoke-alarm drama.

## Brand Voice

The brand voice is:

- Confident
- Irreverent
- Anti-corporate
- Direct
- Playful
- Clear

Write like a sharp friend who has declared war on burnt popcorn.

Use short sentences, plain English, relevant humor, and strong calls to action.

Avoid corporate jargon, empty hype, fake enthusiasm, long technical explanations, condescension, and excessive exclamation marks.

## Banned Language

Never use the word "premium" in customer-facing copy.

Also avoid generic product buzzwords such as:

- Streamlined
- Seamless
- Intuitive
- Robust
- Powerful
- Leverage
- Synergy
- Innovative
- Revolutionary
- Ecosystem

## Product Accuracy and Safety

- Do not claim the app prevents every burnt bag.
- Do not claim the app guarantees safety or perfect results.
- Do not imply that the app controls the microwave.
- Do not invent accuracy rates, scientific validation, certifications, testimonials, partnerships, pricing, or availability.
- Clearly state how microphone audio is processed and stored once the technical approach is confirmed.
- Include a warning that users remain responsible for monitoring and stopping the microwave.
- Do not encourage users to leave a running microwave unattended.

## Design Direction

The current launch page uses:

- Warm cream, bright yellow, red, pink, and near-black.
- Heavy borders and offset shadows.
- Oversized editorial typography.
- Hand-made, anti-corporate energy.
- CSS illustrations and restrained motion.

The app should feel like the same brand while keeping the listening state, stop alert, controls, and safety information immediately understandable.

## Current Project Files

- `AGENTS.md`: project and brand instructions.
- `index.html`: responsive launch landing page.
- `styles.css`: landing-page design and responsive styling.

## Open Decisions

- Final product name; POPSTOP is currently a working name.
- Target build platform and technology stack.
- iOS, Android, or both for v1.
- Whether audio processing runs entirely on-device.
- Pop-detection and stop-estimation method.
- Whether v1 requires accounts or stores session history.
- Final App Store and Google Play URLs.
