# Project DEUZ — Revised Concept Analysis

## Concept

Project DEUZ is a one-tap voice-memo security system. When someone receives a suspicious voice message, they activate DEUZ from a Home Screen or Lock Screen widget and either share the original memo to DEUZ or let DEUZ listen while it plays. The system analyzes the message in seconds and warns the recipient about possible voice synthesis, replay, cutting, rearrangement, identity mismatch, and scam-related language.

The sender does not need to know that DEUZ exists. The system can inspect an ordinary voice memo from WhatsApp, Messenger, Telegram, iMessage, email, or another source without requiring the sender to install DEUZ or provide a code.

When both people use DEUZ, an optional private verification layer can provide additional evidence about the sender or originating device. This verification never replaces audio analysis: a verified account can be stolen, and authentic voice samples or codes can still be replayed, cloned, or cut together.

## Core promise

> **Receive a suspicious voice memo, tap DEUZ, and get an immediate risk assessment without navigating through the app.**

DEUZ is not intended to certify that a recording is absolutely genuine. Its purpose is to interrupt a pressured transaction, expose suspicious evidence, and help the recipient verify the request safely.

## Two operating modes

### Universal detection

Universal detection works for any voice memo, including recordings from people who have never used DEUZ.

DEUZ checks for:

- synthetic or voice-converted speech;
- suspicious cut and join points;
- words assembled from different recordings;
- discontinuities in background noise, room acoustics, frequency patterns, phase, or encoding;
- replayed or loudspeaker-recorded audio;
- abrupt speaker-characteristic changes;
- urgency, secrecy, payment demands, credential requests, or attempts to bypass normal approval.

This mode answers: **“Does this message contain evidence of manipulation or a dangerous request?”** It does not independently prove the sender’s identity.

### DEUZ-enhanced verification

When the sender has enrolled in DEUZ, the scan can add identity and device evidence, such as:

- similarity to consented reference voice samples;
- a valid DEUZ identity or device signature;
- freshness information to distinguish a new message from an old replay;
- optional transaction context known only to the legitimate participants.

The system still performs every universal detection check. If a verified identity is present but the audio looks edited or synthetic, DEUZ must warn the recipient.

## Decision model

DEUZ should treat each signal independently before combining them into an overall risk level.

| Evidence layer | Question answered | Important limitation |
|---|---|---|
| Synthetic-speech detection | Does the audio resemble generated or converted speech? | May miss unknown generators or heavily processed audio |
| Splice localization | Are there signs that separate segments were joined or rearranged? | Crossfading, noise, and message compression can hide edits |
| Speaker comparison | Does the voice resemble the enrolled person? | Authentic replayed audio can still match |
| Device/identity verification | Is the memo linked to a recognized DEUZ identity or device? | Accounts and devices can be compromised |
| Freshness/replay analysis | Does this appear to be a new recording? | Re-recording and transformation can obscure replay evidence |
| Scam-language analysis | Is the message pressuring the recipient into a risky action? | Legitimate urgent messages can trigger the same patterns |

No single successful check should be allowed to overrule a serious warning from another layer.

## Widget experience

The widget is DEUZ’s primary interaction surface, not merely a shortcut to a complicated app.

### Flow A: original voice memo available

1. The recipient presses and holds or opens the voice memo’s Share menu.
2. They select **Scan with DEUZ**, or activate the DEUZ widget and choose the recent memo.
3. DEUZ analyzes the original audio file.
4. A Live Activity, notification, or widget state shows **Receiving → Scanning → Result**.
5. An early warning appears within seconds, followed by a more detailed result when analysis finishes.

This is the preferred path because direct access to the original file preserves forensic evidence and avoids room noise.

### Flow B: the memo cannot be shared

1. The recipient taps **Listen** on the DEUZ widget.
2. A user-visible recording session starts.
3. The recipient plays the voice memo through the phone or another device.
4. DEUZ analyzes the captured audio in overlapping windows.
5. The widget or notification reports risk as evidence accumulates.

This path is more convenient but less accurate because the speaker, microphone, background environment, and automatic noise processing can alter the evidence.

Mobile operating systems restrict indefinite background microphone access. The realistic promise is therefore **one tap to begin an explicit scanning session**, not a widget that secretly listens all the time. The main app remains useful for first-time permissions, voice enrolment, privacy controls, detailed evidence, and scan history, but ordinary scans should not require navigating through it.

## Result design

DEUZ should not display only “80% human” or “100% legitimate.” A scammer may construct a fraudulent message entirely from genuine human recordings, causing a synthetic-voice detector to report that the speech is human.

A safer interface separates the evidence:

> **High risk — pause this transaction**  
> Possible audio joins detected at 00:04 and 00:09. The voice resembles the enrolled contact, but that could result from replayed speech. The memo requests an urgent transfer. Call the person using their previously saved number.

Recommended result states:

- **High risk:** strong manipulation evidence or several independent warnings.
- **Uncertain:** insufficient speech, excessive noise, severe compression, or conflicting detectors.
- **Low evidence of manipulation:** no strong warning found, but authenticity and identity are not guaranteed.

The detailed view can show:

- a timeline marking suspicious regions;
- synthetic-speech evidence;
- possible cut locations;
- speaker consistency;
- DEUZ identity/device verification;
- replay/freshness evidence;
- scam indicators from the transcript;
- recording quality and detection limitations.

## Example scenarios

### Unknown sender, manipulated conference audio

The attacker assembles words from public recordings into an urgent payment request. The sender has no DEUZ account.

DEUZ can still flag changes in acoustic background, timing, pitch continuity, codec characteristics, or word-boundary behavior. It can also recognize the urgent financial request. The correct result is **high risk** or **uncertain with a strong payment warning**, not “human voice confirmed.”

### Unknown sender, clean AI clone

DEUZ has no identity or code information, but its synthetic-speech models detect generator artifacts. It warns that the voice may be generated and recommends independent contact.

### Verified DEUZ user, suspicious memo

The message is connected to a recognized DEUZ identity, but the recording contains splice or synthesis evidence. DEUZ reports **recognized identity, suspicious audio** and blocks any “verified” visual treatment.

### Genuine urgent request

The voice, device, and recording appear consistent, but the transcript requests money urgently. DEUZ reports low technical manipulation evidence while still requiring transaction verification. This avoids treating audio authenticity as proof that a transaction is safe.

## Technical architecture

A practical implementation processes the audio in overlapping two-to-four-second windows:

1. Audio-quality and voice-activity assessment.
2. Streaming transcription.
3. Synthetic-speech ensemble operating on waveform and spectrogram representations.
4. Acoustic change-point and splice analysis.
5. Speaker-consistency and optional enrolled-speaker comparison.
6. Replay and recording-channel analysis.
7. Watermark and provenance checks where supported.
8. Scam-intent analysis of the transcript.
9. Calibrated evidence fusion and safety recommendation.

The first warning can appear before the entire memo finishes. DEUZ should revise the assessment as more evidence becomes available and clearly label preliminary results.

## MVP

The most achievable first release is a voice-message scanner rather than universal live-call monitoring.

Initial scope:

- iOS and Android share-sheet support;
- Home Screen/Lock Screen widget or control;
- explicit listen-and-scan mode;
- synthetic-speech detection using an established API plus an independent model;
- transcript-based scam warnings;
- experimental splice timeline;
- optional consented voice enrolment;
- encrypted processing and automatic raw-audio deletion;
- clear verification actions, such as calling the saved contact or requiring a second approver.

Later versions can add communication-platform integrations, stronger replay protection, cryptographically signed DEUZ-to-DEUZ messages, organization policies, and carefully scoped live-call support.

## Competitive position

Real-time audio deepfake detection already exists, particularly for enterprise calls and meetings. DEUZ’s opportunity is not claiming to invent the detector category. Its potential advantage is making multiple forensic and behavioral checks accessible to ordinary users at the exact moment a scammer creates urgency.

The product becomes defensible through:

- a one-tap consumer workflow;
- support for both unknown senders and enrolled contacts;
- combined synthesis, splice, replay, identity, and scam-risk analysis;
- explanations localized to the suspicious part of the memo;
- privacy-preserving enrolment;
- transaction-focused interventions rather than an isolated probability score;
- real-world scam data and continuous adversarial testing.

## Final assessment

The revised DEUZ concept is stronger than a conventional deepfake detector because it does not depend on both parties adopting the app. It provides useful universal scanning first and adds DEUZ verification only when available.

Its defining experience should be:

> **Tap. Play or share. Pause the scam.**

The product should never claim that a successful code, voice match, or AI-detector result proves legitimacy. Its value comes from combining imperfect evidence quickly enough to stop a recipient from acting under pressure.
