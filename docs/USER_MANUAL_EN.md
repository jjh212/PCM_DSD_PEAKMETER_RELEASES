# PCM/DSD PeakMeter v0.4.0 User Manual

**For:** foobar2000 Windows x64 / Columns UI; standalone and embedded meter.

## Purpose and limitations
PCM/DSD PeakMeter is a native C++ **display-only** level visualization component. It does not process, convert, resample or modify audio. The default PCM display correction is **0 dB** and the DSD display correction is **−6 dB**. These are visualization corrections, **not calibrated measurements of the DAC output or DSD bitstream**.

## Installation
1. Fully close foobar2000 and back up the current `foo_pcm_dsd_peakmeter.dll`.
2. Once the verified v0.4.0 DLL is actually published as a GitHub Release asset, download that artifact. **No public binary asset is currently attached to this repository.**
3. Validate its SHA256 against `74C66AF9E58B5040F6243A90E6DD39B65AB5B1C6B93A4E2A0A5127D6E5535A55` (size 471,040 bytes).
4. Install to your foobar2000 portable profile under `profile\user-components-x64\foo_pcm_dsd_peakmeter\foo_pcm_dsd_peakmeter.dll`. Each portable installation has its own copy; do not assume installing into one updates another.
5. Relaunch foobar2000, verify the component loaded, and test it.

## Usage
- Open the independent **PCM/DSD PeakMeter** window from foobar2000's menu.
- Add the meter to a Columns UI panel layout for the embedded mode.
- Right-click a meter to access its Preferences (same settings page as the main menu).
- Use **PCM** / **DSD** on the meter for a manual display choice.
- Assign rules in **DSP Presets** and **DSP Components**. Only a preset confirmed to match the applied Core DSP chain is treated as active. SACD Output settings alone are not a confirmed route.
- Customize eight Preferences tabs: General, DSP Presets, DSP Components, Panel Appearance, dB Scale, Meter Colours, Fonts / Buttons and Custom Themes.
- Choose horizontal or vertical orientation, buttons, font, colors and tick labels on a per-panel basis.

## v0.4.0 minimum-size behavior
The **button cluster** comprises both PCM/DSD buttons plus the meter title. Minimum **client** sizes (not including OS window border):

| Layout | Min width | Min height |
|---|---|---|
| Horizontal | Cluster width + **100 px** | Cluster height |
| Vertical | Cluster width | Cluster height + **100 px** |

Minimum size adapts to button and font settings. Further shrinking is prevented, rather than leaving a blank canvas. Meter bars and controls remain visible. When too cramped, overlapping dB number labels may be omitted. Standalone windows enforce drag constraints via Win32; embedded Columns UI panels notify the host of new size limits.

## Known limitations
- Fullscreen DarkOne Z-order interactions are a separate issue and are **not** fixed by this resize release.
- Do not interpret the displayed DSD value as a verified true-peak measurement of a native DSD bitstream.
- Multiple portable installations load separate DLLs; check the actual running executable and module path if an update appears to have no effect.
- SDK deprecation warnings remain for existing Columns UI wrapper code.

[한국어 설명서](USER_MANUAL_KO.md) · [Release history](../CHANGELOG.md)
