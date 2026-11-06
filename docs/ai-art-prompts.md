# AI 아트 도구 입력 템플릿 (단계 1~3용)

> 도구마다 입력창 이름이 다르다. 아래 영문 문장을 그대로 붙여 넣고, 크기/스타일 옵션은 "pixel art, isometric-friendly, 64×64 canvas" 계열을 고른다.

## 공통 스타일 문장 (모든 요청 앞에 붙임)
`pixel art, clean 3-tone shading, dark same-hue selective outline, desaturated muted palette, limited colors, light from top-left, melancholic post-apocalyptic mood, no dithering, transparent background`

## 주인공 컨셉 (단계 1, 3장 생성해 1장 고르기)
1. `{공통} young survivor wearing a worn grey hooded jacket, practical boots, a short rusty sword at the hip, faint orange accent on the scarf, calm tired expression, full body, standing, 3/4 isometric view facing south-east`
2. `{공통} lone traveler with a long scarf and a cloth-wrapped backpack, small dim glowing charm (mana crystal) on the belt, lean build, same palette family`
3. `{공통} scavenger in patched work clothes and goggles pushed up on forehead, utility belt, worn leather gloves, a short blade`

고를 때 보는 것: ① 한눈에 실루엣이 읽히나 ② 색이 탁하고 쓸쓸한가 ③ 눈에 띄는 포인트 색이 1개인가.

## 몬스터 컨셉 (이후 단계)
- 시가지 들개: `{공통} thin feral dog with matted grey fur, exposed ribs, orange glowing eyes, isometric view`
- 불나비(경계지): `{공통} large moth with ember-orange wings, soft glowing dust, teal-grey body`
- 가시뿌리(요정숲): `{공통} thorny root creature, mossy green and dark brown, violet glowing buds`

## 걷기 애니메이션 요청 (단계 3)
`walk cycle, 8 frames, loop, same character as reference, direction: south / south-east / east / north-east / north (5 directions, west-side directions will be mirrored)`


## [채택] 기본 캐릭터 v1 프롬프트 (PixelLab, 결정 195)
설정: Humanoid, v3, Low Top-Down, Sprite Size 56×56, Low detail, Black outline. **부정 표현(no backpack 등)은 해당 물건을 그리게 만들므로 쓰지 말고 긍정문으로만 쓴다.**
```
modern pixel art, isometric, chibi proportions, about 2.5 to 3 heads tall, oversized round head, very cute face, two small glossy black dot eyes with a tiny white highlight each, eyes set wide apart low on the face, no nose, tiny smiling mouth, soft pink blush on the cheeks, chubby short body, short stubby arms and legs, pure black outline 2px thick, bold clean black outline, warm low-saturation pastel palette dominated by beige and sage green, only about 24 colors, multi-step soft shading, light from top-left, no dithering. Young post-apocalyptic city survivor, contemporary clothing: faded sage green utility jacket open over a beige hoodie, a bright teal scarf clearly a different color from the green jacket, grey cargo pants with patches, worn lace-up combat boots, fingerless gloves. A small glowing teal crystal pendant hangs on a cord around the neck. Short rounded messy haircut with a small tuft on top. Arms relaxed at the sides, hands open. The jacket back is plain, smooth and clean, showing only the green fabric and the beige hood.
```
