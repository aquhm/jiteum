# maumte-web

마음테 랜딩페이지. GitHub Pages(main 브랜치 root)로 배포되는 순수 정적
HTML/CSS 사이트다. 빌드 과정 없음 — push 하면 배포된다.

- 사이트: https://aquhm.github.io/maumte-web/
- 개인정보처리방침(Play Console 등록 URL):
  https://aquhm.github.io/maumte-web/privacy.html

## 법적 문서 동기화 정책

`privacy.html`, `terms.html`, `ai-safety.html` 본문의 원본(source of
truth)은 앱 저장소(private)의
`lib/features/legal/data/legal_documents.dart`다. 앱 내 문서가 바뀌면
이 저장소의 페이지도 같은 내용으로 수동 갱신하고 '최종 수정' 날짜를
일치시킨다. 웹에서 본문을 임의로 수정하지 않는다.

## Play 배지

출시 승인 전까지 "Google Play 곧 출시" 비활성 배지를 표시한다. 스토어
등록 승인 후 `index.html`의 `.badge-soon` 2곳을 실제 스토어 링크가 담긴
공식 Google Play 배지로 교체한다.
