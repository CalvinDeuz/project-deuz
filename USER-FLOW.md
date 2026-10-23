# DEUZ User Flow

## Purpose

This document describes how a person uses DEUZ to check a suspicious voice memo quickly, without navigating through the full application.

The intended experience is:

> Tap. Play or share. Pause the scam.

## Primary User

A person who receives a voice message requesting:

- Money or a financial transfer
- Account credentials
- Authentication codes
- Confidential information
- An unusual or urgent action

The sender does not need to have DEUZ installed.

## Entry Points

### Share to DEUZ

The user shares the original voice memo directly from a messaging application.

This is the preferred method because DEUZ receives the original audio file and can perform more reliable analysis.

### Widget Scan

The user taps the DEUZ Home Screen or Lock Screen widget and plays the voice memo aloud.

This method is useful when the messaging application does not allow the original file to be shared. However, microphone capture, speaker playback, and background noise may reduce detection accuracy.

## Primary Flow

### Step 1: Suspicious Message Received

The user receives a voice memo containing an unusual request.

**Example:**

> “Transfer the money now. I’m about to board a flight and can’t speak for long.”

The urgency causes the user to question whether the message is genuine.

### Step 2: Start DEUZ

The user either:

- Selects **Share → Scan with DEUZ**, or
- Taps the DEUZ widget and selects **Listen**

DEUZ begins a visible scanning session. The microphone must never activate silently.

### Step 3: Check Audio Quality

DEUZ determines whether the recording contains enough usable speech.

Possible results:

- **Audio ready for analysis**
- **Audio is too short**
- **Excessive background noise**
- **Unsupported or damaged recording**
- **Playback volume is too low**

If the audio quality is insufficient, DEUZ asks the user to share the original file or replay the message.

### Step 4: Analyse the Memo

DEUZ processes the audio in short overlapping sections.

The system checks for:

- Synthetic or voice-converted speech
- Possible cuts and joins
- Replay characteristics
- Speaker inconsistency
- Available watermark or provenance evidence
- Suspicious transaction language

When the sender is enrolled in DEUZ, the system can also check consented voice and device-verification information.

### Step 5: Display Early Signals

DEUZ should return the first useful warning within a few seconds.

While scanning, the interface may display:

> Listening…

> Checking voice consistency…

> Possible edit detected…

Early results must be labelled as preliminary until sufficient audio has been analysed.

### Step 6: Show the Risk Result

DEUZ displays one of three primary results.

#### High Risk

Strong manipulation evidence or several independent warnings were found.

**Example:**

> **High risk — pause this transaction**  
> Possible audio joins were detected around 00:04 and 00:09.  
> The message also contains an urgent payment request.

#### Uncertain

DEUZ cannot reach a reliable conclusion.

**Example:**

> **Unable to determine**  
> The recording is short and heavily compressed. Share the original file or verify the request independently.

#### Low Evidence of Manipulation

No strong manipulation signal was found.

**Example:**

> **Low evidence of manipulation**  
> No strong synthetic-speech or editing signals were detected. This does not prove the message or transaction is legitimate.

DEUZ must never display “100% safe” or “definitely genuine.”

### Step 7: Explain the Evidence

The result screen separates each signal:

- Synthetic-speech evidence
- Possible edit timestamps
- Replay evidence
- Speaker consistency
- DEUZ identity or device verification
- Scam-language indicators
- Audio-quality limitations

The user can replay suspicious sections of the memo.

### Step 8: Recommend a Safe Action

For messages involving money, credentials, or confidential information, DEUZ recommends:

1. Do not reply through the suspicious message.
2. Do not use contact details provided in the message.
3. Call the person using a previously saved number.
4. Use an agreed verification phrase if available.
5. Require a second approver for business transfers.

Primary action:

> **Call the saved contact**

Secondary action:

> **Do not proceed yet**

### Step 9: Finish the Scan

After verification, the user can optionally report:

- The message was genuine
- The message was fraudulent
- The result is still unknown

This feedback may be used to improve DEUZ only with explicit permission.

The user can then delete the recording and analysis.

## DEUZ-to-DEUZ Flow

When both participants use DEUZ, the receiving device may also check:

- Sender identity information
- Registered device information
- Message freshness
- Cryptographic message signatures

These checks provide additional evidence but do not disable deepfake, replay, splice, or scam-language analysis.

A verified account can still be compromised.

## Privacy Flow

Before sending audio to an external server, DEUZ should explain:

- What information will be processed
- Where processing occurs
- How long the recording is retained
- Whether the data may be used for training
- How the user can delete it

Raw recordings should be deleted automatically unless the user chooses to retain them.

## Failure and Recovery

### No Internet Connection

DEUZ performs any available on-device checks and clearly identifies which analysis layers were unavailable.

### Analysis Service Unavailable

DEUZ reports:

> **Analysis unavailable**  
> Do not rely on the voice alone. Verify the request through a trusted contact method.

### Permission Denied

If microphone access is denied, DEUZ offers the share-file method instead.

### Unsupported Messaging Application

The user can save the audio file or use the widget’s listen mode.

## Success Criteria

The flow succeeds when:

- A user can begin scanning in one or two actions
- The first useful warning appears within seconds
- The result explains why the message was flagged
- Uncertainty is communicated clearly
- The user verifies the request before taking a risky action
- Raw voice data is not retained unnecessarily
