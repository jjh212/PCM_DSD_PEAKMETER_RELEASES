# PCM/DSD PeakMeter v0.8.2 — Peak Hold Motion (English)

**Date:** 2026-10-15 · **Platform:** foobar2000 Windows x64, Columns UI / standalone

## Changed (one feature only)

- PCM and DSD Peak Hold markers now capture a new peak immediately, retain it briefly, descend continuously toward the current bar and react immediately to a higher new peak.
- Common initial tuning: **0.50 s hold**, **30 dB/s marker descent**. The movement was visually compared with the foobar2000 built-in Peak Meter in the user's PEAK_TEST instance.
- The previous 1.4-second hold followed by an immediate snap to the current bar is replaced for both routes.

## Not changed

Audio samples/output, PCM/DSD measurement methods, DoP automatic routing, DSD format/window calculations, main bar ballistics (PCM 18 dB/s; DSD 60 dB/s), thresholds, statistics, calibration, UI layout, user settings and the frame-clock scheduling algorithm.

This remains a display-only meter. DSD FAST values represent direct modulation estimates, not reconstructed-waveform True Peak. No LPF has been added.

**v0.8.2 DLL SHA256:** `6A1CF501C12A00BEB92A11FAB139A3EB14BA22C94F1678C031D33549131AC7FC`

**Documentation:** [English manual](USER_MANUAL_EN.md) · [v0.8.1 changes](CHANGELOG_V081_EN.md).
