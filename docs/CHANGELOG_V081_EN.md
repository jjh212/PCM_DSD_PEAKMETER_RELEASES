# PCM/DSD PeakMeter v0.8.1 — Maintenance Changelog (English)

**Date:** 2026-10-15 · **Platform:** Windows x64, foobar2000 / Columns UI

### Fixed

- Corrected `DECLARE_COMPONENT_VERSION` from `0.4.0` to `0.8.1` for foobar2000's **Preferences → Components** entry.
- Corrected the bilingual **Preferences → Tools → PCM/DSD PeakMeter → General** version to `0.8.1`.
- Removed obsolete `TEST ONLY` wording from the native component description and updated the internal startup version message.
- Updated outdated source-file heading comments to reflect the released PCM/DoP DSD meter.

### Unchanged

- v0.8.0 measurement code, automatic DoP PCM/DSD decision and 1-second voting, DSD64–2048 bit-window mappings, peak hold, warning statistics, calibration offset, panel geometry and user settings.
- No manual PCM/DSD selector has been restored. The PCM/DSD labels are indicators only.
- No low-pass filter (LPF) or reconstructed-waveform DSD True Peak measurement has been added.

### Binary integrity

- DLL: `foo_pcm_dsd_peakmeter.dll`
- SHA256: `757A49FEE98FF97CA316D03F1AB772665945586F8661232279FE22BADE27A144`
- Built with Visual Studio 2026 / MSVC v145 / x64 Release.
- Validated by isolated source-hash-guarded build, PEAK_TEST and production deployment with rollback backup. Complete six-rate real-hardware verification remains separate.

**Full features, usage and illustrations:** [v0.8.0 English manual](USER_MANUAL_EN.md) · [v0.8.0 changes](CHANGELOG_V080_EN.md).
