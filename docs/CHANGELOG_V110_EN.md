# PCM/DSD PeakMeter 1.1.0
Released: 2026-10-23

## Changes

- Preferences tabs wrap onto multiple rows without overflow arrows. Layout follows the actual header height after language changes.
- Fixed repaint fragments across labels and buttons during layout changes, tab switching and scrolling.
- Panel Appearance: hide peak warnings and statistics to expand the meter into the released space.
- dB Scale: show labels on both sides, the upper side only, or the lower side only. Vertical layouts use the corresponding rotated sides.
- Meter Colours: toggle Peak Hold, select its RGB colour, restore automatic colour, and choose a fall speed of 10 / 30 / 60 / 120 dB/s. The default is 30 dB/s; the existing 0.50-second hold time is retained.
- Panel Appearance: optional Freeze meter on Pause. Disabled by default, preserving reset-on-pause behaviour. Stop resets the meter even after a frozen pause.
- Changing tick/channel text colours preserves existing font metrics and hold-marker shape. Reset fonts restores the original default metrics and marker shape.
- New per-panel options are saved by Apply/OK and included in theme save/load/import/export.
- Korean/English panel status and scale-row captions refresh immediately when the language changes.
- In-component display checks are available on General; the accepted R7 build passed 28/28 checks.

PCM sample-peak measurement, DoP detection and DSD FAST/LPF measurement kernels are unchanged. No playback audio is modified.

## Installation

Recommended: install `foo_pcm_dsd_peakmeter_v1.1.0.fb2k-component` via Preferences > Components > Install and restart foobar2000. It contains the x86 DLL at the archive root and the x64 DLL under `x64/`. Separate x86/x64 packages are also available.

Select the intended panel before editing. Press Apply or OK to save changes. Scroll down in Meter Colours to reach all Peak Hold options.

## Compatibility and verification

Existing unedited V1–V6 panel records retain their original encoding. Edited records use V7. Back up the profile before downgrading to older component versions that do not understand V7.

Both architectures were built with MSVC v145 and their package entries, DLL bytes and PE architectures were checked. The user accepted the R7 test-host functions and Korean/English Preferences, including the repaint repair and pause freeze. Separate x86 host runtime loading and the official Components Get updates path are not recorded as verified in this release preparation.

## DLL SHA256

- x64: `AB3857BFBB860F8B4F7BA36695C281947B0858FAF6DEEBB413F7F5EE64AE3AE6`
- x86: `78012BFB702ECEEC43903468AED8DFD87E324FCA172DEF0052E6E94E9E9FA4FD`

Package hashes are provided in SHA256SUMS.txt.
