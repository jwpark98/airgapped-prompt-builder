# AirGap PromptForge v4.1 - 오프라인 웹 앱 프롬프트 생성기

■ 개요
  망분리(Air-Gapped) 환경에서 외부 라이브러리(CDN) 없이 단일 HTML 파일로
  동작하는 웹 앱을 AI에게 생성시키기 위한 프롬프트 생성 도구입니다.

■ 주요 기능

  1) 자동 트리거링
     - 앱 이름/목적/핵심기능 입력 시 키워드 기반 자동 체크
     - DB 사용: '데이터베이스', '저장', '기록', '센서' 등
     - 로그인: '로그인', '인증', '권한', '사용자' 등
     - 보고 기능: '보고서'→인쇄, '슬라이드'→슬라이드쇼,
       'docx'→DOCX, 'pdf'→PDF, '클립보드'→클립보드 (개별 자동 체크)
     - 파트 분할: 텍스트 길이 + 복잡도 점수 기반 자동 추천 (Google AI Mode만)
     - 수동 변경 시 MANUAL 라벨 표시, 자동값 복원 시 AUTO 복구

  2) DB 영속성
     - 서버 API(GET/POST /api/db) 기반 JSON 파일 저장
     - localStorage 미사용 (UI 설정만 localStorage 사용)
     - DB 파일 위치: {폴더명}_db/{앱이름}.json (서버 자동 생성)
     - 한글 파일명 정상 지원 (encodeURIComponent/decodeURIComponent)
     - 8MB 도달 시 노란 경고 배너, 10MB 시 빨간 경고 + 수동 삭제 유도
     - 백업 시 JSON 파일 다운로드

  3) 히스토리
     - 좌측 최하단에 이전 프롬프트 이력 저장/검색/재활용
     - 동일 앱 이름+목적 중복 저장 방지 (최신 것만 유지)
     - 최대 100개 이력 보관

  4) 로그인/보고 기능
     - 로그인 화면: 기본 admin/admin
     - 로그인 후 우상단 [관리자] 버튼 (admin 역할만 표시)
     - 관리자 버튼 → 사용자 등록/권한 설정 모달
     - 역할: admin(전체), group_admin(자신 데이터 CRUD), user(읽기 전용)
     - 사용자 데이터도 서버 DB JSON 파일에 저장
     - 보고 기능 5종: 인쇄, 슬라이드쇼, DOCX, PDF, 클립보드

  5) AI 모델별 파트 분할
     - 상용AI(Claude/ChatGPT/Gemini/Grok): 1파트 단일 출력
     - Google AI Mode: 핵심기능 복잡도에 따라 자동 파트분할(1~5)
     - 파트 분할 시 프롬프트에 각 파트별 출력 범위 명시

  6) 슬라이드쇼
     - 앱 데이터를 프리젠테이션 슬라이드 HTML로 변환
     - 전체화면, 다크 배경, 섹션별 슬라이드 자동 생성
     - 하단 네비게이션 바: ◀ ▶ 화살표, 페이지 인디케이터
     - 키보드(←→, Space), 마우스 클릭, 화살표 버튼으로 페이지 이동
     - 슬라이드 전환 애니메이션 (fade 0.3s)

  7) 언어/로그인 기본값
     - 언어: 한국어 (고정, 변경 불가)
     - 로그인: 체크해제 (기본)
     - AI 모델: Google AI Mode (기본)

■ 기술 스택
  - Vanilla JS only (React/Babel/Tailwind 없음)
  - 외부 라이브러리 없음 (CDN 사용 금지)
  - 단일 HTML 파일로 완전 오프라인 동작
  - Python 3 내장 HTTP 서버 (port 5204)

■ 실행 방법
  $ 서버에서 구동 또는 다운로드 후 로컬에서 실행 후 사용 가능

■ 서버 API
  GET  /api/db?app={폴더}/{파일명}     → JSON 데이터 조회 (없으면 {})
  POST /api/db  {app, data}            → JSON 데이터 저장
  → DB 파일: {폴더}/{파일명}.json 으로 자동 생성

■ 라이선스
  MIT License

---------------- ENGLISH -------------------

## ⚡ AirGap PromptForge
An ultra-lightweight, offline-first prompt generator engineered to force Large Language Models (LLMs) to build complete, production-ready web applications in strict air-gapped environments.

## 🌟 The Problem & The Impact
When prompting AIs to build complex web apps, developers face two major bottlenecks:
Token Truncation: The AI stops generating mid-script due to output limits, breaking the codebase and requiring tedious manual stitching.
Dependency Hell in Secure Nets: AI defaults to using React, Tailwind, and external CDNs. These are entirely useless in secure, air-gapped enterprise networks (e.g., defense, heavy industry, finance) with no internet access.
The Effect (Why it matters): AirGap PromptForge completely eliminates these issues. It dynamically calculates code complexity and forces the AI to output the architecture in strategic, byte-sized chunks (P1, P2, P3...). It strictly enforces Vanilla JS, inline CSS, and inline SVGs, ensuring the AI generates a standalone, single-file HTML application that runs flawlessly offline without a single external web request.

## ✨ Core Features
Air-Gapped Ready (Zero Dependencies): Generates prompts that strictly forbid external CDNs. 100% offline fallback using system fonts and inline assets.
Smart Token-Bypass (Auto-Chunking): Real-time text analysis automatically recommends the safest output split (1 to 5 parts) to bypass LLM token cutoff limits.
Dynamic Context Inference: Auto-detects if your app needs time-series data tracking, version control, or simple overwrites based on semantic keyword analysis in your requirements.
Multi-LLM Optimized: Contains pre-engineered system instructions uniquely tailored for Claude, ChatGPT, Gemini, Grok, and Google AI Mode.
Local History Engine: Automatically saves your configurations locally using localStorage (Max 100 entries) with instant search capabilities.
Native I18n: Built-in UI support for English, Korean, Japanese, Chinese, German, and French.

## 🚀 How to Use
Define Requirements: Enter your app's name, purpose, and detailed core logic (numbered lists work best).
Configure Architecture: Select UI theme (Dark/Light/Industrial), layout options, and Data I/O requirements (JSON, CSV, API sync).
Generate & Copy: Click Copy to Clipboard.
Feed the LLM: Paste the prompt into your AI of choice.
Sequential Retrieval: After the AI generates "Part 1" and pauses, type "Next" or "Continue" to fetch the remaining parts.
Merge & Run: Combine all generated code blocks (````html) sequentially into a single .html` file and run it offline.

## 🛠 Tech Stack
100% Vanilla HTML / CSS / JS
No Build Step
No Webpack / Vite
No External Libraries
