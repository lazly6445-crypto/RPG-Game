# 작업 루프 큐 (부모 세션 자체 점검용)

운영 규칙: 자식 세션 1개씩 순차 실행(같은 폴더 충돌 방지). 완료 확인은 `Bash sleep 1500` 백그라운드로 깨어남(예약 알림 trigger는 ACCESS_DENIED로 실패하므로 사용 금지). 완료 시: 보고서 읽기 → dev-backlog-p0.md·dev-review-queue.md 기록 → push → 세션 보관 → 다음 세션 시작. 환경은 `env_01Q4ett3G2vUfZ13ovD9yNC9 (2026-11-11 새 브리지; 이전 env_01Djsxj... 도 삭제됨; 이전 env_01X9PQ75... 는 삭제됨, 브리지를 다시 시작할 때마다 list_environments로 새 id 확인)`(PC 브리지). 자식 프롬프트에 AskUserQuestion 금지, 경로 지정 커밋, 푸시 금지 명시.

## 진행 중
- B41 여진(리셋) 시스템(재개; 이전 세션 상태 복구 불가, 작업 트리의 미커밋 변경을 이어받음) — session_0148ScBAygQTn2YsoTkjWawf
- (완료: B47 f01ab10, 아트 임포트 3e3e891, B46 b002155, B30d2 011e2d4, B42a 1bee406, B42b 8173021, 화풍 시안 687c8db)

- 아트 자동화 시험(PixelLab MCP 연결 + 검수 스크립트, 걷기 A/B) — session_0148ScBAN6kSkKvqsGiJrSi3 (크레딧 상한 8 generations)

## 대기 (순서)
0. (완료) B47 렌더 규격 전환(결정 190)**: 타일 64×32·내부 1280×720·높이 단 16px, HUD/UI/글자/줌/카메라/마우스 변환/성능 재측정 (B46 완료 직후, 충돌 방지 위해 B34 앞). 이어서 C10(레이어 이름 정렬) 확인, B48 건물 가림(결정 191: 입장=페이드·실내 탐험=완전 제거).
1. B42b 맵별 기믹 15~20개 대량 배치(B42a 틀 위). (B42a 후속) / 원 B42 지형 기믹·숨은 상자 (결정 179~181; 지상 맵당 15~20개, 환경 단서만, 숨은 상자=한 단계 높은 등급+스킬북 확률↑). **B39 기믹 퀘스트 5개 실제 연결 필수**: 엔진음(높이차+가연 장애물)·불나비 불빛(물 소화 장치)·식히는 일(얼음 다리)·가시뿌리 곁의 약초(가연+바람)·녹슨 문(전도 퍼즐). `game.quest_flag("<id>")`, `quests.json flags`.
2. (완료) B34 사망 더스트 손실(515e6e6); 허기는 시스템 없음 → 미구현
3. (진행) B41 여진 시스템 (결정 157·158·164)
4. B35 지역 보스 — 시가지 2명 먼저 (결정 178)
5. B30d3 고유 효과 36종 + 방어구·장신구 슬롯 고유 풀 신설(결정 183) 설계·전투 적용
6. B36 난이도 재설계 (결정 172)
7. 이후: 보스 나머지 4명, 경계지·요정숲 확장, 지도 연동 등

## 사용자 확인 대기(루프 비차단)
review-queue 전체, skills-draft.md, 가정값 튜닝, 프로젝트 게이트(화풍·scope cut·일정·제목·예산)

## 병행 트랙
- 화풍 실험(결정 185): 도트 스타일 3안 시안, 별도 폴더 D:\gate-style-lab — 게임 코드 미접촉

## 아트 트랙 (결정 187, 사용자 최우선 가치)
1. B46 스프라이트 애니메이션 시스템: 프레임 수 제한 없는 데이터 기반 애니메이션(방향×동작×프레임, 프레임별 지속 시간, ACT식 레이어: 몸/장비/무기/이펙트 분리, 5방향+반전 또는 8방향), 아트 교체 시 코드 수정 없는 임포트 규약 + 현재 도형 플레이스홀더를 같은 규약 위로 이전. (코드 루프 안에서 진행 가능)
2. [art-bible §6 단계 1 사용자 대기] 아트 파이프라인 시험: 캐릭터 1개 × 8방향 × 걷기 8+프레임·공격 6+프레임 실제 시험 제작(방식 3종: 직접 도트 / Spine·본 / 3D→도트) 비교 — 제작 주체 결정 필요.
3. 화풍 확정(사용자): 시안 3안 검토 + 실제 시험 결과 후.

## 아트 도구 시험 (사용자 진행, 결정 보류)
- ai-art-test-plan.md 기준으로 PixelLab → SpriteCook → Scenario → Spritesheets.ai 순 시험 후 도구 결정. 결과 이미지는 `D:\gate-art-input\test_<도구>\`.

## 상태 메모 (2026-11-07)
- 사용자 PC 재부팅 → 브리지(Remote Control) 재시작 필요: `cd D:\gate-godot; & "C:\Users\User\.local\bin\claude.exe" remote-control`. 재연결 후 B41(session_0148ScBAoWj7wNiquxG5hp5e, 5시간 한도 + PC 종료로 중단, `aftershock.gd` 미추적 파일 존재) 재개: send_message로 이어서 진행.
- PixelLab 잔액 7 generations. 다음 아트: 걷기 W·NW 재생성(2), correct_pixelart 시험(소액), idle 발 기준선 보정(임포트 도구), 몬스터(들개) 시험.

## 아트 품질 우선 작업 (결정 196)
1. 검수 스크립트 강화: 얼굴 세부(눈·볼) 색 변화, 발 접지 타이밍, 후보 비교 선택 시트 자동 생성.
2. 임포트 옵션: Aseprite 보정용 레이어/프레임 내보내기.
3. PixelLab 결제 후: MCP 키 재등록 확인 → 걷기 W·NW 재생성, 색 번짐 후처리, 들개(몬스터) 1종 8방향 풀 품질 파이프라인 실측 → 견적 재계산 → 플랜(Tier 2 유지/상향) 결정.

- PixelLab Tier 2 결제 완료(2026-11-07). 노출된 키 재발급 여부에 따라 MCP 키 재등록 필요.

- PixelLab 동시 생성 상한 10건(확인). 잔액 4968.8(Art 4 후). 다음 아트: 자동 보정(Art 5) → 들개 몬스터 8방향 풀 파이프라인 실측.

- 사용자 확인 대기: 고프레임 걷기 GIF 비교(`D:\gate-shots\art\art6\walk_*_16fps.gif`) → 방식 선택(pixminimax 16f 추천) 후 8방향 확장. ARCHITECTURE §32 절 번호 중복(Art 5·Art 6) 정리 필요.

## 상태 메모 (2026-11-11)
- Art 7·Art 8 완료 기록. B41은 한도+PC 끊김으로 미완(미커밋 변경이 작업 트리에 있음) → 브리지 재연결 후 새 세션으로 이어받기(list_environments로 새 env id 확인).
- 사용자 선택 대기: 몬스터 후보(들개/엘리트/대형 A·B·C, 대형=문지기 여부, 4족 64×64), 걷기 GIF 확인(art8).
- PixelLab 잔액 약 4868.8(11-07 기준), 초기화 12-07.

- 다음 아트 작업(PC 연결 후): Art 9 = 확정 몬스터 4종(들개 DOG-C·엘리트 BOSSDOG-A·곰 GATEKEEPER-C·문지기 GATEKEEPER-B) 8방향 풀 애니메이션(대기·이동·공격·피격·사망, 12~16프레임 기준, 상한 약 300 gen) + 시가지 대형 군집 몬스터 정의(곰) 데이터화.

## 수직 슬라이스(시가지 완성판) 계획 (결정 215, 6~9개월)
범위: 튜토리얼 + 시가지 + 시가지 던전(문지기). 완성 품질 체크리스트:
- 코드: B41 여진(재개), B51 포만감 버프(결정 206), B52 다국어 구조(결정 214), B35 시가지 보스 2명(결정 178), B30d3 고유 효과, B36 난이도, B32d 지형·규칙 스킬, B48 건물 가림(결정 191), 아이소 요정숲 성능 최적화(p99).
- 아트(PixelLab, 월 $50): 주인공 완성(걷기·idle·달리기·구르기·공격 3타·피격·사망·시전 12프레임+유형별 3), 시가지 몬스터 4종(들개·엘리트·곰·문지기) 8방향 풀 애니, 시가지 지형 타일·건물(반파)·오브젝트, 상인 3명(시가지), 아이템 아이콘 32/64, 스킬 이펙트 PixelLab VFX(결정 208), UI 종이·금속(결정 211), 음악·효과음(결정 212).
- 콘텐츠: 시가지 퀘스트·기믹(49개 중 시가지 16), 곽두식·봉순·철민, 곰 대형 군집(결정 213).
- 품질 게이트: 사용자 플레이테스트(로그 분석), 성능 ≤16.6ms, 검수.

- **Art 9a(PC 연결 후 최우선)**: 주인공 걷기·달리기 '통통 튀는' 모션 재생성(결정 218). 후보 3단계(약/중/강) × 걷기 16f·달리기 16f를 S·E 방향으로 먼저 생성 → 선택지 시트(결정 202) → 사용자 선택 후 8방향 확장. 프롬프트 초안(영문, 긍정문): 
  - 걷기: `bouncy cheerful chibi walk cycle, the whole body bobs up and down with a springy hop on every step, squash and stretch, body leaning slightly forward, head bouncing, arms swinging loosely, scarf and hair trailing behind and bouncing a beat later, feet landing clearly, lively and energetic`
  - 달리기: `energetic bouncy run cycle, body leaning forward, long springy strides with a brief airborne moment between steps, big up and down bounce, squash on landing and stretch on takeoff, arms pumping, scarf streaming behind, hair bouncing, lively`
  - 강도 변형: 약(`gentle bounce`), 중(`springy hop`), 강(`exaggerated bouncy hop with a clear airborne phase`).
  - 데이터 보강: 프레임별 `oy`(상하 오프셋 1~2px) 곡선, 프레임당 시간 40~50ms(걷기), 달리기 35~45ms.

- **B53 환경 연출(결정 219)**: 배경 서정·평화 효과 시스템 — 풀·나무·덩굴 흔들림(셰이더 또는 프레임), 물결, 떠다니는 입자(먼지·꽃가루·반딧불, 지역별 색: 시가지 베이지 먼지·경계지 청록 반짝임·요정숲 연두/보라 꽃가루), 구름 그림자, 빛줄기, 환경광(좌상단 따뜻한 햇빛), 아주 느린 움직임·낮은 대비. 성능 예산(아이소 요정숲 p99) 안에서. 설정에서 '환경 효과' 강도 옵션. 이 기준에서 어긋나는 현재 연출(거친 번쩍임·화면 흔들림 세기)도 점검.

- **Art 9(수정, 결정 220)**: 몬스터 체급 재정의 반영 — 들개 DOG-C 소형 64 유지, 엘리트 BOSSDOG-A는 중형(1.25~1.5배, 128 캔버스에서 재생성 또는 확대 후 정리), **곰 GATEKEEPER-C는 대형(약 3배, 192~256 캔버스)로 재생성**, **문지기 GATEKEEPER-B는 보스(4~5배, 256 이상)로 재생성**. 게임 코드: `monsters.json`·`boss.json` 크기·히트박스·점유 칸 확대, 카메라/정렬/가림 점검(코드 세션 필요).

## 진행 중 (2026-11-11, env_01Q4ett3G2vUfZ13ovD9yNC9)
- Art 9a 통통 튀는 걷기·달리기 후보(S·E, 상한 60, 선택지 시트 `D:\gate-shots\art\art9a\choose\`) — session_0148ScBB7LXcna3BDgghzfT2
- 사용자 대기: 몬스터 체급 반영 Art 9(곰 대형·문지기 보스 재생성) 시작 시점 결정, 걷기 GIF 확인(art8).
- B41 완료(여진). 다음 코드 작업: B51 포만감 버프(결정 206), B52 다국어 구조(결정 214), B35 시가지 보스 2명, 몬스터 체급 반영(결정 220).
- 진행: Art 9b(주인공 걷기 B·달리기 B 8방향), B51 포만감 버프 — (시작 후 id 기록)
- 완료: Art 9b(4169cef), 여진 흔들림 10초(912d54f). 진행: B51, Art 9c(결함 보정), Art 10(개 2종). B51 후 전체 스위트 5건 실패(test_game_state/loot_chest/shop/skills/gather) 재확인 필요.
- 완료: B51(2f89497, 음식 9종, 테스트 73/74·test_equipment iso 간헐 실패 원인 미확인), Art 9c(1514339, FAIL 80→46, 수작업 5건 남음). 진행: Art 10(개, 약 95gen 예상), B30d3(+test_equipment 간헐 실패 조사).
- 사용자 확인 대기: 음식 HUD 아이콘·수치 체감, art9c GIF/시트(`D:\gate-shots\art\art9c\`), Aseprite 수작업 5건(걷기 SW 눈 가림, 걷기 N·NW 스카프 꼬리, 달리기 N·NW 이음새, 걷기 NE·SE 접지, 재킷 빨간 패치).
- 완료: Art 10(ab82db5, 들개 연결 완료·엘리트 스프라이트 임포트, 96gen). 진행: Art 10b(개 이동 재생성), B54(엘리트 연결 코드), B30d3. 확인 대기: `D:\gate-shots\art\art10\` 시트.
- 자료 업로드: ref-vfx-map-design.md, ref-marketing-brief.md (design-conflicts §5 반영). B55 후보: 구조물×기믹 조합 라이브러리. 마케팅은 출시 준비기 별도 검토.
- 완료: B30d3(ce26d21, 고유 무기36+슬롯풀28, 간헐 실패=테스트 방어막 롤, 전체 82 exit0, smoke_bot_normal 9분 타임아웃 미확인→B54 세션이 확인 중), Art 10b(96f933a, 개 이동 재생성 24gen). 사용자 검토 대기: ARCHITECTURE §41 고유 효과 표(이름·수치, 특히 dagger_t4·bow_t6·body_lastbreath·boots_afterimage·pistol_t6, stat형 7종), art10b 시트.
- 완료: B54(cc322e0·56af3e9 엘리트 개 연결), B52(5216748, Loc 구조, 영어 초안 611/847, §42). 미해결: test_smoke_bot_normal 20분+ 미완료(조사 세션 진행). 사용자 검토 대기: 영어 초안 전체, 한글 폰트 번들 여부, 미번역 236건(고유효과128·퀘스트대사59·기믹이름49) 처리.
- 대기: smoke_bot_normal 조사 종료 후 (B52b 취소: 번역·폰트는 출시 준비 단계로 연기, 결정 227·228 정정). 이후 큐: B35 시가지 보스, B36 난이도, B32d 지형 스킬, B48 건물 가림, 아이소 성능, Art 11(곰·문지기).
- 진행: Art 11(곰·문지기, 상한 190gen), test_smoke_bot_normal 조사. 다음 코드: B35 시가지 보스 2명(smoke 조사 후).
- 변경: Art 11은 문지기만(120gen), Art 12 곰 재디자인 A/B/C 후보(40gen, 결정 229). 사용자가 `D:\gate-shots\art\art12\choose\`에서 곰 선택 필요.
- 완료: Art 12(b2b6d77), 스모크 조사(원인 확정). 진행: Fix 스모크 봇, Art 11 문지기, Art 13 곰 C 3배 전 동작(상한 150gen).
- 완료: Art 11 문지기(2888e4d, 3.85배, 81gen 추정, 결함: 이동 E·W 방향 이탈·공격 이펙트 색 불일치·body.png 117MB). 진행: B56 체급 연결(문지기 연결·체급 데이터·텍스처 메모리), Fix 스모크 봇, Art 13 곰. 사용자 확인 대기: `D:\gate-shots\art\art11\` 시트·GIF.
- 완료: Art 13 곰 C(64fef1b, 72gen, 높이 158~163px=2.9~3.0배, 결함: attack 갈기 뭉개짐·N/NE 뒤돌아봄), 스모크 봇 수정(§45, normal ALL PASS 32초). 진행: Art 13b(곰 attack 재생성, 상한 40), B56 체급 연결. 다음: B57 곰 연결(bear 몬스터 데이터·군집·구역, B56 후), B35 시가지 보스 2명. 사용자 확인 대기: art11·art13 시트.
- 완료: B56(2f4df20, 체급 데이터·문지기 연결·텍스처 149→69MB), Art 13b(f5bb760, 곰 attack 등 교체, 28gen; 이동 S·N 발 교대 미해결). 진행: B57(곰 연결·대형 판정·카메라·body.png 삭제). 다음: B35 시가지 보스 2명. 확인 대기: art13b 시트, 아이소 문지기 내려찍기 체감.
- 완료: B57(ea2dcf2, 곰 연결·대형 판정·큰 몸 카메라 줌·gatekeeper body.png 삭제, 전체 84스위트 통과). 진행: B35 시가지 보스 2명(임시 boss_dog 스프라이트, [후속 아트] 전용 보스 스프라이트). 확인 대기: 곰 능력치 체감·줌 전환 거슬림·곰 body.png(6.4MB 미사용, 삭제 승인 대기).
- 완료: B35(f8980e9·9468497, 시가지 중간보스 '정예 들개 대장' 2페이즈 + 지역보스 '들개 두목' 3페이즈 소환형, 아레나 21x21, ARCHITECTURE §50, test_city_bosses 163+ PASS, 아이소 보스전 p99 11.1ms). 임시 boss_dog 스프라이트([후속 아트] 전용 보스 스프라이트·번개/창 이펙트). 사용자 확인 대기: 수치·전투 체감, 예고 도형 가독성, 지역보스 판정 크기. 다음: B36 난이도.
- 완료: B36(c00e46d, 유효레벨=레벨+장비보정(−2~+3), d±1 보통, 체력 exp(−0.05d')·피해 exp(−0.07d')·미달 경험치 보너스 ≤1.5, data/fit.json, ARCHITECTURE §51, 세이브 변경 없음, 전체 스위트·스모크 3종 PASS, 아이소 p99 9.1ms). 사용자 확인 대기: 개발자 오버레이 scale 줄·레벨1→경계지 어려움/레벨20→튜토리얼 쉬움 체감, 초반 무장비 보정 적절성. 다음: B32d 지형·규칙 스킬 8종.
- 완료: B32d(8762ec5, 지형·규칙 스킬 8종 융기·함몰·석벽·점화·물소환·동결·뇌운·돌풍, 스킬북 풀 40종, ARCHITECTURE §52, 87스위트 PASS·스모크 3종 PASS). 주의: 요정숲 스킬 반복 최악 p99 16.7~18.1ms(평균 OK) → 아이소 요정숲 성능 최적화 작업에 포함. test_special_effects에 SCRIPT ERROR 1줄(통과하나 원인 미확인). 사용자 확인 대기: 아이소 커서 대상 지정 느낌·표식 가독성, 마소 구역 0에서 지형 편집 1칸 제한이 의도에 맞는지, 수치 밸런스. 다음: B48 건물 가림(결정 191), 이후 아이소 요정숲 성능·test_special_effects 에러 조사.
- 완료: B48 건물 가림(b6e604f, 아이소 입장 시 외벽 지붕과 같이 페이드→알파 0.2 이하 완전 제거, ARCHITECTURE §53), 요정숲 성능 부분 개선(3393820, §54; p99 16.6ms 안정 미달 → 결정 235 보류), test_special_effects 에러 수정(3f9ed69). 전체 스위트·스모크 PASS. 사용자 확인 대기: 건물 입장 페이드 실화면(자연스러움, 외벽 제거 후 바닥 모양). 로컬 커밋만(푸시 안 함).
- 코드 큐 소진. 남은 항목은 아트·사운드·콘텐츠 결정이 필요한 것: 전용 보스 스프라이트, 스킬 VFX(208), UI 종이/금속(211), 사운드(212), 지형·건물 아트(200·207), 경계지·요정숲 보스, B55 조합 라이브러리 문서.
- 완료: Art 14 시가지 보스 전용 스프라이트(ARCHITECTURE §55, 로컬 커밋; 112/150gen, 잔액 4455→4343). city_mid=A2(정면 재생성, 100~122px), city_chief=A(번개 안테나·녹슨 갑옷, 160~174px), B·C 교체 가능(README). 5방향 생성+미러. 전체 스위트 PASS, 스모크 normal은 exit 0이나 'ALL PASS' 줄 미확인, 보스전 아이소 p99 11.6ms. 결함(수작업): 베기·피 자국이 공격 프레임에 구워져 방향별 상이 / mid 공격 N 얼굴 노출 / chief 걷기 SE 루프 이음새 20px 점프 / mid 걷기 S·N 통통함 약함 / chief cast E 한 프레임 청백 플래시·번개 3프레임 상단 잘림 / chief 팔레트 253색. 사용자 확인 대기: `D:\gate-shots\art\art14\choose\choose_sheet.png`, GIF(걷기 바운스·roar·cast 타이밍), mid 크기, 곰 body.png 삭제 승인(권한 검사에 막혀 미삭제).
- 시작: Art 15 시가지 월드 아트 1단계(지형 타일 후보 A/B + 계획서, 상한 120gen) — 사용자 요청 '게임 배경 및 월드 전반 디자인'. 곰 body.png 삭제 세션 진행(session_0148ScB8ErPQ8uKZPTjh5fSk, 사용자 승인).
- 완료: 곰 body.png 삭제(f607d51, 사용자 승인, validate_sprites·관련 테스트 PASS, 전체 스위트는 미실행 — 다음 전체 스위트에서 확인).
- 완료: Art 15 시가지 지형 타일 1단계(§56 계획서 89f658d, §57 B안 타일 42장 7커밋; 75/100gen, 잔액 4268.8; tools/tile_balance.py 밝기 보정, 아이소 연결, 전체 스위트·스모크 PASS, 성능 영향 ≤3%, 탑다운 불변). 사용자 확인 대기: `D:\gate-shots\art\art15b\`(game\·mock\) — 흙 발자국 무늬 반복, 도로-보도 대비, 균열·웅덩이 밀도, 횡단보도·차선 위치, 실내 타일 비율, 외벽 페이드 후 실내 바닥(b_inside2.png). 알려진 한계: 잔해|흙·도로|잔디 직선 경계 눈에 띔(전이 타일 미구현), 물웅덩이는 시각 전용. 다음: 2단계 오브젝트, 3단계 반파 건물.
- 시작: Art 16 시가지 오브젝트 1차 후보(상한 100gen) — session 예정 기록은 아래 id 참조.
- 대기: 결정 244 타일 이음매 해소(오버레이+데칼) — Art 16c 종료 후 착수(코드 충돌 방지).
- 동시 시작(아트 후보, 코드 연결 없음; 계획서는 art_plans/*.md 별도 파일, ARCHITECTURE 포인터는 부모가 후속 추가): Art 17 시가지 반파 건물 후보(session_0148ScBAjaq4nurnqcJ5z2VW, 120gen), Art 18 시가지 데칼 에셋(session_0148ScBC4D3Bty2FuSX7YfrE, 40gen), Art 19 경계지·요정숲 지형 타일(session_0148ScB9wKz7G1h2QjDuSAnf, 120gen). 진행 중: Art 16c(session_0148ScB88qyUjWoRD3QCHqBe) 종료 후 결정 244 오버레이+데칼 연결 코드 세션.
- 완료(후보, 게임 미연결): Art 17 반파 건물(af68dd7, art_plans/art17_building.md, 42gen; A 베이지 플라스터 아파트/B 세이지 벽돌 가게, 외벽 1칸=큐브, 문·지붕·가구 9종; 위험: 벽 3단이 캐릭터보다 낮음·문틀이 캐릭터 가림·지붕 격자 이음), Art 18 데칼(63803b5, art_plans/art18_decals.md, 절차 생성 27장 gen 0 — 유료 승인 확인 불가로 AI 생성 안 함; 낙엽·유리·잡초 약함, 큰 면 데칼 효과적), Art 19 경계지·요정숲 타일(d90669f, art_plans/art19_regions.md, 75gen; A 차분/B 선명, B 일부 형태 깨짐; 직선 경계 어색, 숲 위 캐릭터 가독성). 잔액 약 4137.8. ARCHITECTURE 포인터 추가는 게임 저장소에서 후속(번호 §62+ 확인). 사용자 선택 대기: 17(A/B·문·큐브 방식·가구), 18(채택 종류·AI 재생성 승인·연결), 19(A/B·신규 지면·경계 처리). 시트는 PC에서 열도록 지시함.
