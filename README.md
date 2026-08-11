# Radar-Audio Intrusion Dataset

Multimodal radar-audio dataset for privacy-preserving indoor intrusion-related alarm detection.

## Overview

This dataset was collected for the development and evaluation of indoor intrusion-related alarm detection methods using synchronized radar and audio sensing.

The dataset targets small-room indoor security scenarios and includes both intrusion-related events and challenging non-intrusion conditions. The recordings were designed to include variations in access point, motion style, repeated entry, environmental noise, door interaction, object falls, and other nuisance events.

The dataset contains 70 multimodal recordings acquired using two closely colocated Infineon CY8CKIT-062S2-AI boards.

## Sensor Setup

The acquisition setup includes:

- 60 GHz radar sensing using the onboard BGT60TR13C radar sensor
- Radar macro-detection data acquired at 10 Hz
- Stereo audio acquired at 16 kHz
- Two closely colocated CY8CKIT-062S2-AI boards mounted on a shared support
- Simultaneous radar and audio acquisition
- Indoor acquisition environment of approximately 5 x 5 m

The sensors were positioned to monitor the main door region while maintaining visibility toward other relevant access regions.

## Dataset Structure

The dataset is organized into individual recording folders:

```text
S001_...
S002_...
...
S070_...
```

Each recording folder contains:

```text
Radar-Data.data
Microphone-Data.wav
labelf.label
Session ID.txt
```

where:

- `Radar-Data.data` contains radar macro-detection data acquired at 10 Hz.
- `Microphone-Data.wav` contains stereo audio acquired at 16 kHz.
- `labelf.label` contains the final event annotation.
- `Session ID.txt` contains the recording-level metadata.

## Classes

The dataset uses a binary recording-level target.

### Positive

A positive recording contains an intrusion-related alarm event, including unauthorized access to the protected room.

Positive recordings may contain:

- door entry
- window entry
- rear-side/interior entry
- repeated entry by the same intruder
- slow, normal, fast, or stealth-like movement
- door impacts or knocking
- speech
- falling objects
- environmental background noise
- construction noise
- air-conditioner noise
- rain noise
- external siren noise

Some recordings contain more than one access path or more than one intrusion event.

### Negative

Negative recordings represent non-intrusion or nuisance conditions intended to challenge the alarm system.

Examples include:

- access attempts without entry
- external alarms or sirens
- environmental background noise
- rain noise
- air-conditioner noise
- thrown objects
- falling objects of different materials and sizes

## Metadata

Recording-level metadata are provided in:

```text
sessions.csv
```

The metadata include:

- session identifier
- public folder name
- binary class
- primary action
- access point
- number of intruders
- motion style
- speech presence
- additional disturbances

Detailed label definitions are provided in:

```text
labels.txt
```

## Annotation Format

Each `labelf.label` file contains temporal event annotations using the following fields:

```text
Time(Seconds)
Length(Seconds)
Label(string)
Confidence(double)
Comment(string)
```

`Time(Seconds)` indicates the beginning of the annotated interval and `Length(Seconds)` gives its duration.

The recording-level class describes the overall scenario. Therefore, a positive intrusion recording may also contain nuisance events such as door impacts, environmental noise, or falling objects.

## Data Splitting

No fixed train/validation/test split is imposed in the public metadata.

Users may define their own split depending on the target application and evaluation protocol.

For experiments involving window-based processing, recordings should be kept grouped so that windows originating from the same recording are not distributed across different dataset subsets.

This avoids recording-level information leakage between training and evaluation data.

## Intended Use

The dataset is intended for research on:

- indoor intrusion detection
- multimodal radar-audio sensing
- privacy-preserving sensing
- multimodal data fusion
- radar-only detection
- audio-only detection
- feature-level fusion
- score-level fusion
- edge-oriented alarm systems

## Citation

A DOI and citation information will be added after the first public dataset release.

## Authors

Author information will be added in the corresponding archived dataset record and associated publication.
