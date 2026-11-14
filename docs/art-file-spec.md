# 아트 파일 규약 (B46 구현 기준, 게임 ARCHITECTURE §26 요약)

| 항목 | 규약 |
|---|---|
| 데이터 파일 | `data/sprites/<id>.json` (id = 파일명 = JSON `id`, `[A-Za-z0-9_]+`). `player`·몬스터 id·상인 id면 자동 적용 |
| 그림 파일 | `assets/sprites/<id>/<레이어>.png` 시트, 또는 `<폴더>/*.png` 개별 프레임. 투명 PNG, 알파 0/255 권장, 1:1 도트 |
| 규격 기본값 | `data/sprite_spec.json`: 캔버스 48×64, 피벗 발바닥 중앙, 16FPS, idle·walk 6프레임, `ref_tile_w` 32 |
| 방향 | 화면 기준 `N NE E SE S SW W NW` + `*`(전방향 공통). 8방향 직접 제작이 기본, 5방향(S SE E NE N)만 만들면 JSON에 `"mirror": true` |
| 레이어 | `Shadow BackWeapon BackArmor Legs Body Armor Head Hair Helmet FrontWeapon Shield` (`order`). 모든 레이어가 같은 캔버스·피벗·프레임 번호·타이밍 공유 |
| 레이어 옵션 | `anchor` / `slot`+`variants`(장비 교체용 시트) / `no_mirror` |
| 프레임 | 정수 `i` 또는 `{i, ms, ox, oy, ev, li, bk}` (`ev` 이벤트 마커 `hit`·`hit_end`·`step`, `li` 레이어별 칸, `bk` 몸 뒤로 보낼 레이어) |
| 동작 | `actions.<이름>: {loop, ms, ref_speed, dirs{방향: [프레임…]}}`. 이름 자유(`idle walk run roll attack1~3 hit death cast skill_<id>`). 없는 동작은 대체표(run→walk→idle) → 끝까지 없으면 도형 |
| 임포트 입력 | `D:\gate-art-input\<id>\` (몸 = 폴더 바로 아래, 다른 레이어 = 하위 폴더) |
| 입력 파일명 | `<동작>_<방향>_<번호>.png`(개별 프레임), `<동작>_<방향>.png`(가로 스트립), `<동작>.png`(격자 시트, 세로 = 방향 1·5·8줄), 선택 `manifest.json` |
| 임포트 실행 | `python tools/import_sprites.py [--foot auto] [--keyout] [--alpha-snap] [--palette 파일.json --snap] [--quantize N] [--dry-run] [--strict] [--only id]` |
| 임포트 결과 | `_import_out\report.md` + 방향별 GIF 미리보기·`sheet.png` + `data/sprites/<id>.json` + `assets/sprites/<id>/*.png` |
| 검증 | `godot --headless --path . --script res://tools/validate_sprites.gd` |
| 확인·핫리로드 | F1 개발자 패널 > 스프라이트: 미리보기·대상 교체·다시 읽기 |
| 타일 크기 연동 | 타일이 64×32로 바뀌면 `iso.tile_w / ref_tile_w`의 정수 배율이 그림에 곱해짐(B47에서 `ref_tile_w` 조정) |
