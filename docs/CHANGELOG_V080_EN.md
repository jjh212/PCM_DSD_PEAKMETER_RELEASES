# PCM/DSD PeakMeter — v0.8.0 Release Changes (English)

**Release date:** 2026-10-14 · **DLL SHA256:** `DFEE5B07E0C23D4252C3382F5CE69616D479445B449C20C34031FB33D4F17E60` · [Full manual](USER_MANUAL_EN.md)

## Major upgrades from v0.4.0

1. **Actual DoP stream detection.** Identify PCM versus DoP-carried DSD by alternating `0x05` / `0xFA` markers, validated stereo framing and one-second majority voting. No longer rely on DSP profile name for mode classification.
2. **Removed manual PCM/DSD mode switching.** PCM and DSD are now non-interactive format/status indicators; re-confirmation of the same mode does not reset the meter.
3. **Real sample-rate / format indicators.** Show `PCM 44.1kHz`, `PCM 705.6kHz`, etc., or `DSD64`–`DSD2048` when verified DoP is detected. DoP markers alone do not encode the format multiplier; the verified carrier sample rate supplies it.
4. **DSD-format-dependent FAST bit windows.** DSD64/128/256/512/1024/2048 use **28/56/112/224/448/896 bits** respectively per channel. Includes both 44.1-kHz and 48-kHz transport families.
5. **Common display measurement path.** A single calibrated FAST result drives each channel's bar, Peak Hold, warning-region statistics and maximum displayed peak; short-window diagnostics do not silently trigger independent display warnings.
6. **FAST calibration Preferences.** Adjustable/resettable display offset, default **−4.8586 dB**, with `0.0000 dB` uncalibrated direct modulation. No audible gain adjustment or implemented LPF.
7. **Warning-zone counters.** PCM: orange at 0 dB and red at +5 dB; DSD: orange at 0 dB and red at +3.1 dB. Independent L/R orange/red entries and maximum calibrated peak.
8. **Interactive statistics reset.** Removed the separate RESET button; click the statistics area to reset. Hover/pressed/out colour feedback, narrow/wide responsive rail and automatic clearing on mode changes.
9. **Redesigned horizontal and vertical layouts.** Improved meter expansion, compact L/R statistics alignment, status spacing and minimum-size readability, preserving scale colours and Peak Hold.
10. **Seven bilingual Preferences tabs.** General, Panel Appearance, dB Scale, Meter Colours, Fonts, Custom Themes, DSD. Retained customization and JSON theme import/export, with v0.8.0 version information.
11. **Performance path.** DSD 60-Hz bucket pacing with approximately 60-frame/second design target; measured frame rate and CPU behaviour are system dependent.

## Scope and caveats

- **PCM Golden measurement path preserved.** Component is visualization-only, not a DSP or PCM→DSD converter.
- DSD FAST measures **raw 1-bit modulation density**, not a low-pass-filtered analog output waveform or a certified DSD true-peak value. PCM and DSD numbers are not physically identical measurement units.
- LPF controls (20–200 kHz, planned default 40 kHz; Slow/Normal/Sharp) are **future work and unavailable in v0.8.0**.
- Verified: Windows x64 Release build, v0.8 display in PEAK_TEST and DSD512 playback, synthetic auto-window tests for the six supported formats. All-device long-term validation remains open.
- DarkOne4Mod/JSplitter font errors are third-party skin startup issues, not bundled fixes in this component.

## Screenshots of v0.8.0 updates

### Automatic DSD512 meter and responsive horizontal layout

![v0.8 DSD512 horizontal live view](images/v080/meter_horizontal.png)

### Responsive vertical layout

![v0.8 DSD512 vertical live view](images/v080/meter_vertical.png)

### DSD FAST calibration tab

![DSD FAST settings](images/v080/pref_en_dsd.png)

### Horizontal minimum-size mode

![Horizontal minimum-size display](images/v080/meter_horizontal_min.png)

### Vertical minimum-size mode

![Vertical minimum-size display](images/v080/meter_vertical_min.png)
