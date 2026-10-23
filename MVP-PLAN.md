# DEUZ MVP Plan

## Objective

Build a small proof of concept that analyses a voice memo and presents understandable evidence of possible manipulation or scam risk.

The MVP is an experiment—not a production security system and not proof that a recording is genuine.

## Core User Flow

1. The user shares or uploads a voice memo.
2. DEUZ checks whether the recording is long and clear enough to analyse.
3. The system examines the audio and transcript.
4. Results appear as soon as enough evidence is available.
5. DEUZ explains the warning signs and recommends a safe next action.

## MVP Detection Layers

### 1. Audio Quality Check

Detect recordings that are too short, noisy, quiet, or compressed for reliable analysis.

### 2. Synthetic-Speech Detection

Estimate whether parts of the recording contain characteristics associated with AI-generated speech.

### 3. Splice Detection

Look for abrupt changes in background noise, frequency patterns, timing, room acoustics, or compression that may indicate edited audio.

### 4. Transcript Scam Analysis

Convert speech to text and identify warning signs such as:

- Urgent requests
- Money transfers
- Secrecy
- Unusual payment methods
- Pressure to act immediately
- Requests to bypass normal approval procedures

## Result Categories

### High Risk

Strong manipulation evidence, strong scam indicators, or several independent warnings occur together.

### Uncertain

The recording is too short, noisy, compressed, or outside the detectors’ reliable coverage.

### Low Evidence of Manipulation

The scan did not find strong evidence of manipulation.

This does **not** prove that the speaker or request is genuine.

## Evidence Display

The result should show:

- The overall risk category
- Which checks produced warnings
- Suspicious timestamps
- A short explanation in plain language
- The limitations of the scan
- A recommended verification action

## Safety Actions

For suspicious financial requests, DEUZ should recommend that the user:

1. Stop before transferring money.
2. Contact the person using a previously saved number.
3. Ask a question based on private shared knowledge.
4. Require a second person’s approval for important transfers.
5. Report the message if fraud is suspected.

## Initial Interface

The first prototype may use a simple upload or share interface.

A home-screen widget and real-time microphone capture can be tested after the core detection pipeline works reliably.

## Out of Scope for the First MVP

- Claims of 100% authenticity
- Automatic approval of transactions
- Continuous call monitoring
- Full sender-device enrolment
- Production-grade encrypted cloud infrastructure
- Support for every language and audio format
- Replacement of human verification

## Success Criteria

The MVP should demonstrate that it can:

- Accept and process a voice memo
- Return an initial result quickly
- Identify known test manipulations
- Highlight suspicious audio regions
- Explain why it produced the result
- Return **Uncertain** when evidence is insufficient
- Avoid presenting a clean scan as proof of authenticity

## Evaluation Plan

Test the prototype with:

- Genuine unedited recordings
- AI-generated speech
- Cloned voices
- Manually spliced sentences
- Replayed recordings
- Noisy and heavily compressed messages
- Genuine messages containing urgent financial language

Measure:

- Detection accuracy
- False-positive rate
- False-negative rate
- Time to first warning
- Total processing time
- Performance across different speakers, devices, and environments

## Future Phases

After validating the MVP:

1. Add streaming analysis.
2. Build the one-tap widget experience.
3. Add optional speaker enrolment.
4. Add sender-device verification.
5. Investigate watermark and provenance standards.
6. Conduct larger and more diverse evaluations.

## Current Status

Planning stage. No detection results or accuracy claims have been validated yet.
