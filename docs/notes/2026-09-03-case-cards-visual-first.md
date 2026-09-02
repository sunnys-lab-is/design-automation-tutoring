# 근거 카드를 이미지 중심으로 재구성

- 날짜: 2026-09-03
- 범위: 과외 랜딩 페이지 05 Haruroom · 06 STUDIO 근거 카드 6장, 07 방법 섹션, 08 커리큘럼, 푸터

## 무엇을

사용자 지적 세 가지를 반영했다.

1. 근거 카드(.case)가 글이 너무 많고 이미지가 작았다. 카드 구조를 `태그 → 한 줄 제목 → 큰 시각물(6:5) → 한 줄 결론`으로 바꾸고 본문 문단과 플레이트 캡션을 없앴다.
2. 06 STUDIO 카드의 표 캡처 3장(프리뷰 존, 대비표, 수용 기준표)이 "텍스트 중심 화면"이었다. STUDIO Tokens 프레임(5:2)과 PORTFOLIO Profile B Foundations 프레임(24:2)의 어법, 즉 스와치 타일 + 모노 라벨 + 간격 바로 직접 그린 인라인 SVG로 교체했다. Haruroom 대비 시트와 RecordRhythm 컴포넌트도 같은 어법으로 다시 그렸다.
3. 07 방법 섹션의 과정 산출물 이미지 6장, 06 화면 캡션, 푸터 출처 문장 3줄을 삭제했다. 08 커리큘럼의 큰 고스트 숫자("1주")는 제목 위 작은 모노 라벨로 바꿨다.

## 왜

독자는 과정보다 결과에 관심이 있다는 사용자 판단. 표 캡처는 축소되면 읽히지 않아 장식도 증거도 되지 못했다. 수치는 그대로 두고 표현만 바꾸면 증거 기능이 살아난다.

## 어떻게

- `portfolio/redo-case-cards.py`: 두 섹션의 `.cases` 블록을 통째로 다시 생성한다(재실행 가능). SVG는 viewBox 360×300, 페이지 폰트 변수(`--font-mono`, `--font-sans`)를 그대로 쓴다.
  - 대비 타일: 토큰마다 "Aa" 스와치 + 실측 대비비 + 토큰명. 예외(text/disabled 2.58:1)는 붉게 표시. STUDIO는 "AA 4.5:1 pass 4 / 5" 요약 타일 추가.
  - 수용 기준: SA-01~10 타일(통과 6은 검정, 보류 4는 점선 + P4/P5/P6) + 간격 시트식 바 3줄(수용 기준 6/10, 노드 2508, 미바인딩 0).
  - 프리뷰 원칙: 회색 크롬(gray/0~1000 스트립) 안에 preview/mat, 점선 preview/boundary, PREVIEW 라벨을 두고 그 안에만 사용자 세리프 제목과 웜 팔레트를 그림.
- CSS: `.evidence .plate`를 고정 높이 200px에서 `aspect-ratio: 6/5`로, 폰 화면은 cover 상단 크롭. 결론 바는 `margin-top:auto`로 바닥에 고정.
- 더 이상 안 쓰는 data URI 4개(`--img-st-preview/contrast/accept`, `--img-rhythm`) 제거로 파일 617KB → 520KB.
- 검증: 헤드리스 Chrome 1440/500 폭. 요약 타일 글자 넘침을 두 번 줄여 해결.

## 변경된 파일

- `portfolio/deploy/index.html` — 카드 6장 재생성, CSS, 07 이미지·캡션·푸터 삭제, 주차 라벨
- `portfolio/redo-case-cards.py` — 카드 재생성 스크립트(SVG 빌더 포함)
- `portfolio/studio-section.html` — 06 원본 마크업 동기화
