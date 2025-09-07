# hyebin-dev Astro Blog

Astro + GitHub Pages 블로그/포트폴리오. 푸시하면 자동 배포됩니다.

## 로컬 실행
```
npm install
npm run dev
```

## 배포
1) 이 프로젝트를 GitHub의 `hyebin-dev.github.io`(공개) 저장소로 업로드
2) Settings → Pages → Build and deployment → **Source: GitHub Actions** 선택
3) 커밋/푸시하면 Actions가 빌드 후 Pages에 배포

## 커스터마이징
- 사이트 주소: `astro.config.mjs`의 `site`는 이미 `https://hyebin-dev.github.io`로 설정됨
- 내비/레이아웃: `src/layouts/Layout.astro`
- 글: `src/pages/posts/` 아래 `.md` 또는 `.astro`
- 프로젝트: `src/pages/projects.astro`
- 이력서: `src/pages/resume.astro`(또는 `public/resume.pdf` 추가 후 링크)
