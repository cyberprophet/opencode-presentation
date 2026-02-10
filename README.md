---
marp: true
theme: uncover
paginate: true
---

<style>
@import url('https://fonts.googleapis.com/css2?family=Noto+Sans+KR:wght@300;400;700;900&display=swap');

:root {
  --color-background: #0f0e17;
  --color-foreground: #fffffe;
  --color-highlight: #ff8906;
  --color-highlight-heading: #ff8906;
  --color-header: rgba(255,255,255,0.4);
  --color-header-shadow: rgba(15,14,23,0.8);
}

section {
  font-family: 'Noto Sans KR', -apple-system, BlinkMacSystemFont, sans-serif;
  background: var(--color-background);
  color: var(--color-foreground);
  letter-spacing: 0.5px;
}

section::after {
  color: rgba(255,255,255,0.3);
  background: none;
}

h1 {
  font-weight: 900;
  font-size: 2.2em;
  background: linear-gradient(135deg, #ff8906, #f25f4c);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
}

h2 {
  font-weight: 700;
  color: #fffffe;
  border-bottom: 3px solid #ff8906;
  padding-bottom: 8px;
  display: inline-block;
}

h3 {
  color: #ff8906;
  font-weight: 700;
}

strong {
  color: #ff8906;
}

a {
  color: #e53170;
}

code {
  font-family: 'Fira Code', 'JetBrains Mono', monospace;
  background: rgba(255,137,6,0.12) !important;
  color: #ff8906 !important;
  border-radius: 4px;
  padding: 2px 6px;
}

pre code {
  background: #1a1926;
  color: #fffffe;
  border: 1px solid rgba(255,137,6,0.2);
  border-radius: 8px;
  padding: 16px;
}

ul, ol {
  color: #a7a9be;
}

li {
  margin-bottom: 0.3em;
}

li strong {
  color: #ff8906;
}

table {
  font-size: 0.68em;
  border-collapse: collapse;
  width: 100%;
}

table th {
  background: rgba(255,137,6,0.15);
  color: #ff8906;
  font-weight: 700;
  border-bottom: 2px solid #ff8906;
}

table td {
  color: #a7a9be;
  border-bottom: 1px solid rgba(255,255,255,0.06);
}

table td strong {
  color: #fffffe;
}

img {
  background: transparent !important;
}

blockquote {
  border-left: 4px solid #ff8906;
  background: rgba(255,137,6,0.06);
  color: #a7a9be;
  padding: 8px 16px;
  border-radius: 0 8px 8px 0;
}
</style>

# OpenCode + OhMyOpenCode 실전 활용기

**바이브 코딩 랩 발표**

<!--
- [~0.5분] 인사 및 발표 주제 소개
- 본인 소개 (발표자)
- 발표 목표: 회의론 -> 실시간 증명 -> 바로 시작하기
-->

---

## 바이브 코딩, 왜 관심 없었나

- "AI가 코드를 짠다"는 말이 **과장**처럼 느껴졌음
- 결과물이 내 기준 **품질을 못 맞추는** 경우가 많았음
- 그래서 한동안 실제 업무에는 쓰지 않았음

<!--
- [~1분] 솔직한 출발점 공유
- 전환 질문: "그런데 왜 생각이 바뀌었을까?"
-->

---

## OpenCode를 만나다

- 오픈소스 터미널 기반 **AI 코딩 에이전트**
- **75+ LLM provider**를 그대로 연결해서 사용
- TUI 중심 워크플로우로 **빠른 피드백** 가능

<!--
- [~1.2분] OpenCode의 정체성과 차별점
- "새 도구 학습"보다 "기존 터미널 루틴 확장"
-->

---

## OhMyOpenCode: 한 단계 더

- OpenCode 위에 얹는 **오케스트레이션 레이어**
- 멀티 에이전트 **병렬 실행**으로 탐색/구현/검증 분리
- 복잡한 작업을 **계획 → 실행 → 확인** 루프로 자동화

<!--
- [~1.2분] 도구 조합의 핵심 가치
- 단일 모델 vs 멀티 에이전트 체감 차이 강조
-->

---

## 산출물: diff-to-commit

- VS Code 확장: **git diff 기반 커밋 메시지** 자동 생성
- **Conventional Commit** 포맷으로 일관성 유지
- Marketplace 배포 후 실사용 피드백 반영 중

<!--
- [~1.2분] 증거 1 — 실제 배포된 결과물
-->

---

## 산출물: flutter_device_unique_id

- **Android/iOS/macOS/Windows/Web** 5개 플랫폼 지원
- 플랫폼별 저장소(Keychain/Registry/localStorage) 대응
- pub.dev 패키지명: `flutter_device_platform_id`

<!--
- [~1.2분] 증거 2 — 크로스플랫폼 난도
-->

---

## 그 외 산출물들

| 프로젝트 | 설명 | 배포 |
|---------|------|------|
| **flutter_image_conversion** | HEIC → JPEG 변환 | pub.dev |
| **flutter_native_image_compress** | 네이티브 이미지 압축 | pub.dev |

> "한 번의 우연"이 아닌, **반복 가능한 생산성**

<!--
- [~0.8분] 증거 3 — 포트폴리오 누적
-->

---

## 멀티 에이전트가 일하는 방식

```
계획(Prometheus) ──→ 실행(Sisyphus) ──→ 검증(Guardian)
      ↓                     ↓                    ↓
   아키텍처            코드 작성           테스트/리뷰
```

<!--
- [~1분] 처리 구조 설명
- "팀처럼 분업"이라는 비유를 유지
-->

---

## 핵심 에이전트: 계획과 실행

<div style="display:flex; gap:20px; justify-content:center; align-items:flex-start; margin-top:12px;">
  <div style="flex:1; text-align:center;">
    <img src="https://github.com/user-attachments/assets/f345edfd-401d-4cd3-b79e-4fa5aa9f94d6" width="190" style="border-radius:12px; border:2px solid rgba(255,137,6,0.3);" />
    <div style="font-size:0.58em; margin-top:8px; color:#fffffe;"><strong>Prometheus</strong></div>
    <div style="font-size:0.45em; color:#a7a9be;">Strategic Planner</div>
    <div style="font-size:0.4em; color:#666;">gpt-5.2 · 아키텍처 설계</div>
  </div>
  <div style="flex:1; text-align:center;">
    <img src="https://raw.githubusercontent.com/code-yeongyu/oh-my-opencode/dev/.github/assets/sisyphus.png" width="190" style="border-radius:12px; border:2px solid rgba(255,137,6,0.3);" />
    <div style="font-size:0.58em; margin-top:8px; color:#fffffe;"><strong>Sisyphus</strong></div>
    <div style="font-size:0.45em; color:#a7a9be;">Primary Orchestrator</div>
    <div style="font-size:0.4em; color:#666;">claude-opus-4-6 · 에이전트 조율</div>
  </div>
  <div style="flex:1; text-align:center;">
    <img src="https://raw.githubusercontent.com/code-yeongyu/oh-my-opencode/dev/.github/assets/hephaestus.png" width="190" style="border-radius:12px; border:2px solid rgba(255,137,6,0.3);" />
    <div style="font-size:0.58em; margin-top:8px; color:#fffffe;"><strong>Hephaestus</strong></div>
    <div style="font-size:0.45em; color:#a7a9be;">Deep Worker</div>
    <div style="font-size:0.4em; color:#666;">gpt-5.3-codex · 심층 작업</div>
  </div>
</div>

<!--
- [~1분] 메인 에이전트 3종
- 각 에이전트의 전담 역할과 사용 모델
-->

---

## 오케스트레이터: Atlas

<div style="display:flex; gap:32px; justify-content:center; align-items:center; margin-top:8px;">
  <div style="flex:1; text-align:center;">
    <img src="https://github.com/user-attachments/assets/8467d760-915b-4b5f-a6a3-4b4cadaf711a" width="260" style="border-radius:12px; border:2px solid rgba(255,137,6,0.3);" />
  </div>
  <div style="flex:1.5; text-align:left; font-size:0.68em;">
    <h3 style="margin-top:0; border:none; display:block;">Atlas — Master Orchestrator</h3>
    <ul style="color:#a7a9be;">
      <li><strong>역할</strong>: Sisyphus 위의 상위 오케스트레이터</li>
      <li><strong>모델</strong>: claude-sonnet-4-5</li>
      <li>대규모 프로젝트의 전체 작업 흐름을 총괄</li>
      <li>Sisyphus에게 하위 작업을 위임하고 결과를 조율</li>
    </ul>
  </div>
</div>

<!--
- [~0.8분] Atlas — 그리스 신화에서 하늘을 떠받치는 타이탄
-->

---

## 지원 에이전트들

<div style="font-size:0.63em;">

| 에이전트 | 모델 | 역할 |
|---------|------|------|
| **Oracle** | gpt-5.2 | 아키텍처 상담, 디버깅 · 읽기 전용 고품질 추론 |
| **Metis** | claude-opus-4-6 | 요청의 숨겨진 의도와 모호성을 사전 분석 |
| **Momus** | gpt-5.2 | 작업 계획의 명확성 · 검증 가능성 · 완전성 평가 |
| **Explorer** | claude-haiku-4-5 | 빠른 코드베이스 검색과 패턴 발견 |
| **Librarian** | claude-sonnet-4-5 | 외부 문서, GitHub 검색, API 레퍼런스 조사 |
| **Multimodal Looker** | gemini-3-flash | PDF/이미지 분석과 시각 콘텐츠 해석 |

</div>

<!--
- [~1분] 지원 에이전트 — 각자 특화된 역할 수행
-->

---

## 설정 파일로 모델 자유롭게 선택

<div style="font-size:0.48em;">

```json
{
  "$schema": "https://raw.githubusercontent.com/.../oh-my-opencode.schema.json",
  "agents": {
    "sisyphus":   { "model": "openai/gpt-5.3-codex", "variant": "xhigh" },
    "oracle":     { "model": "openai/gpt-5.2",       "variant": "high"  },
    "prometheus": { "model": "openai/gpt-5.2",       "variant": "xhigh" },
    "metis":      { "model": "anthropic/claude-opus-4-6", "variant": "max" },
    "atlas":      { "model": "anthropic/claude-sonnet-4-5" },
    "librarian":  { "model": "anthropic/claude-sonnet-4-5" },
    "explore":    { "model": "anthropic/claude-haiku-4-5" }
  },
  "categories": {
    "visual-engineering": { "model": "google/gemini-3-pro" },
    "ultrabrain":         { "model": "openai/gpt-5.3-codex", "variant": "xhigh" },
    "quick":              { "model": "anthropic/claude-haiku-4-5" }
  }
}
```

</div>

<div style="font-size:0.5em; color:#a7a9be; margin-top:4px;">

`.config/opencode/oh-my-opencode.json` · **기본값이 내장**되어 별도 설정 없이 즉시 사용 가능

</div>

<!--
- [~1분] 설정 파일 설명
- 기본값 내장 → 바로 사용 가능
- 원하는 모델로 자유롭게 교체 가능
-->

---

## 모델 설정의 핵심

- **기본값 내장** — 설치 즉시 사용, 별도 설정 불필요
- **자유로운 교체** — 에이전트별 모델을 원하는 대로 선택
- **역할별 최적화** — 비싼 모델은 핵심에, 가벼운 모델은 탐색에
- **variant 옵션** — low · medium · high · xhigh · max로 추론 강도 조절

<!--
- [~0.8분] 설정의 장점
- 초보자도 바로 시작 + 파워 유저는 세밀 조정
-->

---

## OpenCode 핵심 특징

- **터미널 중심 TUI**로 빠른 루프
- **세션 기반**으로 작업 이어가기
- **LSP + Bash** 통합으로 검증 자동화
- **모델/프로바이더** 선택권 유지

<!--
- [~1분] 기능 요약 — "왜 실무에서 먹히는지"에 초점
-->

---

## 왜 결과물이 다른가

- 요청 하나를 **병렬 에이전트**로 분해해 처리
- 탐색(explore/librarian)과 **구현을 동시에** 진행
- **빌드/테스트 검증 루프**를 기본으로 탑재
- 결과: **실전 배포**(Marketplace/pub.dev)까지 연결

<!--
- [~1.2분] 근거 중심 마무리
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
- [~0.8분] 바로 실행 가능한 3단계
-->

---

## 감사합니다 / Q&A

**질문 있으신가요?**

🐙 github.com/cyberprophet
