# design-automation-tutoring

'AI 디자인 자동화 1:1 과외' 랜딩 페이지의 배포 저장소입니다.
공개 주소는 GitHub Pages **https://sunnys-lab-is.github.io/design-automation-tutoring/** 입니다(2026-09-03부터, main 브랜치 루트, `.nojekyll`).
같은 내용이 Claude Artifact https://claude.ai/code/artifact/422913a3-3052-468c-9466-1feaaad79fb9 에도 게시되지만 Artifact는 로그인한 사람에게만 열립니다.

## 소스는 `index.html` 하나입니다

2026-08-30 리디자인 이후 **이 저장소의 `index.html`이 편집 대상이자 배포물**입니다.
예전 파이프라인(`portfolio/design-automation-tutoring.src.html` → `build-page.py` → `.html`)은 08-28 상태에서 멈춰 있어 더 이상 쓰지 않습니다. 그 파일을 빌드해 여기로 복사하면 리디자인이 되돌아가니 주의하세요.

이미지는 Artifact CSP 때문에 외부 참조가 막혀 있어 WebP data URI를 `:root`의 `--img-*` 변수로 한 번씩만 넣습니다. 원본 PNG는 `portfolio/shots/`에 있습니다.

## 갱신 방법

1. `index.html`을 직접 고칩니다. 큰 삽입은 `portfolio/add-studio-section.py`처럼 재현 가능한 스크립트로 남깁니다(STUDIO 06 섹션이 그 예이며 마크업은 `portfolio/studio-section.html`).
2. 헤드리스 Chrome으로 1440/500 폭을 렌더해 가로 넘침과 고아 줄을 확인합니다.
3. 커밋·푸시하면 GitHub Pages가 1~2분 안에 갱신됩니다. Artifact도 같은 주소로 재게시합니다(favicon 🎨 유지).
4. 커밋·푸시:

```
cd portfolio/deploy && git add -A && git commit -m "..." && git push
```

## 섹션 순서

01 표지 · 02 · 03 · 04 · 05 Haruroom · **06 두 번째 프로젝트 STUDIO** · 07 순서(방법) · 08 커리큘럼 · 09 · 10 FAQ · 11 마무리(다크).
밴드 색은 tinted/plain 교대이며 06이 plain, 07이 tinted입니다.
