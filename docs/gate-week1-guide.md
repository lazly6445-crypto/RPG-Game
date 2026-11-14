# 엔진 게이트 1주차 준비 가이드 (Windows, 사용자 PC에서 직접 수행)

> 대상: `engine-gate-plan.md` 1주차. 이 세션은 클라우드 컨테이너라 **사용자의 PC에 엔진을 설치하거나 실행할 수 없다.** 이 문서는 사용자가 직접 따라 하는 순서·설정·기록 틀이다. 결과(로그·스크린샷·일지)를 알려 주면 판정과 문서 갱신을 돕는다.
> 근거: 결정 108~118(2D 픽셀 탑다운, 타일 32px, 640×360, 8방향, 블록 높이), 94(기본 무료), 95~97·102(근사 측정, Windows·SSD), 100(엔진당 2주).
> 표기: **[확정]** 사용자 결정 · **[제안]** 제안 · **[가정]** 임시값 · **[미결정]** 사용자 결정 필요.
> **버전·메뉴 이름·설정 이름은 검색 요약 기준이고 공식 문서 원문을 직접 확인한 것이 아니다.** 설치 시점의 공식 안내가 우선이다. 다르면 공식 안내를 따르고 차이를 구현 일지에 적는다.

---

## 0. 1주차의 목표와 순서

**목표:** 엔진 1(Godot 4)을 설치하고, 게이트 측정이 가능한 **빈 프로젝트 템플릿**(640×360 픽셀 퍼펙트, 32px 타일)과 **측정 틀**(로그·빌드)을 만든다. Unity는 **2주차 시작에** 설치한다(엔진당 2주 상한, 게이트는 Godot → Unity 순서; 결정 100).

| 순서 | 작업 | 예상 시간 **[가정]** |
|---|---|---|
| 1 | 환경 확인·기록(§1) | 0.5~1시간 |
| 2 | 도구 결정(§2): 코드 언어, 아트 도구 | 0.5시간 |
| 3 | Godot 설치·첫 프로젝트(§3) | 1~2시간 |
| 4 | 버전 관리 설정(§4) | 1시간 |
| 5 | 픽셀 퍼펙트 템플릿(§5) | 2~4시간 |
| 6 | 임시 타일·스프라이트 제작(§6) | 3~5시간 |
| 7 | 측정 틀·릴리스 유사 빌드(§7) | 3~4시간 |
| 8 | 라이선스·미확인 확인(§8) | 2~3시간 |
| 9 | 1주차 완료 점검(§9) | 0.5시간 |
주 20~30시간(결정 24) 범위 안이다. 막히면 §9의 기록 규칙에 따라 막힌 시간을 기록하고 계속 진행하지 않고 판단한다.

---

## 1. 환경 확인·기록

이미 알고 있는 것(결정 96·102): i5-12400F / DDR4 32GB / RTX 3060 Ti 8GB / Windows / SSD(NVMe 또는 SATA 미확인).
추가로 기록할 것(측정 파일 머리말에 쓴다, `engine-gate-plan.md` §3.1):
- GPU 드라이버 버전, Windows 버전(빌드 번호)
- 모니터 해상도·주사율(수직 동기화 영향)
- 저장장치가 NVMe인지 SATA SSD인지(작업 관리자 → 성능 → 디스크)
- 프로젝트를 둘 드라이브의 **여유 공간**(Unity 설치는 큰 공간이 필요하다는 2차 자료가 있다: 약 25GB 언급, Unity 공식 문서로 확인)
- 전원 계획: 고성능

**근사 측정을 위한 확인(결정 96):** 메모리를 8GB로 제한해 한 번 측정하는 방법을 확인한다. Windows에서 부팅 구성의 최대 메모리를 바꾸는 방법이 알려져 있으나 **이번 검색에서 확인하지 못했다.** 부팅 설정을 바꾸는 방식이라 위험이 있으므로 **지금은 하지 않는다.** 대안(제안): 측정 대상 프로그램의 메모리 사용량 자체를 기록하고 8GB 기기에서 문제가 없을지 판단하는 데 쓴다(작업 관리자/엔진 프로파일러의 사용량 기록). 실제 제한 방식은 사용자가 안전한 방법을 확인한 뒤 결정한다.

---

## 2. 도구 결정 (사용자 결정)

### 2.1 코드 언어 **[확정: 결정 119 — 표준 빌드(GDScript)]**
Godot는 **표준 빌드(GDScript)** 와 **.NET 빌드(C#)** 가 별도로 있다(공식 다운로드 아카이브 페이지 기준). .NET 빌드는 별도의 **.NET SDK**가 필요하다는 안내가 있다(2차 자료).
| 선택 | 장점 | 주의 |
|---|---|---|
| 표준(GDScript) **[제안]** | 설치가 단순, Godot 전용 문법, 이터레이션이 빠름 | 다른 엔진(Unity)으로 옮길 때 코드 재작성 |
| .NET(C#) | Unity와 언어가 같아 지식 이전이 쉬움 | SDK 설치·설정, 이터레이션 비용이 늘 수 있음 |
**[제안] 기본안: 표준(GDScript).** 팀에 숙련 엔진·언어가 없고(결정 5) 게이트 2주 상한이 있다. 단 Unity 게이트도 있으므로 사용자의 선호가 있으면 알려 달라.

### 2.2 픽셀 아트 도구 **[확정: 결정 120 — Pixelorama, 결정 94 적용]**
기본은 무료·오픈소스(결정 94). 후보(2차 자료, 최신 라이선스·가격은 각 공식 사이트에서 확인):
| 도구 | 비용 | 메모 |
|---|---|---|
| **Pixelorama** | 무료·오픈소스(Godot로 만들어짐, 여러 사이트에서 추천) | **[제안] 기본안** |
| LibreSprite | 무료·오픈소스(Aseprite의 포크) | 개발 속도가 느리다는 평 |
| Krita | 무료·오픈소스 | 페인팅 도구, 픽셀 아트 가능 |
| Piskel | 무료(브라우저 기반) | 간단한 스프라이트용 |
| Aseprite | **유료**(자료마다 약 $15~20, 소스를 직접 컴파일하면 무료라는 언급) | 결정 94에 따라 구매 여부는 사용자 결정. 이번 1주차에는 필요 없음 |
타일맵 편집은 **엔진 내장 타일맵**을 쓰므로 Tiled는 필요 없다 **[제안]**.

---

## 3. Godot 설치와 첫 프로젝트

1. **공식 사이트(godotengine.org)의 다운로드 페이지**에서 현재 안정(stable) 버전을 받는다. 포크·미러·"데코이" 사이트는 피한다(GodotSteam 쪽에서 가짜 포크 경고가 있었다).
   - 한 문서 미러는 4.7이 최신이라고 했으나 **공식 확인은 못 했다.** 설치할 때 보이는 버전을 기록한다. **사용자 설치 버전: Godot 4.7.2(표준 빌드, 한국어 UI 프로젝트 매니저 확인).**
   - 2.1의 결정대로 표준(GDScript) 또는 .NET 빌드.
2. 설치 방식·실행 방식은 다운로드 페이지의 안내를 따른다(**이 세션은 설치 절차를 확인하지 못했다**).
3. **[사용자 실측 기록]** 새 프로젝트 대화상자(4.7.2, 한국어 UI): 렌더러 선택지는 Forward+ / 모바일 / **호환성**. 호환성 설명: "저성능이거나 오래된 기기에서 사용, OpenGL 3 백엔드(OpenGL 3.3/ES 3.0/WebGL2), 단순한 씬을 가장 빠르게". Forward+는 "단순한 씬을 그리는 성능은 떨어집니다". **호환성 선택, 버전 컨트롤 메타데이터 Git, 경로 D:/gate-godot.** 처음 실행해 프로젝트 관리자에서 새 프로젝트를 만든다. 이름: `gate-godot` **[제안]**. 렌더러는 **호환성(Compatibility) 또는 저사양 친화 옵션**을 선택할 수 있는지 확인한다(옵션 이름·존재는 **미확인**, 통합 그래픽 목표라 선택지가 있다면 가장 가벼운 쪽을 기록하고 이유를 일지에 쓴다).
4. 버전 관리를 쓸 때 **새 프로젝트 대화상자의 Git 옵션** 또는 `Project > Version Control > Generate Version Control Metadata`로 .gitignore/.gitattributes를 만들 수 있다(공식 문서).
5. 프로젝트가 실행되는지 확인: 빈 씬 하나를 실행해 창이 뜨는지만 본다.
- 기록: 엔진 버전(정확한 빌드 이름), 설치 소요 시간, 막힌 지점.

---

## 4. 버전 관리 **[확정: 결정 121 — 별도 저장소]**

**질문:** 게임 프로젝트(코드·에셋)를 어디에 둘까? 지금 이 레포(`RPG-Game`)는 **문서 중심**이다. 이전에 "기존 2D 코드를 이 레포에 올리지 않는다"(결정 16)고 했지만 새 프로젝트는 별개다. 옵션 **[제안]**:
- A. **별도 저장소**(권장): 문서 레포와 분리해 에셋이 큰 게임 프로젝트의 이력·크기를 독립 관리.
- B. 이 레포의 하위 폴더(`game/`): 문서와 한곳에서 관리하지만 이진 파일이 레포를 키운다.
→ 사용자가 정한다. 이 세션은 사용자의 로컬 PC에서 저장소를 만들 수 없다(GitHub 연동 레포는 `lazly6445-crypto/rpg-game`만 범위).

**공식 문서가 말하는 Godot 4의 Git 설정:**
- `.godot/`(캐시)와 `*.translation`(CSV에서 생성)은 **무시(ignore)** 한다.
- 무시 목록은 **Godot 3.x/4.0과 4.1 이상이 다르다**(4.0 이하는 `export_presets.cfg`에 민감 정보가 들어갈 수 있다는 경고). 버전에 맞는 목록을 쓴다. **서드파티가 제공하는 "권장 .gitignore"는 공식에 없는 항목이 있어 신뢰하지 않는다.**
- **Git LFS:** 이진 파일(PNG, JPG, WebP, WAV, OGG 등)은 LFS로 관리하도록 공식 문서가 예시 `.gitattributes`를 제공한다. 이미 커밋한 파일은 제거 후 LFS 설정 뒤 다시 추가해야 하므로 **처음부터** 설정한다.
- 공동 작업자(미래)는 Git LFS 설치가 필요하다.

**Unity용 .gitignore·LFS는 이번 검색에서 확인하지 못했다.** Unity는 2주차에 설치할 때 Unity 공식 문서로 확인한다.

---

## 5. 픽셀 퍼펙트 템플릿 (Godot)

`engine-gate-plan.md` §4.5의 목표: 내부 640×360, 출력 1920×1080(3배)·1280×720(2배) 정수 확대, 흐림·떨림 없음.

**알려진 설정(2차 자료, 포럼 기준이며 공식 문서 원문 미확인, 버전별 차이 가능):**
- 프로젝트 설정의 **창(Window) 항목**: 기본 뷰포트 크기를 **640×360**으로.
- **스트레치(Stretch)**: 모드 `viewport`, 비율 `keep`, 스케일 모드 `integer`.
- **기본 텍스처 필터**: `nearest`(Rendering → Textures).
- **2D 픽셀 스냅**: 활성화(Rendering → 2D).
- 한 포럼은 4.5에서 정수 스케일이 동작한다고 했고, 다른 노트는 구버전에서 정수 스케일을 강제하지 못한다고 했다. **설치한 버전에서 직접 확인**한다.
- 1920×1080과 1280×720에서 확대 후 **검은 여백, 흐림, 비율 깨짐**을 눈으로 확인하고 스크린샷을 남긴다.

**확인 항목(§4.5의 합격선):** 정수 배 확대에서 흐림 없음, 서브픽셀 떨림 없음(8방향 이동·스크롤 중), 설정 소요 반나절 이내.

(Unity용: URP **Pixel Perfect Camera** 컴포넌트, 기준 해상도 640×360, Assets Pixels Per Unit 32 **[제안]**, 2주차에 설정. 옵션 이름은 버전별로 다르다.)

---

## 6. 임시 타일·스프라이트 (게이트 시나리오용 더미)

`prototype-d-spec.md` §3·§4.1의 최소 에셋. **정식 아트가 아니라 측정용 더미**다(화풍 실험은 P0 별도 작업).

| 에셋 | 크기 | 용도 |
|---|---|---|
| 평지 타일 3종(시가지 회갈색 / 경계지 보라청록 / 요정숲 저채도 녹색) | 32×32 | 농도 3단계 구역 구분(결정 109) |
| 구덩이(깎임) 타일 | 32×32 | Δh < 0 표시 |
| 돋운 땅 타일 | 32×32 | Δh > 0 표시 |
| **절벽 면 타일** 최소 세트 | 32×16 및 32×32 두 버전 | 3/4 뷰 남쪽 경계 면, 16px vs 32px 비교(M17) |
| 건물 더미(판자 바닥·벽) | 32×32 | 기초 보호 마스크 시험 |
| 플레이어 더미 | 32×32 정도, **방향별 정지 이미지 최소**(8방향이면 5개+미러) | 이동 규칙 시험 |
| 대형 더미 | 64×64 정도 | 구덩이 함정 시험 |
| 마스크·한계 표시 오버레이 | 32×32 | 디버그 표시 |
- 팔레트: 결정 109(차분한 탁한 색 + 지역 포인트). 이번엔 구분만 되면 된다.
- 시간: 이 단계의 **소요 시간을 기록**한다. 32px 타일·8방향 제작량(`2d-transition-impact.md` §4.1 경고)을 실측하는 첫 자료다.

---

## 7. 측정 틀

### 7.1 CSV 로그(`engine-gate-plan.md` §3.3)
머리말(측정 파일 첫 줄들): 엔진·버전, 날짜, CPU/GPU/드라이버/RAM/저장장치/OS, 출력 해상도, 내부 해상도, 근사 방법(결정 96의 ①~⑤ 중 적용한 것).
열: `run_id, date, engine, engine_version, device, output_resolution, scenario, frame_idx, frame_ms, cpu_ms, gpu_ms, mem_mb, edit_latency_ms, note`
- 프레임 로그는 엔진 코드에서 프레임 시간을 기록해 파일로 쓰는 간단한 스크립트로 만든다(엔진 프로파일러가 파일로 내보내는지는 **확인 필요**). 필요하면 이 세션에서 스크립트 초안을 제안할 수 있다.

### 7.2 릴리스 유사 빌드
- 에디터에서의 성능이 아니라 **내보낸(export) 빌드**로 측정한다(`engine-gate-plan.md` §3.2). 첫 내보내기를 1주차에 한 번 해 보고 **빌드 시간, 빌드 크기, 깨끗한 환경에서 실행 여부**를 기록한다.
- Godot 내보내기에는 **내보내기 템플릿**이 필요할 수 있다(설치 안내는 공식 문서). 내보내기 템플릿 설치 방법은 이번 검색에서 확인하지 못했다.
- **GodotSteam은 1주차에 설치하지 않는다.** 게이트 3~4주차 Steam 최소 테스트에서 공식 튜토리얼대로 진행(전용 내보내기 템플릿, godotsteam.dll·steam_api64.dll 동봉, MinGW 금지).

### 7.3 이터레이션 측정 도구
- 초시계 또는 스크린 녹화. 측정 항목: 코드 한 줄 수정 → 실행까지 시간, 빈 프로젝트 → 릴리스 유사 빌드 시간(`engine-gate-plan.md` §4.3).

---

## 8. 라이선스·미확인 확인 (`engine-gate-plan.md` §6)

1주차에 확인하고 `engine-comparison-memo-2d.md` §6의 표를 갱신한다.
| # | 확인 | 방법 |
|---|---|---|
| 1 | Godot 공식 LICENSE 원문(MIT) | 공식 저장소의 LICENSE 파일 |
| 2 | Godot TileMapLayer 공식 API: 커스텀 데이터, 일괄 갱신, 충돌 갱신 | 공식 문서 |
| 3 | Godot 스트레치·정수 스케일 현재 버전 동작 | §5 직접 실측 |
| 4 | 렌더러 선택지(호환성 등) | 새 프로젝트 대화상자 |
| 5 | 내보내기 템플릿 설치 방법 | 공식 문서 |
| 6 | 프로파일러/프레임 시간 내보내기 방법 | 공식 문서·실측 |
| 7 | **(2주차 시작 전)** Unity Personal 최신 약관(20만 vs 10만 달러), Unity Hub 설치·2D URP 템플릿 이름, Unity Tilemap·Pixel Perfect Camera 버전별 옵션 | Unity 공식 문서 |

---

## 9. 1주차 완료 점검 (체크리스트)

- [ ] 환경 정보 기록(§1)
- [x] 도구 결정: 코드 언어 GDScript(결정 119), 픽셀 아트 도구 Pixelorama(결정 120)
- [ ] Godot 설치·프로젝트 실행, 정확한 버전 기록
- [ ] 버전 관리 설정(저장소 위치 결정 포함), Git LFS 설정
- [ ] 640×360 픽셀 퍼펙트 템플릿 동작(2배·3배 확대 스크린샷, 흐림·떨림 없음 판정)
- [ ] 더미 타일·스프라이트 제작 시간 기록
- [ ] 프레임 로그 스크립트 동작, 첫 릴리스 유사 빌드 성공(크기·시간 기록)
- [ ] 라이선스·미확인 항목 1~6 확인 및 메모 갱신
- [ ] Unity 항목(§8-7)을 2주차 전에 확인할 일정 잡기
- [ ] **구현 일지** 작성: 막힌 지점, 소요 시간, 학습 곡선(엔진 간 비교용)

### 기록 규칙
- 모든 막힘(30분 이상)은 일지에 적는다. 같은 문제로 반나절 이상 막히면 **그 시점의 증거로 판정**하고 퇴로(`engine-gate-plan.md` §7)를 검토한다.
- 측정 결과는 합격선에 가깝게 맞추려고 조건을 바꾸지 않는다(결정 97: 조정은 측정 후에만).

### 완료 후 이 세션에 알려 주면 좋은 것
- 설치한 Godot 정확한 버전과 선택한 빌드(표준/.NET)
- §5의 확대 스크린샷과 판정, 막힌 설정
- §6 제작 시간, §7의 빌드 크기·시간
- 일지와 로그 파일 내용(스포일러 문구 없이)
그러면 2주차(타일 월드 스트리밍·T1~T8) 사양을 구체화하고 문서를 갱신한다.

---

## 10. 사용자 결정이 필요한 것
해결: 코드 언어(결정 119), 픽셀 아트 도구(결정 120), 저장소 위치(결정 121).
남은 것: **8GB 메모리 제한 방식** — 안전한 방법을 확인할 때까지 보류(제안).

---

## 11. 실측 기록: 원격 세션으로 확인한 현재 상태 (2026-11-01, 읽기 전용)

사용자 PC의 Claude Code 세션(Remote Control, `D:\gate-godot`)이 읽기 전용으로 확인한 결과다. 파일은 수정하지 않았다.
- **프로젝트 폴더:** `.editorconfig`(숨김), `.gitattributes`, `.gitignore`, `icon.svg`, `icon.svg.import`, `project.godot`. 씬·스크립트는 아직 없다. 엔진은 프로젝트 안에 없다.
- **Git:** 설치됨(`C:\Program Files\Git\cmd\git.exe`). 그러나 **저장소가 아님**(`fatal: not a git repository`). Godot의 Git 옵션은 `.gitignore`·`.gitattributes`만 만들고 `git init`은 하지 않았다.
- **`project.godot` 현재 값:** `config/name="2026-11-02 2D RPG"`, `config/features=("4.7","GL Compatibility")`, `[display] window/stretch/mode="canvas_items"`, `window/stretch/aspect="expand"`, `[physics] 3d/physics_engine="Jolt Physics"`, `[rendering] renderer/rendering_method="gl_compatibility"`, `rendering_device/driver.windows="d3d12"`. 뷰포트 크기·scale_mode·텍스처 필터·픽셀 스냅 키는 **없음**.
- **키 이름 확인 수준:** 파일에서 직접 확인한 것은 `window/stretch/mode`, `window/stretch/aspect`뿐이다. 나머지(`window/size/viewport_width`·`viewport_height`, `window/stretch/scale_mode`, `textures/canvas_textures/default_texture_filter`, `2d/snap/snap_2d_transforms_to_pixel`·`snap_2d_vertices_to_pixel`)는 기억 기반이라 **에디터에서 한 번 설정해 저장된 이름으로 확정**한다.
- **Godot 실행 파일 경로(정정):** 사용자가 알려 준 `D:\tools\gate-godot\Godot_v4.7.2-stable_win64.exe`는 파일이 아니라 **폴더**였다(압축 해제 때 폴더 이름에 `.exe`가 붙음). 실제 실행 파일:
  - 에디터: `D:\tools\gate-godot\Godot_v4.7.2-stable_win64.exe\Godot_v4.7.2-stable_win64.exe`
  - 콘솔: `D:\tools\gate-godot\Godot_v4.7.2-stable_win64.exe\Godot_v4.7.2-stable_win64_console.exe`
- **명령줄 옵션(4.7.2 콘솔 `--headless --help`, 종료 코드 0):** `--headless`, `--path <dir>`, `-s/--script`, `--scene <path>`, `--quit-after <int>`(반복 횟수), **`--check-only`(`--script`와 함께, 문법 오류만 검사)**, `--export-release <preset> <path>`(`export_presets.cfg` 필요), `--import`. 이전에 미확인이던 `--check-only`가 **확인됐다.**

### 11.1 자동 루프 결과 (2026-11-01, PC 쪽 Claude Code 세션)

- **픽셀 퍼펙트 설정 키 검증 완료(헤드리스 확인 스크립트 `tools/verify_settings.gd`, 후보 8개 모두 유효):**
  - `display/window/size/viewport_width` = 640, `viewport_height` = 360
  - `display/window/stretch/mode` = viewport, `aspect` = keep, `scale_mode` = integer
  - `rendering/textures/canvas_textures/default_texture_filter` = 0 (Nearest, 기본값 1은 Linear)
  - `rendering/2d/snap/snap_2d_transforms_to_pixel` = true, `snap_2d_vertices_to_pixel` = true
  - `application/run/main_scene` = `res://scenes/main.tscn`
- **만든 파일:** `tools/verify_settings.gd`, `scripts/player.gd`(8방향 이동, 실수 좌표 누적 후 반올림), `scenes/main.tscn`, `CLAUDE.md`. 수정: `project.godot`.
- **검사:** `player.gd --check-only` 종료 코드 0 / `main.tscn --headless --quit-after 60` 종료 코드 0, 오류 없음. 수정 루프는 돌지 않았다.
- **.gitignore:** `.godot/`, `/android/` 무시. **.gitattributes:** `* text=auto eol=lf`만 있고 **LFS 설정은 없다**(이미지·오디오 추가 전에 `.gitattributes`에 LFS 규칙 추가 필요).
- **Git:** `user.name`·`user.email`이 설정돼 있지 않아 **저장소 생성·커밋을 못 했다**(`git init`도 안 함). 사용자가 이름·이메일을 알려 주면 이 프로젝트에만(전역 아님) 설정하고 커밋한다.
- **사람이 에디터에서 눈으로 확인할 것:** 창을 2배/3배로 키웠을 때 정수 배율 확대와 검은 여백, 이동 중 가장자리 흔들림·번짐, 대각선 이동 속도와 카메라 추적.
- 참고: PC 세션의 Bash `python3` 호출이 멈춰 중지시켰고, 그 과정에서 프로젝트 밖 `/tmp`에 빈 임시 파일 `p.ps1`이 남았다(내용 없음).

### 11.2 Git 저장소 생성 결과 (2026-11-01)

- `D:\gate-godot`에 저장소를 만들고(`main` 브랜치) 커밋 4개를 순서대로 만들었다. push·remote 추가 없음.
  ```
  deab39d Add project instructions
  3959be1 Add minimal 8-direction movement test scene
  0ca4e01 Set 640x360 pixel-perfect display settings and settings verifier
  55e2ab2 Initial Godot 4.7.2 project files
  ```
- 커밋별 파일: ① `.editorconfig`, `.gitattributes`, `.gitignore`, `icon.svg`, `icon.svg.import` ② `project.godot`, `tools/verify_settings.gd`(+`.uid`) ③ `scenes/main.tscn`, `scripts/player.gd`(+`.uid`) ④ `CLAUDE.md`.
- Git 작성자 설정은 **이 저장소에만(로컬)** 적용했다(`--global` 없음). 상태는 깨끗하고(`git status --short` 비어 있음) 예상 밖 파일은 없었다.
- 이 이름·이메일은 커밋 기록에 남는다. 원격 저장소에 올릴 때 공개되므로, 공개를 원하지 않으면 올리기 전에 작성자를 noreply 이메일로 바꾸는 작업이 필요하다.
- 아직 LFS 규칙이 없다(`.gitattributes`에는 줄바꿈 규칙만). 이미지·오디오를 넣기 전에 추가한다.
