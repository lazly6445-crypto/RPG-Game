# 엔진 게이트 3주차 사양 — Unity 비교 측정 준비

> 선행: `gate-week2-spec.md`(Godot 측정 결과 §8~§9), `engine-gate-plan.md`(§2 후보, §4 측정 항목, §5 합격 규칙, §8 일정), `prototype-d-spec.md`(S1~S8).
> 표기: **[확정]** 사용자 결정 · **[제안]** 제안 · **[가정]** 임시값 · **[확인]** 설치 후 직접 확인할 것 · **[미결정]** 사용자 결정 필요.
> 이 문서의 Unity 사실은 아래 §10의 2차 자료(공식 문서 검색 결과)에 근거하며, **설치한 에디터에서 직접 확인하기 전까지 모두 미검증**이다.

---

## 0. 위치와 범위

**왜 하는가:** `engine-gate-plan.md` §5의 규칙은 "엔진 1(Godot) 필수 통과 → 엔진 2(Unity)를 같은 최소 시나리오로 측정해 비교, 엔진 1이 불합격이고 엔진 2가 합격이면 엔진 2 선택"이다. Godot은 이 PC에서 합격선을 큰 여유로 통과했다(`gate-week2-spec.md` §8). 따라서 Unity 측정은 **탈락 방지용이 아니라 비교용**(결정 101의 가중 합산 입력)이다.

**범위 선택 [미결정]:**
| 안 | 내용 | 비용 | 얻는 것 |
|---|---|---|---|
| **A. 최소(제안)** | 타일 월드 스트리밍 + 높이 변형/절벽 갱신 + 이터레이션 시간 + 픽셀 퍼펙트 + Steam 연동 최소 확인. 이동·함정·저장 규칙 이식은 하지 않음 | 작음 | 성능·작업 흐름·배포 경로 비교 |
| B. 전체 | A + T2~T8 규칙 전체를 C#으로 이식하고 테스트 동등성 확인 | 큼(Terrain·GridMover·SaveDelta·PitTrap 재작성) | 동일 시나리오 완전 비교 |
근거: 규칙 로직은 엔진 독립이라 어느 엔진에서도 같은 알고리즘이면 같은 결과가 나온다. 엔진을 가르는 변수는 렌더·타일 갱신 비용·작업 속도·배포이므로 A로 충분하다는 것이 제안 이유다. B는 A에서 두 엔진이 비슷하게 나와 가중치가 모호할 때만 추가한다.

**상한:** 엔진당 2주(결정 100). 일정상 Unity는 2~3주차. 이 문서는 A를 기본으로 쓰고 B 항목은 "B만"으로 표시한다.

---

## 1. 사전 확인 (2차 자료, 미검증)
| 항목 | 확인된 내용(검색 결과) | 남은 확인 |
|---|---|---|
| 버전 | Unity 6.3 LTS가 최신 LTS이고 2027년 12월까지 지원, 6.0 LTS는 2026년 10월까지 지원 | 설치 시점의 Hub 목록에서 실제 버전 번호 확인. **6.3 LTS 권장 [제안]** |
| 라이선스 | Personal은 무료, 재무 한도 최근 12개월 20만 달러(Unity 6에서 10만→20만으로 상향). 초과 시 Personal 사용 불가(프로토타이핑 포함) | 약관 원문과 현재 적용 일자 확인. 런타임 요금은 이후 정책에서 폐지됐다는 자료가 있으나 최신 약관으로 재확인 |
| 2D 템플릿 | 6.3 문서에서 이름은 **Universal 2D**(URP 2D 렌더러 구성, 2D 기능 세트 자동 설치) | 설치 후 Hub의 실제 템플릿 이름 |
| 픽셀 퍼펙트 | URP에서는 Pixel Perfect Camera 컴포넌트를 URP가 제공(별도 2D Pixel Perfect 패키지는 내장 렌더 파이프라인 전용이므로 설치 금지). 옵션: Assets Pixels Per Unit, Reference Resolution, Crop Frame, Pixel Snapping(6.0에서는 Grid Snapping 표기), Upscale Render Texture | 6.3에서의 옵션 이름·동작 직접 확인 |
| 타일 일괄 갱신 | `Tilemap.SetTiles(Vector3Int[], TileBase[])`와 `SetTiles(TileChangeData[], bool)` 존재(공식 스크립팅 문서). `SetTilesBlock`은 이번 검색에서 문서 확인 못함 | 설치 후 API 목록 확인 |
| 타일 렌더러 | TilemapRenderer 모드: Chunk(여러 타일 일괄 배치, SRP Batcher와 호환 안 됨), Individual, SRP Batch | 모드별 비교 측정(§5) |
| 성능 보고 | 오래된 포럼 글에서 대량 `SetTilesBlock` 극단적 지연 사례 — 구버전·커스텀 Tile 서브클래스 조건, **참고용** | 이번 측정으로 대체 |

---

## 2. 설치 (사용자 필요)
Unity는 계정 로그인과 라이선스 활성화가 필요해 **자동화할 수 없다.** 사용자가 직접 한다.
1. unity.com에서 **Unity Hub** 설치(Windows). 설치 경로 기본값. [확인: 현재 다운로드 경로]
2. Hub에서 Unity 계정으로 로그인하고 **Personal 라이선스** 활성화. 소득·자금 한도 확인 문구가 나오면 해당 여부를 사용자가 판단(한도 초과 시 Personal 불가).
3. Hub → Installs → 6.3 LTS(또는 목록의 최신 LTS) 설치. 모듈은 **Windows Build Support (Mono)** 만 선택하고 Android·WebGL·iOS·Mac 등은 선택하지 않는다. [용량 미확인 — 설치 화면의 표시값을 알려줄 것]
4. 설치 위치: 용량이 부족하면 D 드라이브 지정. [확인: Hub 설정에서 변경 가능한 경로]
5. 설치 후 Hub 화면의 에디터 버전 번호와 설치 용량을 알려준다.
이 단계 이후부터는 PC 세션(Claude Code)이 명령줄로 일부 작업을 수행할 수 있다(§7, **[확인]**).

---

## 3. 프로젝트 구성 (Godot 설정 대응)
| 항목 | Godot 1주차 설정 | Unity 대응 [제안] |
|---|---|---|
| 프로젝트 위치 | `D:\gate-godot` | `D:\gate-unity` (별도 git 저장소, 결정 121) |
| 템플릿 | — | Universal 2D |
| 기준 해상도 | 640×360 viewport 스트레치 | Pixel Perfect Camera Reference Resolution 640×360 |
| PPU | 타일 32px | Assets Pixels Per Unit 32, 모든 스프라이트 PPU 32 |
| 필터 | 텍스처 필터 Nearest | 스프라이트 Filter Mode Point, 압축 None |
| 스냅 | 2D 변환 픽셀 스냅 | Pixel Snapping 옵션(버전 표기 확인) |
| 확대 | 정수 스케일(1080p 3×, 720p 2×) | Crop Frame / Upscale Render Texture 설정을 변경해 비교 |
| 타일 | `TileMapLayer` 청크마다 | Grid 아래 청크별 `Tilemap`(+TilemapRenderer) |
| 타일셋 | 코드 생성 아틀라스 12종 | 같은 12종을 코드로 `Tile`/`Sprite` 생성(ScriptableObject·PNG 없이 `Texture2D`에서 런타임 생성 가능 여부 [확인]) |
| 물리 | 사용 안 함 | 사용 안 함(Tilemap Collider 추가 금지) |
| 렌더러 | Compatibility | URP 2D 렌더러, 그림자·후처리 끔 |
| vsync | 측정 시 해제 | `QualitySettings.vSyncCount = 0`, `Application.targetFrameRate = -1` [확인] |
프로젝트 `CLAUDE.md`에 Godot 쪽과 같은 규칙(스포일러 금지, 푸시·삭제·설치 금지, 프로젝트 밖 쓰기 금지)을 쓴다.
`.gitignore`는 Unity 표준(Library, Temp, Logs, obj, Builds, UserSettings 등)이 필요하다. `.gitattributes`의 LFS 규칙은 이 시점에 PNG 등 바이너리를 추가하지 않으므로 보류.

---

## 4. 월드·지형 구현 방침 (A 기준)
- **월드 데이터는 엔진 독립 C# 클래스로**: 원본 높이 함수, 델타 딕셔너리, 구역 한계표, 편집 함수. 동일 알고리즘을 Godot `Terrain`과 대응시킨다(B 이식의 기초).
- **원본 높이:** Godot은 `FastNoiseLite`를 쓰므로 Unity에서 값을 똑같이 재현할 수 없다. 대신 정수 0~3의 비슷한 분포(공간 주파수 포함)를 쓰고, **양쪽의 절벽 밀도(절벽 셀 / 전체 셀)와 높이 분포를 같은 방법으로 측정해 비교 가능성을 확인**한다(3-0). 절벽 밀도가 크게 다르면 성능 비교가 오염되므로 Unity 쪽 주파수를 조정한다.
- **스트리밍:** 청크 32×32, 반경 1·2, 프레임당 로드 상한 1청크 — Godot과 같다. 청크 = 자식 `Tilemap` 오브젝트(바닥 + 절벽 2개). 일괄 갱신은 `SetTiles` 배열로, 비교용으로 단건 `SetTile` 루프도 측정(Godot의 `set_cell` 단건 루프와 대응).
- **오브젝트 풀링:** 청크 Tilemap 오브젝트를 파괴·재생성하지 말고 풀링한 경우와 하지 않은 경우를 비교 측정한다(Unity의 GC·인스턴스화 비용 확인용, Godot은 노드 free/생성).
- **TilemapRenderer 모드:** Chunk 모드와 Individual 모드를 비교. 이 프로토타입에서는 캐릭터 정렬 요구가 단순하므로 Chunk 모드를 기본으로 하고, 오브젝트 정렬이 필요해지는 시점의 영향은 별도 메모.
- **절벽 규칙·편집·영향 범위(2셀)·범위 모드·흙 블록·마스크:** Godot과 동일 규칙. (B만: 이동·낙하·함정·저장)

---

## 5. 측정 항목과 방법
Godot 측정과 같은 시나리오·같은 CSV 컬럼(`gate-week2-spec.md` §1.9, summary.csv 열 구성)을 쓴다. 비교 가능성 유지를 위해 열 이름은 동일하게 한다.

| 항목 | 방법 | Godot 대응 |
|---|---|---|
| 스트리밍 stream | 지그재그 고정 경로, 반경 1·2, 속도 480px/s, 1080p·720p, **vsync 해제**, 120초 ×각 + 10분 ×1 | `bench.gd` stream |
| 편집 edit | 6프레임마다 BOX3 깎기/쌓기 교대, 편집 지연(호출~반환), 구역별 적용 횟수 | `bench.gd` edit |
| 프레임 시간 | `Time.unscaledDeltaTime`. 가능하면 `FrameTimingManager`(CPU/GPU 시간) — Player Settings에서 Frame Timing Stats 활성 필요 [확인] | `delta`, `TIME_PROCESS`, GPU 측정 |
| 메모리 | Profiler 메모리 API(총 할당·GC 힙) [확인 함수명]. 행 기록은 처음부터 디스크 스트리밍 + `--record=off` 대응 옵션 | `MEMORY_STATIC` |
| 객체 수 | `Resources.FindObjectsOfTypeAll` 등 부하 큰 호출은 피하고 시작/끝 1회만. 청크 풀 크기 기록 | `OBJECT_COUNT` 등 |
| GC 히치 | 프레임 시간 최대·100ms 초과, GC.Collect 횟수(`GC.CollectionCount`) | — (Unity 고유 위험) |
| 빌드 | **스탠드얼론 Windows 플레이어(Mono, Development 끔)** 로 측정. 에디터 내 실행(Play)은 참고용으로만. 빌드 시간·빌드 크기 기록 | Godot은 프로젝트 직접 실행(console exe) — 아래 공정성 주의 |
| 픽셀 퍼펙트 | 2×·3× 확대 비교, 이동 중 떨림, Crop Frame 설정별 결과. 사람 확인 + 스크린샷 | `gate-week1-guide.md` §5 |
| 이터레이션 시간 | 스크립트 한 줄 수정 → 실행 가능 상태까지 시간(스톱워치). Unity는 도메인 리로드·컴파일 포함. 5회 평균 | Godot도 같은 방법으로 **같이 측정**(2주차에 미기록) |
| 라이선스·약관 | §1 항목 원문 확인(Personal 한도, 런타임 요금 없음) | `engine-gate-plan.md` §6 |
| Steam 연동 최소 | 빈 프로젝트에서 Steamworks 래퍼 앱 초기화·오버레이 수준 확인. 래퍼 후보는 조사 필요(검증 안 됨) [미확인] | GodotSteam 대응 |
| B만: T2~T8 | 규칙 이식 후 헤드리스 테스트 동등성(EditMode 테스트, 배치 모드 실행) | `test_rules.gd` 등 |

**공정성 주의:** Godot 측정은 에디터 바이너리로 프로젝트를 직접 실행한 값이고(내보낸 릴리스 아님), Unity는 빌드한 플레이어다. 전자가 불리할 수 있다. 비교 시 이 차이를 명시하고, 가능하면 Godot 내보내기 템플릿 설치 후 릴리스 내보내기 1회를 추가 측정한다(템플릿 설치 방법 미확인).
**저사양 근사:** Godot과 같은 방식(720p/최소 품질 + 마진 50%)으로, 통합 그래픽은 재현하지 못함을 같이 적는다.

합격선(전부 [가정], Godot과 동일): 평균 33ms, p99 50ms, 100ms 초과 히치 0, 편집 지연 100ms, 안전 마진 평균 16.5ms 이하. 합격선 자체의 조정은 측정 후(결정 97).

---

## 6. 단계 (PC 세션에 위임, A 기준)
| # | 작업 | 사람 필요 | 자동 검사 |
|---|---|---|---|
| 3-0 | **Godot 쪽 비교 기초 수집:** 절벽 밀도·높이 분포 계산 스크립트 실행(헤드리스), Godot 이터레이션 시간 5회 측정은 사용자 스톱워치(또는 PC 세션 자동화 가능 여부 검토) | 이터레이션만 | 스크립트 종료코드, 값 기록 |
| 3-1 | Unity 설치 확인(§2) | **사용자(로그인·라이선스)** | `Unity.exe -version` 등 [확인] |
| 3-2 | 프로젝트 생성·설정(§3): 명령줄 `-createProject` 또는 Hub 생성 [확인], Pixel Perfect Camera, 더미 타일셋 | 필요 시 | 배치 모드 컴파일 성공 |
| 3-3 | 월드·청크 로더·높이 변형·절벽(§4) | — | 배치 모드 EditMode 테스트(`-runTests` 계열 옵션 [확인]) |
| 3-4 | 측정 씬 + 실행 스크립트(CSV 동일 열) + 스탠드얼론 빌드 | — | 빌드 성공, 헤드리스(`-batchmode -nographics`) 스모크 [확인] |
| 3-5 | 측정 실행(창): Quick → 전체 → 10분 | 외출 중이면 PC 세션 가능 | CSV·summary 비교 |
| 3-6 | 이터레이션·픽셀 퍼펙트 사람 확인, Steam 최소 확인, 약관 확인 | **사용자** | — |
| 3-7 | Godot/Unity 비교 보고서 → 가중 합산(결정 101) 입력 | — | — |
| B만 | T2~T8 이식 + 동등성 테스트 | — | — |

---

## 7. 알려진 위험·불확실성
| 위험 | 대응 |
|---|---|
| Unity 명령줄 옵션(`-batchmode`, `-runTests`, `-createProject`, 라이선스가 필요한 배치 실행)의 정확한 동작 | 설치 후 `--help`/공식 문서로 먼저 검증. 안 되면 에디터 GUI 작업이 늘어남 → 사용자 부담 증가 |
| 배치 모드에서 라이선스 재인증 문제 | 첫 실행 시 확인. 문제 시 Hub 로그인 상태에서 실행 |
| 도메인 리로드·컴파일 시간 | 이터레이션 측정에 포함. Enter Play Mode 옵션(도메인 리로드 비활성) 설정도 비교 [확인] |
| Tilemap `SetTiles` 대량 갱신·GC | `TileChangeData`/배열 재사용, 청크 풀링 비교 |
| 절벽 밀도 불일치로 비교 오염 | 3-0·3-3에서 같은 방법으로 측정해 조정 |
| 렌더러(URP 2D) 오버헤드가 640×360에서도 고정비로 존재 | 측정 결과로만 판단, 추정 금지 |
| 용량·디스크 | 설치 용량 확인 후 결정, 프로젝트 Library 폴더 용량 기록 |
| Personal 라이선스 한도 | 사용자 확인 필수(초과 시 사용 불가) |

---

## 8. 사용자 결정·행동이 필요한 것
1. **범위 A(최소) / B(전체)** 선택 [미결정] — 기본 A.
2. Unity Hub 설치, 로그인, Personal 활성화, 6.3 LTS(Windows Build Support Mono만) 설치. 설치 용량과 버전 번호 회신.
3. Personal 한도(최근 12개월 재무 20만 달러 이하) 해당 여부는 사용자가 판단·확인.
4. 외출 중 측정 허용 여부(창 모드 성능 측정은 PC를 쓰지 않을 때만).
5. Godot 쪽 이터레이션 시간 측정에 사용자 스톱워치 참여 여부(자동화하면 정확도 떨어질 수 있음).

---

## 9. 일정 제안
| 일 | 작업 |
|---|---|
| 0일차 | 설치(§2), 3-0 |
| 1~2일차 | 3-2, 3-3 |
| 3일차 | 3-4, 3-5(Quick) |
| 4~5일차 | 3-5(전체·10분), 3-6 |
| 6일차 | 3-7 비교 보고서 |
상한 2주. 초과하면 그 시점의 측정으로 판정(결정 100).

---

## 10. 근거 자료 (2차, 미검증)
- Unity 6 릴리스·지원: https://unity.com/releases/unity-6/support
- Unity 6.3 URP 새 프로젝트(Universal 2D 템플릿): https://docs.unity3d.com/Manual/urp/creating-a-new-project-with-urp.html
- Unity Personal 요금·한도: https://unity.com/products/unity-personal , 가격 업데이트 https://unity.com/pricing-updates
- Pixel Perfect Camera(URP) 레퍼런스: https://docs.unity3d.com/Manual/urp/2d-pixelperfect-ref.html
- `Tilemap.SetTiles`: https://docs.unity3d.com/ja/6000.0/ScriptReference/Tilemaps.Tilemap.SetTiles.html
- TilemapRenderer 모드(Chunk): https://docs.unity3d.com/ScriptReference/Tilemaps.TilemapRenderer.Mode.Chunk.html
- `SetTilesBlock` 성능 포럼 글(구버전, 참고용): https://forum.unity.com/threads/tilemap-settilesblock-performance.537274/

---

## 11. 진행 기록
### 3-0 완료 — Godot 원본 월드 통계 (게임 PC 커밋 218b8c3, `bench/godot_world_stats.txt`)
델타 없는 1024×1024 월드 전체 순회.

| 항목 | 값 |
|---|---|
| 높이 0 / 1 / 2 / 3 (전체) | 17,385 / 508,571 / 504,259 / 18,361 (구역별 거의 동일) |
| 절벽 셀(북쪽 이웃이 더 높음, y=0 제외) | 31,092 / 1,047,552 = **2.97%** (구역 0/1/2: 2.95/2.95/3.00%) |
| 높이차 n=1 / 2 / 3 | 31,092 / 0 / 0 |
| 청크당 절벽 수 | 평균 30.4, 최소 1, 최대 75, 표준편차 12.3 (1024청크) |
| 가로 인접 동일 높이 비율 | 94.0% |
| 노이즈 | `TYPE_SIMPLEX_SMOOTH`, seed 12345, frequency 0.02, **FBM 5옥타브(코드에서 설정하지 않은 Godot 기본값)**, lacunarity 2.0, gain 0.5 |
| 높이 변환식 | `clampi(int((noise * 0.5 + 0.5) * 4.0), 0, 3)` |

해석과 주의:
- 원본 월드는 **대부분 높이 1~2의 평탄한 지형**이고 절벽이 3%뿐이며 모두 1단이다. 2주차 Godot 성능 수치(`gate-week2-spec.md` §8)는 이런 지형에서의 값이다. 절벽이 많은 지형(예: 산지)이나 편집으로 절벽이 늘어난 상태의 비용은 이 수치로 알 수 없다. 편집 시험은 델타를 만들기는 하지만 월드 전체의 절벽 밀도를 높이지 않는다.
- Unity 쪽은 위 노이즈 설정(FBM 5옥타브 포함)과 변환식, 절벽 밀도 2.97% ± 오차, 인접 동일 비율 94%에 맞춰 생성한다. 정확히 같은 값이 나오지 않는 것은 정상이며, 같은 방법으로 측정해 비교 가능한지만 본다.
- **[제안] 절벽 부하 시험 추가:** 양쪽 엔진에서 고밀도 절벽 지형(예: 주파수를 높여 절벽 비율 20% 이상)을 같은 방법으로 한 번 더 측정한다. 평탄한 지형만으로는 최악 부하를 놓친다. 범위 A에 포함하는 것을 권한다.
- 남은 3-0 항목: Godot 이터레이션 시간(사용자 스톱워치 필요).

### 3-0b 완료 — 고밀도 절벽 지형 측정 (게임 PC 커밋 9bd3285)
프로파일: `WorldConfig`의 flat(frequency 0.02, contrast 1.0 = 기존 식 동일)과 dense(frequency 0.15, contrast 4.0). 높이 식 `clampi(int((noise*contrast*0.5+0.5)*4.0),0,3)`. flat 회귀(절벽 31,092, 히스토그램) 동일 확인. 인자 `--terrain=flat|dense`.

dense 월드 통계(`bench/godot_world_stats_dense.txt`): 높이 0/1/2/3 = 338,071/185,983/186,621/337,901. 절벽 24.72%(구역별 24.67/24.79/24.69%), n=1/2/3 = 168,507/72,166/18,239(n≥2 34.9%). 청크당 절벽 평균 252.8(218~290). 인접 동일 높이 50.59%. (flat은 절벽 2.97%, 청크당 평균 30.4.)

1080p, vsync 해제, 120초, 기록 on, 같은 빌드:

| | dense stream | dense edit | flat edit(기준선) |
|---|---|---|---|
| 프레임 수 | 330,565 | 279,396 | 281,739 |
| 평균 / p99 / 최대 (ms) | 0.363 / 0.940 / 12.18 | 0.429 / 1.390 / 13.46 | 0.424 / 1.140 / **130.19** |
| 33·50·100ms 초과 | 0·0·0 | 0·0·0 | 1·1·1 |
| avg_cpu_ms | 5.31 | 5.42 | 10.86 |
| avg_gpu_ms | 0.073 | 0.079 | 0.080 |
| 메모리 시작→끝 (MB) | 69.4→73.9 | 69.4→83.8 | 68.6→75.7 |
| 편집 지연 평균/p99/최대 (ms) | — | 0.079/0.200/0.690 | 0.083/0.210/0.544 |

- 고밀도 절벽(8배 이상)에서도 프레임 평균·p99는 평탄 지형과 같은 수준이다. 합격선과의 간격은 여전히 매우 크다. 절벽 밀도가 성능에 큰 영향을 주지 않는 것으로 보이나, 이 PC 한 대·한 번의 실행 결과다.
- **flat edit 기준선에서 130ms 끊김 1회와 avg_cpu_ms 약 2배(10.86ms)** — 편집 시간 지표는 dense와 같은 수준이라 외부 요인(다른 프로그램 등)일 가능성을 추정하나 **확인하지 않았다.** 같은 flat edit 120초와 10분 실행(앞선 §8)에서는 100ms 초과가 0회였다. 100ms 초과 0회 기준을 이 한 번의 실행만으로 판정하지 말고, 재측정으로 확인해야 한다.
- dense edit의 메모리 증가(+14.4MB)가 flat(+7.1MB)보다 크다. 원인은 조사하지 않았다(변경 타일 델타·절벽 딕셔너리 증가 가능성은 추정일 뿐).

### 3-0c 완료 — flat edit 재측정 (1080p, vsync 해제, 120초 ×3)
130ms대 끊김이 이전 실행과 재측정 3회 **모두에서** 재현됐다(각 1~3회, 130.2~135.9ms). 단 33ms 초과 프레임 7건(이전 1건 포함)은 **전부 note 에 `flush`가 붙은 프레임**(프레임 index가 5000의 배수, 측정 도구가 행을 디스크에 쓰는 시점)이다. flush 프레임의 `cpu_ms`(TIME_PROCESS)는 2.5~7.1ms로 낮았다. 이후 구현 변경 없이 같은 flat edit 조건의 평균 프레임은 0.42→0.55ms로 올랐고, `avg_cpu_ms`는 10.9/19.2/19.6/48.0으로 편차가 컸다.
- 실행 중 백그라운드에서 LeagueClient·OP.GG·brave·RiotClientServices가 돌고 있었고, 시스템 CPU 사용률은 실행 전 34~42%, 후 31~57%였다. **측정 환경이 격리되지 않았다.** 이것이 원인인지는 확인하지 못했다.
- 이전의 dense 실행과 2-6d 실행(같은 flush 지점 포함)은 최대 10~13ms였으므로, flush 지연이 항상 있는 것은 아니다.
- 결론: 130ms 끊김은 게임 로직이 아니라 **측정 도구의 동기 디스크 쓰기**와 연결돼 보이지만 원인(디스크 경합, 백신, 백그라운드 프로그램)은 미확인이다. "100ms 초과 0회" 기준은 flush 프레임을 분리한 뒤 다시 판정한다(3-0d). 측정 시 백그라운드 프로그램을 종료해야 한다.
