# AI 아트 도구 비교 시험 계획 (결정: 모든 후보를 시험한 뒤 도구 선택)

대상: PixelLab, SpriteCook, Scenario, Spritesheets.ai(서비스 확인 포함). 같은 조건으로 시험해 같은 표에 점수를 매긴다. 사용자는 이미지를 저장·전달하고 "느낌 맞나"만 판단한다.

## 공통 입력 (모든 도구 동일)
- 캐릭터 문구(영문): `modern pixel art, isometric, balanced proportions, thick clean black outline, warm low-saturation pastel palette (beige and sage green), multi-step soft shading, light from top-left, no dithering, young survivor in a worn tactical vest over a cloth tunic, practical boots, short rusty sword at the hip, small teal glowing charm on the belt`
- 크기: 가능한 한 64×64(안 되면 가장 가까운 크기와 도구가 제공한 선택지를 기록)
- 시점: 로우 탑다운/아이소메트릭에 가장 가까운 옵션, 방향 8방향(안 되면 되는 방향 수 기록)
- 저장 위치: `D:\gate-art-input\test_<도구명>\` (예: `test_pixellab`, `test_spritecook`)

## 시험 단계 (도구마다 같은 순서)
1. 캐릭터 1개 생성(8방향) — 이미지 저장
2. Idle 또는 Walk 애니메이션 생성(가능하면 6프레임, 가능한 옵션 기록)
3. 같은 문구로 2번 더 생성해 **일관성** 확인(같은 캐릭터가 방향·프레임마다 유지되는가)
4. 크레딧 소모량 기록(생성 전·후 잔액)
5. 약관 페이지의 상업 이용·AI 학습·소유권 문장 확인(화면 캡처 또는 복사)

## 평가표 (0~5점, 사용자가 이미지를 보고 / 나머지는 Claude가 임포트 도구로 점검)
| 항목 | 누가 | PixelLab | SpriteCook | Scenario | Spritesheets.ai |
|---|---|---|---|---|---|
| 첫인상(감성: 따뜻한 파스텔·쓸쓸함+신비) | 사용자 | | | | |
| 실루엣 가독성 | 사용자 | | | | |
| 검은 굵은 외곽선·깔끔한 클러스터(노이즈 없음) | Claude | | | | |
| 팔레트(베이지+세이지) 적합도 | Claude | | | | |
| 8방향 일관성 | 사용자/Claude | | | | |
| 애니메이션 부드러움·프레임 일관성 | 사용자 | | | | |
| 크기 규격(48×64/64×64) 지원, 투명 배경 | Claude | | | | |
| 레이어 분리 가능(몸/장비 별도) | Claude | | | | |
| 자동화(API/MCP) | Claude | | | | |
| 가격/크레딧 효율 | Claude | | | | |
| 약관(상업 이용·소유) | Claude | | | | |

## 진행 상태
- PixelLab: 가입 완료, 캐릭터 설정 완료(Humanoid·v3·Low Top-Down·64×64·Low detail·Black outline), 생성 대기
- SpriteCook / Scenario / Spritesheets.ai: 미시작
