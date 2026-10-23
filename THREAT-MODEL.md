# DEUZ Threat Model

## Purpose

This document defines the voice-message attacks Project DEUZ is intended to identify, the people and information being protected, and the limitations of automated detection.

DEUZ is a risk-assessment tool—not proof that a recording or transaction is legitimate.

## Assets to Protect

- A user's money and accounts
- Personal and business credentials
- A person's voice identity
- Private voice messages
- Trust between contacts
- Business approval processes

## Potential Attackers

- Financial scammers
- Social-engineering groups
- Identity thieves
- Disgruntled employees
- Attackers targeting company executives
- People with access to public voice recordings

## Main Threats

### 1. AI Voice Cloning

An attacker generates new speech that resembles a trusted person.

**Example:** A manager receives a fake voice memo from someone imitating the company director and requesting an urgent transfer.

**Possible DEUZ signals:**

- Synthetic-speech artifacts
- Unnatural breathing or timing
- Generator-specific frequency patterns
- AI watermark or provenance evidence
- Voice mismatch with enrolled samples

### 2. Spliced Genuine Recordings

An attacker cuts words from authentic recordings and rearranges them into a fraudulent message.

**Example:** Separate phrases from a public conference are combined to create an urgent payment request.

**Possible DEUZ signals:**

- Sudden background-noise changes
- Inconsistent room acoustics
- Abnormal word transitions
- Pitch, phase, or frequency discontinuities
- Different encoding characteristics between segments

### 3. Replay Attacks

An attacker reuses an authentic older recording.

**Example:** A genuine memo containing approval language is replayed during a different transaction.

**Possible DEUZ signals:**

- Loudspeaker or re-recording characteristics
- Missing freshness information
- Duplicate audio matching an earlier recording
- Conflict between the message and current transaction context

### 4. Compromised Accounts or Devices

A voice memo is sent through a trusted account that has been stolen.

**Risk:** Account or device verification alone could incorrectly make the message appear safe.

**DEUZ response:** Continue checking the audio and transaction language even when the sender's account is verified.

### 5. Detector-Evasion Attacks

An attacker modifies fraudulent audio to avoid detection.

**Possible techniques:**

- Adding background noise
- Changing speed or pitch
- Compressing the recording repeatedly
- Re-recording through a loudspeaker
- Using short audio clips
- Applying smooth crossfades between cuts

**DEUZ response:** Report uncertainty when audio quality is insufficient instead of declaring the memo legitimate.

### 6. Social Engineering

The recording may be technically genuine but still contain a fraudulent or coerced request.

**Warning signs:**

- Urgent payment demands
- Requests for secrecy
- Changed bank details
- Requests to bypass normal approval
- Pressure not to call the sender back
- Requests for passwords or authentication codes

## Important Failure Cases

### False Positive

DEUZ labels a genuine message as suspicious.

**Impact:**

- User confusion
- Delayed legitimate transactions
- Loss of trust in DEUZ

### False Negative

DEUZ fails to detect a manipulated or fraudulent message.

**Impact:**

- Financial loss
- Identity theft
- False confidence caused by a "safe" result

False negatives are especially dangerous if DEUZ presents its result as proof of authenticity.

## Safety Rules

DEUZ should never display:

- "100% legitimate"
- "Definitely human"
- "Safe to transfer"
- "Identity confirmed" based only on voice similarity

Instead, DEUZ should use results such as:

- **High risk**
- **Uncertain**
- **Low evidence of manipulation**

Every result involving money or credentials should recommend independent verification through a previously trusted contact method.

## Privacy Risks

Voice recordings and voiceprints may contain sensitive biometric information.

DEUZ should:

- Obtain consent before enrolling a voice
- Encrypt stored voice representations
- Delete raw recordings by default
- Avoid using customer recordings for training without permission
- Provide clear deletion controls
- Minimize information sent to external services

## Out of Scope for the First Version

The initial DEUZ prototype may not protect against:

- Perfect zero-day voice generators
- Audio that is too short or damaged to analyze
- Fraud performed entirely by a genuine speaker
- Compromised phones operating with the owner's permission
- Legal or forensic proof of audio authenticity

## Security Principle

> A genuine-sounding voice is not proof that a request is safe.

DEUZ should create a pause, explain the evidence, and help the recipient verify the request independently.
