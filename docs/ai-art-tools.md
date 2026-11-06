# AI 아트 도구 후보 조사 (DESIGN.md §8.1 후보 4개) — 2026-11-06

> 출처는 대부분 제3자 비교 글·리뷰다. 가격·약관은 **도입 전 공식 페이지에서 직접 확인**해야 한다(DESIGN.md §8.1 방침).

| 도구 | 8방향 | 애니메이션 | Aseprite | 가격(조사 시점 보도) | 상업 이용 | 비고 |
|---|---|---|---|---|---|---|
| **PixelLab** | 4/8방향(아이소 포함) | 뼈대(skeleton) 또는 텍스트로 애니메이션 | 확장 있음 | 무료 체험(빠른 생성 40회 후 하루 5회), 유료 $12/월(2,000회)~$24~$50 | 소유·상업 이용 허용으로 보도(AI 학습에 쓰는 것만 금지). 무료 체험도 허용이라는 글과 개인 평가용이라는 글이 엇갈림 | API·MCP 있음(Claude Code에서 직접 호출 가능) |
| **Spritesheets.ai**(이름 확정 불확실) | 확인 못함 | 확인 못함 | 확인 못함 | 취미용 $3.50/월부터 | 상업 이용 가능이라 안내 | 이름이 같은 사이트인지부터 확인 필요 |
| **SpriteCook** | 8방향 지원 확인 못함 | Idle/Walk/Attack/Run 프리셋, 애니메이션당 약 20크레딧 | 확인 못함 | 무료(40크레딧/30일), 유료 $8/월(800크레딧)부터 | 모든 요금제 상업 이용 허용으로 보도(무료 포함) | PNG·스프라이트시트 내보내기, Godot 언급, API·MCP |
| **Scenario** | 직접 지원 확인 못함 | (Retro Diffusion 애니메이션 모델 호스팅 언급) | 확인 못함 | 무료(일 50크레딧), Starter $15, Pro $45(커스텀 모델 학습), Max $75 | 유료 요금제 상업 라이선스·소유, 무료 출력은 개인용이라는 글 있음 | **화풍 학습(커스텀 모델)이 강점** — 에셋 전체 일관성용. 모델 가중치 다운로드 불가라는 보도 |

## 새 규격(결정 189~194) 대비 확인할 것 — 아직 확인 못함
- 캔버스 48×64, 발바닥 중앙 정렬, 투명 배경 출력 지원
- 프레임 간 일관성(Idle/Walk 6프레임에서 얼굴·옷 유지)
- 장비 레이어 분리(몸/갑옷/무기) 출력 가능 여부 — 지원 도구가 거의 없을 수 있음 → 레이어 분리는 사람이 Aseprite에서 하거나 장비를 따로 생성
- 검은 굵은 외곽선·파스텔 팔레트 지시가 잘 먹는지
- Steam AI 공개 의무(플레이어가 보는 AI 아트는 공개 대상으로 보도됨, 원문 확인 필요)

## 추천 [제안]
1. **PixelLab을 1순위 시험 대상**: 8방향 + 뼈대 애니메이션이 이 프로젝트 요구에 가장 가깝고, MCP/API가 있어 Claude Code가 직접 생성·임포트 파이프라인(B46)에 연결할 수 있음.
2. **SpriteCook 2순위**(가격 낮음, 애니메이션 프리셋) — 8방향 지원 여부는 시험으로 확인.
3. **Scenario는 후반**: 에셋 수가 많아져 화풍 일관성이 문제가 될 때 커스텀 모델 학습용(Pro $45).
4. Spritesheets.ai는 정확한 서비스 확인 후 판단.

## 출처
- PixelLab: https://www.pixellab.ai/ , https://ludo.ai/compare/best-ai-pixel-art-generators , https://sunoboard.com/blog/pixellab-mcp-pixel-art-claude-code , https://www.usethissi.com/tools/pixellab/ , https://knowara.com/ai-tools/image/pixellab-review/
- Spritesheets.ai: https://www.spritesheets.ai/free-ai-sprite-generator , https://www.spritecook.ai/compare/spritesheets-ai
- SpriteCook: https://makeaigames.com/tools/spritecook , https://alternativeto.net/software/spritecook-ai/about/ , https://inite.ai/en/atlas/spritecook.ai
- Scenario: https://www.scenario.com/pricing , https://help.scenario.com/articles/1129045411-frequently-asked-questions-faq , https://www.therundown.ai/tools/scenario , https://aitools.fyi/scenario


## 시험 결과 갱신 (2026-11-06)
- **PixelLab**: MCP 연결 성공(107 tools). 캐릭터 v3(64×64→56×56 설정) 8방향 품질 우수(코어 키퍼식 귀여운 치비형 채택). 애니메이션 비용(공식 가격표+실측): template 1/방향, skeleton-v3 3/방향(프레임 수 기준 3·8·15프레임 = 2·3·4), pro 10~25/방향. 걷기 6프레임 실측: template가 가장 걷기답고(눈·볼 색 번짐은 후처리 필요) skeleton-v3는 일관되지만 약함. 무료 체험 월 40 generations(남은 21), 동시 생성 1건. 캐릭터 다운로드 ZIP은 인증 없이 받을 수 있음.
- **SpriteCook**: 호스팅 MCP(`https://mcp.spritecook.ai/mcp/claude`) + OAuth(키 불필요) + REST API(Bearer 키, 범위 generate/read_assets/read_credits). 4/8방향 지원 문서 없음, 비용표는 `GET /v1/api/models`. 연결/인증 진행 중(미시험).
- **Scenario / Spritesheets.ai**: 미시험.
