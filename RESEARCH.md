# DEUZ Research Notes

_Last reviewed: 23 October 2026_

## Research Question

What already exists for detecting AI-generated or manipulated content, and where could DEUZ offer something meaningfully different?

## Short Answer

Audio deepfake detection is **not an empty field**. Researchers already benchmark spoofed-speech detectors, and some AI providers watermark audio they generate. The opportunity for DEUZ is the product layer: fast consumer access, combined detection signals, suspicious-timestamp evidence, and a clear action that stops an urgent scam.

## Comparison

| Project or standard | Main approach | Relevant to DEUZ | Important limitation |
|---|---|---|---|
| Google SynthID | Embeds detectable watermarks in AI-generated content, including supported audio | DEUZ could check for known provenance or watermarks as one evidence source | A missing watermark does not prove audio is human; coverage depends on participating generators |
| Pangram | Classifies text using learned patterns from human and AI-written examples | Its classifier and segment-highlighting approach is a useful product reference | Pangram is primarily a text detector, not a general voice-memo authenticity system |
| Claude watermarking | Adds a statistical watermark to Claude-generated text; supported files may also carry C2PA credentials | Shows how provider-side marking can complement post-hoc detection | Text watermarking does not detect voice cloning or audio splicing, and provider watermarks only cover participating systems |
| C2PA Content Credentials | Cryptographically records provenance and edits in supported media | DEUZ could display valid signed provenance when it exists | Metadata may be absent or stripped; absence is not evidence of fraud |
| ASVspoof | Research benchmarks for spoofing, replay, speech deepfakes, and spoofing-robust speaker verification | Useful datasets, metrics, baselines, and evaluation discipline | Benchmark performance may fall when recordings pass through real phones, messaging apps, noise, and compression |
| NIST GenAI Audio Deepfake Challenge | Evaluates audio generation and discrimination systems | Confirms audio deepfake detection is an active technical field | A challenge detector is not automatically a safe or understandable consumer product |

## What DEUZ Should Borrow

### From SynthID and C2PA

Treat provenance as strong positive evidence when it validates correctly, but never treat missing provenance as proof that audio is genuine or fake.

### From Pangram

Return a simple overall result while also highlighting which segments contributed to it. DEUZ should avoid presenting a bare percentage without explaining its meaning or uncertainty.

### From ASVspoof and NIST

Use public evaluation protocols, report false positives and false negatives, and test against unseen attacks. Results should also be measured after replay, transcoding, compression, background noise, and microphone capture.

### From Claude Watermarking

Separate watermark detection from classifier-based detection. They answer different questions:

- A watermark asks whether a participating generator likely created the content.
- A classifier estimates whether the content resembles known synthetic or manipulated examples.
- Neither proves that the request inside a recording is legitimate.

## Proposed DEUZ Difference

DEUZ should combine several independent layers in one quick workflow:

1. Synthetic-speech detection
2. Cut and splice localization
3. Replay and recording-channel detection
4. Optional speaker consistency checks
5. Watermark and signed-provenance checks
6. Transcript-based scam-pressure analysis
7. Safe next actions before money is transferred

The differentiator is not simply saying “AI” or “human.” It is helping a person answer three practical questions quickly:

1. Is there evidence that this recording was generated, replayed, or edited?
2. Which part of the recording caused concern?
3. What should I do before trusting the request?

## Product Gap

Most existing approaches concentrate on one of these areas:

- Provider-created watermarks
- General content provenance
- Laboratory detection benchmarks
- Text classification
- Enterprise fraud or identity systems

DEUZ is aimed at a consumer moment: someone receives an urgent voice memo and needs a useful warning without opening a complicated forensic tool.

## Risks and Open Questions

- Can useful preliminary results appear while the memo is still playing?
- How much accuracy is lost when the widget hears audio through a microphone instead of receiving the original file?
- Can splice localization survive messaging-app compression?
- How should multiple weak signals be calibrated without creating a misleading certainty score?
- What audio duration is required before a result becomes meaningful?
- How should performance be tested across languages, accents, devices, ages, and disabilities?
- Can processing remain on-device for privacy and speed?

## Research Position

DEUZ should not claim to authenticate a person from audio alone. Its defensible role is to combine evidence, show uncertainty, and interrupt high-risk decisions long enough for independent verification.

## Sources

- [Google DeepMind: SynthID](https://deepmind.google/models/synthid/)
- [Google DeepMind: Gemini Audio](https://deepmind.google/models/gemini-audio/)
- [Pangram: How AI detection works](https://www.pangram.com/research/how-it-works)
- [Anthropic: How Claude's text watermark works](https://www.anthropic.com/news/claude-text-watermark)
- [C2PA technical specifications](https://c2pa.org/specifications/specifications/)
- [ASVspoof](https://www.asvspoof.org/)
- [NIST AI Challenges](https://ai-challenges.nist.gov/challenges)
