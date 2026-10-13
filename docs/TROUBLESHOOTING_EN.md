# PCM/DSD PeakMeter — Troubleshooting (English)

[Full manual](USER_MANUAL_EN.md) · [한국어 문제 해결](TROUBLESHOOTING_KO.md) · [v0.4.0 release](https://github.com/jjh212/PCM_DSD_PEAKMETER_RELEASES/releases/tag/v0.4.0)

## 1. I updated the DLL, but the old interface / resizing behavior is still running

Foobar2000 Portable folders each have independent component DLLs. In the v0.4.0 validation an older DLL in the **PEAK_TEST** copy was found even though a different working copy had already been updated. First check the actual running executable and loaded module path:

```powershell
Get-Process | Where-Object { $_.ProcessName -like 'foobar2000*' } | ForEach-Object {
    Write-Host "EXE: $($_.Path)"
    try {
        $_.Modules | Where-Object { $_.ModuleName -eq 'foo_pcm_dsd_peakmeter.dll' } |
            ForEach-Object { Write-Host "DLL: $($_.FileName)" }
    } catch { Write-Host "Module inspection unavailable: $_" }
}
```

If foobar2000 is not running, start the desired installation before inspecting modules. **Never replace a DLL in a running host.** Check each target DLL with:

```powershell
Get-FileHash -Algorithm SHA256 -LiteralPath 'C:\path\to\foo_pcm_dsd_peakmeter.dll'
```

**v0.4.0 expected SHA256:** `74C66AF9E58B5040F6243A90E6DD39B65AB5B1C6B93A4E2A0A5127D6E5535A55`.

## 2. Component does not appear or load

Close foobar2000, check Windows/x64 compatibility, actual component folder, DLL integrity, and foobar2000 Console messages. Back up the old DLL first. Avoid mixing plugin files/configuration from different portable installations. Do not assume a prior release has the same SHA256 or binary size as v0.4.0.

## 3. Bars disappear if the panel is made very small

The v0.4.0 minimum-size rules are:

- Horizontal: client width ≥ button/title cluster width +100px; client height ≥ cluster height.
- Vertical UP/DOWN: client width ≥ cluster width; client height ≥ cluster height +100px.

Verify the actual v0.4.0 DLL is loaded. Check your font/button sizes, orientation, and the host Columns UI layout. dB *text* may be suppressed at extremely small sizes; bars and PCM/DSD buttons are preserved in the verified implementation.

## 4. The meter shows PCM although I configured a DSD preset

The selected DSP Manager preset name alone is **not** evidence of an active processing chain. Verify that the preset is actually applied, that the chain matches it, and that no competing DSP component rule or manual selection is relevant. The resolver uses user applied-preset rules → active user component rules → recognized built-in DSD processors → unknown. Unknown may be shown with PCM as a default without proving the output is PCM. SACD Output setting alone is diagnostic, not conclusive.

## 5. A correction value doesn't seem to affect playback volume

That is intentional: the PCM/DSD corrections affect the **visual display only**. Their defaults are PCM 0dB and DSD −6dB. A matched user rule supplies one correction, not a sum. The component does not modify gain or samples.

## 6. Reset / Apply / Cancel / themes are confusing

**Apply** saves; **OK** saves and closes; **Cancel** only discards changes not yet saved. Reset buttons prepare a new state that still needs Apply/OK. General and DSP rule pages are global; visual design tabs are per-panel. JSON themes contain **appearance only** and never global route/DSP rules. An imported theme name must fit 1–64 UTF-8 bytes.

## 7. DarkOne fullscreen hides the independent window

A fullscreen Z-order interaction was observed, including with other floating components. The cause is not conclusively isolated here, and v0.4.0's sizing fix is **not** a remedy for this unrelated behavior. Test standalone/embedded layouts separately and preserve a working backup.

## 8. DSD level differs from another meter or the DAC display

The default DSD −6dB is a **visual correction** in this component. This release is not a certified native DSD bitstream true-peak analyzer. Do not infer the physical output mode solely from the display label.
