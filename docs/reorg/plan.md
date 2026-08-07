# sungd.uk 사이트 재편

## 목표

사이트가 넷인데 서로 관계가 안 보이고, 루트 주소(sungd.uk)를 에세이 블로그가 쓰고 있어 나머지가 형제인지 자식인지 애매하다. tech 는 넉 달째 멈춰 있다. 루트를 "나"로 되찾고 멈춘 사이트를 해체해 관리 대상을 줄인다.

## 최종 모양

```
sungd.uk          나 — 소개 + 프로젝트 14개   (newhigen.github.io repo 개조, Netlify)
├── resume.       이력서                      (그대로)
├── writing.      글 — 책·생각·기술            (blog-writing 이사)
└── today.        Claude Code·Codex 큐레이션   (ai-pick, ai. 에서 개명)
```

tech. 는 없어진다. 콘텐츠는 둘로 나뉜다.

- 프로젝트 소개 14개 → 루트에 남는다 (repo 를 그대로 쓰므로 이동 없음)
- 기술 글 12편 → writing 으로 옮기고 "기술" 카테고리를 만든다

## 단계

각 단계에 끝났는지 확인할 방법을 같이 적는다. 1 과 2 는 서로 독립이라 순서를 바꿔도 된다. 3 은 1·2 가 끝난 뒤.

### 1. 루트 사이트 만들기 (newhigen.github.io repo)

- [ ] 기술 글 12편(`src/content/blog/`)을 blog-writing 으로 옮기고 여기선 지운다
- [ ] blog 컬렉션 흔적 정리 — `src/content.config.ts`, 홈·목록 페이지에서 blog 참조 제거
- [ ] 홈을 소개 + 프로젝트 + 다른 사이트 링크 구조로 다시 쓴다
- [ ] GitHub Pages → Netlify (`netlify.toml` 추가, `.github/workflows/deploy.yml` 제거)
- [ ] `public/CNAME` 을 `sungd.uk` 로

검증: 로컬 빌드에 blog 관련 에러·깨진 링크가 없고, 홈에서 세 사이트로 다 넘어간다.

### 2. writing 이사 (blog-writing repo)

- [ ] "기술" 카테고리 추가하고 1단계에서 넘어온 글 12편을 붙인다
- [ ] Netlify 커스텀 도메인을 `writing.sungd.uk` 로 변경

검증: 기존 글 67편 + 기술 글 12편이 다 뜨고, 카테고리 필터가 셋 다 동작한다.

### 3. 리다이렉트 (옛 링크 살리기)

- [ ] 루트 `netlify.toml`: `/posts/* → https://writing.sungd.uk/posts/:splat` 301
- [ ] tech.sungd.uk 처리 — 지금은 GitHub Pages 라 301 을 못 건다. repo 가 루트로 바뀌면 tech DNS 는 갈 곳이 없어지므로, tech 도 같은 Netlify 사이트에 붙이고 거기서 301 을 건다
  - `/projects/* → https://sungd.uk/projects/:splat`
  - `/blog/* → https://writing.sungd.uk/...`

검증: 옛 주소 몇 개를 직접 열어 새 주소로 넘어가는지 본다.

### 4. today 개명 (ai-pick repo)

- [ ] `CNAME` → `today.sungd.uk`
- [ ] `sitemap.xml`·`robots.txt`·README 의 ai.sungd.uk 문자열 교체
- [ ] ai.sungd.uk → today.sungd.uk 301
- [ ] README 의 죽은 링크 수정 — `tech.sungd.uk/projects/claude-code-tracking` 이 루트로 옮겨간다

검증: today 로 열리고, ai 로 들어가도 넘어온다.

## 보류

- calc-tools — 도메인 안 붙임. 나중에 붙인다면 tools. 아래로 묶는 안이 있다.
- newhigen.github.io repo 이름 — Netlify 로 가면 GitHub Pages 용 이름일 이유가 없다. 급하지 않다.
