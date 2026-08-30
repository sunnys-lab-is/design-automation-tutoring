# design-automation-tutoring

`portfolio/design-automation-tutoring.html`의 배포용 사본입니다. **이 저장소의 `index.html`은 생성물이라 직접 편집하면 안 됩니다.**

갱신 방법:

```
python portfolio/build-page.py
cp portfolio/design-automation-tutoring.html portfolio/deploy/index.html
cd portfolio/deploy && git add -A && git commit -m "update" && git push
```

편집 대상은 `portfolio/design-automation-tutoring.src.html`입니다.
