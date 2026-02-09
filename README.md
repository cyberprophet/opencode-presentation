---
marp: true
theme: uncover
paginate: true
---

<style>
@import url('https://fonts.googleapis.com/css2?family=Noto+Sans+KR:wght@400;700&display=swap');

:root {
  --font-family: 'Noto Sans KR', sans-serif;
  --color-background: #1a1a2e;
  --color-foreground: #eee;
}

section {
  font-family: var(--font-family);
  background-color: var(--color-background);
  color: var(--color-foreground);
}

h1, h2, h3 {
  font-family: var(--font-family);
}

code {
  font-family: 'Fira Code', monospace;
}
</style>

<!--
================================================================================
스크린샷 캡처 체크리스트 (발표자용)
================================================================================

TODO: OpenCode TUI 실행 화면 캡처 - 터미널에서 `opencode` 명령어 실행 후 메인 화면
TODO: OhMyOpenCode 멀티 에이전트 실행 화면 - 여러 에이전트가 동시에 작업하는 모습
TODO: diff-to-commit VS Code Marketplace 페이지 스크린샷
TODO: flutter_device_unique_id pub.dev 페이지 스크린샷 (flutter_device_platform_id)
TODO: 발표자의 실제 터미널 화면 - opencode 명령어 입력 중인 모습
TODO: 프로젝트 GitHub 리포지토리 메인 페이지 스크린샷

================================================================================
-->

# OpenCode + OhMyOpenCode 실전 활용기

**바이브 코딩 랩 발표**

<!--
- [~0.5분] 인사 및 발표 주제 소개
- 본인 소개 (발표자)
- 발표 개요: OpenCode 발견 → OhMyOpenCode 활용 → 실제 산출물
- 청중에게 기대: "여러분도 이렇게 쓸 수 있습니다"
-->

---

## 바이브 코딩, 왜 관심 없었나

- "AI가 코드를 짠다고?" - 회의적이었음
- 기존 툴 결과물이 마음에 안 들었음
- 품질과 내 의도가 잘 맞지 않았음

<!--
- [~1분] 솔직한 고백으로 시작
- 기존 바이브 코딩 툴의 한계 2-3가지 언급
- "결과물이 제 마음에 안 들었어요"
- Claude 사용자들과 공감대 형성
- 전환점: "그런데 OpenCode를 만나고..."
-->

---

## OpenCode를 만나다

- 오픈소스 터미널 기반 AI 코딩 에이전트
- 75+ LLM 프로바이더 지원 (Anthropic, OpenAI, Ollama)
- VS Code처럼 TUI로 작업 가능

<!--
- [~1.5분] OpenCode 소개 (What + Why)
- 오픈소스: 커스터마이징 가능, 락인 없음
- 75+ 프로바이더: Anthropic, OpenAI, Ollama, Copilot 등
- TUI: 터미널에서 직접 작업, 빠른 피드백
- "Claude Code 대안으로 딱!"
-->

---

## OpenCode 핵심 특징

- 🖥️ 터미널 기반 TUI (Bubble Tea)
- 💾 세션 관리 (SQLite) - 작업 이어하기
- 🔧 LSP 통합, Bash 실행
- 🔓 프로바이더 자유 (구독 그대로 사용)

<!--
- [~1.5분] 핵심 기능 4가지 소개
- TUI: 마우스 없이 키보드로 빠른 작업
- 세션: 이어서 작업 가능
- LSP: 코드 품질 자동 검증
- 프로바이더: 기존 구독 그대로 사용
-->

---

## OhMyOpenCode: 한 단계 더

- OpenCode 위의 오케스트레이션 레이어
- 멀티 에이전트 병렬 실행
- 복잡한 빌드 파이프라인 자동 이해

<!--
- [~1.5분] OhMyOpenCode 소개
- "OpenCode에 날개를 달아주는 플러그인"
- 멀티 에이전트: 한 번에 여러 작업 수행
- 오케스트레이션: 계획→실행→검증 자동화
- 결과: 더 빠르고, 더 나은 코드
-->

---

## 신화 속 에이전트들

- 🎯 Prometheus: 기획 및 아키텍처 설계
- 🏋️ Sisyphus: 코드 실행 및 반복 작업
- 🔍 Explorer: 탐색 및 리서치
- 🛡️ Guardian: 검증 및 보안

<!--
- [~1분] 그리스 신화 캐릭터 소개
- Prometheus: "불을 가져온 자" → 아이디어와 계획
- Sisyphus: 끈질긴 실행자 → 코딩과 반복 작업
- Explorer: 탐험가 → 코드베이스 탐색
- Guardian: 수호자 → 품질 검증
- "재미있는 네이밍이지만 실제로 잘 어울려요"
-->

---

## 멀티 에이전트가 일하는 방식

```
계획(Prometheus) → 실행(Sisyphus) → 검증(Guardian)
     ↓                    ↓                    ↓
  아키텍처           코드 작성          테스트/리뷰
```

<!--
- [~1.5분] 병렬 실행 플로우 설명
- Prometheus가 전체 계획 수립
- 여러 Sisyphus 에이전트가 병렬로 작업
- Guardian이 결과물 검증
- Explorer가 필요한 정보 수집
- "마치 개발팀이 일하는 것처럼"
-->

---

## 🎬 데모 타임

▶️ 90초 녹화 영상 재생
"OpenCode + OhMyOpenCode로 간단한 유틸리티 함수 구현"

<!--
- [~1.5분] 데모 영상 재생
- 90초 녹화 영상을 재생합니다
- 시나리오: 배열 중복 제거 함수 구현
- 보여주는 것:
  * OpenCode TUI 실행
  * 프롬프트 입력
  * 멀티 에이전트 병렬 작업
  * 결과물 생성 및 테스트 통과
  * diff-to-commit으로 커밋 메시지 생성
- 발표자는 각 단계를 간단히 설명하며 진행
-->

---

## 산출물: diff-to-commit

- VS Code 확장: AI가 git diff로 커밋 메시지 작성
- Conventional Commit 포맷 자동 생성
- GitHub Copilot / API Key 지원

<!--
- [~1.5분] 첫 번째 딥다이브 프로젝트
- VS Code Marketplace에 배포됨 (Dayond.diff-to-commit)
- 기능: git diff → AI 분석 → 커밋 메시지 자동 생성
- 보안: API 키 등 시크릿 자동 마스킹
- "이 확장도 OpenCode로 개발했습니다"
-->

---

## 산출물: flutter_device_unique_id

- 5개 플랫폼 지원 (Android, iOS, macOS, Windows, Web)
- Keychain/Registry/localStorage 활용
- pub.dev: flutter_device_platform_id (4⭐)

<!--
- [~1.5분] 두 번째 딥다이브 프로젝트
- 크로스 플랫폼 디바이스 ID 플러그인
- 각 플랫폼별 네이티브 구현 (Swift, Kotlin, C++, JS)
- pub.dev에 배포, 4 stars, 3 forks
- "복잡한 네이티브 코드도 바이브 코딩으로"
-->

---

## 그 외 산출물들

| 프로젝트 | 설명 | 배포 |
|---------|------|------|
| flutter_image_conversion | HEIC → JPEG 변환 | pub.dev |
| flutter_native_image_compress | 네이티브 이미지 압축 | pub.dev |

<!--
- [~1분] 나머지 프로젝트 간단히 소개
- flutter_image_conversion: iOS/macOS/Web 지원
- flutter_native_image_compress: WebP/JPEG/PNG 포맷
- 두 프로젝트 모두 pub.dev에 배포 완료
- "총 4개 프로젝트, 모두 OpenCode로 개발"
-->

---

## 왜 결과물이 다른가

- 멀티 에이전트의 병렬 처리
- 자동 검증 및 테스트
- 프로바이더 자유로운 선택
- **결과: 만족스러운 코드 품질**

<!--
- [~1.5분] 다른 툴 대비 차이점
- 병렬 처리: 동시에 여러 작업 → 더 빠른 결과
- 자동 검증: 코드 오류 미리 잡아줌
- 프로바이더: 내가 원하는 AI 모델 사용
- 핵심: "결과물의 품질이 다릅니다"
- 개인 경험 기반으로 진정성 있게 설명
-->

---

## 시작하기

```bash
# 1. OpenCode 설치
curl -fsSL https://opencode.ai/install | bash

# 2. OhMyOpenCode 설치
bunx oh-my-opencode install

# 3. 첫 실행
opencode
```

<!--
- [~1분] 실제 설치 및 시작 방법
- 한 줄 설치 (curl)
- OhMyOpenCode 플러그인 설치
- 터미널에서 `opencode` 실행
- "지금 바로 시작할 수 있습니다"
- GitHub: github.com/opencode-ai/opencode
-->

---

## 감사합니다 / Q&A

**질문 있으신가요?**

🐙 github.com/cyberprophet

<!--
- [~0.5분] 마무리
- 감사 인사
- 질문 받기
- 연락처 및 리소스 공유
- "OpenCode로 여러분의 프로젝트도 만들어보세요!"
-->
