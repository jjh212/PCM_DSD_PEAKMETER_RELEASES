# PCM/DSD PeakMeter — Change History / 변경내역

## v0.8.1 — Metadata maintenance (2026-10-15)

- [English](docs/CHANGELOG_V081_EN.md) | [한국어](docs/CHANGELOG_V081_KO.md)
- DLL SHA256: 757A49FEE98FF97CA316D03F1AB772665945586F8661232279FE22BADE27A144

---


## v0.8.0 (2026-10-14)

- [English v0.8.0 details](docs/CHANGELOG_V080_EN.md)
- [한국어 v0.8.0 업데이트](docs/CHANGELOG_V080_KO.md)
- Binary SHA256: DFEE5B07E0C23D4252C3382F5CE69616D479445B449C20C34031FB33D4F17E60

---

# PCM/DSD PeakMeter — Changelog / 변경내역

## English

### v0.4.0 — Stable release (2026-10-13)

**Download:** [official v0.4.0](https://github.com/jjh212/PCM_DSD_PEAKMETER_RELEASES/releases/tag/v0.4.0) · **Binary:** 471,040 bytes · **SHA256:** `74C66AF9E58B5040F6243A90E6DD39B65AB5B1C6B93A4E2A0A5127D6E5535A55`.

#### Visible changes and new user controls

1. **Minimum usable dimensions (new in v0.4.0).** Standalone and Columns UI embedded meters now honor minimum bounds. The window stops shrinking, rather than blanking the bars and PCM/DSD buttons.
2. **Horizontal layout:** minimum client width = button/title cluster width **+100 px**; minimum client height = cluster height.
3. **Vertical UP/DOWN:** minimum client width = cluster width; minimum client height = cluster height **+100 px**.
4. **Compact rendering:** keep bar and mode controls visible; omit colliding dB tick text only when insufficient space remains. Limits respond to button size, title font and DPI.
5. **Global configuration:** bilingual UI, global PCM/DSD display corrections, preset and DSP component rules; automatic route selection uses actual applied DSP evidence.
6. **Per-panel configuration:** orientation, button dimensions, editable dB scale, color styles, installed fonts, button shapes and state colors.
7. **User theme library:** save, load, rename, remove, JSON export/import of **appearance settings only**. Global DSP rules are not part of a theme.
8. **Independent window and Columns UI mode:** standalone placement/sizing preservation; host minimum-size notification for embedded panels.

#### Implementation and regression scope

- The Windows standalone frame enforces limits with `WM_GETMINMAXINFO` and `WM_SIZING` across edge/corner drag directions; DPI-aware frame-size fallback is supported.
- Columns UI integrates `WM_GETMINMAXINFO` and host `on_size_limit_change` notification.
- C++ minimum-size geometry is separately regression-tested, including content-preserving compact rendering.
- The meter remains **display-only**: does not insert a DSP, change playback samples, switch DAC modes or perform PCM→DSD conversion.
- Auto route priority: user applied-preset rule → user component rule by chain order → built-in recognized DSD DSP → unknown. A SACD Output value alone does not confirm the route; manual PCM/DSD selection is a separate state.
- Legacy V3 rendering semantics, panel persistence and the existing meter behavior were preserved as part of the resize patch.

#### Verified release evidence

| Check | Result |
|---|---|
| Windows Release x64 / VS2026 / MSVC v145 | PASS |
| Core/layout regression tests | **15 / 15 PASS** |
| Standalone horizontal and vertical minimum-size tests | **2 / 2 PASS** |
| Columns UI horizontal and vertical minimum-size tests | **2 / 2 PASS** |
| Compact meter/buttons/tick-label test | **1 / 1 PASS** |
| Previous meter/routes/Preferences validation | PASS in earlier acceptance |
| Four backed-up portable installation DLLs | Identical SHA256 / **4 of 4 PASS** |
| GitHub Release binary re-download and SHA256 | PASS |

#### Known limits / not changed

- The DarkOne fullscreen **Z-order** issue is a separate topic and is **not** claimed fixed.
- This is not a certified native DSD bitstream true-peak analyzer. DSD −6dB is a **display correction** default.
- Existing third-party SDK deprecation/build warnings are tracked separately; no mass SDK replacement was performed as part of minimum-size work.
- Test results document the verified environment rather than universal compatibility with every foobar2000 theme.

---

## 한국어

### v0.4.0 — 정식 릴리스 (2026-10-13)

**다운로드:** [공식 v0.4.0](https://github.com/jjh212/PCM_DSD_PEAKMETER_RELEASES/releases/tag/v0.4.0) · **DLL 크기:** 471,040바이트 · **SHA256:** `74C66AF9E58B5040F6243A90E6DD39B65AB5B1C6B93A4E2A0A5127D6E5535A55`.

#### 사용자에게 보이는 기능 변경

1. **최소 크기 보호(이번 버전의 핵심).** 독립 창과 Columns UI 삽입형 모두 최소 크기 이하로 줄어들지 않도록 변경했습니다. 창을 지나치게 줄였을 때 피크바와 버튼이 사라지는 현상을 방지합니다.
2. **가로 방향:** 최소 클라이언트 너비 = 버튼/제목 묶음 너비 **+100px**; 최소 높이 = 버튼부 높이.
3. **세로 UP/DOWN:** 최소 너비 = 버튼부 너비; 최소 높이 = 버튼부 높이 **+100px**.
4. **축소 상태 렌더링:** 피크바와 PCM/DSD 버튼은 표시하고, 공간이 부족할 경우 겹치는 dB 눈금 텍스트만 생략합니다. 실제 버튼 크기·글꼴·DPI에 맞춰 제한값을 계산합니다.
5. **전역 설정:** 한글·영문 UI, PCM/DSD 표시 보정, DSP 프리셋 및 구성요소 규칙. 자동 판별은 실제 적용 DSP 체인 근거를 사용합니다.
6. **패널별 설정:** 방향, 버튼 치수, dB 눈금, 색상, 설치 글꼴, 버튼 모양 및 상태별 색상.
7. **사용자 테마:** 패널의 **디자인만** 저장·불러오기·이름변경·삭제·JSON 가져오기/내보내기 합니다. 전역 DSP 규칙은 테마에 포함되지 않습니다.
8. **독립 창 및 Columns UI:** 독립 창의 위치·크기 유지와 삽입형 패널 호스트의 최소 크기 변경 통지를 지원합니다.

#### 기술적 구현·회귀검증 범위

- 독립 창은 `WM_GETMINMAXINFO`, `WM_SIZING`에서 최소 크기 강제 및 DPI 호환 프레임 계산을 수행합니다.
- Columns UI는 `WM_GETMINMAXINFO`와 `on_size_limit_change` 호스트 통지로 제한값 변경을 전달합니다.
- 최소 크기 계산·렌더링 보존을 별도 C++ 회귀 테스트로 검증했습니다.
- 오디오 DSP 삽입, 샘플 수정, 출력 모드 전환, PCM→DSD 변환은 수행하지 않습니다.
- 자동 판별 우선순위: 실제 적용 프리셋 규칙 → 실제 DSP 구성요소 규칙(체인 순위) → 내장 DSD DSP 확인 → Unknown. SACD Output 단독으로 확정하지 않으며 수동 선택은 별도 상태입니다.
- 최소 크기 작업으로 기존 V3 피크 렌더링·설정 저장 및 나머지 피크미터 기능을 임의 변경하지 않았습니다.

#### 릴리스 검증 결과

| 검증 | 결과 |
|---|---|
| Windows Release x64 / VS2026 / MSVC v145 | PASS |
| Core/레이아웃 자동 테스트 | **15 / 15 PASS** |
| 독립 창 가로·세로 최소 크기 | **2 / 2 PASS** |
| Columns UI 가로·세로 최소 크기 | **2 / 2 PASS** |
| 축소 상태 피크바·버튼·dB 글자 처리 | **1 / 1 PASS** |
| 기존 피크·판별·Preferences 기능 | 선행 실사용 검증 PASS |
| Portable 4개 설치본(각각 백업) | 동일 SHA256 **4 / 4 PASS** |
| GitHub Release DLL 재다운로드 SHA256 | PASS |

#### 이번 버전의 범위 밖

- DarkOne 전체화면의 독립 창 **Z-order** 가림 현상은 별도 진단 과제로 유지합니다. 이번에 해결했다고 주장하지 않습니다.
- DSD −6dB는 **표시 보정 기본값**이며 네이티브 DSD True Peak 측정 인증이 아닙니다.
- 기존 SDK의 레거시 경고 정리는 이번 최소 크기 기능 범위가 아닙니다.
- 검증된 Windows/foobar2000 구성 이외의 모든 테마에서 호환성을 보장한다고 주장하지 않습니다.

[Illustrated manual / 19장 이미지 상세 설명서](docs/USER_MANUAL.md)
