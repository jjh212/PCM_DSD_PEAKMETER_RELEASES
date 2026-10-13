# PCM/DSD PeakMeter — 문제 해결 (한국어)

[상세 사용자 설명서](USER_MANUAL_KO.md) · [English troubleshooting](TROUBLESHOOTING_EN.md) · [v0.4.0 정식 릴리스](https://github.com/jjh212/PCM_DSD_PEAKMETER_RELEASES/releases/tag/v0.4.0)

## 1. DLL을 업데이트했는데 이전 화면·창 크기 동작이 그대로다

Portable foobar2000 폴더마다 DLL이 별도로 존재합니다. v0.4.0 검증 과정에서도 사용본을 업데이트한 뒤 실제로는 이전 DLL이 남은 **PEAK_TEST** 설치본을 실행 중인 사례가 있었습니다. **실행 파일 경로와 실제 로딩 모듈을 먼저 확인**하세요.

```powershell
Get-Process | Where-Object { $_.ProcessName -like 'foobar2000*' } | ForEach-Object {
    Write-Host "EXE: $($_.Path)"
    try {
        $_.Modules | Where-Object { $_.ModuleName -eq 'foo_pcm_dsd_peakmeter.dll' } |
            ForEach-Object { Write-Host "DLL: $($_.FileName)" }
    } catch { Write-Host "모듈 조회 실패: $_" }
}
```

프로세스가 없다면 확인할 foobar2000을 **실행한 상태에서** 검사해야 합니다. 실행 중에는 DLL을 덮어쓰지 마세요. 파일 해시를 확인하는 명령은 다음과 같습니다.

```powershell
Get-FileHash -Algorithm SHA256 -LiteralPath 'C:\path\to\foo_pcm_dsd_peakmeter.dll'
```

**v0.4.0 SHA256:** `74C66AF9E58B5040F6243A90E6DD39B65AB5B1C6B93A4E2A0A5127D6E5535A55`.

## 2. 컴포넌트가 보이지 않거나 로드되지 않는다

foobar2000을 완전히 종료한 뒤 Windows x64 호환성, 실제 컴포넌트 폴더, DLL 무결성, foobar2000 Console 오류를 확인하세요. 기존 DLL은 반드시 백업하세요. 다른 포터블 설치본의 설정 파일이나 DLL을 무심코 혼합하지 마세요. 이전 버전의 바이너리 크기와 SHA256이 v0.4.0과 같다고 가정하면 안 됩니다.

## 3. 아주 작은 크기에서 미터가 사라진다

v0.4.0 최소 크기 규칙은 다음과 같습니다.

- 가로: 클라이언트 너비 ≥ 버튼/제목 너비 +100px, 높이 ≥ 버튼부 높이.
- 세로 UP/DOWN: 너비 ≥ 버튼부 너비, 높이 ≥ 버튼부 높이 +100px.

실제로 v0.4.0 DLL을 로드 중인지 확인하고, 글꼴/버튼 크기, 패널 방향, Columns UI 레이아웃 제한을 점검하세요. 공간 부족 시 **dB 숫자**는 생략될 수 있지만 피크바와 PCM/DSD 버튼은 유지되는 것이 검증된 동작입니다.

## 4. DSD 프리셋을 지정했는데 PCM으로 나온다

DSP Manager에서 **선택된 이름**은 **실제로 적용된 DSP 체인**과 다를 수 있습니다. 프리셋이 적용됐는지, 현재 체인과 정확히 일치하는지, 다른 DSP 구성요소 지정이나 수동 선택이 영향을 주는지 확인하세요. 우선순위는 적용 프리셋 규칙 → 실제 DSP 구성요소 규칙 → 내장 DSD 감지 → Unknown입니다. Unknown 상태의 기본 화면이 PCM이어도 실제 PCM 출력이 확정된 것은 아닙니다. SACD Output 설정 하나만으로도 확정하지 않습니다.

## 5. 보정값을 수정했는데 실제 음량이 변하지 않는다

정상입니다. PCM/DSD 보정은 **화면 표시 전용**입니다. 기본값은 PCM 0dB, DSD −6dB이며, 사용자 규칙에 일치한 경우 그 규칙의 보정값 **하나만** 적용합니다. 실제 재생 게인이나 오디오 샘플에는 영향을 주지 않습니다.

## 6. Apply / Cancel / 초기화와 사용자 테마의 관계

**Apply:** 저장 후 창 유지. **OK:** 저장 후 종료. **Cancel:** *아직 저장되지 않은 변경*만 취소합니다. 초기화 버튼도 변경 상태를 준비하며 Apply/OK가 필요합니다. 일반·DSP 규칙은 전역, 패널 디자인·눈금·색상·글꼴/버튼은 선택한 패널에 적용됩니다. JSON 테마는 **외형 전용**이며 DSP 규칙·보정을 포함하지 않습니다. 테마 이름은 UTF-8 **1~64바이트** 범위입니다.

## 7. DarkOne 전체화면에서 독립 창이 뒤로 숨는다

다른 플로팅 컴포넌트에서도 관찰된 전체화면 Z-order 현상입니다. 원인을 DarkOne이라고 확정할 수 없으며, v0.4.0 최소 크기 기능으로 **해결된 문제가 아닙니다.** 독립 창/삽입형을 구분해 검증하고, 원본을 백업한 상태로 별도 조사하세요.

## 8. DSD 수치가 다른 피크미터나 DAC 표시와 다르다

DSD −6dB는 이 컴포넌트의 **화면 표시 보정값**입니다. 네이티브 DSD 비트스트림의 True Peak를 공인 측정하는 기능은 아닙니다. 표시 버튼만 보고 실제 DAC 출력 모드를 추정하지 마세요.
