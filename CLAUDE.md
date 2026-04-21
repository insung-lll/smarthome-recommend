# CLAUDE.md — Zibis Quiz 프로젝트 컨텍스트

## 이 프로젝트란?
지비스(zibismart.co.kr) 스마트홈 패키지 추천 퀴즈 페이지.
3개의 A/B 질문으로 방문자에게 베이직 / 스탠다드 / 프리미엄 패키지를 추천함.

## 기술 스택
- 단일 HTML 파일 (외부 의존성 없음)
- 폰트: Google Fonts — Noto Sans KR (한글), DM Serif Display (장식용)
- CSS: 인라인 `<style>` 태그
- JS: 인라인 `<script>` 태그, 바닐라 JS

## 주요 작업 히스토리
1. 3문항 A/B 퀴즈 구조 설계
2. 베이직 / 스탠다드 / 프리미엄 분기 로직 구현
3. 질문 전환 애니메이션 (qContent fade 방식)
4. 결과 카드에 패키지별 썸네일 이미지 (base64) 삽입
5. 모바일 반응형 최적화 (max-width: 520px)
6. 버그 수정: 백지 현상, 깜빡임 현상

## 현재 상태
- index.html 단일 파일로 완성
- 카페24 업로드 또는 GitHub Pages 배포 가능
- 프리미엄 패키지 링크 URL 확인 필요

## 수정 시 주의사항
- 이미지(icon)는 base64로 인코딩되어 JS 코드 안에 있음 — 직접 수정 시 base64 값 교체 필요
- selectAnswer() 함수의 애니메이션 타이밍을 건드리면 깜빡임 재발 가능
- showResult()에서 qContent 상태 초기화 코드 삭제하면 백지 버그 재발
