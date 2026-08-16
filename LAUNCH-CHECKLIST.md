# 출시 체크리스트

Google Play 출시 당일에 이 저장소에서 바꿀 것과, 그 뒤로 되풀이할 일.
당일에 헤매지 않으려고 미리 적어 둔다. **push = GitHub Pages 배포**임을 잊지 말 것.

---

## D-day — 한 번에 바꾸는 것

### 1. "곧 출시" 여섯 곳을 실제 링크로

| 파일 | 줄 | 지금 | 바꿀 것 |
|---|---|---|---|
| `index.html` | 66 | `<span class="nav-chip">곧 출시</span>` | 헤더 칩 → 스토어 링크 또는 제거 |
| `index.html` | 81 | `badge-soon on-dark` (히어로) | 공식 Play 배지 `<a>` |
| `index.html` | 468 | `badge-soon` (하단 CTA) | 공식 Play 배지 `<a>` |
| `maumte/privacy.html` | 21 | `nav-chip` | 제거 (고지 페이지엔 CTA 불필요) |
| `maumte/terms.html` | 21 | `nav-chip` | 〃 |
| `maumte/ai-safety.html` | 16 | `nav-chip` | 〃 |

`index.html:466` 에 교체 방법 주석이 이미 있다.

### 2. 링크에 UTM 을 붙인다

```
https://play.google.com/store/apps/details?id=com.weight500.maumte&utm_source=landing&utm_medium=web&utm_campaign=launch
```

**안 붙이면 웹에서 몇 명이 설치했는지 영영 모른다.** Play Console >
획득 보고서에서 이 값으로 갈린다. 히어로와 하단 CTA 는 `utm_content`
(`hero` / `footer`)로 나눠 어느 자리가 먹히는지 본다.

### 3. 공식 배지 에셋을 쓴다

구글이 브랜드 가이드를 강제한다 — **직접 그린 버튼은 정책 위반.**
공식 배지를 내려받아 `assets/` 에 두고 `.badge-soon` 을 대체한다.
한국어 배지가 따로 있다.

### 4. 구조화 데이터

`index.html` 의 `SoftwareApplication` 블록에 `downloadUrl` 을 넣는다.

> ⚠️ `aggregateRating`(별점)은 **실제 평점이 쌓인 뒤에만.** 없는 별점을
> 넣으면 구조화 데이터 정책 위반이라 리치 결과가 통째로 내려간다.

### 5. 실기기 스크린샷 (미뤄 둔 건)

스테이지의 폰 화면 넷은 아직 CSS 재현(`.sc-day`·`.sc-week`·
`.sc-galaxy`·`.sc-year`)이다. `<img>` 로 교체한다.

- 필요한 화면: 하루 카드 / 주간 돌아봄 / 감정 은하 / 지나온 길
- 프레임 안쪽 `294 × min(660, 100vh-148)`, 각 60KB 이하 webp
- `object-fit: cover; object-position: top`
- 프레임·전환·눈금은 바깥이라 안 건드려도 된다

### 6. 앱 쪽 블로커 (웹 아님, 같이 확인)

- **판매자 정보** — `lib/features/legal/domain/seller_info.dart` 가 전부
  공란이라 화면에 절이 안 그려진다. 인앱결제를 파는 순간 전자상거래법
  제10조 대상.
- **Play 데이터 안전 신고** — "수집 없음"은 이제 틀리다. 기기를 나가는
  것은 둘: **Sentry 크래시 진단**, **받아쓰기 온디바이스 실패 폴백**.
  애널리틱스는 전송 0(`HarnessAnalyticsService` 뿐).

---

## 출시 후 — 되풀이하는 일

### ① 앱과 동기화 (가장 자주 깨진다)

두 번 크게 벌어진 적이 있다.

- 랜딩이 앱보다 **369커밋** 뒤처져 "음성 30초"처럼 없는 기능을 광고했다.
- 웹 법적 고지가 앱보다 **두 달** 낡아 Sentry·받아쓰기 폴백·구매정보가
  빠져 있었다.

의지로는 안 된다. **릴리스 절차에 항목으로 박는다.**

- 앱 `lib/features/legal/data/legal_documents.dart` 가 **원본**,
  `maumte/*.html` 이 **사본**이다. 앱을 고치면 **같은 작업 안에서** 웹도
  고친다. 두 파일 머리에 서로를 가리키는 주석이 있다.
- 기능을 더하거나 감추면(`feature_flags.dart`) 랜딩 문구도 함께 본다.
- 유료 구성이 바뀌면(`monetization_config.json`) Pro 목록도 함께 본다.

### ② FAQ 가 지원 창구로 바뀐다

지금 FAQ 열 문항은 전부 "살까 말까" 하는 사람용이다. 출시 후엔 산
사람의 질문이 온다 — 구매 복원, 기기 변경, 백업 실패, 모델 다운로드.
**같은 질문이 문의 메일로 세 번 오면 FAQ 에 올린다.**

### ③ 검색 유입

무예산이라 검색이 1순위 채널이다(`haruhoego/docs/MARKETING_STRATEGY.md`).

- `robots.txt`·`sitemap.xml` 는 갖췄다.
- 새 페이지를 만들면 `sitemap.xml` 에 추가한다.
- 법적 고지 3종은 지금 `noindex` 다. 검색에서 "마음테 개인정보처리방침"
  이 안 잡힌다 — 의도한 것인지 한 번은 되짚을 것.

### ④ 측정

계측이 없으면 관리가 아니라 감이다. 무엇을 붙였는지·무엇을 보는지는
`README.md` 에 적어 둔다.

---

## 잊기 쉬운 것

- **`css/style.css` 를 고치면 `index.html` 의 `?v=` 를 올린다.** 안 올리면
  브라우저가 옛 스타일시트를 계속 써서 "고쳤는데 안 바뀐다"가 된다.
  실제로 한 번 겪었다.
- **`maumte/` 경로는 스토어에 등록된 주소다.** 옮기지 말 것.
- 배포 확인은 캐시를 의심하며 — `Ctrl+Shift+R`, 안 되면 `?x=1`.
