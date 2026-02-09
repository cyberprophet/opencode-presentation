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

| 항목 | 소스 | 저장 경로 | 담당 |
|------|------|---------|------|
| OpenCode TUI | `opencode` 명령 실행 후 메인 화면 | .sisyphus/evidence/opencode-tui.png | [MANUAL] 발표자 |
| OhMyOpenCode 에이전트 | 멀티 에이전트 병렬 작업 화면 | .sisyphus/evidence/ohmyopencode-agents.png | [MANUAL] 발표자 |
| diff-to-commit Marketplace | https://marketplace.visualstudio.com/items?itemName=Dayond.diff-to-commit | .sisyphus/evidence/shot-diff-to-commit.png | [AUTO] Playwright |
| flutter_device_platform_id pub.dev | https://pub.dev/packages/flutter_device_platform_id | .sisyphus/evidence/shot-pubdev-flutter-device-platform-id.png | [AUTO] Playwright |
| Terminal input | 발표자 터미널에서 `opencode` 입력 중인 모습 | .sisyphus/evidence/terminal-input.png | [MANUAL] 발표자 |
| GitHub OpenCode | https://github.com/opencode-ai/opencode | .sisyphus/evidence/shot-github-opencode.png | [AUTO] Playwright |
| GitHub OhMyOpenCode | https://github.com/code-yeongyu/oh-my-opencode | .sisyphus/evidence/shot-github-oh-my-opencode.png | [AUTO] Playwright |

================================================================================
-->

# OpenCode + OhMyOpenCode 실전 활용기

**바이브 코딩 랩 발표**

<!--
- [~0.5분] 인사 및 발표 주제 소개
- 본인 소개 (발표자)
- 발표 목표: 회의론 -> 실시간 증명 -> 바로 시작하기
- 청중에게 기대: "오늘 끝나고 바로 써볼 수 있다"
-->

---

## 바이브 코딩, 왜 관심 없었나

- "AI가 코드를 짠다"는 말이 과장처럼 느껴졌음
- 결과물이 내 기준 품질을 못 맞추는 경우가 많았음
- 그래서 한동안 실제 업무에는 쓰지 않았음

<!--
- [~1분] 솔직한 출발점 공유
- 기술 낙관보다 실무자의 품질 기준으로 시작
- 청중(Claude 사용자)와 공감대 형성
- 전환 질문: "그런데 왜 생각이 바뀌었을까?"
-->

---

## OpenCode를 만나다

- 오픈소스 터미널 기반 AI 코딩 에이전트
- 75+ LLM provider를 그대로 연결해서 사용
- TUI 중심 워크플로우로 빠른 피드백 가능

<!--
- [~1.2분] OpenCode의 정체성과 차별점
- "새 도구 학습"보다 "기존 터미널 루틴 확장"으로 설명
- 락인보다 선택권 강조
-->

---

## OhMyOpenCode: 한 단계 더

- OpenCode 위에 얹는 오케스트레이션 레이어
- 멀티 에이전트 병렬 실행으로 탐색/구현/검증 분리
- 복잡한 작업을 계획 -> 실행 -> 확인 루프로 자동화

<!--
- [~1.2분] 도구 조합의 핵심 가치
- 단일 모델 사용과 멀티 에이전트 사용의 체감 차이 강조
- 다음 슬라이드에서 실시간으로 바로 증명 예고
-->

---

## 🎬 라이브 데모

실시간으로 OpenCode + OhMyOpenCode 실행 (3분 타임박스)

1. 발표 5분 전 warm-up 실행으로 초기 지연 제거
2. `opencode`로 TUI 진입
3. `ulw - 배열 중복 제거 함수 + 테스트까지` 입력
4. 병렬 에이전트 흐름 확인
5. 결과/테스트 확인 후 다음 슬라이드로 이동

<!--
- [~3분] 라이브 데모
- 중단 신호: "여기서부터는 결과 화면으로 이어가겠습니다"
- 플랜 B 없음 -> 타임박스와 컷오프 멘트를 반드시 사용
- 데모 실패 시에도 산출물 슬라이드로 메시지 유지
-->

---

## 산출물: diff-to-commit

- VS Code 확장: git diff 기반 커밋 메시지 자동 생성
- Conventional Commit 포맷으로 일관성 유지
- Marketplace 배포 후 실사용 피드백 반영 중

<!--
- [~1.2분] 증거 1
- 단순 데모가 아니라 실제 배포 결과임을 강조
- 체크리스트의 Marketplace 캡처와 연결
-->

---

## 산출물: flutter_device_unique_id

- Android/iOS/macOS/Windows/Web 5개 플랫폼 지원
- 플랫폼별 저장소(Keychain/Registry/localStorage) 대응
- pub.dev 패키지명: `flutter_device_platform_id`

<!--
- [~1.2분] 증거 2
- 크로스플랫폼 난도를 짧게 짚고 결과를 보여줌
- 체크리스트의 pub.dev 캡처와 연결
-->

---

## 그 외 산출물들

| 프로젝트 | 설명 | 배포 |
|---------|------|------|
| flutter_image_conversion | HEIC -> JPEG 변환 | pub.dev |
| flutter_native_image_compress | 네이티브 이미지 압축 | pub.dev |

<!--
- [~0.8분] 증거 3
- "한 번의 우연"이 아닌 반복 가능한 생산성임을 전달
- 세부 설명보다 포트폴리오 누적으로 설득
-->

---

## 멀티 에이전트가 일하는 방식

```
계획(Prometheus) -> 실행(Sisyphus) -> 검증(Guardian)
     ↓                    ↓                    ↓
  아키텍처           코드 작성          테스트/리뷰
```

<!--
- [~1분] 처리 구조 설명
- 데모/산출물에서 본 현상을 구조로 해석
- "팀처럼 분업"이라는 비유를 유지
-->

---

## Agent Models: 역할로 분리

<div style="display:flex; gap:32px; justify-content:center; align-items:center;">
  <div style="flex:1; text-align:center;">
    <img src="https://raw.githubusercontent.com/code-yeongyu/oh-my-opencode/refs/heads/dev/.github/assets/sisyphus.png" width="320" />
    <div style="font-size:0.75em; margin-top:8px;">Sisyphus - Orchestrator (anthropic/claude-opus-4-6)</div>
  </div>
  <div style="flex:1; text-align:center;">
    <img src="https://raw.githubusercontent.com/code-yeongyu/oh-my-opencode/refs/heads/dev/.github/assets/hephaestus.png" width="320" />
    <div style="font-size:0.75em; margin-top:8px;">Hephaestus - Craftsman (openai/gpt-5.3-codex)</div>
  </div>
</div>

<!--
- [~1분] 역할별 모델 분리 이유: 품질 + 속도/비용 + 코드 특화
- fallback 체인: 가용성/복원력 확보
- 예외: Hephaestus는 일관성을 위해 no-fallback
-->

---

## OpenCode 핵심 특징

- 터미널 중심 TUI로 빠른 루프
- 세션 기반으로 작업 이어가기
- LSP + Bash 통합으로 검증 자동화
- 모델/프로바이더 선택권 유지

<!--
- [~1분] 기능 요약
- 이미 본 증거를 기능과 연결해서 정리
- 장점 나열보다 "왜 실무에서 먹히는지"에 초점
-->

---

## 신화 속 에이전트들

- Prometheus: 기획/설계
- Sisyphus: 실행/반복
- Explorer: 탐색/리서치
- Guardian: 검증/품질

<!--
- [~0.8분] 네이밍을 기억 장치로 활용
- 역할 분리 구조를 다시 짧게 리마인드
-->

---

## 왜 결과물이 다른가

- 요청 하나를 병렬 에이전트로 분해해 처리함
- 탐색(explore/librarian)과 구현을 동시에 진행함
- 빌드/테스트 검증 루프를 기본으로 탑재함
- 결과: 실전 배포(Marketplace/pub.dev)까지 연결됨

<!--
- [~1.2분] 추상 설명 대신 근거 중심으로 마무리
- 앞선 산출물 슬라이드와 자연스럽게 연결
-->

---

## 시작하기

```bash
# 1) OpenCode 설치
curl -fsSL https://opencode.ai/install | bash

# 2) OhMyOpenCode 설치
bunx oh-my-opencode install

# 3) 실행
opencode
```

<!--
- [~0.8분] 바로 실행 가능한 시작점 제공
- 발표 직후 따라할 수 있는 3단계만 유지
-->

---

## 감사합니다 / Q&A

**질문 있으신가요?**

🐙 github.com/cyberprophet

<!--
- [~0.4분] 마무리
- 질문이 Agent Models로 가면 다음 Appendix로 이동
-->

---

## Appendix: Agent Models (Full Map)

<div style="font-size:0.72em;">

| Agent | Model | Purpose |
|---|---|---|
| Sisyphus | anthropic/claude-opus-4-6 | Primary orchestrator (fallback: kimi-k2.5 -> glm-4.7 -> gpt-5.3-codex -> gemini-3-pro) |
| Hephaestus | openai/gpt-5.3-codex | Autonomous deep worker, "The Legitimate Craftsman" (requires gpt-5.3-codex, no fallback) |
| Atlas | anthropic/claude-sonnet-4-5 | Master orchestrator (fallback: kimi-k2.5 -> gpt-5.2) |
| oracle | openai/gpt-5.2 | Consultation, debugging |
| librarian | zai-coding-plan/glm-4.7 | Docs, GitHub search (fallback: glm-4.7-free) |
| explore | xai/grok-code-fast-1 | Fast codebase grep (fallback: claude-haiku-4-5 -> gpt-5-mini -> gpt-5-nano) |
| multimodal-looker | google/gemini-3-flash | PDF/image analysis |
| Prometheus | anthropic/claude-opus-4-6 | Strategic planning (fallback: kimi-k2.5 -> gpt-5.2) |
| Metis | anthropic/claude-opus-4-6 | Pre-planning analysis (temp 0.3, fallback: kimi-k2.5 -> gpt-5.2) |
| Momus | openai/gpt-5.2 | Plan validation (temp 0.1, fallback: claude-opus-4-6) |
| Sisyphus-Junior | anthropic/claude-sonnet-4-5 | Category-spawned executor (temp 0.1) |

</div>

<!--
- [~0.2분] 필요 시에만 설명하고 스킵 가능
- 본문은 역할 분리 원리 중심, 상세 표는 부록에서 대응
-->
