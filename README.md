# jiteum

짙은 — 하루를 짙게 남기는 앱들. www.jiteum.com (GitHub Pages, 커스텀 도메인)

- 루트 `index.html`: 마음테 랜딩 — https://www.jiteum.com/
  - 에셋은 루트의 `css/`, `assets/` 에 둔다. GitHub Pages 는 정적이라 301 을 못 주므로,
    첫 진입 주소에는 리다이렉트 스텁 대신 실제 페이지가 있어야 한다(스텁을 두면
    흰 화면에 안내 문구가 한 번 깜빡인 뒤 넘어간다).
- `maumte/`: 법적 고지 — 스토어에 등록된 주소라 경로를 그대로 유지한다.
  - 개인정보처리방침: https://www.jiteum.com/maumte/privacy.html
  - 이용약관: https://www.jiteum.com/maumte/terms.html
  - AI 및 안전 안내: https://www.jiteum.com/maumte/ai-safety.html
  - `maumte/index.html` 은 옛 랜딩 주소 리다이렉트 스텁(→ `/`). 2026-07-23 랜딩이
    루트로 옮겨오기 전 정식 주소였으므로 걸린 링크·색인을 위해 남겨 둔다.
- 다음 앱은 폴더 추가 (폴더명 = URL 경로). 허브를 되살릴 땐 `hub.html` 참고.
- `eungyeol/`: 옛 경로 리다이렉트 스텁만 — 2026-07-17 앱명이 은결→마음테로 되돌아가며
  `/eungyeol/*` → `/maumte/*` 로 이동했다. 그 사이(07-13~17) 걸린 링크·색인이 깨지지 않게
  meta refresh + canonical 스텁을 남겨 둔다. 새 링크는 랜딩이면 `/`, 고지면 `/maumte/*`.
- `robots.txt`·`sitemap.xml`: 색인 대상은 `/` 하나뿐이다. 법적 고지 3종과 리다이렉트
  스텁은 `noindex` 라 sitemap 에 넣지 않는다(넣으면 신호가 어긋나 경고가 뜬다).
  **새 페이지를 만들면 `sitemap.xml` 에 추가할 것.**

## 문서

- [`LAUNCH-CHECKLIST.md`](LAUNCH-CHECKLIST.md) — 출시 당일에 바꿀 것(“곧 출시” 여섯 곳·
  UTM·공식 배지·실기기 스크린샷)과 그 뒤로 되풀이할 일(앱과의 동기화·FAQ·검색·측정).

## 손대기 전에

- **push = GitHub Pages 배포.** 로컬 확인은 `python -m http.server 8123` 로.
- **`css/style.css` 를 고치면 `index.html` 의 `?v=` 를 올린다.** 안 올리면 브라우저가
  옛 스타일시트를 계속 써서 "고쳤는데 안 바뀐다"가 된다.
- 법적 고지는 앱 `lib/features/legal/data/legal_documents.dart` 가 원본, `maumte/*.html`
  이 사본이다. 앱을 고치면 **같은 작업 안에서** 여기도 고친다.
