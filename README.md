# resume.sungd.uk

이력서와 만든 것들(Projects). Astro 정적 사이트, GitHub Pages 배포.

```sh
npm install
npm run dev
```

## 구성

```
public/index.html      이력서 (한국어) — 손으로 관리, 빌드에 안 태운다
public/en/index.html   이력서 (영문)
public/style.css       이력서 전용 스타일
public/script.js       재직 기간 자동 계산 + 사이드바 현재 섹션 표시
src/content/projects/  프로젝트 14개 (마크다운)
src/pages/projects/    프로젝트 목록·상세
```

이력서 두 쪽은 **같은 구조·같은 클래스**를 쓴다. 한쪽 내용을 고치면 다른 쪽도 같이 고칠 것.
경력 기간은 `data-from` / `data-to` 속성만 넣으면 오늘 날짜 기준으로 자동 계산된다.

## 옛 주소

이 사이트는 `tech.sungd.uk` 였다. 2026-08-09 재편 때 기술 글 12편은 글 블로그로 보내고
프로젝트만 남긴 뒤, 이력서를 첫 쪽으로 들여왔다. 옛 주소를 넘기는 리다이렉트는 걸지 않았다.

재편 배경과 결정 과정은 `docs/reorg/` 참고.

다른 사이트는 [sungd.uk](https://sungd.uk) 에서 찾을 수 있다.
