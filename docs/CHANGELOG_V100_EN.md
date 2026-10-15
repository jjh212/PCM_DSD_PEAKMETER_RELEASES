# v1.0 Change Log — English

This is the user-approved PCM/DSD PeakMeter release candidate, building on v0.8.2 while preserving previous release history.

## Features

- DSD metering modes: FAST direct modulation and LPF-filtered meter peaks.
- Format-specific FAST 28–896-bit windows and configurable display offset (default −4.8586 dB).
- Meter-only LPF high-cut: 20–200 kHz cutoff, default 40 kHz.
- Slow, Medium (previously Normal), Sharp Roll-off; Medium is default.
- One selected response curve on fixed frequency-response axes.
- Top and bottom PCM/DSD threshold **text** highlighting rather than brightening the meter region background.
- PCM caution/danger thresholds: 0/+5 dB. DSD caution/danger thresholds: 0/+3.1 dB.
- Version 1.0 displayed in Components and bilingual General settings.
- Updated bilingual user manuals and actual v1.0 DSD settings screenshots.

## Validation and scope

- Successful MSVC v145 Release x64 TEST rebuild.
- Live Karma / DSD64 / SDM Type B metering demonstrated changes from cutoff and roll-off settings.
- Stage 26 UI approved in practice; version 1.0 display checked in both languages and Components.
- LPF is **metering-data-only** and does not alter playback, DSP audio output, or the DAC-bound stream.
- Calculated LPF response is neither playback EQ nor certified reconstructed DSD True Peak.

**Approved TEST DLL SHA256:** `AA2F514B8C8199923BBEE9F730A42222878B437DF5F6558BA94C6268160CF561`

Use the official release's `SHA256SUMS.txt` for the final distribution DLL and packages.

### Finalized manuals and screenshots

- Added **22 user-provided UI screenshots**: 14 Korean/English Preferences tabs, two PCM layouts, four DSD512 layouts, menu navigation, and Components version.
- Documentation and imagery only; no measurement or playback-path modifications.
