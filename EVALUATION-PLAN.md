# DEUZ Evaluation Plan

## Purpose

This document explains how DEUZ should be tested before making claims about its accuracy or reliability.

The goal is not only to test whether DEUZ detects fake audio. It must also avoid falsely accusing genuine recordings and clearly admit when it is uncertain.

## Test Audio Categories

### Genuine Audio

Unedited voice memos recorded by real people using different:

- Phones
- Microphones
- Messaging apps
- Languages and accents
- Rooms and outdoor environments
- Speaking speeds and emotions

### AI-Generated Speech

Test audio created using multiple speech-generation and voice-cloning systems.

The evaluation should include generators that were not used to train the detector.

### Spliced Audio

Create recordings by cutting words or phrases from genuine speech and rearranging them to change the meaning.

Examples should include:

- Obvious cuts
- Carefully hidden cuts
- Cuts between separate recordings
- Cuts within the same recording
- Changed background noise
- Matching background noise

### Replay Attacks

Play genuine or synthetic audio through:

- Phone speakers
- Laptop speakers
- Headphones
- High-quality speakers

Record the playback using different microphones and distances.

### Difficult Audio

Test recordings affected by:

- Background noise
- Echo
- Low volume
- Music
- Multiple speakers
- Messaging-app compression
- Repeated encoding
- Speed changes
- Very short duration
- Poor internet connections

### Scam-Language Tests

Include both genuine and manipulated recordings containing:

- Urgent money requests
- Secrecy demands
- Requests to bypass normal procedures
- Unusual payment methods
- Threats or emotional pressure

Also include harmless messages with similar words to measure false alarms.

## Test Methods

DEUZ should be tested in two modes:

1. **Original-file mode:** The voice memo is shared directly with DEUZ.
2. **Widget-listening mode:** The memo plays through a speaker while DEUZ captures it through the microphone.

Results from these modes must be reported separately because microphone capture may reduce accuracy.

## Results to Measure

### False Positive Rate

How often DEUZ incorrectly warns that genuine audio may be manipulated.

### False Negative Rate

How often DEUZ fails to warn about synthetic, spliced, or replayed audio.

### Detection Accuracy

Performance for each attack category—not only one combined accuracy number.

### Time to First Warning

How long DEUZ takes to show its first useful warning while audio is playing.

### Total Processing Time

How long the complete analysis takes.

### Splice Localization

How closely the highlighted suspicious timestamps match the actual edited sections.

### Uncertain Results

How often DEUZ correctly refuses to provide a confident result because the audio quality or duration is insufficient.

## Required Comparisons

Test each detection layer separately:

- Synthetic-speech detector
- Splice detector
- Replay detector
- Watermark and provenance checker
- Scam-language analyser

Then test the combined DEUZ risk system.

This shows whether combining the detectors improves results or introduces additional false alarms.

## Dataset Separation

Recordings used for final testing must not appear in training data.

Speakers, devices, environments, and AI generators should be separated between training and testing whenever possible.

## Fairness Checks

Compare performance across:

- Languages
- Accents
- Age groups
- Voice pitches
- Speech disabilities
- Recording devices
- Quiet and noisy environments

Large performance differences must be documented before public release.

## Pass Conditions for an Early Prototype

The prototype should:

- Process an ordinary voice memo successfully
- Detect some known synthetic and spliced test recordings
- Return suspicious timestamps
- Produce understandable explanations
- Return **Uncertain** for unusable audio
- Avoid describing a clean scan as proof of authenticity
- Show an initial result quickly enough to interrupt an urgent decision

Exact accuracy targets should only be chosen after a representative test dataset exists.

## Reporting Rules

Every published result should state:

- Dataset size
- Audio sources
- Languages and devices tested
- Attack types tested
- Original-file or widget-listening mode
- False positive and false negative rates
- Processing time
- Known limitations

DEUZ should never advertise “100% accurate” or “guaranteed genuine.”

## Current Status

Evaluation planning only. No detector has been validated and no accuracy results are available yet.
