# sungd.uk

소개와 만든 것들(Projects)을 모아둔 개인 홈. Astro 정적 사이트, Netlify 배포.

```sh
npm install
npm run dev
```

## 사이트 구성

| 주소               | 내용                                | repo                 |
| ------------------ | ----------------------------------- | -------------------- |
| sungd.uk           | 소개 + 프로젝트 (이 repo)           | newhigen.github.io   |
| writing.sungd.uk   | 글 — 책·생각·기술                   | blog-writing         |
| resume.sungd.uk    | 이력서                              | resume               |
| today.sungd.uk     | Claude Code·Codex 릴리스 큐레이션   | ai-pick              |

`tech.sungd.uk` 는 없어졌다. 프로젝트 소개는 이 repo 에 그대로 남았고, 기술 글 12편은
writing 으로 옮겼다. 옛 주소는 `netlify.toml` 의 리다이렉트가 받는다 — tech 도메인을
이 Netlify 사이트에 함께 붙여야 동작한다.

재편 배경과 단계별 작업은 `docs/reorg/` 참고.
