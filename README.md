# Zibis Smart Home — 패키지 추천 퀴즈

## 프로젝트 개요
지비스 스마트홈 패키지(베이직 / 스탠다드 / 프리미엄) 중 방문자에게 맞는 패키지를 추천해주는 인터랙티브 퀴즈 페이지

## 파일 구조
```
zibis-project/
└── index.html   # CSS + JS 모두 포함된 단일 파일
```

## 주요 구성 (index.html 내부)

### 1. 질문 데이터 — `questions` 배열 (JS)
```js
const questions = [
  { text: "질문 텍스트", options: [{ label: "A", text: "...", value: "A" }, ...] },
  ...
]
```
- 총 3개 질문, 각 질문마다 A/B 2지선다

### 2. 패키지 데이터 — `packages` 객체 (JS)
```js
const packages = {
  basic:    { name, icon(base64이미지), desc, price, features[], link },
  standard: { ... },
  premium:  { ... }
}
```
- `icon` 필드: base64 인코딩된 PNG 이미지 (각 패키지 썸네일)
- `link` 필드: 각 패키지 상세 페이지 URL

### 3. 분기 로직 — `logic` 객체 (JS)
```js
const logic = {
  "AAA": "basic",
  "AAB": "standard",
  "ABA": "standard",
  "ABB": "premium",
  "BAA": "standard",
  "BAB": "premium",
  "BBA": "standard",
  "BBB": "premium"
}
```
- 3개 질문의 답(A/B)을 조합한 8가지 경우의 수로 패키지 결정

### 4. 디자인 토큰 — `:root` CSS 변수
```css
--cream: #F7F4EF       /* 배경 */
--warm-white: #FDFCFA  /* 카드 배경 */
--sand: #E8E0D4        /* 보조 선 */
--taupe: #C4B8A8       /* 흐린 텍스트 */
--brown: #8B7355       /* 보조 텍스트 */
--dark: #2C2416        /* 주 텍스트 */
--accent: #4A6741      /* 포인트 컬러 (그린) */
```

### 5. 주요 함수 (JS)
| 함수 | 역할 |
|------|------|
| `renderQuestion()` | 현재 질문 카드 렌더링 |
| `selectAnswer(value)` | 답 선택 처리 + 전환 애니메이션 |
| `showResult()` | 결과 카드 표시 |
| `resetQuiz()` | 처음으로 돌아가기 |

## 카페24 적용 방법
1. `index.html`을 `zibis-quiz.html`로 이름 변경
2. 카페24 관리자 → 디자인 → FTP → 파일 업로드
3. 접근 URL: `https://zibismart.co.kr/zibis-quiz.html`

## 수정 가이드

### 질문 변경
`questions` 배열에서 `text`, `options[].text` 수정

### 패키지 링크 변경
`packages.premium.link` 등 각 패키지의 `link` 값 수정
현재 프리미엄 링크: `https://zibismart.co.kr/package/premium.html` (미확인, 실제 URL로 교체 필요)

### 이미지 교체
패키지 썸네일 이미지를 교체하려면:
```bash
base64 -w 0 새이미지.png
```
출력값을 `packages.basic.icon` 등의 값으로 교체

### 색상 변경
`:root` CSS 변수에서 `--accent` 등 수정

## Claude Code에서 이어서 작업하기
```bash
# 프로젝트 폴더로 이동
cd zibis-project

# 브라우저로 미리보기
open index.html
```

Claude Code에 이 README와 index.html을 열고 아래처럼 요청하세요:
> "index.html 기반으로 [원하는 수정사항]을 적용해줘"
