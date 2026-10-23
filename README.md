# Project DEUZ

**Dual Encrypted User Zone** is a proposed one-tap voice-message security assistant. It could help people pause suspicious transactions by checking voice memos for signs of synthetic speech, replay, splicing, speaker inconsistency, and scam pressure.

> Tap. Play or share. Pause the scam.

## Current scope

This repository currently documents the initial DEUZ concept, its safety principles, and a possible path toward an MVP. It does not yet contain an application or working detector.

## Proposed detection layers

1. Synthetic-speech detection
2. Audio-splice localization
3. Replay and recording-channel analysis
4. Optional consented speaker verification
5. Optional device and identity verification
6. Transcript-based scam-risk analysis

## Safety principle

DEUZ should provide risk evidence and verification actions—not claim that audio is absolutely genuine. A clean technical scan cannot prove that a payment request is legitimate.

## Documentation

- [DEUZ concept analysis](DEUZ-concept-analysis.md)

## Status

Concept and research stage. No application or production detection backend is included.
