# Changelog — PCM/DSD PeakMeter

## v0.4.0 (2026-10-13) — Host Resize V2

**Status:** Official [v0.4.0 stable release](https://github.com/jjh212/PCM_DSD_PEAKMETER_RELEASES/releases/tag/v0.4.0) published 2026-10-13. Binary artifact + checksum file uploaded and independently downloaded for SHA256 verification. **The historical changelog below refers to this verified DLL.**

### 사용자 관점 변경 요약
- 최소 크기 도달 후 창이 더 줄어들지 않도록 수정했습니다. 예전처럼 지나치게 좁은 영역에서 피크미터가 사라지는 동작을 사용하지 않습니다.
- 가로 모드: 최소 너비 **버튼부 +100px**, 최소 높이 **버튼부 높이**.
- 세로 모드: 최소 너비 **버튼부 너비**, 최소 높이 **버튼부 +100px**.
- 버튼부 정의: PCM/DSD 버튼 + 제목 글자. 글꼴/버튼 설정을 반영해 동적으로 최소 크기를 계산합니다.
- 공간이 부족할 때 미터와 버튼을 남기고 dB 글자만 선택적으로 생략합니다.
- 독립 창과 Columns UI 삽입형의 크기 제한을 각각 구현했습니다.

### 기술적 수정
- `core/v040_minimum_size.hpp`: 가로/세로 최소 크기 산식 정리.
- `win/main.cpp`: 삽입형 `WM_GETMINMAXINFO` 제한 + 호스트 `on_size_limit_change` 통지.
- `win/v040_standalone.hpp`: 독립 창 `WM_GETMINMAXINFO` 유지, `WM_SIZING` 8방향 제한 및 DPI 호환 처리.
- Windows 도구체인: VS2026 / MSVC v145. v143 필요 오류 및 DPI API 선언 문제를 수정하고 x64 Release 빌드 완료.
- 기존 미터 알고리즘, PCM/DSD 자동·수동 판별, Preferences 구조, 사용자 설정, 폰트/색상 시스템과 Z-order 동작은 최소 크기 패치에서 변경하지 않았습니다.

### v0.4 전체 기능
- PCM/DSD 표시 자동 판별, 수동 PCM/DSD 선택.
- 250ms Core DSP 상태 조사, 적용 확인된 프리셋/사용자 DSP 규칙, 식별 가능한 DSD Processor/Trellis 경로.
- 기본 PCM 0 dB / DSD −6 dB 표시 보정, 사용자 보정 규칙.
- 가로·세로 방향, 스테레오 채널, 피크 홀드, 편집 가능한 dB 눈금과 미터 색.
- 글꼴·버튼 스타일, 독립 창, Columns UI 패널, 사용자 정의 테마(JSON 가져오기/내보내기).
- 모든 기능은 **표시 전용**이며 음악 출력 경로를 변경하지 않습니다.

### 검증
| 검증 대상 | 결과 |
|---|---|
| Windows Release x64 DLL 빌드 | PASS |
| C++ core/layout tests | **15 / 15 PASS** |
| 독립 창 가로 최소 크기 | PASS |
| 독립 창 세로 최소 크기 | PASS |
| Columns UI 가로 최소 크기 | PASS |
| Columns UI 세로 최소 크기 | PASS |
| 최소 크기 버튼·피크바·dB 레이블 | PASS |
| 기존 자동 판별·피크·Preferences | PASS (선행 실사용 검증) |

**정확한 검증 DLL:** 471,040 bytes, SHA256 `74C66AF9E58B5040F6243A90E6DD39B65AB5B1C6B93A4E2A0A5127D6E5535A55`.

### 미해결/별도 과제
- DarkOne 전체화면의 독립 창 Z-order 가림 현상. 다른 컴포넌트에서도 관찰됨. 원인을 확정하거나 여기서 해결했다고 주장하지 않습니다.
- 서드파티 환경에서 foo_outinfo를 제거한 깨끗한 설치 상태의 독립 검증은 공개 배포 전 추가 검증 권장.
- 기존 Columns UI Helper의 C4996 경고 정리는 별도 버전에서 다룹니다.
- 공개 배포 바이너리는 GitHub Release 자산 업로드/해시 재검증 뒤에만 안내합니다.

### 비고
본 문서와 [사용 설명서](docs/USER_MANUAL_KO.md)는 개발자가 승인한 최소 창 크기 규칙과 실제 사용자 실사용 판정을 기준으로 합니다.
