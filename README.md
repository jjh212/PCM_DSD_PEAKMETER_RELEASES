# PCM/DSD PeakMeter for foobar2000

Native C++ **display-only PCM/DSD peak meter** for foobar2000 on Windows x64. Provides stereo L/R peak metering, selectable PCM/DSD display and per-panel appearance settings. Works as a **Columns UI panel** or an **independent window**.

> **v0.4.0 — verified build identified, release asset not yet attached.** A GitHub Release download will be linked here **only after** the verified DLL has actually been uploaded. This repository currently contains public documentation, not an installable DLL.

## v0.4.0 at a glance

- Automatic route detection using current Core DSP configuration and explicitly assigned Preset/DSP rules; manual PCM/DSD override available.
- PCM default display correction **0 dB**, DSD default **−6 dB** (configurable display-only correction).
- Horizontal and vertical layouts, stereo peaks and peak-hold indicators.
- Minimum window sizes that **stop shrinking**, instead of turning the meter blank.
- Full 8-section Preferences for route rules, layout, scale, colors, fonts/buttons and themes.
- Per-panel configuration, independent window position/size persistence.
- No mandatory `foo_outinfo` dependency for the meter's route detection path.

[한국어 사용 설명서](docs/USER_MANUAL_KO.md) · [English manual](docs/USER_MANUAL_EN.md) · [v0.4.0 상세 업데이트](CHANGELOG.md) · [문제 해결](docs/TROUBLESHOOTING_KO.md)

## Download / verification

Release artifact status: **not yet uploaded**. Do not download unverified DLLs from unrelated links.

Verified Windows Release x64 build:
- File: `foo_pcm_dsd_peakmeter.dll`
- Size: **471,040 bytes**
- SHA256: `74C66AF9E58B5040F6243A90E6DD39B65AB5B1C6B93A4E2A0A5127D6E5535A55`

A successfully created and locally validated DLL is **not** proof that a file is available through GitHub Releases. Once published, compare the downloaded file hash with this value.

## Platform and limits

Windows x64, foobar2000 with compatible Columns UI SDK component host. The meter is a visualizer; it does **not** encode, convert, or modify audio. DSD displayed levels depend on the available observation path and defined correction; **do not treat the display as a laboratory-certified bitstream true-peak measurement**.

DarkOne full-screen Z-order interactions are tracked separately from the meter's resizing fix.

## Evidence

- Windows Release x64 build: PASS.
- Automatic core/geometry regression tests: 15/15 PASS.
- End-user minimum-size acceptance: 5/5 PASS (standalone horizontal/vertical; Columns UI horizontal/vertical; compact rendering).
- Previously verified existing meter and Preferences functions: PASS.

Screenshots shown in the documentation are user-observed examples. No UI artwork or DarkOne screenshot is a promise of a universal skin layout.

The private development source is maintained separately at the developer's repository.
