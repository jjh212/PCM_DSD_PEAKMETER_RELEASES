# PCM/DSD PeakMeter v0.8.0 for foobar2000

**[Download v0.8.0](https://github.com/jjh212/PCM_DSD_PEAKMETER_RELEASES/releases/tag/v0.8.0)** · **Windows x64** · Native C++ · [English manual](docs/USER_MANUAL_EN.md) · [한국어 설명서](docs/USER_MANUAL_KO.md) · [Change history](CHANGELOG.md)

## English

An independent/Columns UI stereo PCM/DSD peak meter for foobar2000. **DoP-marker-based automatic detection** (`0x05/0xFA`), PCM sample-rate or DSD64–2048 format indication, and **per-format FAST direct-modulation measurement** (28–896 bit moving windows). **Manual PCM/DSD switching has been removed**. Includes L/R peaks, Peak Hold, warning counts/maxima, clickable statistics reset, horizontal/vertical minimum modes, per-panel appearance themes, and English/Korean settings.

The DSD default **−4.8586 dB FAST offset is display-only**. **LPF is not implemented** in this release; this is **not a certified reconstructed-audio DSD True Peak meter**. It does not alter actual playback data or DAC mode.

### Screenshots

![v0.8.0 horizontal PCM/DSD PeakMeter](docs/images/v080/meter_horizontal.png)

![v0.8.0 vertical PCM/DSD PeakMeter](docs/images/v080/meter_vertical.png)

### Install

Exit foobar2000, back up the installed DLL and replace `profile\user-components-x64\foo_pcm_dsd_peakmeter\foo_pcm_dsd_peakmeter.dll` in your **actual portable host folder**, then restart. Download/check SHA256 from the Release assets. Latest DLL SHA256: `DFEE5B07E0C23D4252C3382F5CE69616D479445B449C20C34031FB33D4F17E60`.

## 한국어

foobar2000용 Windows x64 네이티브 C++ PCM/DSD 스테레오 피크미터입니다. **DoP 마커(`0x05/0xFA`)로 자동 판별**하며 **수동 전환 모드는 제거**했습니다. PCM은 실제 샘플레이트, DSD는 DSD64~2048 포맷을 표시하고 **포맷별 28~896비트 FAST 직접 변조 피크**를 계산합니다. 좌우 독립 피크바/Peak Hold, 경고 진입 횟수·최고 피크, **통계영역 클릭 초기화**, 가로/세로·최소 모드, 패널별 사용자 테마와 한글/영문 UI를 제공합니다.

DSD FAST 기본 **−4.8586 dB 보정은 표시 전용**입니다. **v0.8.0에서 LPF는 미구현**이며 재구성된 아날로그 파형의 공인 DSD True Peak를 표시한다고 주장하지 않습니다. 재생 오디오 데이터·출력 기기를 변경하지 않습니다.

**설치:** foobar2000 완전 종료 → 기존 DLL 백업 → Release 다운로드와 SHA256 검증 → 실제 Portable 설치본의 `profile\user-components-x64\foo_pcm_dsd_peakmeter\foo_pcm_dsd_peakmeter.dll` 교체 → 재시작.

### 문서 / Documentation

- [사용설명서 한국어](docs/USER_MANUAL_KO.md) · [User manual English](docs/USER_MANUAL_EN.md) · [통합 설명서 / combined](docs/USER_MANUAL.md)
- [업데이트 내역 한국어](docs/CHANGELOG_V080_KO.md) · [Changelog English](docs/CHANGELOG_V080_EN.md)
- [이전 v0.4.0 릴리스](https://github.com/jjh212/PCM_DSD_PEAKMETER_RELEASES/releases/tag/v0.4.0)

## Minimum-size views / 최소 모드

**Horizontal minimum / 가로 최소**

![Minimum horizontal mode](docs/images/v080/meter_horizontal_min.png)

**Vertical minimum / 세로 최소**

![Minimum vertical mode](docs/images/v080/meter_vertical_min.png)
