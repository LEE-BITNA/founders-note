# 대표의 기록 — 운영 가이드

> 정영일 대표님의 기록 아카이브 사이트 운영자를 위한 문서입니다.

---

## 🚀 처음 배포하기 (GitHub Pages)

GitHub 계정이 이미 있다면 이 순서대로 하시면 웹사이트가 뜹니다. (총 5-10분)

### 1. 새 저장소 만들기
1. [github.com](https://github.com) 로그인
2. 우측 상단 `+` → `New repository` 클릭
3. 입력:
   - **Repository name**: `founders-note` (원하는 이름 가능)
   - **Public** 선택 ⭐ (Private이면 GitHub Pages 무료 호스팅 불가)
   - `Add a README file` 체크 해제
4. `Create repository`

### 2. 파일 업로드
1. 방금 만든 저장소에서 `uploading an existing file` 링크 클릭
2. 이 폴더 안의 파일 **전부** (`index.html`, `post.html`, `README.md`, `assets/`, `posts/`) 드래그앤드롭
3. 스크롤 내려서 `Commit changes`

### 3. GitHub Pages 켜기
1. 저장소 상단 `Settings` → 왼쪽 메뉴 `Pages`
2. Source: `Deploy from a branch`
3. Branch: `main` / Folder: `/ (root)` → `Save`
4. **1-2분 기다리기** (페이지 새로고침하면 상단에 주소가 뜹니다)
5. 주소 예시: `https://[본인계정명].github.io/founders-note/`

그 주소가 바로 공개된 사이트입니다. 즐겨찾기에 추가하세요.

---

## ✍️ 새 글 올리기

### 1. 본문 파일 만들기

GitHub 저장소의 `posts/` 폴더 → `Add file` → `Create new file`

파일명: `YYYY-MM-DD-영문슬러그.md`
예: `2026-05-01-vietnam-first-partnership.md`

내용 예시 (마크다운 문법):
```markdown
창업 초기, 한 평짜리 가게에서 시작했을 때 우리는 한 가지 약속을 했다.

## 큰 제목

본문 글을 이어 씁니다.

> 인용구는 이렇게.

**굵은 글씨**, *기울임*.
```

`Commit new file` 클릭.

### 2. posts.json에 정보 추가

`posts/posts.json` 파일 → 연필 아이콘(편집) → 맨 앞에 새 항목 추가:

```json
[
  {
    "slug": "vietnam-first-partnership",
    "title": "베트남 하노이, 첫 파트너십의 기억",
    "excerpt": "현지 파트너와의 신뢰를 쌓기까지 걸린 3년의 시간.",
    "date": "2026-05-01",
    "author": "정영일",
    "categories": ["global", "behind"],
    "tags": ["베트남", "하노이", "파트너십"],
    "image": "",
    "file": "2026-05-01-vietnam-first-partnership.md"
  },
  {
    "slug": "sharing-ten-percent",
    ...
```

`Commit changes` 클릭 → 1분 후 사이트에 반영됩니다.

### 카테고리 종류

| 값 (영문) | 표시 이름 |
|---|---|
| `philosophy` | 경영 철학 |
| `behind` | 사업 비하인드 |
| `foundation` | 이랜드재단 |
| `welfare` | 이랜드복지재단 |
| `global` | 글로벌 |
| `insight` | 인사이트 |

한 글에 여러 카테고리 가능: `"categories": ["behind", "welfare"]`

---

## 🎨 디자인 직접 수정하기

**디자인 관련 설정은 한 곳에 모아뒀습니다.** `assets/style.css` 파일을 열면 맨 위에 이런 섹션이 있습니다:

```css
:root {
  /* ───── 폰트 ───── */
  --font-serif: 'Noto Serif KR', 'Times New Roman', serif;
  --font-sans: 'Pretendard', -apple-system, BlinkMacSystemFont, sans-serif;

  /* ───── 색상 ───── */
  --color-accent: #1a7a6e;   /* 포인트 컬러 */
  --color-ink: #111111;       /* 가장 진한 글자 */
  --color-text: #2a2a2a;      /* 본문 글자 */
  --color-bg: #fafaf7;        /* 페이지 배경 */
  ...

  /* ───── 글씨 크기 ───── */
  --size-h1-hero: 44px;      /* 메인 페이지 대문 제목 */
  --size-h1-post: 38px;      /* 글 상세 페이지 제목 */
  --size-body: 16.5px;       /* 본문 글자 */
  ...
}
```

이 값만 바꾸면 사이트 전체가 반영됩니다.

### 자주 조정하실 만한 것들

**포인트 컬러 바꾸기** — `--color-accent` 값 수정
- 녹색 → `#1a7a6e` (현재)
- 네이비 → `#1a3a7a`
- 와인 → `#7a1a3a`
- 검정 포인트로 단조롭게 → `#111111`

**폰트 바꾸기** — `--font-serif` 값 수정
- 현재: `'Noto Serif KR'`
- 바꿀 수 있는 것들: `'Nanum Myeongjo'`, `'Gowun Batang'`, `'Song Myung'`
  (이 경우 HTML 파일 상단 Google Fonts 링크도 바꿔야 함 — 말씀주시면 도와드립니다)

**글씨 크게 / 작게** — 각 `--size-*` 숫자를 크게/작게

**배경 바꾸기** — `--color-bg` 수정
- 현재는 따뜻한 오프화이트(`#fafaf7`)
- 완전 흰색 → `#ffffff`
- 차가운 회색 → `#f5f5f7`

저장하고 GitHub에 `Commit` 하면 1분 뒤 반영됩니다.

---

## 🖼️ 이미지 추가

### 대표 이미지 (썸네일)
1. GitHub에서 `assets/` 아래 `images/` 폴더를 만들고 이미지 업로드
2. `posts.json`의 `image` 필드에 경로 입력:
   ```json
   "image": "assets/images/vietnam-2026.jpg"
   ```

### 글 본문 안 이미지
마크다운에:
```markdown
![설명](../assets/images/파일명.jpg)
```

💡 **이미지 크기 권장**: 가로 1200px 이하, 300KB 이하. [tinypng.com](https://tinypng.com)에서 무료 압축.

---

## 🔗 기존 CSR 사이트와 연결

CSR 사이트 운영 업체에 요청:

> "커뮤니티 메뉴 맨 위에 '대표의 기록' 항목을 추가해주세요.
> 링크: `https://[본인계정명].github.io/founders-note/`"

나중에 자체 도메인(`founders.elandcsr.or.kr` 등)으로 바꾸실 수도 있습니다.

---

## ❓ 자주 하는 질문

**Q. 글을 수정하려면?**
A. GitHub에서 해당 `.md` 파일 열고 연필 아이콘 → 수정 → `Commit changes`

**Q. 글을 삭제하려면?**
A. `posts.json`에서 해당 항목 블록만 지우면 목록에서 사라집니다.

**Q. 쓰는 도중 JSON 문법 틀려서 사이트가 안 뜨면?**
A. 당황하지 마시고 `posts.json`에서 직전 편집만 되돌리면 됩니다. GitHub는 모든 변경 이력을 저장하거든요 (`History`에서 이전 버전 복원 가능).

**Q. 나만 글쓰게 하려면?**
A. 저장소 `Settings → Collaborators` 에서 본인만 있으면 됩니다. 다른 사람은 파일을 편집할 수 없습니다.

---

## 📞 도움이 필요할 때

이 파일은 비개발자를 위해 작성됐지만, 막히시면:
1. Claude 같은 AI에게 이 폴더를 통째로 보내고 "뭘 어떻게 해야 해?" 라고 물어보세요
2. 또는 웹 개발자에게 이 README를 함께 전달

구조가 단순해서 누구든 쉽게 작업할 수 있습니다.
