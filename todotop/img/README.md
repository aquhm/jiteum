# 랜딩 페이지 이미지 자리

> 생성한 이미지(PNG·JPG)는 `img/` 에 같은 이름 다른 확장자(예: `stage-3.png`)로 넣어 두면, WebP로 바꿔 아래 이름으로 넣는다(위키 규칙: 이미지는 WebP).

이 폴더(`img/`)에 아래 **파일 이름 그대로** 넣으면 `index.html`의 점선 이름표를 덮는다. 없으면 그 자리에 파일 이름이 적힌 이름표가 보인다.

| 파일 | 쓰이는 곳 | 상태 (2026-10-18) |
|------|-----------|-------------------|
| `shots/tower-week.webp` | 히어로 폰 틀 · 스크롤 구간 오늘(윗부분)·어제(아랫부분) · 룩 "나무" | 실기기 캡처 반영(스토어 01) |
| `shots/strike.webp` | "끝내면, 긋는다" 띠(영상 포스터 겸) | 반영(스토어 02) |
| `shots/week-flag.webp` | 스크롤 구간 — 한 주 | 반영(스토어 03) |
| `shots/look-bright.webp` · `shots/look-cartoon.webp` | 룩 "화사한 색"·"카툰" | 반영(스토어 04·05) |
| `shots/pen-shop.webp` | 펜 구역 오른쪽 | 반영(스토어 06) — ₩4,400·₩6,000이 찍혀 있다. 가격 표기를 빼기로 하면 펜 카드만 보이게 잘라 다시 만든다 |
| `stage-4.webp` | 스크롤 구간 — 미룬 일(먼지·이끼 앉은 블록 근접) | 반영(실기기 캡처 900×1125, 2026-10-18) |
| `strike.webm` | 띠의 긋기 영상(선택) | 비어 있음 — 아래 "긋기 영상" 절차. 포스터는 `shots/strike.webp`를 쓴다 |

- 실기기 캡처 원본은 앱 저장소 `design/store/screenshots/*.png`(1080×1920). 변환: `900×1600`, WebP q78(장당 30~60KB).
- `hero-wide/tall.webp`·`strike.webp`(사진)·`stage-1~3.webp`·`pens.webp` 생성은 **더 이상 필요 없다** — 코드에서 그 자리를 걷어냈다(아래 프롬프트는 기록으로 남김). 옛 렌더 `looks/*.webp`도 안 쓴다.

## 공통 규칙 (생성할 때)

- **참고 이미지로 앱 저장소의 `design/brand/icon/icon-master-1254.png`(아이콘 원본 렌더)를 함께 올린다** — 블록의 재질·모서리·빨간 줄이 아이콘과 같아야 한다.
- **글자를 넣지 않는다.** 블록 위 손글씨는 생성 이미지에서 깨지기 쉽다. 빨간 줄만 그린다.
- 블록: 밝은 너도밤나무, 모서리가 둥근 직육면체(가로로 긴 벽돌 모양), 무광에 가까운 매끈한 표면.
- 빨간 줄: 마커로 그은 듯한 한 줄, 색 `#D7263D` 근처.
- 하늘빛 배경: 위 `#6FA8FF`(파랑) → 아래 `#FF7350`(코랄)로 이어지는 매끈한 그라데이션.
- 어두운 장면의 바탕: 따뜻한 짙은 갈색 `#3A2F27` ~ `#241C17`.

## 프롬프트

### hero-wide.jpg
```
Photorealistic 3D product render, 16:9, 2400x1350. A tall freestanding tower of smooth beech-wood blocks (rounded-edge rectangular bricks, same material and proportions as the reference image), stacked in layers of three with each layer rotated 90 degrees like a Jenga tower, about 9 layers tall. A few blocks stick out slightly from the stack. Several blocks have a single hand-drawn red marker line (#D7263D) across their front face; the others are clean. No text, no letters, no numbers anywhere. The tower stands in the RIGHT third of the frame, slightly cut off at the bottom edge, seen from a low three-quarter angle. Background: a seamless smooth gradient from sky blue (#6FA8FF) at the top to warm coral (#FF7350) at the bottom, no horizon line, no props. Soft warm key light from upper left, gentle contact shadow under the tower. The LEFT two thirds of the image must stay empty gradient for headline text. Clean, calm, premium app-store hero.
```

### hero-tall.jpg
```
Same scene and style as the reference tower render, portrait 9:17, 1290x2400. The beech-wood block tower stands centered in the LOWER half of the frame, about 7 layers visible, base cut off by the bottom edge. Several blocks have one red marker line; no text or letters anywhere. Background: seamless gradient from sky blue (#6FA8FF) at the top to warm coral (#FF7350) at the bottom. The UPPER half must stay empty gradient for headline text. Soft warm light from upper left.
```

### strike.jpg
```
Cinematic macro photograph, 16:9, 2400x1350, shallow depth of field. A red marker pen tip drawing a single bold red line (#D7263D) across the long face of a smooth beech-wood block, caught mid-stroke, the line still slightly glossy. Other wooden blocks stacked out of focus behind it. Dark warm brown background (#241C17), low-key lighting with a warm rim light from the right. The subject sits in the RIGHT half; the LEFT half falls off into dark, empty shadow for text. No text, no letters, no hands.
```

### stage-1.jpg (오늘)
```
Photorealistic 3D render, portrait 4:5, 1600x2000. The TOP of a tall beech-wood block tower (Jenga-style layers of three, each layer rotated 90 degrees) against a warm dark brown backdrop (#463A30). The topmost bundle of 2 layers is brightly lit and in focus: two of its blocks have a red marker line and sit flush, the rest are clean and stick out of the stack by a few centimeters. Layers below are slightly dimmer. No text, no letters. Three-quarter view from slightly above, soft warm light from upper left.
```

### stage-2.jpg (어제)
```
Same tower and style as the previous image, portrait 4:5, 1600x2000, camera moved DOWN the tower. A thin visible gap separates two bundles of layers. The lower bundle (yesterday) fills the frame center: almost all its blocks have red marker lines and sit flush, one block without a line still sticks out. The bundle above is dimmed and partly out of frame. Warm dark brown backdrop (#463A30). No text, no letters.
```

### stage-3.jpg (한 주 — 깃발)
```
Same tower and style, portrait 4:5, 1600x2000. The very top of the beech-wood block tower, every visible block has a red marker line and sits perfectly flush. A small triangular pennant flag in warm coral (#FF7350) on a thin dark wooden pole is planted on the top block, slightly waving. Warm dark brown backdrop (#463A30), a soft celebratory glow behind the flag. No text, no letters, no confetti.
```

### stage-4.jpg (미룬 일 — 이끼)
```
Photorealistic macro render, portrait 4:5, 1600x2000. Close-up of a beech-wood block tower. ONE block in the center sticks out of the stack and looks old and neglected: a film of grey dust, small patches of green moss on its top edge, and a few fine hairline cracks. It has no red line. The blocks around it are clean and fresh, some with red marker lines. Warm dark brown backdrop (#463A30), soft side light that makes the dust and moss texture visible. No text, no letters.
```

### pens.jpg
```
Cinematic product photograph, 16:9, 2400x1350. Six different pens lying side by side at a slight diagonal on a dark warm wooden surface (#3A2F27): a red felt-tip marker, a pink highlighter, a navy fountain pen with a gold nib, a red wax crayon with a paper wrap, a glitter gel pen with a sparkling barrel, and a pen with a softly glowing cyan neon tip. The pens sit in the RIGHT half of the frame; the LEFT half is empty dark wood for text. Low-key warm lighting, shallow depth of field. No text, no logos, no letters.
```

## 따로 준비하면 좋은 것 (생성이 아니라 실기기 캡처)

- S23 현재 버전 캡처 3장: 나무 · 화사한 색 · 카툰 룩의 오늘 화면(블록 6개 이상, 몇 개는 그은 상태). `index.html`의 "탑의 모양은 세 가지예요" 구역 렌더를 바꾼다.
- 공식 Google Play 배지 이미지(한국어). 지금은 글자 버튼이다.

## 긋기 영상 — `strike.webm` (2026-10-18 추가)

"끝내면, 긋는다" 띠의 이미지 자리에 **앱에서 찍은 긋기 장면**을 먼저 쓴다. 파일이 있으면 영상이, 없으면 `strike.webp`(사진) 또는 이름표가 보인다. 움직임 줄이기를 켠 사람에게는 포스터만 보인다.

- 세로(9:16), 3~5초, 소리 없음, 1MB 안쪽. 블록 하나를 눌러 펜이 날아와 네 면에 줄을 긋고 블록이 들어가는 순간까지.
- 찍기(S23, USB): `adb shell screenrecord --size 720x1600 --bit-rate 6000000 --time-limit 10 /sdcard/strike.mp4` → 앱에서 블록 하나 누르기 → `adb pull /sdcard/strike.mp4`
- 자르기·변환(ffmpeg): `ffmpeg -i strike.mp4 -ss 1.5 -t 4 -an -c:v libvpx-vp9 -b:v 0 -crf 34 strike.webm`
- 이 폴더(`img/`)에 둔다. 포스터는 이미 있는 `shots/strike.webp`를 쓴다.

## 타일 실기기 캡처 (있으면 CSS 미니어처를 대신한다)

| 타일 | 찍을 것 |
|------|---------|
| 홈 화면에서 바로 그어요 | 홈 화면의 오늘 목록 위젯(4×2)과 미니 탑 위젯(2×2) |
| 아침·저녁에 묶어서 알려 줘요 | 저녁 묶음 알림(✓ 버튼 1~3개 보이게) |
| 이어 가면 메달이 쌓여요 | 기록 탭 맨 위 진열장 띠 |
