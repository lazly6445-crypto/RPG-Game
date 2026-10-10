# 몇백 시간을 즐기는 오픈월드 RPG 개발 요소 조사

목표: 플레이어가 푹 빠져 수백 시간을 즐기는 오픈월드 RPG를 만들기 위해 필요한 요소를 조사한다. (조사일: 2026-10-10)

관련 문서: `zelda-design-reference.md`(젤다 시리즈), `zelda-like-games-reference.md`(젤다류 게임)

---

## 0. 먼저 읽을 것: 범위·신뢰도·한계

### 신뢰도 표기
- **A**: 개발자·연구자 본인 발언/논문을 2차 보도가 인용한 것
- **B**: 기사·분석 글의 해석
- **C**: 블로그·포럼·팬 위키·리스트 기사 (참고용, 단독 근거로 쓰지 말 것)
- **[제안]**: 조사 내용에서 내가 도출한 제안. 누구의 발언도 아님.

### 한계 (중요)
1. **웹 페이지 원문 열람이 전부 막혀 있다.** 모든 내용은 검색 결과 요약이다. GDC Vault, Game Developer, Wikipedia 원문을 직접 읽지 못했다.
2. **수치는 대부분 추정이거나 출처가 약하다.** 확인된 수치는 해당 위치에 따로 표기했다.
3. **"전부"는 불가능하다.** 아래는 조사로 확인된 만큼이며, 확인하지 못한 영역은 18장에 모았다.
4. 몇백 시간 몰입의 원인을 규명한 실증 연구는 찾지 못했다. 가장 가까운 것은 동기 이론(SDT)과 사례 분석이다.

### 요약이 아니라 깊이를 원하는 경우
이 문서는 확인된 사실을 가능한 한 빠짐없이 담았다. 다만 근거 자체가 얕은 영역(예: 전투 설계, 스킬 트리, 경제)은 일반론 수준이다. 그런 영역은 18장의 추가 조사 계획대로 원문(GDC 발표, 개발자 인터뷰)을 직접 확인해야 깊이를 확보할 수 있다.

---

## 1. "몇백 시간"은 어디서 나오는가

### 1.1 확인된 사례
| 게임 | 확인된 내용 | 신뢰도 |
|---|---|---|
| 스카이림 | 메인 스토리는 약 30시간, 곁가지 탐험으로 100시간 이상. 선택 콘텐츠와 자유감이 특징. 모드 커뮤니티가 수명을 늘림 | C |
| 엘든 링 | 정보 없이 가서 조금씩 알아가는 경험, 방대한 무기·갑옷·부적 조합이 재시작 동기 | C |
| 발더스 게이트 3 | 롤플레이·퀘스트 해결 방식의 다양성, 분기. 얼리 액세스에서 300~400시간 플레이한 사람이 있었다고 스벤 빈케가 언급 | A/C |
| 위쳐 3 | 글쓰기와 순간 플레이의 만족이 재방문 동기라는 의견. 반대로 한 번 끝내고 다시 하고 싶지 않다는 의견도 있음 | C |
| 켄쇼 같은 샌드박스 | 무한히 플레이 가능 | C |

### 1.2 반복되는 원인 후보 (사례 분석 기반, 모두 B/C)
1. 선택 콘텐츠와 자유 (스카이림)
2. 발견과 미스터리 (엘든 링)
3. 선택·분기·롤플레이 (BG3)
4. 빌드·장비 다양성 (엘든 링, 스카이림)
5. 창발적 시스템: 설계자가 예상 못 한 상호작용이 플레이 시간과 재방문을 늘린다 (생산 분석 글)
6. 글쓰기와 순간 플레이의 감각 (위쳐 3)
7. 모드·커뮤니티 (스카이림, BG3)

### 1.3 반대 증거
- 한 분석은 대부분 오픈월드에는 **대부분의 콘텐츠를 수행할 이유가 충분하지 않다**고 지적한다. (B/C)
- 플레이 시간 길이 자체는 가치가 아니며 사용자는 "재미를 찾는" 시간이 없다는 의견이 있다. (C)

### 1.4 [제안] 이 장의 결론
수백 시간의 원인은 단일 요소가 아니라 **계속 이어지는 목표·발견·선택·표현(빌드)·사회적 연결**의 조합으로 보인다. 어느 하나라도 끊기면 중간에 이탈한다. 따라서 각 시간대(1시간/10시간/50시간/200시간)에 이탈 방지 장치를 설계 단계에서 따로 정한다.

---

## 2. 동기 이론

### 2.1 자기결정이론(SDT)
- 라이언·릭비·프르지빌스키(2006, 《Motivation and Emotion》) 4개 연구: 게임 내 **자율성**과 **유능감**의 인식이 즐거움, 선호, 플레이 전후 웰빙 변화와 연결된다. 온라인 멀티플레이 커뮤니티 연구에서는 자율성·유능감·**관계성** 세 욕구가 각각 독립적으로 즐거움과 향후 플레이를 예측했다. (A)
- 2010년 후속 모델: 게임의 매력과 웰빙 효과가 세 기본 심리 욕구를 충족하는 잠재력에 기반한다. 측정 도구로 PENS(Player Experience of Need Satisfaction)가 나왔다. (A)
- 후속 연구는 게임 기능이 세 욕구를 어떻게 일으키거나 해치는지, 그리고 내재 동기·즐거움·지속 참여에 미치는 영향을 다룬다. (B)
- **한계**: 웰빙 효과는 단기이며 장기 지속 참여를 직접 검증한 증거는 얇다. CHI/CHI Play 리뷰는 관계성이 거의 연구되지 않았다고 지적한다. (A)

### 2.2 Quantic Foundry 게이머 동기 모델
- 12개 동기 요인을 6개 클러스터(Action, Social, Mastery, Achievement, Immersion, Creativity)로 묶는다. 닉 이의 이전 연구를 확장한 것이며 175만 명 이상 설문 데이터에 기반한다고 주장한다. (B)
- 동기 12개의 전체 이름과 RPG 장르별 수치는 이번에 확인하지 못했다.

### 2.3 [제안] 설계에 대한 함의
- **자율성**: 목표·순서·접근 방식을 플레이어가 고른다 (BotW, 스카이림, BG3의 공통점).
- **유능감**: 성장이 체감된다. 레벨 스케일링처럼 성장 체감을 깎는 요소를 경계한다 (9장).
- **관계성**: 동료 캐릭터, 세계 속 NPC 관계, 커뮤니티/모드 (6장, 15장).
- 위 세 욕구를 각 시간대마다 최소 하나씩 만족시키는지 점검 항목으로 쓴다.

---

## 3. 루프 구조

### 3.1 확인된 개념
- 루프는 순간(moment-to-moment), 분, 시간, 일 단위로 중첩해 설계한다. (B)
- 핵심 루프는 5분을, 메타 루프는 5개월을 유지시킨다는 표현이 있다. 메타 루프의 업그레이드가 핵심 루프로 다시 흘러 들어간다. (B)
- 장기 유지는 **진행감**과 **다가올 진행의 암시**의 조합이 뼈대다. (B)
- 플레이어는 환경에 익숙해지면 더 큰 랜드마크를 알아보고 점점 더 멀리 나아가며 스스로 목표를 만든다. (B)
- 오픈월드·스토리 중심 RPG는 단기 진행보다 장기 목표에 초점을 맞추므로, 이미 투자한 팬에게는 통하지만 신규 플레이어에게는 동기가 약할 수 있다는 경고가 있다. (B)

### 3.2 [제안] 루프 설계 틀
| 시간대 | 질문 | 예시 장치(조사에서 확인된 것) |
|---|---|---|
| 몇 초 | 한 번의 조작이 즐거운가 | 입력 버퍼, 히트스톱 (8장) |
| 몇 분 | 눈에 띈 것을 향해 가는 동기가 있는가 | 랜드마크 유도 (젤다 문서 참고) |
| 한 시간 | 한 번의 모험이 완결감이 있는가 | 퀘스트 구조 (5장) |
| 10시간 | 성장과 새 가능성이 열리는가 | 이동기·아이템 게이팅 (젤다 문서 참고) |
| 50시간+ | 새 목표와 새 빌드, 새 관계가 생기는가 | 빌드 다양성, 동료, 모드 (6·9·15장) |

---

## 4. 월드 설계

### 4.1 이동과 지형이 월드 체감 크기를 만든다
- 토드 하워드(Gamasutra): 스카이림의 산은 직선 이동을 막고 우회·등반을 강제한다. 맵 크기는 오블리비언과 비슷하게 유지하면서 이동 시간이 길어져 더 크게 느껴진다. 고도가 높을수록 난이도를 높이려 했다. (A)
- 팀 모토: "위대한 게임은 만들어지는 게 아니라 플레이된다" → 종이에서 완벽하게 만들기보다 게임에서 시험한다. 드래곤 설계는 한 장짜리 문서였다. (A)
- 하워드는 이후 스카이림 일부는 충분히 깊지 않았고 상호작용이 겉치레인 부분이 있었다고 회고했다. (A)

### 4.2 관심 지점(POI) 배치
- 60~120초 이동 간격, 빠른 이동 지점은 도보 3~5분 간격이라는 제안이 있다. **단일 블로그의 경험칙이며 검증된 표준이 아니다.** (C)
- 자원이나 POI를 무작위로 뿌리기보다 "미니 클러스터"로 묶는다는 주장. (B)
- "POI 다양성 규칙": 어디로 가든 지평선에 서로 다른 플레이를 제공하는 POI가 최소 세 개 보이게. (C)
- BotW 사례(젤다 문서 참고): 삼각형 지형으로 시선을 유도하고, 랜드마크 빵 부스러기로 호기심을 끈다.

### 4.3 유비소프트식 공식에 대한 비판
- 높은 전망대를 올라 지도 아이콘을 열고, 임무를 반복하는 루프가 업계의 농담거리가 됐다는 비판. 전망대 대부분이 주변을 드러내 아이콘을 추가하는 용도뿐이다. (B)
- 지도가 커지면서 상호작용 콘텐츠의 밀도가 낮아졌고, 반복·과다 마커·체크리스트가 독창성을 없앤다는 지적. (B)
- 반대 의견: 전망대는 미니맵 의존을 줄여 주고 잘 만들면 재미있다. (C)
- 대비 사례: 워치독스 2는 사이드 미션마다 고유한 이야기와 배경이 있다는 평. (B)

### 4.4 스타필드의 교훈 (비판 사례)
- 로딩 화면과 빠른 이동 중심이라 이륙·착륙·진입이 이음새 없지 않다는 비판. (B/C)
- 행성이 1,000개이지만 의미 있는 POI가 부족하고 콘텐츠가 복제된다는 불만. 베데스다는 "작음과 압도감"을 의도했다고 반박. 스팀 평가는 출시 당시 "복합적"(약 69% 추천). (C)
- 옹호 의견: 다른 장르의 조밀한 월드는 행성 규모로 확장되지 않는다. (C)
- [제안] 규모보다 **밀도와 고유성**이 우선이다. 복제 콘텐츠로 규모를 늘리면 발견의 가치가 떨어진다.

### 4.5 엘든 링 월드 구조
- 개발 초기에 보스 위치를 맵 전체에 먼저 놓고, 맵을 보스 전투에 맞춰 설계한 뒤 보스를 환경에 맞춰 조정했다 (미야자키). (A)
- 레거시 던전 6개: 서로 얽힌 거대한 레벨, 수백 개의 비밀, 지름길, 수직성. 카타콤 등 소형 던전은 휴식 역할. 필드 보스는 서로 섞여 보인다는 불만도 있음. (B/C)
- 핵심 과제 두 가지: 스튜디오 스타일 유지 + 새 개방감, 탐험과 보스전의 균형·진행 순서(페이싱). (A)

### 4.6 PCG vs 수작업
- 호라이즌 제로 던: GPU 기반 런타임 절차적 배치 시스템. 아티스트가 그래프 에디터로 배치 규칙을 만들고, 식생·바위뿐 아니라 사운드, 이펙트, 야생동물, 게임플레이 요소까지 플레이어 주변에 실시간 생성한다. 아티스트가 수작업 에셋과 함께 규칙을 수정할 수 있어 결과물이 편집 가능하다. (A/B, GDC 2017로 추정되나 연도 불확실)
- 하우디니(Houdini)로 만든 강 도구도 사용. (B)

---

## 5. 퀘스트와 서사

### 5.1 위쳐 3 퀘스트 설계 (CDPR)
- 파웨우 사스코(GDC 2023, "위쳐 3·사이버펑크 2077에서 얻은 10가지 퀘스트 설계 교훈"): 비선형 서사를 만드는 사람을 위한 내용. 핵심 정보 전달법, 선택의 의미 부여, 자원 낭비 없이 서사 복잡성을 더하는 법. (A)
  - 플레이어가 이야기를 **원하게** 만든다. 일부 핵심 정보를 숨기면 다음 조각을 쫓게 된다. (A)
  - 감정적 임팩트를 스펙터클보다 우선한다. (A)
  - 과설계를 피한다. "게임은 인생 시뮬레이션이 아니라 엔터테인먼트다". 의미 있는 곳에만 디테일. (A)
  - Play(하게 한다) → Show(보여 준다) → Tell(말한다) 순서 (Gamescom LATAM). (A)
  - 장르와 테마를 초기에 정의해 팀이 검증 기준을 갖는다. (A)
  - 열 가지 중 일부만 확인. 나머지는 GDC Vault 원문 필요.
- 아이디어 수용률: 좋은 디자이너의 아이디어 채택률은 5~10% (사스코, PC Gamer). 최고의 사이드 콘텐츠는 큰 폐기 풀에서 나온다. (A)
- 파이프라인(마테우시 토마셰프스키): 메인 퀘스트 아이디어는 작가팀에서 많이 나오고, 사이드 퀘스트는 대부분 퀘스트 디자이너가 직접 제안한다. 짧은 피치 → 팀이 추림 → 사건의 토대와 구체적 장면 아이디어를 담은 시나리오 → 작가의 여러 차례 수정 → 퀘스트 디자이너가 임시 에셋으로 엔진에서 1차 초안 구현(필요한 캐릭터·장소·아이템·음악 목록 작성) → 다른 부서가 최종 에셋 제작. (A)
- 가장 오래 걸린 것: 피투성이 남작 퀘스트라인(글쓰기), 케어 모헨 전투(기술적 난이도, 선택에 따라 조연 9~16명이 임의 조합으로 등장). (A)
- 콘라트 토마셰프스키(총괄): 감정을 불러일으키고 서사적으로 무언가를 이끌어내지 못하는 퀘스트는 가치가 적다. 스카이림 퀘스트를 일반적이라고 비판. (A)
- 수집 퀘스트: 드래곤 에이지: 인퀴지션은 수집 퀘스트가 너무 많다는 평가, 폴아웃: 뉴 베가스를 퀘스트 모델로 선호 (마테우시). (A)
- 위쳐 2는 사이드 퀘스트가 부족하다는 피드백이 있어 3편에서 사이드 활동을 크게 늘렸다. (B)

### 5.2 스카이림 방식
- 라디언트 스토리(Radiant Story): 선택형 사이드 퀘스트를 만들고, 플레이어 행동에 따라 퀘스트 구조를 동적으로 바꾼다. (B)
- 직접 작성한 퀘스트(위쳐 3)와 시스템 생성 퀘스트(스카이림)의 대비는 반복적으로 거론된다. 5~10%의 채택률 같은 수작업 방식은 비용이 크다.

### 5.3 [제안]
- 사이드 퀘스트마다 서로 다른 감정, 장소, 메커니즘을 목표로 하고 수집·배달 퀘스트는 최소화한다.
- 퀘스트당 피치 → 폐기 → 초안 → 임시 에셋 구현 파이프라인을 일찍 확립한다 (생산 비용 추정의 기준).

---

## 6. 선택, 반응성, 동료

### 6.1 BG3 (라리안)
- 대화뿐 아니라 전투와 탐험에서의 결정도 장·단기 결과를 만들어 고유한 이야기를 형성하는 것이 목표. 동료 관계가 진행되는 모든 단계에 반응 시스템이 있고 관계 전개의 순열이 수백 가지. (A)
- 얼리 액세스에서 플레이어 행동을 추적했다: 어디서 죽는지, 누구에게 호감을 표하는지, 누구를 죽이는지·영입하는지, 어떤 대화 선택지를 고르는지, 어떤 분기가 플레이어를 막는지. 이 데이터로 설계를 조정. (A)
- 피드백이 캐릭터 조정으로 이어진 사례: 섀도하트가 너무 못됐다는 피드백이 반복돼, 성격은 유지하면서 이해하고 가까워질 기회를 늘렸다. (A)
- 번아웃을 막으려 콘텐츠를 아껴 둔 점도 언급. (A)
- 모든 취향을 만족시키는 균형은 불가능하다고 보고 모딩이 여러 버전을 낳으리라 예상했다. (A)
- BG3 모드 다운로드 규모를 다룬 기사가 있으나 수치는 확인하지 못했다. (C)

### 6.2 동료 캐릭터 연구
- 로맨스는 신뢰·선택·집단 역학·실패 비용을 바꿀 때 RPG를 개선한다. BG3는 로맨스 전에 행동 기록을 쌓아 승인(approval)이 동료가 플레이어 결정을 해석하는 틀이 되게 한다. 대화와 동료 퀘스트가 관계를 지속시킨다. (B)
- CHI PLAY 2019 연구(213명): 감정적 애착은 7가지로, 게임 내 능력에 대한 존경부터 안위에 대한 깊은 걱정까지. (A)
- Mindtrek 논문: 동료 설계 공간 = 외형, 지각력, 개성, 행동, 의사소통 능력, 플레이어와의 관계, 중요도. (A)
- 옵시디언 작가: 팀에 도움이 안 되는 동료는 오래 남지 않는다. (B)

### 6.3 [제안]
- 동료는 서사만이 아니라 **전투/탐험 기능**에서도 유용해야 한다.
- 선택의 결과를 짧은 시간 안에 한 번 이상 눈에 보이게 한다.
- 출시 전에 행동 텔레메트리를 얻을 방법(얼리 액세스, 내부 플레이테스트)을 계획한다.

---

## 7. 시스템 시뮬레이션과 창발

### 7.1 이머시브 심(Immersive Sim)
- 장르가 아닌 설계 방향. 룩킹 글래스에서 출발해 워런 스펙터(이온 스톰 → 데우스 엑스), 아케인(디스아너드)이 계승. (B)
- 특징: 물리·AI로 믿을 만한 행동 구현, 한 상황에 여러 해법, 월드가 플레이어 행동을 기록, 일관된 시뮬레이션, 선택에 대한 게임의 반응. (B)
- "되어야 할 것이 되면 보상받는다" 원칙(PC Gamer). 블링크는 거의 모든 표면을 도구로 만든다. (B)
- 직접 인용할 스펙터 본인의 발언은 확인하지 못했다.

### 7.2 레드 데드 리뎀션 2 (록스타)
- 임란 사르와르(디자인 디렉터): 갱 멤버가 더 똑똑하고 기억력이 좋아야 하며 아서에게 자연스럽게 반응해야 한다. 모든 NPC와 총을 뽑지 않고도 여러 방식으로 상호작용 가능, 사람·상황에 따라 선택지 달라짐. 갱 구성원은 아서가 캠프에 있는지, 바깥에서 문제가 있는지 안다. (A, Official Xbox Magazine 2018)
- 팀 약 1,600명(총 약 2,000명, 기네스 기록), 추정 개발비 1.7~2.4억 달러(공식 수치 없음), 일부 구간 "주 100시간" 근무 보도, 댄 하우저는 일정과 예산을 초과했다고 인정. (B)
- NPC 반응이 일관되지 않다는 플레이어 보고도 있음. (C)
- 시스템적 AI의 세부(스크립트 vs 시스템 비율)는 확인하지 못함.

### 7.3 NPC 일정과 라디언트 AI
- 오블리비언: NPC 1,000명 이상이 24시간 일정(수면, 식사, 근무, 독서)을 가지며 목표를 위해 월드 지식을 사용하도록 설계됐지만, 출시판은 훨씬 제한됐다. (B)
- 부작용 사례: 모든 마을 사람이 점심에 한 술집으로 몰려 도둑이 소매치기. 경비병끼리 전투. (C)
- 스카이림: 일정은 유지, 창발 층은 축소. (B)
- 핵심 난제: 규모(1,000명+), 상호작용 경우의 수, 스크립팅 부담. (B)
- 킹덤 컴 디라이버런스의 방식은 확인 못 함.

### 7.4 [제안]
- 시스템 창발은 **통제 가능한 범위**로 시작한다 (스카이림이 오블리비언의 창발을 축소한 사례).
- 창발 시스템을 테스트하는 전용 시나리오와 자동 시뮬레이션 테스트를 일찍 갖춘다 (규모 증가 시 결함이 폭증하는 사례 참고).

---

## 8. 전투와 게임 필

> 이 영역은 근거가 가장 얕다. 스티브 스윙크의 《Game Feel》과 GDC 발표는 확인하지 못했다.

- 입력 버퍼링: 동작 창이 열리기 전에 누른 입력이 사라지지 않게 짧게 기억한다. (C)
- 히트스톱이 타격감을, 입력 버퍼가 타이밍 관대함을, 코요테 타임이 의도 존중을 만든다. (C)
- 읽기 쉬움, 즉각 반응, 행동 확정(commitment), 피드백 / 공격은 예고(telegraph)할 것 / 입력 지연 최소화 / 안전한 선택이 항상 있으면 전투가 얕아진다. (C, AI 에이전트용 스킬 문서이므로 권위 낮음)
- 소리·진동·화면 효과 조합과 카메라 흔들림·줌이 타격감과 템포에 영향. (C)
- 스카이워드 소드의 적 표현 과장 등 읽기 쉬움 사례는 젤다 문서 참고.

**[제안]** 신뢰할 만한 근거를 위해 18장에서 《Game Feel》, GDC 전투 발표, 특정 게임의 전투 인터뷰를 따로 조사한다.

---

## 9. 성장, 빌드, 루팅, 난이도

### 9.1 레벨 스케일링
- 오블리비언: 적이 플레이어 레벨에 맞춰 스케일링되어 성장 체감이 약해지고, 적이 비례가 아니라 기하급수로 강해지며, 스킬 포인트를 잘못 쓰면 일부 적이 매우 어려워진다는 비판. 모로윈드는 레벨이 등장 적 종류만 조절했다. (B/C)
- 대안: 고정 레벨 적 (Nehrim 모드, 이후 스카이림). 옹호: 규모가 큰 게임에는 스케일링이 좋은 아이디어이며 문제는 실행. 스카이림이 균형이 낫다는 평. (C)
- 위쳐 3, 엘든 링의 난이도 설계 비교는 확인하지 못했다.
- [제안] 월드 지역마다 고정 위험도를 두면 "다시 와서 강해진 나를 확인"하는 보상이 생긴다. 스케일링을 쓰려면 성장 체감 방식을 별도로 설계한다.

### 9.2 스킬 트리
- 리스펙: 가능하되 비용이 있어야 한다. 비용이 높으면 불안, 너무 싸면 선택이 비인격적. 리스펙을 강요하는 콘텐츠로 긴장을 강점으로 바꿀 수 있다는 의견. 반대로 리스펙이 자유로우면 영구성이 없어진다는 비판도 있다. (C)
- 노드 대부분이 작은 수치 증가면 생각 없이 클릭한다. 새 선택지를 열거나 체감되는 수치를 바꿔야 한다. 메카닉 기반 업그레이드가 퍼센트 보너스보다 낫다. 위쳐 3 전투 트리는 기본 공격에 머무르게 되는 사례로 지적. (C)
- 트리 형태: 선형 = 따라가기 쉬움, 분기 = 전문화, 그리드(Path of Exile) = 거대한 창의성이지만 압도적. 키스톤(keystone)이 기이한 빌드를 허용. 스카이림은 최소 기능에 가깝다는 의견. 중형 게임에 15~40 노드가 적당하다는 경험칙. (C)
- 스카이림 퍽, 엘든 링 빌드 구조는 확인하지 못함.

### 9.3 루팅과 보상 심리
- 가변 비율 강화 스케줄은 반응률이 높지만 비디오게임에서는 선호되지 않을 수도 있다는 실험 연구(프린스턴 보고서, MIT 논문). (A)
- 현대 게임은 여러 가변 비율 루프를 겹친다 (루크 클라크, PC Gamer). (B)
- 희귀도 색상 등급이 지각된 가치를 만든다. 블리자드 디자이너가 "사실상 슬롯머신"을 만들었다고 인정했다는 2차 인용(주의). (C)
- 균형: 좋은 전리품이 너무 쉬우면 무의미해지고 너무 어려우면 좌절. 블리자드가 텔레메트리로 가정과 실제를 점검. 디아블로 3 현금 경매장이 루팅 동기를 해쳤다는 주장 (AI 스킬 문서 출처, 주의). (B/C)
- 로타 박스 규제 논의와 연결되므로 가변 보상 설계는 윤리·법적 이슈를 함께 점검해야 한다. (B)
- 디아블로 접두사·드롭 테이블 세부는 확인하지 못함.

### 9.4 진행감 설계 [제안]
- 매 구간 "이전에는 못 하던 것을 이제 할 수 있다"는 능력 해금(젤다 문서의 아이템 게이팅·이동기)과 수치 성장을 함께 쓴다.

---

## 10. 경제 설계 (일반론 중심)

- 파우셋(faucet)과 싱크(sink): 파우셋이 많으면 인플레이션, 싱크가 많으면 좌절. 제작·내구도는 서바이벌에서 자연스러운 싱크. (C)
- 하드 싱크(화폐가 사라짐: 소모품, 수리비, 제작 재료, 빠른 이동 비용, 리스펙) vs 소프트 싱크(속도만 늦춤). (C)
- 열망형 싱크가 가장 효과적이고, 세금 같은 수리비는 반감을 부른다. (C)
- 화폐가 제작 재료도 겸하게 하는 Path of Exile 방식. (C)
- 실제 돈이나 지름길로 힘을 살 수 있으면 힘을 찾는 의미가 사라진다. (C)
- 화폐 풀마다 stock-flow 모델을 만들어 감이 아니라 모델링으로 설계하라는 조언. (C)
- 모든 항목이 블로그/AI 스킬 문서이므로 **검증이 필요**하다. 싱글 플레이어 RPG 경제의 사례 분석(위쳐 3, 스카이림)은 확인하지 못했다.

---

## 11. UI, 내비게이션, 온보딩, 접근성

### 11.1 지도와 나침반
- 나침반 2단계: 추적 중인 퀘스트 마커와 플레이어 웨이포인트는 항상 표시, NPC·자원·일반 요소는 반경 안에서만. (C, 미들웨어 문서)
- 안개 낀 지도는 런타임에 갱신되는 렌더 타깃으로 저장, 발견 반경은 타이머로 확장. (C)
- 길드 워 도구: 활성 퀘스트만 보이는 기본값에 더해 모든 퀘스트 목표 핀 표시와 사용자 웨이포인트 옵션. (C)
- 마커 과다는 지루함, 과소는 막다른 길 좌절이라는 균형 (할로우 나이트 분석, 젤다류 문서). (B)
- [제안] 마커 밀도를 설정 옵션(탐험 모드/가이드 모드)으로 제공해 자율성을 보장한다.

### 11.2 온보딩
- 고스트 오브 요테이 GDC 발표 "Meaningful Reasons to Wander": 탐험이 왜 중요한지, 게임이 월드를 어떻게 전달하는지, 초반 페이싱이 이후 기대를 어떻게 정하는지. 구현 세부는 요약에 없다. (B)
- 챌머스 석사 논문(2021): 서사 중심 게임 온보딩은 숙달감, 목적감, 몰입감을 줘야 이탈을 줄인다 (초록만 확인). (A)
- 길고 지루한 온보딩도 나쁘다 (UX Collective). (B)
- 구체적 이탈률 수치는 출처가 없어 사용하지 않는다.
- 플로 채널·난이도 곡선 이론은 이번에 확인하지 못했다.

### 11.3 접근성
- 라스트 오브 어스 파트 2: 접근성 옵션 약 60개. 2017년부터 조사, 접근성 옹호자와 협업, 포커스 테스트. 동기는 퀵타임 이벤트 때문에 언차티드 2를 못 끝낸 플레이어의 편지. 청각·시각·운동 프리셋, 완전 키 리매핑, 고대비 모드, 터치패드 확대, 전투 튜닝. (A)
- **처음부터 계획했기에 가능했다**는 발언. (A)
- 오픈월드 RPG 난이도·접근성 상호작용은 확인하지 못함.

---

## 12. 사운드와 음악

- RDR2: 음악을 스템으로 쪼개 층층이 쌓거나 전환하는 "살아 있는 스코어". "건파이트 컨덕터"라는 AI 시스템이 전환을 구동 (GTA V에서 도입, RDR2에서 개편). 일반 플레이에서는 전체 제작 음악의 약 3분의 1만 듣게 된다 (파블로비치, 음악·오디오 디렉터). (A/B)
- 위쳐 3: 광대한 월드를 채울 앰비언스 콘텐츠와 반복을 피하는 변주를 확보하려 했다 (Wwise 사례 연구). 음악 시스템 세부는 확인 못 함. (A)
- 학술 논문(2025): 동적 음악과 적응형 오디오가 플레이어와 월드를 잇는 다리라고 주장. (A)
- BotW: 오픈월드에서 BGM을 줄여 환경음이 들리게 한 선택(젤다 문서 참고).
- GDC 오디오 발표 원문은 확인하지 못함.

---

## 13. 기술

### 13.1 대형 월드 스트리밍
- 언리얼 월드 파티션: 월드를 하나의 지속 레벨로 두고 그리드 셀로 나눠 스트리밍 소스 거리에 따라 로드/언로드. 오픈 월드 템플릿에서 HLOD 기본 활성, One File Per Actor, Data Layers 지원. (A, 공식 문서)
- HLOD는 월드 파티션이 큰 섬/월드를 지원하는 두 축 중 하나(스트리밍과 함께). (A)
- 나나이트 콘텐츠의 HLOD는 메시 단순화보다 인스턴스 병합에 집중해야 한다는 서드파티 주장 (공식 문서 미확인). (C)
- 지형 규모: 오래된 UE 4.8 시절 GDC 데모(1m 해상도 약 16,000×16,000 버텍스, 4×4 스트리밍 레벨). 약 20km를 넘으면 부동소수점 정밀도 문제. (C, 역사적 자료)
- 나나이트 한계, 월드 파티션 셀 로딩 동작, 트래버설 스터터(셰이더 컴파일/스트리밍)는 확인하지 못함.

### 13.2 절차적 배치
- 4.6 참조 (호라이즌 제로 던 GPU 기반 런타임 배치).
- 가이드: 절차적 생성 + 아티스트 편집 가능한 파이프라인. (B)

### 13.3 엔진 선택 (일반 비교, 모두 C)
- 언리얼: 월드 파티션, 레벨 스트리밍, 시퀀서, 애니메이션 도구가 AAA 수준. 단점: 무거운 빌드, 높은 하드웨어 요구, 소규모 팀에는 학습 곡선·복잡성이 생산성을 깎을 수 있음.
- 유니티: 1~5인 상업용 2D/모바일에 추천 사례, 3D는 HDRP 튜닝 필요. 오픈월드 특화 정보는 없음.
- 고도: 무료·단순, 3D는 최적화에 손이 더 간다. 카세트 비스트(오픈월드 RPG 사례).
- 엔진 선택 결정에 쓸 만한 검증된 사례/벤치마크는 확인하지 못했다.

### 13.4 [제안]
- 엔진은 기능 목록보다 **팀의 숙련도와 빌드·이터레이션 속도**로 고른다. 오픈월드에서는 스트리밍 프로토타입을 초기에 만들어 병목을 측정한다.

---

## 14. 제작·프로젝트 관리

### 14.1 확인된 규모
| 프로젝트 | 확인된 내용 | 출처 신뢰도 |
|---|---|---|
| 위쳐 3 | 제작비+마케팅 합계 3.06억 즈워티(약 8,100만 달러), 개발 3.5년, CDPR 직원 240명, 외부 협력자 포함 1,500명 이상 (2015년 CDPR 발표) | A |
| RDR2 | 약 1,600~2,000명, 비공식 추정 1.7~2.4억 달러, 일정·예산 초과, 일부 "주 100시간" 근무 | B |
| 엘든 링 | 프롬소프트웨어가 엘든 링과 아머드 코어 6를 약 300명으로 제작(사람을 프로젝트 간 이동). 2017년 발표~2022년 2월 출시 약 5년(2차 출처). 예산은 모두 추정이며 신뢰 불가 | B/C |
| 사이버펑크 2077 | 3.3 참고 | A/B |

### 14.2 엘든 링: 위임과 규모 확장
- 미야자키: 게임 규모가 커진 것은 일부 인력 합류 때문이고 위임이 평소보다 많았다. 위임할 때 자신의 "논리, 철학, 사고 과정"을 더 충분히 공유하려 했다. (A)
- 원래 훨씬 작은 규모로 계획됐다는 기사가 있음. (B)

### 14.3 수직 슬라이스와 스코프
- 수직 슬라이스는 최종 게임의 부분집합을 플레이 가능하게 하는 마일스톤 (Unity Learn). (A)
- 슬라이스는 데모가 아니라 **파이프라인 측정 도구**: 한 레벨 제작 시간을 알면 현실적 스코프를 계산 가능 (Codecks). (B)
- 폴리싱된 슬라이스가 풀 게임 조립 시 미해결 버그·파이프라인 문제를 가릴 수 있다는 경고 (출처 불확실한 블로그). (C)
- 스코프 사례: Zeboyd의 Breath of Death VII 사후 분석 — 5시간 분량, 레트로 비주얼, 복잡하지 않은 게임플레이로 계획해 3개월 안에 완성. (A)
- 스타듀 밸리: 핵심 농사 루프를 먼저 중독적으로 다듬고 나서 낚시, 채굴, 관계를 추가했다는 사례. (C)
- GTA 5조차 시간·예산 때문에 기능을 뺐으므로 컷은 정상. (C)

### 14.4 사이버펑크 2077 실패 요인
- CDPR 공동 창립자 마르친 이빈스키: PC에 집중하고 콘솔 버전은 이후 조정했으며 구세대 콘솔이 초기 대상 하드웨어라고 판단했다. (A)
- 공동 CEO 아담 키친스키: 문제의 규모와 복잡도를 과소평가했고, 구세대 기본 콘솔에서 다듬을 추가 시간이 필요하다는 신호를 무시했다. 캠페인 중 게임이 주로 PC에서 시연됐다. (A)
- 범위가 크고 커스텀 오브젝트·상호작용 시스템·메카닉이 많았으며 PC 우선 후 구세대로 축소하는 방식이 어려움을 키웠다. (A)
- 애니메이션, 군중, 운전 AI에 검증된 서드파티 대신 커스텀 시스템을 만들었다는 외부 분석. (B)
- 2020년 말 출시 압박. 블룸버그: 콘솔 성능 문제로 창립자들이 약 10억 달러를 잃었고, 소니·MS가 환불 정책에 예외. (B)
- [제안] **최저 사양 플랫폼에서 일찍, 자주 돌려 본다.** 시연 빌드와 실제 타깃의 차이를 숨기지 않는다.

### 14.5 [제안] 제작 원칙
1. 스코프 결정 기준: 가장 얇은 슬라이스(탐험→전투→퀘스트→성장)를 먼저 수치로 측정한 뒤 월드 크기를 정한다.
2. 퀘스트·월드 콘텐츠는 "채택률 5~10%" 같은 폐기 비율을 제작비에 반영한다.
3. 규모를 위임할 때는 설계 원칙 문서를 함께 공유한다 (미야자키 사례).
4. 크런치에 대한 보도(RDR2)를 전제로 일정 버퍼를 설계한다.

---

## 15. 출시 후와 커뮤니티

### 15.1 모드
- 스카이림: 넥서스 모드에서 60억 건 이상 다운로드(BG3 모드 관리자 도입 전), 베데스다 크리에이션 키트가 모더를 지원. 일부 모드는 수십 시간 분량의 새 퀘스트라인을 추가한다는 주장. (C)
- 스카이림이 지금도 인기인 이유가 모드라는 의견. (C)
- 플레이 시간과의 정량 관계는 확인하지 못했다.
- 라리안은 BG3에서 모딩이 여러 버전을 낳으리라 예상했다. (A)
- [제안] 데이터 중심 설계(퀘스트·아이템·NPC를 데이터 파일로 정의)와 에디터 공개는 초기 아키텍처 결정이다.

### 15.2 노 맨즈 스카이
- 출시 때 약속된 기능이 빠져 혹평 → 2년 동안 대형 무료 업데이트 → 2018 NEXT 업데이트(멀티플레이, 3인칭 등)가 전환점. 출시 전부터 지속 업데이트를 말했고, 소규모 팀이라 지속 개발이 가능했다. 숀 머레이는 플레이어가 있기에 업데이트를 한다고 언급. 10년 시점에도 지원 중. (B)
- 교훈: 약속 관리(B). 스팀 80% 긍정까지 회복했다는 기사가 있음(C).

### 15.3 얼리 액세스
- BG3: 얼리 액세스 데이터와 피드백으로 캐릭터와 분기를 조정 (6.1).
- 얼리 액세스 일반론(수익, 위험)은 이번에 조사하지 않았다.

---

## 16. 실패 사례 종합

| 사례 | 실패 요인 | 교훈 |
|---|---|---|
| 사이버펑크 2077 | 범위 과다, 저사양 플랫폼 검증 부족, 출시 압박 | 14.4 |
| 스타필드 | 콘텐츠 복제, 로딩 의존, 의미 부족한 POI | 4.4 |
| 유비소프트식 공식 | 반복, 체크리스트, 마커 과다 | 4.3 |
| 오블리비언 | 레벨 스케일링으로 성장감 상실 | 9.1 |
| 오블리비언 라디언트 AI | 창발 통제 실패 | 7.3 |
| 물의 신전·피(Fi) 등 | 마찰 | 젤다 문서 |
| 노 맨즈 스카이(출시) | 약속 불이행 | 15.2 |
| 대형 오픈월드 전반 | "대부분 콘텐츠를 수행할 이유가 부족" | 1.3 |

---

## 17. [제안] 수백 시간 오픈월드 RPG의 필수 요소 체크리스트

> 조사에서 도출한 제안. 각 항목 옆에 근거 위치를 적었다.

### 17.1 동기/루프
- [ ] 자율성·유능감·관계성 세 욕구를 시간대별로 만족하는가 (2장)
- [ ] 1시간/10시간/50시간/200시간 이탈 방지 장치가 있는가 (3.2)
- [ ] 핵심 루프가 메타 루프와 연결되는가 (3.1)

### 17.2 월드
- [ ] 이동이 월드 체감 크기를 만든다 (지형·이동기) (4.1)
- [ ] 규모보다 밀도: 복제 콘텐츠로 크기를 늘리지 않는다 (4.4)
- [ ] 마커 없이도 호기심으로 이동할 수 있다 (젤다 문서, 11.1)
- [ ] 핵심 지점(보스·도시)을 먼저 놓고 지형을 맞춘다 (4.5)
- [ ] 레거시 던전급의 "손으로 만든 정수" 구역을 정한다 (4.5)

### 17.3 퀘스트/서사/관계
- [ ] 퀘스트마다 서로 다른 감정·장소·메카닉 (5.3)
- [ ] 수집·배달 퀘스트 최소화 (5.1)
- [ ] 플레이어가 이야기를 "원하게" 만드는 정보 설계 (5.1)
- [ ] 선택의 결과가 짧은 시간 안에 눈에 보인다 (6.3)
- [ ] 동료는 서사와 기능 모두에서 쓸모가 있다 (6.2)

### 17.4 시스템/전투/성장
- [ ] 창발 시스템은 통제 가능한 범위에서 시작 (7.4)
- [ ] 성장이 체감되고 스케일링이 성장감을 깎지 않는다 (9.1)
- [ ] 스킬 트리 노드가 새 선택지를 연다 (9.2)
- [ ] 보상 심리를 쓰되 윤리·규제 문제를 점검 (9.3)
- [ ] 경제 stock-flow 모델이 있다 (10)

### 17.5 UX/접근성
- [ ] 마커 밀도 옵션 (11.1)
- [ ] 접근성 옵션을 초기부터 계획 (11.3)
- [ ] 온보딩이 숙달감·목적감·몰입감을 준다 (11.2)

### 17.6 기술/제작
- [ ] 스트리밍 프로토타입으로 병목을 일찍 측정 (13.4)
- [ ] 최저 사양 플랫폼에서 일찍·자주 실행 (14.4)
- [ ] 수직 슬라이스를 파이프라인 측정 도구로 쓰고, 그 수치로 스코프를 정한다 (14.3)
- [ ] 퀘스트 폐기율을 제작비에 반영 (5.1)
- [ ] 데이터 중심 설계와 에디터 공개를 초기 아키텍처에 포함 (15.1)

### 17.7 출시 후
- [ ] 출시 전 약속 관리 (15.2)
- [ ] 지속 업데이트 계획과 팀 규모의 정합성 (15.2)

---

## 18. 확인하지 못한 영역과 추가 조사 계획

### 18.1 미조사/불충분
1. 전투 설계: 《Game Feel》, GDC 전투 발표, 개별 게임 인터뷰 (8장)
2. 캐릭터 성장: 스카이림 퍽, 엘든 링 스탯, 위쳐 3 난이도 비교 (9장)
3. 경제: 싱글 플레이 RPG 사례, 위쳐 3·스카이림 (10장)
4. 월드 설계 정량 데이터: 개별 게임의 POI 간격, 밀도 (4.2)
5. 기술: 나나이트 한계, 월드 파티션 셀 로딩, 스터터 원인, 이동 속도와 스트리밍 설계 (13장)
6. 서사: 위쳐 3·사이버펑크 10가지 교훈 전체, 서사 구조(분기), 대화 시스템
7. 사운드: GDC 오디오 발표 원문 (12장)
8. 유저 이탈·리텐션 데이터: 스팀 업적 통계, HowLongToBeat 통계
9. 얼리 액세스 일반론, 가격/수익 모델, 마케팅
10. 현지화, 성우 캐스팅, 모션 캡처 파이프라인, QA 규모
11. 법적·윤리: 확률형 아이템 규제, 연령 등급
12. 기타 참고 게임: 호라이즌, 킹덤 컴, 디스코 엘리시움, 아웃터 와일즈, 발헤임, 다크 소울 시리즈
13. 개발 일정/인력 모델: 스튜디오별 구성 비율(디자이너/프로그래머/아티스트)

### 18.2 원문 확인이 필요한 1차 자료
- GDC Vault: 사스코 위쳐 3·사이버펑크 퀘스트 발표(1028897), 호라이즌 GPU 배치(1024120)
- Game Developer: 사이버펑크·위쳐 3 퀘스트 10가지 교훈, 오픈월드 레벨 디자인 시리즈
- 토드 하워드 Gamasutra 인터뷰, 사르와르 Official Xbox Magazine 인터뷰
- 미야자키 인터뷰(PlayStation Blog, Xbox Wire)
- Quantic Foundry 방법론 페이지, SDT 논문(Ryan·Rigby·Przybylski 2006)

접속 제한이 풀리면 위 순서로 직접 읽고 문서를 보강한다.

---

## 19. 출처

**동기·루프**
- [SDT: PENS](https://selfdeterminationtheory.org/player-experience-of-needs-satisfaction-pens/)
- [Rochester: Ryan et al. 2006](https://www.rochester.edu/warner/lida/wp-content/uploads/2022/11/02bfe513dd59366750000000.pdf)
- [Game Developer: Why do we really play](https://www.gamedeveloper.com/design/why-do-we-really-play-)
- [Quantic Foundry](https://quanticfoundry.com/)
- [Player Driven: Nick Yee](https://playerdriven.substack.com/p/quantic-foundrys-nick-yee-on-gamer)
- [Game Design Skills: core loops](https://gamedesignskills.com/game-design/core-loops-in-gameplay/)
- [Game Wisdom: focused gameplay loop](https://game-wisdom.com/critical/gameplay-loop)
- [Free to Play Bible: core loop](https://mobilefreetoplay.com/bible/crafting-strong-core-loop/)

**월드 설계**
- [Game Developer: Todd Howard on Skyrim](https://gamedeveloper.com/business/interview-todd-howard-on-the-scope-vision-of-i-skyrim-i-)
- [NME: Skyrim not deep enough](https://www.nme.com/news/skyrim-did-not-go-deep-enough-in-parts-says-todd-howard-3091226)
- [Game Developer: Open World Level Design series](https://www.gamedeveloper.com/design/open-world-level-design-the-full-vision-part-5-5-)
- [Strayspark: open world pacing](https://www.strayspark.studio/blog/open-world-design-pacing-player-freedom)
- [Medium: POIs Diversity Rule](https://medium.com/my-games-company/how-to-make-an-exciting-open-world-the-pois-diversity-rule-90de6d748eac)
- [Radiator: BotW spatial composition](https://www.blog.radiator.debacle.us/2017/10/open-world-level-design-spatial.html)
- [Design Dive: Viewpoints](https://40more.substack.com/p/design-dive-viewpoints)
- [Jboger: Towers](https://jboger.substack.com/p/towers)
- [PCWorld: Watch Dogs 2](https://www.pcworld.com/article/3146700/watch-dogs-2-review-a-fresh-interesting-rebirth-that-ditches-the-stale-ubisoft-formula.html)
- [Finger Guns: Ubisoft](https://fingerguns.net/games/2024/09/13/ubisofts-rise-and-fall-from-vibrant-open-worlds-to-hollow-shells/)
- [80.lv: Starfield planets](https://80.lv/articles/starfield-s-procedural-planets-are-empty-boring-by-design/)
- [KnowYourMeme: Starfield Steam](https://trending.knowyourmeme.com/news/bethesda-is-telling-its-critics-on-steam-that-starfield-is-not-boring-actually)
- [TechRadar: Miyazaki](https://www.techradar.com/news/elden-ring-director-reveals-his-favorite-boss-and-open-world-inspiration)
- [PlayStation Blog: Miyazaki](https://blog.playstation.com/2022/01/28/an-interview-with-fromsoftwares-hidetaka-miyazki/)
- [Medium: Elden Ring legacy dungeons](https://joncheetham.medium.com/elden-rings-six-legacy-dungeons-ranked-e45ab3ae6830)
- [A Banana Peeled: Elden Ring level design](https://abananapeeled.com/fun/elden-ring-and-elegant-level-design)
- [80.lv: Horizon procedural placement](https://80.lv/articles/real-time-procedural-placement-in-horizon-zero-dawn)
- [GDC Vault: GPU-based procedural placement](https://www.gdcvault.com/play/1024120/GPU-Based-Run-Time-Procedural)

**퀘스트·서사·동료**
- [GDC Vault: 10 Key Quest Design Lessons](https://gdcvault.com/play/1028897/10-Key-Quest-Design-Lessons)
- [Game Developer: 10 key takeaways](https://www.gamedeveloper.com/marketing/10-key-takeaways-from-the-quest-design-of-cyberpunk-2077-and-the-witcher-3)
- [GameBanshee: Quest design lessons](https://www.gamebanshee.com/news/127453-the-witcher-3-wild-hunt-and-cyberpunk-2077-key-quest-design-lessons.html)
- [Game Rant: CDPR quest design](https://gamerant.com/cd-projekt-red-witcher-cyberpunk-2077-quest-design-how/)
- [Game Rant: quests empathy](https://gamerant.com/witcher-3-cyberpunk-2077-quests-empathy/)
- [Shacknews: Witcher 3 quest designers](https://www.shacknews.com/article/94509/witcher-3-quest-designers-talk-design-process-most-difficult-quest-to-create)
- [Vulkk: Witcher 3 Q&A](https://vulkk.com/2016/05/07/witcher-3-qa-cdprs-quest-designers/)
- [GamePro: Dragon Age fetch quests](https://www.gamepro.de/artikel/the-witcher-3-wild-hunt-quest-designer-dragon-age-3-ist-gut-hat-aber-zu-viele-sammelquests,3082625.html)
- [GameBanshee: Swen Vincke](https://www.gamebanshee.com/3hrxw)
- [GaymingMag: BG3 feedback](https://gaymingmag.com/2023/08/how-community-feedback-has-shaped-baldurs-gate-3/)
- [FinalBoss: BG3 romance](https://finalboss.io/baldur-s-gate-3-shows-romance-must-change-the-story)
- [Game Developer: Companions](https://www.gamedeveloper.com/design/companions-creating-player-bonds)
- [Mindtrek 2018 paper](https://www.medien.informatik.uni-muenchen.de/pubdb/publications/pub/bouquet2018mindtrek/bouquet2018mindtrek.pdf)

**시스템·AI·창발**
- [Giant Bomb: Immersive Sim](https://giantbomb.com/wiki/Concepts/Immersive_Sim)
- [80.lv: Five pillars of immersive sims](https://80.lv/articles/five-pillars-of-immersive-sims)
- [PC Gamer: Dishonored](https://www.pcgamer.com/uk/saying-one-last-goodbye-to-dishonored)
- [TweakTown: RDR2 NPC system](https://www.tweaktown.com/news/63303/red-dead-redemption-2-npc-system-explained-rockstar-devs/index.html)
- [Wikipedia: Development of RDR2](https://en.wikipedia.org/wiki/Development_of_Red_Dead_Redemption_2)
- [Destructoid: RDR2 100-hour weeks](https://destructoid.com/?p=230544)
- [Guinness: largest dev team](https://www.guinnessworldrecords.com/world-records/557449-largest-development-team-for-a-videogame)
- [Giant Bomb: Radiant AI](https://giantbomb.com/wiki/Concepts/Radiant_A_I)
- [Oblivion interview (GameBanshee)](https://gamebanshee.com/k68pc)
- [Zhao et al.: Behavior Architecture](https://cspages.ucalgary.ca/~richard.zhao1/publications/2014fdg-Behavior-Architecture.pdf)

**성장·보상·경제**
- [Retromo: Oblivion](https://retromo.substack.com/p/elder-scrolls-iv-oblivion-pc-2006)
- [RPGCodex: Oblivion](https://rpgcodex.net/article.php?id=4312)
- [GDKeys: skill trees](https://gdkeys.com/keys-to-meaningful-skill-trees/)
- [Design Dive 20](https://designdive.substack.com/p/design-dive-20)
- [Game Informer: science of loot](https://gameinformer.com/b/features/archive/2015/10/23/the-science-behind-why-we-love-loot)
- [Princeton report](https://www.cs.princeton.edu/techreports/2012/931.pdf)
- [MIT paper](https://people.csail.mit.edu/dkao/pdf/kao2012rewardpreference.pdf)
- [PC Gamer: loot box psychology](https://www.pcgamer.com/uk/behind-the-addictive-psychology-and-seductive-art-of-loot-boxes/)
- [Medium: game economies](https://medium.com/@msahinn21/designing-game-economies-inflation-resource-management-and-balance-fa1e6c894670)
- [Gold sinks](https://gamedepth.onrender.com/posts/gold-sinks-why-most-mmorpgs-dont-remove-enough-currency)

**전투·UX·접근성·사운드**
- [Wayline: input buffering](https://www.wayline.io/blog/input-buffering-responsive-game-feel)
- [Gamesbyhyper: Map System](https://gamesbyhyper.com/docs/exploration-and-narrative/map-system/)
- [GWToolbox: World map](https://www.gwtoolbox.com/docs/world_map/)
- [GameDev.net: Ghost of Yotei first hour](https://gamedev.net/news/5594-gathering-first-hour-needs-for-ghost-of-yotei/)
- [Chalmers: onboarding thesis](https://odr.chalmers.se/items/208425d7-7e28-4386-88a7-56edbd4ab554)
- [UX Collective: games onboarding](https://uxdesign.cc/games-ux-building-the-right-onboarding-experience-a6e99cf4aaea)
- [CanIPlayThat: TLOU2 accessibility](https://caniplaythat.com/2020/06/01/the-last-of-us-part-2-accessibility-interview-the-verge/)
- [PlayStation Blog: TLOU2 accessibility](https://blog.playstation.com/2020/06/09/the-last-of-us-part-ii-accessibility-features-detailed)
- [Wikipedia: Music of RDR2](https://en.wikipedia.org/wiki/Music_of_Red_Dead_Redemption_2)
- [Audiokinetic: Witcher 3 audio](https://www.audiokinetic.com/en/blog/the-witcher-3-wild-hunt-game-audio-wwise-tour)
- [Linguistic Frontiers: open world sound](https://journals.upol.cz/lingfrontiers/article/view/647)

**기술·제작·출시 후**
- [Unreal: World Partition](https://dev.epicgames.com/documentation/en-us/unreal-engine/world-partition-in-unreal-engine)
- [Unreal: Streaming and HLODs in UEFN](https://dev.epicgames.com/documentation/en-us/fortnite/streaming-and-hlods-in-unreal-editor-for-fortnite)
- [Strayspark: Godot vs Unity vs Unreal](https://www.strayspark.studio/blog/godot-vs-unity-vs-unreal-2026)
- [Dev.to: engines for indies](https://dev.to/oceanviewgames/unity-vs-godot-vs-unreal-for-indie-developers-2026-which-engine-wins-lal)
- [PC Gamer: Witcher 3 cost](https://www.pcgamer.com/uk/the-witcher-3-wild-hunt-cost-81-million-to-make)
- [MCV: Witcher 3 1,500 devs](https://www.mcvuk.com/development/cd-projekt-spent-53m-developing-the-witcher-3)
- [CD Projekt: Witcher 3 summary](https://www.cdprojekt.com/en/media/news/the-cd-projekt-group-summarizes-the-release-of-the-witcher-3/)
- [MP1st: FromSoftware 300 staff](https://mp1st.com/?p=230137)
- [GGRecon: Elden Ring originally smaller](https://www.ggrecon.com/articles/elden-ring-was-originally-going-to-be-much-smaller)
- [Game Informer: Cyberpunk what went wrong](https://www.gameinformer.com/2021/01/13/cd-projekt-red-co-founder-explains-what-went-wrong-with-cyberpunk-2077)
- [MCV: Iwinski apology](https://www.mcvuk.com/development-news/cd-projekt-reds-iwinski-apologises-and-gives-limited-insight-into-cyberpunk-2077-launch-issues/)
- [PC Gamer: CDPR bad week](https://www.pcgamer.com/au/cd-projekts-very-bad-week-a-breakdown)
- [Unity Learn: production](https://learn.unity.com/course/game-development-in-a-nutshell/tutorial/production-and-post-release)
- [Codecks: pre-production](https://www.codecks.io/blog/2026/how-to-set-your-game-up-for-success-pre-production--forecasting)
- [Game Developer: Breath of Death VII postmortem](https://www.gamedeveloper.com/business/breath-of-death-vii-the-beginning-a-post-mortem)
- [Inverse: No Man's Sky 7th anniversary](https://www.inverse.com/gaming/no-mans-sky-7th-anniversary)
- [NicheGamer: Sean Murray](https://nichegamer.com/sean-murray-says-players-keep-no-mans-sky-updates-alive/)
- [EIP: Do people still play Skyrim](https://eip.gg/skyrim/news/do-people-still-play-skyrim/)
- [Gfinity: BG3 mods](https://www.gfinityesports.com/article/1-billion-mod-downloads-later-baldurs-gate-3-is-starting-to-look-like-skyrims-successor)
- [Game Rant: 100+ hour RPGs](https://gamerant.com/rpgs-that-last-over-100-hours/)
- [Post Physical: open vs closed world](https://www.postphysical.io/blog/world-structure-an-open-or-closed-space-conundrum)
- [ResetEra: open world replayability](https://www.resetera.com/threads/open-world-games-and-replayability-like-oil-and-water.17591/)
