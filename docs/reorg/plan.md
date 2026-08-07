# sungd.uk 사이트 재편

## 목표

사이트가 넷인데 서로 관계가 안 보이고, 루트 주소(sungd.uk)를 에세이 블로그가 쓰고 있어 나머지가 형제인지 자식인지 애매하다. tech 는 넉 달째 멈춰 있다. 루트를 "나"로 되찾고 멈춘 사이트를 해체해 관리 대상을 줄인다.

## 최종 모양

```
sungd.uk          나 — 소개 + 프로젝트 14개   (newhigen.github.io repo, Netlify)
├── resume.       이력서                      (그대로)
├── writing.      글 — 책·생각·기술            (blog-writing)
└── today.        Claude Code·Codex 큐레이션   (ai-pick, ai. 에서 개명)
```

tech. 는 없어졌다. 프로젝트 소개 14개는 루트에 남고, 기술 글 12편은 writing 으로 갔다.

## 코드 작업 — 끝남

세 repo 모두 브랜치에 커밋했다. **아직 push 안 됨** (아래 "남은 일" 참고).

| repo               | 브랜치           | 한 일                                                            |
| ------------------ | ---------------- | ---------------------------------------------------------------- |
| newhigen.github.io | `worktree-reorg-plan` | blog 걷어내고 루트 사이트로 개조, Netlify 설정·리다이렉트 표      |
| blog-writing       | `reorg-writing`  | 기술 글 12편 흡수, 기술 카테고리 추가, 도메인 표기 변경           |
| ai-pick            | `reorg-today`    | CNAME·sitemap·robots·README 를 today.sungd.uk 로                  |

검증한 것: 두 Astro 사이트 모두 빌드 통과. writing 은 글 79편이 다 생성되고 옮겨온 12편의 주소가 예전 그대로(`/claude-code-tips/` 등). 루트는 18쪽이 나오고 내부 링크에 깨진 곳이 없다.

## 남은 일 — 사람이 해야 하는 것

코드로는 못 하는 부분이다. **순서대로** 해야 도메인이 겹치지 않는다.

### 1. 브랜치 합치기

이 세션의 SSH 키가 회사 계정이라 개인 repo 에 push 를 못 했다. 로컬에서 합치고 올리면 된다.

```sh
cd ~/dev/sites/newhigen.github.io && git merge worktree-reorg-plan && git push
cd ~/dev/sites/blog-writing      && git merge reorg-writing      && git push
cd ~/dev/sites/ai-pick           && git merge reorg-today        && git push
```

### 2. GitHub Pages 끄기

- `newhigen.github.io` — Settings → Pages 에서 배포 끄기. 배포 워크플로는 지웠지만 Pages 설정이 살아 있으면 tech.sungd.uk 를 계속 잡고 있어 Netlify 에 못 붙인다.
- `ai-pick` — Pages 는 유지. 커스텀 도메인만 `today.sungd.uk` 로 바꾼다. (CNAME 파일은 이미 바뀌어 있으니 push 후 자동 반영될 수도 있다. Settings 에서 확인.)

### 3. Netlify

- **새 사이트**: `newhigen.github.io` repo 연결. 빌드 설정은 `netlify.toml` 이 갖고 있다. 커스텀 도메인으로 `sungd.uk`(대표), `tech.sungd.uk`, `ai.sungd.uk` 셋 다 붙인다 — 뒤의 둘은 옛 주소를 넘겨주기 위한 것이라 꼭 붙여야 리다이렉트가 산다.
- **기존 blog-writing 사이트**: 커스텀 도메인을 `sungd.uk` → `writing.sungd.uk` 로 바꾼다.

⚠ sungd.uk 를 blog-writing 사이트에서 떼어낸 뒤에 새 사이트에 붙여야 한다. 동시에 두 사이트가 같은 도메인을 가질 수 없다.

### 4. DNS

```
sungd.uk          → 새 Netlify 사이트 (루트)
writing.sungd.uk  → 기존 blog-writing Netlify 사이트
tech.sungd.uk     → 새 Netlify 사이트 (리다이렉트 전용)
ai.sungd.uk       → 새 Netlify 사이트 (리다이렉트 전용)
today.sungd.uk    → GitHub Pages (newhigen.github.io)
resume.sungd.uk   → 그대로
```

### 5. 확인

옛 주소 몇 개를 직접 열어본다.

- `sungd.uk/the-go-giver-1/` → writing 으로 넘어가야 한다
- `tech.sungd.uk/claude-code-tips` → writing 의 같은 글로
- `tech.sungd.uk/projects/claude-watch` → sungd.uk 의 같은 쪽으로
- `ai.sungd.uk` → today 로

## 보류

- calc-tools — 도메인 안 붙임. 나중에 붙인다면 tools. 아래로 묶는 안이 있다.
- newhigen.github.io repo 이름 — Netlify 로 가면 GitHub Pages 용 이름일 이유가 없다. `package.json` 의 이름은 아직 `blog-tech` 다. 급하지 않다.
- Google Analytics 태그는 tech 시절 것을 그대로 쓴다. 새 사이트로 성격이 바뀌었으니 나중에 볼 것.
