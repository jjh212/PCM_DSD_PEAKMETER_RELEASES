# PCM/DSD PeakMeter 문제 해결

## 업데이트했는데 이전 크기 제한으로 보인다
포터블 foobar2000을 여러 개 사용하는 경우 **서로 다른 DLL**이 로드될 수 있습니다. 실제 실행된 `foobar2000.exe` 위치와 모듈 경로를 확인하세요. 사용본만 바꾸고 `PEAK_TEST`를 실행한 사례가 실제로 있었습니다.

검사 예시(PowerShell, 실행 중인 foobar2000을 종료하지 말 것):
```powershell
Get-Process -Name 'foobar2000*' | ForEach-Object {
  Write-Host "PID=$($_.Id) EXE=$($_.Path)"
  $_.Modules | Where-Object ModuleName -eq 'foo_pcm_dsd_peakmeter.dll' |
    ForEach-Object { Write-Host "DLL=$($_.FileName)" }
}
```
권한/호스트 아키텍처에 따라 Modules 조회가 실패할 수 있습니다. 해당 경우 설치본 경로와 실제 프로세스를 별도 확인하세요.

## 컴포넌트가 로드되지 않는다
- foobar2000이 완전히 종료된 상태에서 올바른 x64 컴포넌트를 복사했는지 확인하세요.
- 이전 DLL을 복구할 수 있도록 백업 보존.
- 해시: `74C66AF9E58B5040F6243A90E6DD39B65AB5B1C6B93A4E2A0A5127D6E5535A55`, 크기 471,040 bytes.
- foobar2000 콘솔에 관련 오류가 있는지 확인합니다.

## 최소 크기에서 내용이 보이지 않는다
v0.4.0 V2는 독립 창과 Columns UI 패널 모두 테스트 PASS입니다. 실제 로딩 DLL이 V2인지 먼저 확인하고, 방향과 버튼/폰트 설정, 호스트 스플리터 설정을 확인합니다.

## 전체화면 DarkOne에서 독립 미터가 뒤로 가려진다
관련 현상은 별도 Z-order 이슈입니다. 이번 최소 크기 보정과 관계없습니다. DarkOne 테마 문제라고 **확정되지는 않았습니다**.

## DSD 표시가 예상과 다르다
PCM/DSD 자동 판단은 확인된 DSP chain과 사용자 규칙에 의존합니다. SACD Output 설정만으로 판별하지 않습니다. PCM 0dB/DSD -6dB는 미터 표시 보정값이며 출력 변환·true peak 측정 인증이 아닙니다. 사용자의 활성 DSP 프리셋/규칙과 수동 모드 상태를 확인하세요.
