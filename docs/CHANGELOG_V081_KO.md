# PCM/DSD PeakMeter v0.8.1 — 수정 내역 (한국어)

**일자:** 2026-10-15 · **환경:** Windows x64 / foobar2000 / Columns UI

### 수정 항목

- `DECLARE_COMPONENT_VERSION`의 컴포넌트 등록 버전을 `0.4.0` → `0.8.1`로 변경. **환경설정 → Components**에서도 정식 버전으로 표시.
- **환경설정 → Tools → PCM/DSD PeakMeter → 일반** 화면의 버전을 `0.8.1`로 통일.
- 컴포넌트 설명에 남아 있던 `TEST ONLY` 시험용 문구 및 구버전 시작 진단 문자열 정리.
- 실제 PCM/DoP DSD 피크미터 구현과 맞지 않던 오래된 소스 헤더 주석 정리.

### 변경하지 않은 항목

- v0.8.0 PCM/DSD 계측, DoP 마커 자동판별·1초 다수결, DSD64~2048 비트연산, Peak Hold, 경고 통계, 보정값, UI·설정값은 그대로 유지.
- PCM/DSD 수동 전환 모드는 제거된 상태 유지. 두 표시는 조작 버튼이 아니라 인디케이터.
- LPF, 재구성 DSD 파형의 True Peak 측정은 아직 구현하지 않음.

### DLL 무결성

- 파일: `foo_pcm_dsd_peakmeter.dll`
- SHA256: `757A49FEE98FF97CA316D03F1AB772665945586F8661232279FE22BADE27A144`
- Visual Studio 2026 / MSVC v145 / Release x64 빌드.
- 원본 해시 보호 독립 빌드, PEAK_TEST·실사용본 백업 후 배포 검증. 전 DSD 포맷의 실제 하드웨어 실증 완료를 의미하지는 않음.

**전체 기능 및 이미지 설명서:** [한국어 사용설명서](USER_MANUAL_KO.md) · [v0.8.0 상세 기능 내역](CHANGELOG_V080_KO.md).
