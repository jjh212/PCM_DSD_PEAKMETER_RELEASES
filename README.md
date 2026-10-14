# PCM/DSD PeakMeter v0.8.1 — foobar2000 x64

**Latest release:** [v0.8.1](https://github.com/jjh212/PCM_DSD_PEAKMETER_RELEASES/releases/tag/v0.8.1) · [English manual](docs/USER_MANUAL_EN.md) · [한국어 설명서](docs/USER_MANUAL_KO.md) · [Full changelog](CHANGELOG.md)

## English

**v0.8.1 is a metadata-only maintenance release of v0.8.0.** foobar2000 Components now identifies this component as **0.8.1**, the General Preferences page identifies **0.8.1**, outdated `TEST ONLY` component wording has been removed, and startup diagnostics use the current version. **Peak measurement, PCM/DSD automatic detection, DSP and audio output processing, layout, and calibration are unchanged.**

Main features (introduced in v0.8.0): DoP markers `0x05` / `0xFA` with 1-second voting, PCM sample-rate and DSD64–2048 format indications, format-specific 28–896-bit FAST direct-modulation windows, per-channel stereo peaks, peak hold, warning counters, maximum values, clickable statistics reset, horizontal/vertical compact layouts, panel themes and bilingual Preferences. **Manual PCM/DSD switching is not available.**

DSD FAST default offset: **−4.8586 dB** (display only, user-adjustable). **LPF audio reconstruction and certified DSD true-peak metering are not implemented.** The component never modifies output audio or changes the DAC mode. Actual end-to-end DSD runtime verification is not claimed for all six DSD rates.

### Downloads / integrity

- DLL: `foo_pcm_dsd_peakmeter.dll` — SHA256: `757A49FEE98FF97CA316D03F1AB772665945586F8661232279FE22BADE27A144`.
- [v0.8.1 release package and SHA256SUMS](https://github.com/jjh212/PCM_DSD_PEAKMETER_RELEASES/releases/tag/v0.8.1)
- [v0.8.1 patch notes (English)](docs/CHANGELOG_V081_EN.md)
- [v0.8.0 full feature changes](docs/CHANGELOG_V080_EN.md)

Close foobar2000 before replacing the DLL; preserve a backup of the previous component. The usual portable component path is `profile\user-components-x64\foo_pcm_dsd_peakmeter\foo_pcm_dsd_peakmeter.dll`.

## 한국어

**v0.8.1은 v0.8.0의 메타데이터 정정 릴리스입니다.** foobar2000 Components에 표시되는 컴포넌트 버전과 Preferences 일반 탭의 버전을 **0.8.1**로 통일하고, `TEST ONLY` 시험판 표기 및 구버전 시작 진단 문구를 정리했습니다. **PCM/DSD 판별·피크 계측·출력 신호·UI·보정 알고리즘은 변경하지 않았습니다.**

v0.8.0 기능: DoP 마커 자동판별(수동 전환 없음), PCM 샘플레이트·DSD64~2048 포맷 표시, 포맷별 28~896비트 FAST 측정, 좌우 피크/홀드·경고·최대치·통계 초기화, 가로/세로 최소 레이아웃, 테마 및 한영 환경설정. FAST −4.8586 dB는 표시 보정이며 **LPF 및 재구성된 DSD True Peak 계측은 미구현**입니다.

- [v0.8.1 변경 내역 한국어](docs/CHANGELOG_V081_KO.md)
- [v0.8.0 기능 변경 내역](docs/CHANGELOG_V080_KO.md)
- [한국어 사용설명서](docs/USER_MANUAL_KO.md) · [English User Manual](docs/USER_MANUAL_EN.md)

### Horizontal and vertical / 가로·세로 실사용 화면

![Horizontal](docs/images/v080/meter_horizontal.png)

![Vertical](docs/images/v080/meter_vertical.png)

### Minimum-size modes / 최소 모드

**가로 최소 / Horizontal minimum**

![Horizontal minimum](docs/images/v080/meter_horizontal_min.png)

**세로 최소 / Vertical minimum**

![Vertical minimum](docs/images/v080/meter_vertical_min.png)

Earlier stable releases, including [v0.8.0](https://github.com/jjh212/PCM_DSD_PEAKMETER_RELEASES/releases/tag/v0.8.0), remain available. 이전 릴리스는 보존합니다.
