# 개인 홈페이지 — 시작 가이드

빌드 도구 없이 그냥 여는 순수 HTML/CSS 사이트입니다. GitHub Pages에 바로 올릴 수 있습니다.
(기존 academicpages/Jekyll 템플릿에서 Ruby/bundler 설치 문제로 막혔던 것을 대체하는 버전입니다.)

## 페이지 구성

| 파일 | 역할 |
|---|---|
| `index.html` | 홈 (히어로 + 소개 + 연구 요약 + 최근 글 + 논문 미리보기) |
| `research.html` | 연구 상세 (프로젝트별 설명) |
| `publications.html` | 논문 목록 — `data/publications.json`을 읽어서 자동 렌더링 |
| `cv.html` | CV — PDF 다운로드 링크 + 학력/경력/스킬/수상 |
| `news.html` | 연도별 News 로그 (발표/수상/미디어 등 시간순 기록) |
| `blog.html` + `posts/*.html` | 블로그 목록과 개별 글 |

## 1. 채워야 할 것들

- `index.html`, `cv.html`, `research.html`: 이름, 이메일, Google Scholar/GitHub 링크
- `data/publications.json`: 논문 정보 (title, authors, venue, year, type: "journal"|"conference", pdf/doi/code 링크)
- `files/cv.pdf`: 실제 CV PDF 파일을 이 경로에 두면 CV 페이지의 다운로드 버튼이 작동합니다
- `news.html`: 새 소식은 해당 연도의 `<ul class="news-list">` 맨 위에 `<li><span class="news-date">YYYY. M.</span> 내용</li>` 한 줄 추가. 연도가 바뀌면 `<div class="news-year-head">연도</div>`를 새로 추가
- 원하는 색/폰트는 `styles.css` 상단 `:root` 변수만 바꾸면 전체에 반영됩니다

## 기존 Jekyll(academicpages) 저장소에서 이전하는 경우

- `CNAME` 파일이 있다면 **그대로 유지**하세요 (커스텀 도메인 설정, 삭제하면 도메인 연결이 끊깁니다)
- `files/`, `images/` 폴더의 기존 자료(PDF, 사진)는 그대로 재사용 가능합니다
- `_config.yml`, `Gemfile`, `_layouts`, `_includes`, `_sass` 등 Jekyll 전용 파일/폴더는
  더 이상 필요 없으니 삭제해도 됩니다 (헷갈림 방지 차원에서 삭제 권장)
- `_posts`에 있던 마크다운 글들은 `posts/` 폴더의 HTML 템플릿 형식으로 옮겨 담으면 됩니다

## publications.json이 로컬에서 안 보일 때

`publications.html`을 더블클릭해서 `file://`로 열면 브라우저 보안 정책 때문에
JSON을 못 불러올 수 있습니다. 로컬 확인 시:

```bash
cd personal-site
python -m http.server 8000
# 브라우저에서 http://localhost:8000 접속
```

GitHub Pages에 배포된 이후에는 이 문제가 없습니다 (정상 https 서빙이라서).

## 2. GitHub Pages로 배포하기

```bash
# 1) GitHub에 새 저장소 생성 (예: yourname.github.io — 이 이름이면 바로 루트 도메인으로 배포됨)
git init
git add .
git commit -m "Initial site"
git remote add origin https://github.com/<username>/<username>.github.io.git
git push -u origin main
```

그 다음 저장소 Settings → Pages → Source를 `main` 브랜치로 설정하면
`https://<username>.github.io` 에서 바로 볼 수 있습니다.

## 3. 새 블로그 글 추가하는 워크플로우

1. Claude에서 논문/텍스트북 챕터를 올리고 "정리해줘" 요청
   → `paper-summarizer` 또는 `textbook-study` 스킬이 자동으로 `_blog.md` 생성
2. 그 내용을 `posts/새글이름.html`로 변환 요청
   ("이 블로그 마크다운을 posts 템플릿 형식으로 HTML 만들어줘, brain-networks-intro.html 참고해서")
3. `blog.html`과 `index.html`의 "최근 글" 섹션에 링크 한 줄 추가 (nav는 이미 모든 페이지에 동일하게 연결돼 있어 따로 손댈 필요 없음)
4. `git add . && git commit -m "new post" && git push`

## 4. 나중에 업그레이드하고 싶다면

지금은 빌드 도구 없는 순수 정적 사이트라 가장 마찰 없이 시작하기 좋습니다.
나중에 코드 실행이 포함된 포스트(Python/MATLAB 결과 임베드)나 논문 목록 자동
생성이 필요해지면 **Quarto**로 옮기는 걸 고려해보세요 — 지금 만든 콘텐츠는
그대로 재사용 가능합니다.
