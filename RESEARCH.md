# DEUZ Research Notes

_Last reviewed: 23 October 2026_

## Research Question

What already exists for detecting AI-generated or manipulated content, and where could DEUZ offer something meaningfully different?

## Short Answer

Audio deepfake detection is **not an empty field**. Researchers already benchmark spoofed-speech detectors, and some AI providers watermark audio they generate. The opportunity for DEUZ is the product layer: fast consumer access, combined detection signals, suspicious-timestamp evidence, and a clear action that stops an urgent scam.

## What These Tools Actually Are

### Google SynthID

Google puts an invisible marker, called a watermark, inside some content created by its AI systems. If DEUZ finds that marker in supported audio, it is evidence that a participating AI system created or edited the recording.

If DEUZ finds no SynthID watermark, that does **not** prove the audio is genuine. The audio may have come from a different AI tool, or it may not have been watermarked.

### Pangram

Pangram is mainly an AI-writing detector. It studies patterns in text and estimates whether the writing looks human-written or AI-generated. It is not currently a general voice-memo detector.

Pangram is relevant as a product example because it gives an overall result and can highlight suspicious sections. DEUZ could use a similar presentation for suspicious moments in audio.

### Claude Watermarking

Claude watermarking places a statistical pattern in text produced by Claude. A detector with the correct key can check for that pattern. This concerns text, not general voice-clone or audio-splice detection.

It is useful to DEUZ as an example of provider-side marking: the company generating AI content helps identify it later.

### C2PA Content Credentials

C2PA is like a signed history card attached to a media file. It can record where the file came from and whether supported tools changed it.

A valid credential can provide useful evidence. A missing credential does not mean the file is fraudulent because many recordings never had one, and metadata can be removed.

### ASVspoof

ASVspoof is a research challenge for systems that detect fake speech, cloned voices, replayed recordings, and attacks against speaker verification. It shows that audio deepfake detection is already an active research field.

Its datasets and testing methods could help DEUZ measure performance, but laboratory scores may not survive phone speakers, messaging-app compression, background noise, or microphone recording.

### NIST Audio Deepfake Challenge

NIST runs evaluations where teams test systems that generate and detect audio deepfakes. It provides another serious benchmark for the technology.

A strong competition result does not automatically create a safe consumer product. DEUZ still needs fast processing, understandable warnings, privacy protection, and useful next steps.

### The Simple Difference

- **SynthID** checks for a marker placed into supported AI content.
- **Pangram** estimates whether text resembles AI writing.
- **Claude watermarking** marks Claude-generated text.
- **C2PA** checks a signed record of a file’s origin and edits.
- **ASVspoof and NIST** test systems that analyse audio for deepfakes and replay attacks.
- **DEUZ** would combine relevant audio evidence with splice detection, scam-language analysis, and immediate safety actions.

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
