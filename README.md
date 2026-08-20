<div align="center">

<img src="docs/icon.png" width="88" alt="ProjectorWarp" />

# ProjectorWarp

**굽은 벽면·기둥·아치에 투사할 때, 원본 화면을 실시간으로 역왜곡해<br>실제 벽면에서 직선이 직선으로 보이도록 맞추는 Windows 유틸리티**

[![최신 릴리스](https://img.shields.io/github/v/release/MinaryHub/ProjectorWarp?label=%EB%8B%A4%EC%9A%B4%EB%A1%9C%EB%8D%94&color=0f7ea6)](https://github.com/MinaryHub/ProjectorWarp/releases/latest)
[![Windows](https://img.shields.io/badge/Windows-10%201903%2B-0f7ea6)](#요구-사항)
[![Sponsor](https://img.shields.io/badge/Sponsor-MinaryHub-bf3989)](https://github.com/sponsors/minaryhub)

<sub>Projecting onto a curved wall, a pillar, or an arch bends every straight line, and moving the projector never fixes it.<br>
ProjectorWarp warps the image in real time — corner-pin keystone, a Bézier surface mesh, masking, colour correction<br>
and edge blending — so straight lines land straight on the surface. Free, single executable, no runtime to install.</sub>

</div>

---

## 설치

[**최신 릴리스**](https://github.com/MinaryHub/ProjectorWarp/releases/latest) 에서 `ProjectorWarp.exe` 하나만 내려받아 실행하세요.
.NET 설치가 필요 없는 self-contained 단일 실행 파일입니다. 설치 관리자도, 레지스트리 등록도 없습니다.

### 요구 사항

| 항목 | 값 |
|---|---|
| OS | Windows 10 1903(빌드 18362) 이상 · Windows 11 권장 |
| 그래픽 | Direct3D 11 지원 GPU (실패 시 WARP 소프트웨어 렌더러로 자동 폴백) |
| 아키텍처 | x64 |

---

## 무엇을 하나

<img src="docs/panel.png" width="380" align="right" alt="컨트롤 패널" />

**소스** — 두 가지 중 하나를 씁니다.

- **내장 재생** — 동영상과 PPT · PDF · 이미지 슬라이드를 앱이 직접 재생합니다.
  외부 플레이어나 PowerPoint 를 띄워 둘 필요가 없습니다.
- **창 캡처** — 실행 중인 창을 `Windows.Graphics.Capture` 로 가져옵니다.

**기하 보정** — 세 단계를 겹쳐 씁니다.

1. **코너 핀 / 키스톤** — 네 모서리를 끌어 3×3 호모그래피를 만듭니다.
2. **베지어 곡면** — 3×3 ~ 6×6 제어점을 끌어 굽은 면을 따라갑니다.
   테셀레이션은 16×16 ~ 128×128.
3. **마스킹** — 다각형 블랙 마스크로 새는 빛을 잘라냅니다.

**색상 보정 · 엣지 블렌딩** — 밝기 · 대비 · 감마와, 멀티 프로젝터용 네 변 블렌딩.

**정렬 도구** — 격자 · 체커보드 · 원형 링 · 컬러바 등 테스트 패턴과 참조 그리드를
출력 창에 띄운 채로 제어점을 끌 수 있습니다.

**프리셋 · 자동 시작** — 보정값과 소스 · 출력 모니터를 저장하고, 앱을 끄면 마지막 상태가
자동 저장됩니다. 로그온 시 자동 실행과 자동 투사 시작도 켤 수 있습니다.

<br clear="right" />

---

## 사용 순서

1. **소스 선택** — `[내장 재생]` 에서 파일을 열거나, `[창]` 에서 캡처할 창을 고릅니다.
2. **출력 모니터 선택 → `[출력 시작]`** — 해당 모니터에 테두리 없는 전체화면 창이 열리고
   선택한 소스가 함께 시작됩니다. 화면 표시 여부는 `[출력 시작]` / `[출력 중지]` 두 버튼으로만 결정됩니다.
3. **`F1` 편집 모드** — 제어점을 끌어 곡면을 맞춥니다. `F2` 로 테스트 패턴을 띄우면 정렬이 쉽습니다.
4. **`Ctrl+S`** 로 저장 — 다음 실행 때 그대로 복원됩니다.

### 출력 창 단축키

| 키 | 동작 | 키 | 동작 |
|---|---|---|---|
| `F1` | 편집 모드 | `Space` | 재생 / 일시정지 |
| `F2` | 테스트 패턴 | `PgUp` `PgDn` | 슬라이드 넘기기 |
| `F3` | 참조 그리드 | `Ctrl+S` `Ctrl+O` | 프리셋 저장 / 열기 |
| `F4` | 대각선 | `Ctrl+R` | 워핑 초기화 |
| `Esc` | 전체화면 해제 | `Ctrl+Z` `Ctrl+Y` | 실행 취소 / 다시 실행 |

방향키로 선택한 제어점을 1px 씩(`Shift` + 방향키는 10px) 미세 이동합니다.

---

## 자동 업데이트

앱의 **`[9. 버전 · 업데이트]`** 가 이 저장소의 최신 릴리스를 확인합니다. **설정할 것이 없습니다.**

시작 후 조용히 확인하고 새 버전이 있을 때만 알리며, **`[설치 후 재시작]`** 을 누르지 않으면
아무것도 바뀌지 않습니다 — 투사 중에 저절로 재시작되는 일은 없습니다.

---

## 후원

무료로 쓰실 수 있고, 앞으로도 그렇습니다. 실제 프로젝터와 까다로운 디스플레이 구성에서
검증하고 Windows 코덱 · 드라이버 문제를 쫓는 데 후원이 쓰입니다.

[![Sponsor](https://img.shields.io/badge/GitHub%20Sponsors-MinaryHub-bf3989?logo=githubsponsors&logoColor=white)](https://github.com/sponsors/minaryhub)

---

## 이 저장소

**배포 전용입니다.** 소스는 비공개 저장소에서 관리하고, 이곳에는 실행 파일만 올립니다.
앱의 자동 업데이트가 여기의 최신 릴리스를 확인합니다.

버그나 요청 사항은 [Issues](https://github.com/MinaryHub/ProjectorWarp/issues) 에 남겨 주세요.
재현에 도움이 되는 정보는 다음과 같습니다.

- ProjectorWarp 버전 (제목줄 또는 `[9. 버전 · 업데이트]`)
- Windows 버전과 GPU
- 소스 종류(내장 재생 / 창 캡처)와, 동영상이라면 컨테이너·코덱
- 컨트롤 패널 상태 표시줄에 나온 메시지
