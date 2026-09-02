# STUDIO를 과외 랜딩 페이지의 두 번째 케이스로 추가

- 날짜: 2026-09-02
- 범위: 과외 랜딩 페이지 `portfolio/deploy/index.html` 06 섹션

## 무엇을

Figma 파일 "STUDIO — Portfolio Generator App"(`ufc1ZEZmSfq0xjwxfSjqsL`)을 전부 읽고, 그 내용을 과외 랜딩 페이지에 **06 두 번째 프로젝트** 섹션으로 넣었다. 기존 05 Haruroom 케이스 뒤, 07 방법 설명 앞이다. 뒤따르는 섹션은 07~11로 번호를 밀었고 서브내비, 섹션 카운터(`/11`), 푸터 문장까지 함께 고쳤다. Artifact(422913a3)를 같은 주소로 재게시했다.

섹션 구성:

- 리드: Haruroom(다이어리)과 다른 종류의 앱(디자이너 도구)에 같은 순서를 다시 썼다는 것. 개인 프로젝트, 출시 전이라고 명시.
- 화면 4장: 결 고르기, Style DNA 14축, Art Direction, 생성 완료.
- 수치 6개: 원칙 5, 디자인 토큰 124, 컴포넌트 43종, 화면 13장, 수용 기준 통과 6/10, 미바인딩 0. 통과 못 한 넷은 "해당 화면이 아직 없어 판정을 미뤘다"고 캡션에 적음.
- 근거 카드 3장: 원칙(사용자 색이 앱 크롬에 스며들면 막힘, 미리보기 존 표), 접근성 대비(본문 글자색 세 단계 실측 대비비), 감사 수치(7페이지 2508노드, 미바인딩 0).
- 콜아웃: 마지막 UX 법칙 대조에서 실제 위반 넷(터치 영역 44pt, 화면당 강조색 하나, 결과물 먼저 보여주기, 생성 중 화면)이 걸려 그 자리에서 고친 이야기.

## 왜

과외 페이지의 케이스는 원래 Haruroom 하나로 제한했다(전 과정 로그가 남은 유일한 케이스). STUDIO는 같은 순서를 처음부터 끝까지 다시 돌린 두 번째 기록이라, "방법이 한 앱에만 맞는 게 아니다"라는 증거로 쓸 수 있다. 사용자가 "내가 디자인한 앱 → 케이스로 추가", 상태는 "개인 프로젝트, 미출시"로 확정했다.

## 어떻게

- **파일 읽기**: URL의 노드 65:494는 파일에 없어 `use_figma`로 페이지를 열거해 01 Foundations(원칙·수용 기준·감사표)·02 Style DNA·03 Components·04/05 화면·06 Library·07 Editor를 읽었다. 수치는 커버에 적힌 값(103)이 아니라 변수 컬렉션을 직접 세어(124) 썼다.
- **이미지**: `download_assets`로 2배 PNG를 받아 `portfolio/shots/studio/`에 두고, 스크립트가 WebP data URI로 인라인한다. 폭이 넓은 표(대비표, 수용 기준표)는 `join_cols()`로 라벨·값 칼럼 사이 빈 공간만 잘라내 붙였다. 순서나 겹침 없음.
- **삽입 스크립트** `portfolio/add-studio-section.py`: `id="second"`가 이미 있으면 중단. `--img-refs` 뒤에 변수 7개 추가, `/10`→`/11`, 서브내비 교체, 섹션 번호 id별로 재부여, 07 `#method` 밴드를 tinted로 바꿔 교대 유지, `studio-section.html`을 06 위치에 삽입, 푸터 문장 추가.
- **문장 규칙**: 카드 한 줄 25자 안에 들어가게 문장을 줄였다(고아 줄 3회 수정). 대시·글리프 화살표·과장 표현 없음. 출시 배지 없음.
- **검증**: 헤드리스 Chrome 1440/500 폭 렌더로 가로 넘침 없음, 태그 균형 확인. Artifact를 read 후 같은 URL로 재게시.

## 변경된 파일

- `portfolio/deploy/index.html` — 06 섹션 삽입, 07~11 번호 이동, 서브내비·카운터·푸터·이미지 변수 추가
- `portfolio/studio-section.html` — 06 섹션 마크업 원본
- `portfolio/add-studio-section.py` — 재현 가능한 삽입 스크립트(1회 실행 보호)
- `portfolio/shots/studio/*.png` — Figma 2배 내보내기 10장
- `portfolio/deploy/README.md` — `index.html`이 소스라는 사실과 갱신 절차로 갱신

## 남긴 것

- 옛 `design-automation-tutoring.src.html`과 `build-page.py`는 손대지 않았다(08-28 상태, 더 이상 소스가 아님).
- GitHub Pages는 꺼져 있어 저장소 push는 백업 용도다.
