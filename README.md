# PCM/DSD PeakMeter for foobar2000

## English

### v0.4.0 — Official Stable Release

Native Windows x64 C++ **display-only** PCM/DSD stereo peak meter for foobar2000. Use it as a standalone window or an embedded Columns UI panel. The v0.4.0 stable release is **published and available to download**.

**[Download v0.4.0](https://github.com/jjh212/PCM_DSD_PEAKMETER_RELEASES/releases/tag/v0.4.0)** · [Direct DLL](https://github.com/jjh212/PCM_DSD_PEAKMETER_RELEASES/releases/download/v0.4.0/foo_pcm_dsd_peakmeter.dll) · [SHA256SUMS](https://github.com/jjh212/PCM_DSD_PEAKMETER_RELEASES/releases/download/v0.4.0/SHA256SUMS.txt)

- **471,040 bytes** · SHA256: `74C66AF9E58B5040F6243A90E6DD39B65AB5B1C6B93A4E2A0A5127D6E5535A55`
- Horizontal / vertical stereo peak bars, PCM/DSD automatic display detection and manual mode buttons.
- Configurable display-level correction (PCM 0 dB; DSD −6 dB default), scale, appearance, fonts, buttons and themes.
- Standalone and embedded minimum-size constraints: stop shrinking at the computed boundary rather than blanking the meter. dB text may be omitted to prevent overlap.
- Verified Windows x64 Release build, 15/15 core regression tests, 5/5 live resizing checks.
- Display only: does not modify DSP chains, output samples or the audio path; not a certified DSD bitstream true-peak analyzer.
- DarkOne fullscreen Z-order behavior is a separate unresolved matter.

**Documentation:** [Full bilingual manual — English first, Korean below](docs/USER_MANUAL.md) · [English-only manual](docs/USER_MANUAL_EN.md) · [Changelog](CHANGELOG.md)

### Verified minimum-size screenshots

| Vertical | Horizontal |
|:--:|:--:|
| ![Vertical minimum PeakMeter](docs/images/minimum_vertical.png) | ![Horizontal minimum PeakMeter](docs/images/minimum_horizontal.png) |
| Min client width = button cluster width; min height = button cluster height + 100px | Min client width = button cluster width + 100px; min height = button cluster height |

---

## 한국어

### v0.4.0 — 정식 릴리스

foobar2000 Windows x64용 네이티브 C++ **PCM/DSD 피크미터**입니다. 독립 창과 Columns UI 삽입형 패널을 지원하며, 오디오 신호를 변경하지 않는 시각화 전용 컴포넌트입니다.

**[v0.4.0 다운로드](https://github.com/jjh212/PCM_DSD_PEAKMETER_RELEASES/releases/tag/v0.4.0)** · [DLL 직접 다운로드](https://github.com/jjh212/PCM_DSD_PEAKMETER_RELEASES/releases/download/v0.4.0/foo_pcm_dsd_peakmeter.dll) · [SHA256 체크섬](https://github.com/jjh212/PCM_DSD_PEAKMETER_RELEASES/releases/download/v0.4.0/SHA256SUMS.txt)

- **471,040바이트**, SHA256은 위 영문 설명의 값과 동일합니다.
- PCM/DSD 자동 판별, 수동 전환, L/R 피크, 가로·세로 방향, 눈금·글꼴·버튼·색상·사용자 테마 설정.
- PCM 0dB / DSD −6dB 기본 **표시 보정**. 오디오 출력이나 DSP 처리 자체는 변경하지 않습니다.
- 최소 크기에서 더 이상 줄어들지 않도록 수정했습니다. 피크바·버튼은 계속 표시하며, 공간이 부족하면 겹치는 dB 숫자만 생략합니다.
- 독립 창과 Columns UI 패널의 최소 크기 검증 5/5 PASS, 코어 자동 회귀검증 15/15 PASS.
- DarkOne 전체화면의 Z-order 가림 현상은 별도 과제로 남겨두었습니다.

**설명서:** [영문 위·한글 아래 통합 사용 설명서](docs/USER_MANUAL.md) · [한국어 전용 설명서](docs/USER_MANUAL_KO.md) · [상세 업데이트 내역](CHANGELOG.md) · [문제 해결](docs/TROUBLESHOOTING_KO.md)

### 최소 크기 검증 화면

| 세로 모드 | 가로 모드 |
|:--:|:--:|
| ![세로 모드 최소 크기](docs/images/minimum_vertical.png) | ![가로 모드 최소 크기](docs/images/minimum_horizontal.png) |
| 최소 너비 = 버튼부 너비, 높이 = 버튼부 높이 + 100px | 최소 너비 = 버튼부 너비 + 100px, 높이 = 버튼부 높이 |

**설치 전:** foobar2000을 완전히 종료하고 기존 DLL을 백업한 다음, 다운로드한 DLL의 SHA256을 확인하세요. 포터블 설치본마다 각각의 DLL 파일이 존재합니다.
