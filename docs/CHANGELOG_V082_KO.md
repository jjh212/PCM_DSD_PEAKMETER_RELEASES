# PCM/DSD PeakMeter v0.8.2 — Peak Hold 액션 개선 (한국어)

**일자:** 2026-10-15 · **환경:** foobar2000 Windows x64 / Columns UI / 독립 창

## 수정 항목 (1개)

- PCM과 DSD의 **최대 피크 마커(Peak Hold)**가 신규 피크에 즉시 반응하고, 일정 시간 유지한 뒤 현재 피크바 쪽으로 연속 하강하며, 하강 중 더 높은 피크가 나오면 다시 즉시 반응하도록 개선.
- 초기 설정: **유지 0.50초**, **마커 하강 30 dB/s**. 사용자의 PEAK_TEST에서 foobar2000 내장 Peak Meter와 시각 비교 후 채택.
- 종전의 1.4초 유지 뒤 현재 피크값으로 순간 이동하는 동작을 PCM·DSD 모두 교체.

## 변경하지 않은 항목

오디오 입력/출력, PCM/DSD 계측식, DoP 자동판별, DSD 포맷별 비트 윈도우, **일반 피크바 하강 속도**(PCM 18 dB/s, DSD 60 dB/s), 경고·통계·표시 보정, 화면 배치, 사용자 설정, UI 프레임 클럭.

본 컴포넌트는 표시 전용이며 DSD FAST는 직접 변조 측정값임. 재구성 파형의 True Peak나 LPF는 이번 업데이트에 포함하지 않음.

**v0.8.2 DLL SHA256:** `6A1CF501C12A00BEB92A11FAB139A3EB14BA22C94F1678C031D33549131AC7FC`

**관련 자료:** [한국어 설명서](USER_MANUAL_KO.md) · [v0.8.1 변경내역](CHANGELOG_V081_KO.md).
