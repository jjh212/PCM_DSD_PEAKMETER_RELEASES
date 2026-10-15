# v1.0 변경내역 — 한국어

PCM/DSD PeakMeter의 사용자 승인 최종본입니다. v0.8.2 이후의 변경사항을 포함하며 기존 버전 이력은 보존합니다.

## 주요 기능

- DSD 측정 모드 선택: FAST 직접 변조 피크 / LPF 필터 처리 피크.
- FAST 포맷별 28–896비트 이동 윈도우와 사용자 표시 보정값(기본 −4.8586 dB).
- LPF 측정 전용 High-cut: Cut-off 20–200 kHz, 기본 40 kHz.
- Slow Roll-off, Medium Roll-off(이전 Normal), Sharp Roll-off, 기본 Medium.
- 주파수 응답곡선은 선택된 방식 한 개만 표시하며 고정 축에서 컷오프를 안내.
- PCM/DSD 피크미터 상·하단 초과 눈금 글자 강조; 밝아지는 배경 제거.
- PCM 주의/위험: 0 dB / +5 dB. DSD 주의/위험: 0 dB / +3.1 dB.
- Components 및 한영 일반 탭 버전 1.0 표시.
- 한국어/영어 설명서 및 v1.0 DSD UI 스크린샷 갱신.

## 검증과 범위

- MSVC v145 Release x64 TEST 전체 빌드 성공.
- Karma / DSD64 / SDM Type B 실사용 화면에서 Cut-off·Roll-off 설정에 따른 실제 피크미터 값 변화 확인.
- Stage 26 UI 수정 실사용 승인 및 v1.0 버전 표시 확인.
- DSD LPF는 **계측 데이터에만 적용**. 재생 신호·DSP 출력·DAC 신호를 변경하지 않음.
- LPF 응답 계산값은 오디오 출력이나 인증된 DSD True Peak를 의미하지 않음.

**최종 검증 TEST DLL SHA256:** `AA2F514B8C8199923BBEE9F730A42222878B437DF5F6558BA94C6268160CF561`

공식 배포용 DLL 및 설치 패키지의 최종 해시는 릴리스의 `SHA256SUMS.txt`에서 확인합니다.

### 설명서 및 UI 이미지 확정

- 한국어·영어 설정 탭 14장, PCM 화면 2장, DSD512 화면 4장, 메뉴 1장, Components 1장 등 **사용자 제공 UI 이미지 22장** 반영.
- 기능·신호 경로 수정 없음. 설명서 및 이미지 갱신만 수행.
