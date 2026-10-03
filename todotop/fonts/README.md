# 글꼴

앱(`daystack`)과 같은 글꼴을 웹용으로 줄여 넣었다. 둘 다 SIL Open Font License 1.1(같은 폴더의 `OFL-*.txt`).

| 파일 | 원본 | 크기 |
|------|------|------|
| `Pretendard-Regular.woff2` · `-SemiBold` · `-ExtraBold` | Pretendard (앱 `assets/fonts/*.otf`) | 각 약 200KB |
| `NanumPenScript-Regular.woff2` | 나눔손글씨 펜 (앱 `assets/fonts/NanumPenScript-Regular.ttf`) | 약 470KB |

**남긴 글자:** 한글 KS X 1001 완성형 2,350자 + 페이지에 쓰인 한글(현재 추가 0자) + 영문·숫자·라틴 기호, 문장부호(— · … “ ” 등), 화살표, ₩, 한글 자모, 전각 기호, 원문자.
페이지 문구에 2,350자 밖의 글자(예: 똠, 뷁)가 새로 들어가면 그 글자는 시스템 글꼴로 보인다 — 다시 줄여야 한다.

다시 만드는 법: fontTools + brotli(`pip install fonttools brotli`)로 `pyftsubset`과 같은 처리를 한다. 앱 저장소의 원본 글꼴에서 위 글자 집합으로 `flavor=woff2`, 레이아웃 기능 전부 유지.
