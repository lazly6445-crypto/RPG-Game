# 젤다의 전설 시리즈 개발 철학·기법 조사 문서

신규 게임 개발의 설계 토대로 쓰기 위한 조사 정리. (조사일: 2026-10-10)

## 0. 읽는 법 / 신뢰도

- **A**: 개발자 본인 발언(인터뷰·발표)을 2차 보도가 인용한 것
- **B**: 기사·분석 글의 해석
- **C**: 팬 위키·블로그 수준 (참고용)
- 원문(Iwata Asks, CEDEC 2017 슬라이드, GDC 2017·2024 영상)은 접속 제한으로 **직접 확인하지 못했다.** 인용 전에 원문 확인 필요.
- 이 문서의 "10. 적용 원칙"은 조사 내용에서 도출한 **제안**이며 개발진이 직접 한 말이 아니다.

---

## 1. 개발진

| 구분 | 내용 |
|---|---|
| 개발사 | 닌텐도 EAD → (2015) 닌텐도 EPD |
| 협력 | 캡콤(Flagship), 그레쪼, 코에이테크모(오메가 포스) |
| 미야모토 시게루 | 창시자, 프로듀서·감수 |
| 데즈카 다카시 | 1편 공동 디렉터, 꿈꾸는 섬 디렉터 |
| 아오누마 에이지 | 시간의 오카리나 공동 디렉터, 이후 프로듀서 |
| 후지바야시 히데마로 | 스카이워드 소드·BotW·TotK 디렉터 |
| 도타 다쿠히로 | BotW·TotK 기술 디렉터 |
| 타키자와 사토루 | 바람의 택트 디자인 매니저, BotW·TotK 아트 디렉터 |
| 고이즈미 요시아키 | Z주목 고안, 무쥬라의 가면 3일 주기 제안, 꿈꾸는 섬 스토리 |
| 곤도 고지 | 초기 작품 작곡가 |
| 와카이 하지메·가타오카 마나카·이와타 야스아키 | BotW 음악 |

(역할 일부는 기억 기반이므로 크레딧 확인 필요.)

---

## 2. 시리즈 관통 설계 수칙

1. **가르치지 않고 유도한다.** 지형·랜드마크·일관된 규칙으로 안내하고 마커·튜토리얼을 줄인다. (BotW, TotK)
2. **적은 규칙을 넓게 곱한다.** 상황별 버튼(OoT) → 화학·물리 엔진(BotW) → 합체·울트라핸드(TotK).
3. **조작 마찰을 줄인다.** Z주목, 스냅 건설. 반대로 마찰이 큰 곳(물의 신전, 피 튜토리얼, 무기 파손)은 비판받았다.
4. **밀도 > 크기.** 무쥬라의 가면, 스카이로프트. 황혼의 공주의 "너무 큼"은 반성 대상이 됐다.
5. **제약 속에서 핵심 하나로 압축한다.** 평행 세계 여러 개 → 빛·어둠 둘, 일주일 주기 → 3일, 바다+셀 셰이딩.
6. **테스트로 보정한다.** 플레이어가 건너뛰는 구역에 표지를 추가.
7. **비판을 다음 작품에 반영한다.** 물의 신전 3DS판 수정, 황혼의 공주 → 스카이워드 소드의 압축 설계.

---

## 3. 작품별 정리

### 3.1 젤다의 전설 (1986)
- 처음엔 오버월드 없는 던전 위주 게임으로 설계됐다는 기사가 있음 (B, 원문 미확인).
- 미야모토가 『슈퍼 마리오』와 거의 동시에 만들었고 발매 간격은 반년 미만 (Iwata Asks).

### 3.2 신들의 트라이포스
- 평행 세계 여러 개 구상 → 빛·어둠 두 세계로 축소 (타나베, 데즈카) **A**
- 마법 거울로 두 세계를 오가며 같은 지형을 머릿속에 겹쳐 유지 **B**
- 어둠 세계 던전 일부가 빛 세계의 같은 위치에 있음 **C**
- 아이템이 진행 순서를 결정(아이템 게이팅). 던전 번호가 아니라 다음에 필요한 도구가 순서를 정함 **B**
- 대각선 공격 문제를 검 길게 누르기 회전 베기로 해결 (데즈카) **A**
- SNES 메모리 한계와 씨름 (데즈카). 오픈 월드 구상은 메모리에 막혔다 (미야모토) **A**
- 미야모토가 구상했다가 접은 것: 드퀘식 파티, 랜턴으로 풀밭에 불 지르기, 늪 파기 **A**

### 3.3 꿈꾸는 섬
- 비공식 사이드 프로젝트("방과 후 동아리" 분위기, 데즈카) → 트라이포스 게임보이판 구상이 독자 게임으로 발전 **A**
- 트윈 픽스처럼 소수 인물이 한 마을에서 만드는 드라마, 이해하기 쉬운 규모 + 뚜렷한 개성 (데즈카) **A**
- 타나베가 서브 이벤트, 고이즈미가 스토리 → 줄거리가 있는 첫 젤다 (아오누마) **A**

### 3.4 시간의 오카리나
- **Z주목**: 고이즈미가 마리오 64 작업 중 구상. 닌자·사무라이 무대 쇼에서 영감 **A/C**. 나비가 목표 적으로 날아가고 공격이 그 적을 향함 **C**
- **상황별 A 버튼**: 말 근처면 승마, 폭탄을 들면 던지기, 풀 앞이면 뽑기 **B**
- 아오누마가 던전 설계 담당. 보스방 입구를 일찍 보여 줘서 길을 찾게 하는 "미끼" 기법 **A**
- 3D에서는 패미컴식 "수상한 곳 시험" 비밀 방식이 안 맞아서 새 방식을 고민 (미야모토) **A**
- 물의 신전: 철 장화 반복 착탈로 최대 비판. 아오누마 사과, 3DS판에서 장화를 일반 아이템화+색 구분 **A/B**

### 3.5 무쥬라의 가면
- 미야모토 도전: 1년 안에 만들면 "뒷이야기" 스핀오프는 만들지 않아도 됨 **A**
- 3일 주기: 미야모토+고이즈미 아이디어. 컴팩트한 세계를 반복. 고이즈미가 OoT의 시간 경과 시스템 재활용 제안, 영화 「런 롤라 런」 언급(Famitsu) **A**
- 일주일 → 3일: 첫날 반복이 지루하고 마을 사람들의 일과를 기억하기 어려워서 **A**
- 평가: 출시 후 지속 상승, 컬트 지지. 3일 주기는 독특함 vs 답답함으로 갈림 **B**

### 3.6 바람의 택트
- 초기에 바다 배경 확정. 열린 바다가 게임 메커니즘을 만든다고 판단 (아오누마) **A**
- 셀 셰이딩은 아오누마 제안. N64판의 사실적 묘사가 조작성을 해쳤다고 판단, 캐릭터를 작게 만듦 (CVG 2003) **A**
- 처음엔 비주얼을 미야모토에게 비밀로 했다는 인터뷰 (MTV) **A**
- 링크가 멈추면 눈이 좌우로 움직임 → "시선이 곧 힌트". 이 기법은 바람의 택트가 처음, OoT 3D에 재사용 (Arimoto, 아오누마) **A**
- 툰 링크 디자인은 하루하나 요시키가 가져옴 (타키자와) **A**
- 출시 때는 화풍·낮은 난이도 논란과 판매 부진 → 후대 재평가 **B**. 약점: 항해가 지루하고 반복적이라는 평
- HD판 약 6개월, 셀 셰이딩 경험 부족으로 수작업 많음 (4Gamer) **A**

### 3.7 몽환의 모래시계
- 바람의 택트 판매 부진 후 셀 셰이딩에 다시 기회를 주려고 아오누마가 DS 프로토타입에 적용 요청 **A**

### 3.8 황혼의 공주
- 원래 게임큐브 전용 → Wii 대응, 발매 약 1년 지연. 미야모토는 "조작만 바꾸면 된다"고 했고 현장은 의문 (Iwata Asks) **A**
- 늑대 링크: 아오누마가 늑대가 되어 우리에 갇힌 꿈에서 착상, 다른 동물은 고려 안 함 (2016 Miiverse) **A** (보도 간 세부 차이 있음)
- 아오누마는 이후 "너무 크게 만들었다"고 돌아봄 **B**
- 모션 조작은 평이 엇갈림

### 3.9 스카이워드 소드
- 모션플러스로 검 조작 정밀도 상승, 처음엔 원하는 효과가 안 나와 여러 접근 시도 (아오누마) **A**
- 적 표현을 과장해 무기 든 모습을 읽고 대처하게 함 → 사실적 화풍과 안 맞아 화풍 변경 (아오누마) **A**
- 스카이로프트: 필드와 오가는 거점이라 방문 빈도가 높아 밀도를 높여야 했음 (이와모토·후지바야시) **A**
- 던전은 정통 퍼즐형. BotW의 "움직이는 던전"과 대비 (후지바야시) **A**
- 지역 간 **연결부**와 던전 입구 프레임을 미세 조정 **B**
- 평가: 출시 때 극찬 → 후대에 피 튜토리얼·반복 시련·선형성·모션 호불호로 재평가 **B**
- 음악: 오케스트라 녹음을 후반으로 미뤄 수정 여지 확보, 클릭 트랙으로 인터랙티브 음악 유지 (Wired 2011) **A**

### 3.10 시간 너머의 링크
- 벽 합체: 디렉터 시카타가 제안했지만 재미를 확신 못 함. 미야모토 첫 반응은 "20년 된 아이디어" **A**
- 위에서 내려다보는 시점 고정으로 벽 진입 시 측면 시점 전환이 설득력을 얻음, 프로토타입 후 퍼즐 확장 **A**
- 아오누마가 트라이포스 지형 재사용 제안 **A**

### 3.11 브레스 오브 더 와일드
- **곱셈형 설계**(후지바야시): 퍼즐 전용 오브젝트를 만드는 "덧셈형"에서 벗어나 오브젝트가 플레이어·서로에게 반응. 초대 NES 젤다의 2D 재현 프로토타입에서 시작 **A**
- **화학 엔진 + 물리 엔진**(도타): 불·얼음·바람 등 원소 규칙. 세계 규칙이 일관되면 플레이어가 스스로 시도를 떠올림 **A**
- **삼각형 규칙**(CEDEC 2017 보도): 큰 삼각형=랜드마크, 중간=경로 차폐, 작은 것=속도 조절, 직사각형=완전 가림. 시선을 정상으로 유도하고 경치를 점진적으로 드러냄 **B**
- **랜드마크 빵 부스러기**: 처음엔 탑+경로 → 흥미로운 랜드마크가 중요 장소로 이끄는 방식으로 변경 (GMTK 영상, 2차) **B**
- **플레이테스트 보정**: 플레이어가 건너뛰는 구역에 은은한 표지 추가 **B**
- 정보 최소화·튜토리얼 축소 (팬 블로그) **C**
- 음악: 오픈 월드에서 BGM을 줄여 환경음·발소리가 들리게 함. 와카이: 월드 규모 앞에서 음악 한 곡은 플레이어가 받는 영감에 못 미침. 시리즈 최초 피아노 주 악기 보도 **A/B**
- 평가: 칭찬은 플레이어 주도 이야기·창발적 플레이. 비판은 **무기 내구도**(전투 흐름 끊김), 조용한 스토리, 전통 던전 아쉬움

### 3.12 티어스 오브 더 킹덤
- **울트라핸드**: BotW 개발 막바지에 후지바야시가 물체 붙이기 실험, 전작 부품(톱니바퀴 바퀴 등)으로 만든 탈것을 프로토타입으로 제시 **A**
- **어센드**: 후지바야시가 테스트 중 동굴 천장에 오르려고 쓰던 디버그 기능에서 유래, 아오누마가 "돌아가기 번거롭다"며 도입을 밀음. 아오누마는 후기 추가라고 설명 **A**
- 전 오브젝트 물리화(GDC 2024), 45도 회전·스냅 포인트(2차 분석), 조합 경우의 수를 기획자·프로그래머가 하나하나 조정(도타) **A/B**
- 레고 같은 쉬움을 목표 **B**
- 하늘 섬: 새 메커니즘 시험하려고 계속 추가, 디자이너가 "어수선해졌다"고 불평할 정도. 지상~하늘을 이음새 없는 하나의 3차원 공간으로 **A**
- 던전: 전통 던전+BotW 신수 혼합. 하늘에서 뛰어내려 던전 이벤트 진입 **A**
- 지저(Depths): 지표와 반전된 대응 관계 덕에 프로그래머가 프로토타입을 빠르게 완성 (Famitsu) **A**
- 평가: 칭찬은 기존 맵 재맥락화, 창의적 건설. 비판은 탈것이 탐험 감소, 신규 지역 단조로움, 맵 재사용 반응 엇갈림

---

## 4. 호평받은 요소

| 요소 | 작품 |
|---|---|
| 탐험의 자유, 플레이어 주도 이야기 | BotW |
| 기존 세계의 재해석, 합체·건설의 창의성 | TotK |
| 압축된 세계의 반복 플레이, 감정적 깊이 | 무쥬라의 가면 |
| 분위기, 음악, 튜토리얼형 던전 | 시간의 오카리나 |
| 검 조작의 정밀함 | 스카이워드 소드 (호불호 있음) |
| 표현력 있는 화풍·캐릭터 | 바람의 택트 (후대 재평가) |
| 아이템 게이팅 + 두 세계 구조 | 신들의 트라이포스 |

---

## 5. 성공한 시스템·구현 기법

| 시스템 | 구현 | 효과 | 신뢰도 |
|---|---|---|---|
| Z주목 | 목표 적에 고정, 나비가 날아가 정보 제공 | 3D 카메라·조준 안정 | C |
| 상황별 A 버튼 | 주변 상황에 따라 기능 변경 | 버튼 수 증가 없이 조작 단순화 | B |
| 곱셈형 설계 + 화학·물리 엔진 | 일관된 원소 규칙 | 해법이 하나로 고정되지 않음 | A |
| 합체·울트라핸드 | 전 오브젝트 물리화, 45도·스냅 | 건설 장벽 낮춤 | A/B |
| 삼각형 규칙 | 지형으로 시선·경로 유도 | 강제 없이 목적지 선택 | B |
| 랜드마크 빵 부스러기 | 흥미로운 시각 목표 배치 | 호기심 기반 탐험 | B |
| 아이템 게이팅 | 던전이 다음 도구를 줌 | 진행감·순서 통제 | B |
| 두 세계 구조 | 같은 지형의 두 버전 | 적은 자산으로 콘텐츠 2배, 공간 기억 퍼즐 | B/C |
| 3일 주기 | 반복되는 컴팩트 세계 | 밀도 확보 | A |
| 시선 힌트 | 멈추면 눈이 사물을 봄 | UI 없이 힌트 | A |
| 적 표현 과장 | 무기 든 모습 읽기 | 모션 검술의 가독성 | A |
| 반전 대응 지형 | 지저=지표 반전 | 제작 속도 | A |

---

## 6. 몰입 장치

- 정보 최소화 / 지도 마커 없이 "저기 가고 싶다"는 동기 (Sandfall 기욤 브로슈의 BotW 평) **B**
- 일관된 규칙의 세계(도타) **A**
- 환경음 중심 사운드, 오픈 월드 BGM 절제 **A/B**
- 환경 중심 설계: 학술 연구(Shinobi Valley)에서 플레이어의 호기심 성향보다 환경이 탐험을 좌우함. 젤다가 아닌 게임의 실험이라 간접 근거 **B**
- 시선 힌트 같은 비UI 안내 **A**
- 지역 간 연결부와 입구 연출 **B**

---

## 7. 비판과 실패에서 얻는 교훈

| 문제 | 사례 | 교훈 |
|---|---|---|
| 반복되는 착탈·조작 | 물의 신전 철 장화 | 같은 번거로움을 반복시키지 말 것 |
| 건너뛸 수 없는 안내 | 피(Fi) 튜토리얼 | 안내는 스킵 가능하게 |
| 반복 콘텐츠 | 빛의 눈물 시련, 감금된 자 전투 | 같은 구조 재사용 시 변주 필요 |
| 선형성·빈 공간 | 스카이워드 소드 하늘 | 이동 구간에도 의미를 |
| 자원 관리 마찰 | BotW 무기 내구도 | 실험 유도 vs 전투 흐름 끊김의 균형 |
| 이동 수단의 탐험 잠식 | TotK 탈것 | 강한 도구는 탐험 동기를 깎을 수 있음 |
| 지역 단조로움 | TotK 하늘 섬·동굴 | 규모를 늘려도 변주가 없으면 얕아짐 |
| 규모 과다 | 황혼의 공주 | 밀도 확보 |
| 화풍 논란 | 바람의 택트 | 새 시도는 단기 판매 위험, 장기 재평가 가능 |
| 지루한 이동 | 바람의 택트 항해 | 이동 자체를 콘텐츠로 만들거나 줄일 것 |

---

## 8. 음악·사운드

- 곤도 고지, OoT 메인 테마: 8마디 단위로 나누고 무작위 구성을 넣어 들을 때마다 선율이 달라지게 함. 미야모토·아오누마가 테마 발전에 재량을 줌 **A**
- 스카이워드 소드: 오케스트라 녹음을 개발 후반으로, 클릭 트랙에 맞춰 연주를 겹쳐 인터랙티브 음악 유지, 역동성이 필요한 곳엔 생성 음악 **A**
- BotW: 아래 3.11 참조. 전투 음악은 1년간 여러 유형을 시도하고 게임플레이와 상호작용하는 방식을 넣음 **A**

---

## 9. 확인하지 못한 부분 (추가 조사 대상)

- Iwata Asks, CEDEC 2017, GDC 2017·2024 원문 직접 확인
- 리콜(Recall)의 유래
- 스카이워드 소드의 침묵의 영역, 스카이로프트 철학
- 시간 너머의 링크의 대여·비선형 설계 의도
- 바람의 택트의 풍향 시스템
- 1편(NES) 개발 배경, 캡콤 협업작(이상한 모자·이상한 열매 등)
- 황혼의 공주의 어두운 사실적 분위기 의도
- 점수/집계 (Metacritic 직접 확인 필요)

---

## 10. 신규 게임 개발 적용 원칙 (제안)

> 위 조사에서 도출한 제안. 개발진의 발언이 아님.

1. **핵심 규칙 1~2개를 정하고 세계 전체에 일관되게 적용한다.** 퍼즐마다 전용 오브젝트를 만들기 전에 규칙으로 풀 수 있는지 먼저 본다.
2. **조작은 맥락 기반으로 단순화한다.** 버튼 추가보다 상황별 기능 변경을 우선한다.
3. **안내는 환경으로 한다.** 랜드마크, 시선 유도, 소리와 연출. 마커·튜토리얼은 필요 시 스킵 가능하게.
4. **세계는 크기보다 밀도.** 이동 구간에도 의미를 부여하고, 영역 간 연결부·입구에 공을 들인다.
5. **한 가지 핵심 아이디어에 압축한다.** 제약(기간·기기·메모리)을 압축의 이유로 쓴다.
6. **프로토타입으로 재미를 검증한다.** 벽 합체, 울트라핸드처럼 확신이 없는 아이디어도 작게 만들어 본다.
7. **플레이테스트로 건너뛰는 구역과 마찰 지점을 찾는다.** 반복되는 착탈·튜토리얼·전투 흐름 단절을 우선 점검한다.
8. **강한 이동/해결 도구는 탐험 동기와의 충돌을 미리 검토한다.**
9. **지역마다 변주를 확보한다.** 규모를 늘릴 때 반복 구조를 점검한다.
10. **음악·사운드로 페이싱을 조절한다.** 침묵과 환경음도 설계 대상으로 둔다.
11. **UI 없이 전달하는 힌트(시선, 소리, 지형)를 설계 단계에서 목록화한다.**
12. **디버그 기능과 실험 도구에서 신규 기능을 건진다.** (어센드 사례)

### 체크리스트 (설계 리뷰용)
- [ ] 이 규칙이 새 상황에서 조합되는가(곱셈형)?
- [ ] 같은 번거로움이 3번 이상 반복되는 곳이 있는가?
- [ ] 플레이어가 건너뛸 수 있는 중요한 구역이 있는가?
- [ ] 이동 수단/도구가 콘텐츠를 건너뛰게 하는가?
- [ ] 영역·던전 진입 연출이 있는가?
- [ ] 새 지역마다 서로 다른 규칙/위협/보상이 있는가?

---

## 11. 출처

**개발자 인터뷰·발표**
- [Iwata Asks: Skyward Sword](https://iwataasks.nintendo.com/interviews/wii/zelda-skyward-sword/4/1) / [Vol.1](https://nintendo.co.uk/Iwata-Asks/Iwata-Asks-The-Legend-of-Zelda-Skyward-Sword/Vol-1-Wii-MotionPlus-Inspires-New-Controls/1-Starting-with-a-Detour/1-Starting-with-a-Detour-236062.html)
- [Iwata Asks: Wind Waker](https://iwataasks.nintendo.com/interviews/wiiu/wind-waker/0/4)
- [Iwata Asks: Majora's Mask 3D](https://nintendo.co.uk/Iwata-Asks/Iwata-Asks-The-Legend-of-Zelda-Majora-s-Mask-3D/The-Legend-of-Zelda-Majora-s-Mask-3D/1-Make-it-in-a-Year/1-Make-it-in-a-Year-959667.html)
- [Iwata Asks: ALBW](https://iwataasks.nintendo.com/interviews/3ds/a-link-between-worlds/0/1)
- [Iwata Asks: Zelda handheld history](https://nintendo.co.uk/Iwata-Asks/Iwata-Asks-The-Legend-of-Zelda-Spirit-Tracks/Iwata-Asks-Zelda-Handheld-History-/2-Kirby-and-Chomps-in-Zelda/2-Kirby-and-Chomps-in-Zelda-233781.html)
- [Nintendo: TotK Ask the Developer 03](https://www.nintendo.com/sg/interview/totk/03.html) / [04](https://www.nintendo.com/sg/interview/totk/04.html)
- [CVG 2003 interview](https://zeldadungeon.net/wiki/Interview:CVG_May_23rd_2003)
- [Wired 2011 (Kondo)](https://zeldadungeon.net/wiki/Interview:Wired_October_26th_2011)
- [Nintendo Life: Kondo](https://www.nintendolife.com/news/2014/12/koji_kondo_discusses_music_creation_for_iconic_mario_and_legend_of_zelda_games)
- [Engadget: BotW GDC](https://www.engadget.com/2017-03-12-breath-of-the-wild-gdc-talk.html)
- [Thumbsticks: BotW GDC 2017](https://www.thumbsticks.com/gdc-17-breath-of-the-wild-science-lies/)
- [TechSpot: Zelda physics GDC](https://www.techspot.com/news/102483-nintendo-explains-philosophy-behind-zelda-physics-gdc.html)
- [Game Developer: Majora's Mask in a year](https://www.gamedeveloper.com/game-platforms/aonuma-i-zelda-majora-s-mask-i-made-in-one-year-after-miyamoto-s-challenge)
- [Nintendo Life: Miyamoto LttP interview](https://www.nintendolife.com/news/2016/12/freshly_translated_interview_with_miyamoto_gives_insight_into_the_development_of_a_link_to_the_past)
- [GoNintendo: LttP parallel worlds](https://gonintendo.com/archives/328296-nintendo-originally-considered-multiple-parallel-worlds-for-the-legend-of-zelda-a)
- [Zelda Universe: Link's Awakening side project](https://zeldauniverse.net/2016/03/11/links-awakening-started-as-unsanctioned-side-project/)
- [Zelda Universe: ALBW Iwata Asks](https://zeldauniverse.net/2013/11/21/iwata-asks-albw-began-as-spirit-tracks-sequel-originally-the-new-legend-of-zelda-slanted-visual-perspective-and-more/)
- [Nintendo Wire: Aonuma Miiverse](https://nintendowire.com/news/2016/04/16/eiji-aonuma-discusses-twilight-princess-hd-miiverse/)
- [GoNintendo: TotK Ultrahand and Ascend](https://gonintendo.com/contents/20253-zelda-tears-of-the-kingdom-devs-reveal-what-inspired-link-s-ultrahand-and-ascend)
- [Zelda Dungeon: TotK dungeon design](https://www.zeldadungeon.net/?p=201151)
- [Zelda Dungeon: Depths made quickly](https://www.zeldadungeon.net/the-legend-of-zelda-tears-of-the-kingdom-developers-say-the-depths-were-made-in-a-surprisingly-short-period-of-time/)
- [Destructoid: BotW soundtrack](https://www.destructoid.com/?p=264144) / [iMore](https://www.imore.com/why-legend-zelda-breath-wilds-sound-design-perfect)

**분석·리뷰**
- [GMTK: How Nintendo Solved Zelda's Open World Problem](https://gmtk.substack.com/p/how-nintendo-solved-zeldas-open-world)
- [GamingBolt: BotW triangles](https://gamingbolt.com/the-legend-of-zelda-breath-of-the-wilds-ingenious-world-design-owes-itself-to-triangles/amp)
- [80.lv: BotW design secrets](https://80.lv/articles/the-design-secrets-of-breath-of-the-wild/)
- [Gigazine: BotW design secret](https://gigazine.net/gsc_news/en/20171004-breath-of-the-wild-design-secret)
- [Medium: Dohta's multiplicative gameplay](https://medium.com/design-bootcamp/designing-action-exploring-takuhiro-dohtas-framework-of-multiplicative-gameplay-1caf3a833a38)
- [Game Developer: LttP Light World analysis](https://www.gamedeveloper.com/business/overworld-overload-an-analysis-of-link-to-the-past-s-light-world-part-2)
- [Game Developer: art of Wind Waker and Twilight Princess](https://www.gamedeveloper.com/business/becoming-the-brand-the-art-of-wind-waker-and-twilight-princess)
- [Games.gg: Expedition 33 director on BotW](https://games.gg/news/expedition-33-director-breath-of-the/)
- [CHI Play study](https://api.crossref.org/works/10.1145%2F3474698)
- [GameCritics: BotW second opinion](https://gamecritics.com/brad-gallaway/the-legend-of-zelda-breath-of-the-wild-second-opinion/)
- [RPG Site: TotK review](https://www.rpgsite.net/review/14176-the-legend-of-zelda-tears-of-the-kingdom-review)
- [Reverse Shot: TotK](https://reverseshot.org/features/3092/tears_kingdom)
- [Den of Geek: forgive Skyward Sword](https://www.denofgeek.com/games/the-legend-of-zelda-why-its-time-to-forgive-skyward-sword/)
- [Cubed3: Skyward Sword second opinion](https://www.cubed3.com/games/reviews/wii/the-legend-of-zelda-skyward-sword-second-opinion)
- [Nintendo Life: Water Temple](https://www.nintendolife.com/features/soapbox-ocarina-of-times-water-temple-was-tough-but-it-doesnt-deserve-its-reputation)
- [Inverse: OoT Water Temple](https://inverse.com/gaming/zelda-ocarina-of-time-25-anniversary-water-temple)
- [Inverse: Majora's Mask 25th](https://www.inverse.com/gaming/legend-of-zelda-majoras-mask-25-anniversary)
- [Wikipedia: Ocarina of Time](https://en.wikipedia.org/wiki/The_Legend_of_Zelda:_Ocarina_of_Time) / [Wind Waker](https://en.wikipedia.org/wiki/The_Legend_of_Zelda:_The_Wind_Waker)
- [Zelda Wiki: Z-Targeting](https://zeldawiki.wiki/wiki/Z-Targeting)
