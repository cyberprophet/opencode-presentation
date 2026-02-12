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

<div style="margin-top:32px; font-size:0.75em; color:#a7a9be;">
<strong style="color:#fffffe; font-size:1.1em;">박상우</strong> · 공유인베스트
<br/>
🐙 <a href="https://github.com/cyberprophet">github.com/cyberprophet</a>
</div>

<!--
- [~0.5분] 인사 및 발표 주제 소개
- 본인 소개 (발표자)
- 발표 목표: 회의론 -> 실시간 증명 -> 바로 시작하기
-->

---

## 바이브 코딩, 왜 관심 없었나

<div style="font-size:1.1em; margin:24px 0 16px; color:#a7a9be;">
"AI가 코드를 짠다"는 말이 <strong>과장</strong>처럼 느껴졌다
</div>

<div style="font-size:0.65em; color:#666; line-height:1.8;">
결과물 품질이 내 기준에 못 미침 · 실제 업무에선 쓰지 않았음<br/>
<strong style="color:#ff8906;">그런데 왜 생각이 바뀌었을까?</strong>
</div>

<div style="font-size:0.58em; color:#a7a9be; margin-top:12px; border-left:3px solid #ff8906; padding-left:12px;">
직접 써보니 — 하루 만에 <strong>pub.dev 배포</strong>까지 완료된 순간, 생각이 바뀌었다
</div>

<!--
- [~0.9분] 회의적인 출발점을 한 문장으로 강하게 전달
- 전환 계기를 구체적 경험으로 한 줄 추가
- "왜 생각이 바뀌었는가"를 다음 슬라이드로 연결
-->

---

## OpenCode를 만나다

- 오픈소스 터미널 기반 **AI 코딩 에이전트**
- **75+ LLM provider**를 그대로 연결해서 사용
- TUI 중심 워크플로우로 **빠른 피드백** 가능

<!--
- [~1.1분] OpenCode의 정체성과 차별점
- "새 도구 학습"보다 "기존 터미널 루틴 확장"
-->

---

## OhMyOpenCode: 한 단계 더

- OpenCode 위에 얹는 **오케스트레이션 레이어**
- 멀티 에이전트 **병렬 실행**으로 탐색/구현/검증 분리
- 복잡한 작업을 **계획 → 실행 → 확인** 루프로 자동화

<!--
- [~1.1분] 단일 에이전트 대비 체감 차이 소개
- 이제부터 실제 결과물로 증명
-->

---

## 산출물: diff-to-commit

<div style="display:flex; gap:28px; justify-content:center; align-items:center; margin-top:8px;">
  <div style="flex:1.2; text-align:center;">
    <img src="https://github.com/user-attachments/assets/c7fb4f02-c84b-4279-bd5e-843e72eb4388" width="480" style="border-radius:12px; border:2px solid rgba(255,137,6,0.2); box-shadow: 0 4px 24px rgba(0,0,0,0.4);" />
  </div>
  <div style="flex:1; text-align:left; font-size:0.68em;">
    <ul style="color:#a7a9be;">
      <li>VS Code 확장: <strong>git diff 기반 커밋 메시지</strong> 자동 생성</li>
      <li><strong>Conventional Commit</strong> 포맷으로 일관성 유지</li>
      <li>민감 정보(API 키 등) <strong>자동 마스킹</strong></li>
      <li>Marketplace 배포 후 실사용 피드백 반영 중</li>
    </ul>
  </div>
</div>

<!--
- [~1.1분] 증거 1 — 실제 배포된 결과물
- 스크린샷으로 사용성/완성도 빠르게 전달
-->

---

## 산출물: flutter_device_platform_id

- **Android/iOS/macOS/Windows/Web** 5개 플랫폼 지원
- 플랫폼별 저장소(Keychain/Registry/localStorage) 대응
- pub.dev 패키지명: `flutter_device_platform_id`

<!--
- [~1.1분] 증거 2 — 크로스플랫폼 구현 난도와 완성도
-->

---

## 그 외 산출물들

| 프로젝트 | 설명 | 배포 |
|---------|------|------|
| **flutter_image_conversion** | HEIC → JPEG 변환 | pub.dev |
| **flutter_native_image_compress** | 네이티브 이미지 압축 | pub.dev |

> "한 번의 우연"이 아닌, **반복 가능한 생산성**

<!--
- [~0.8분] 증거 3 — 포트폴리오가 누적되는 재현성 강조
-->

---

## 왜 결과물이 다른가

- 요청 하나를 **병렬 에이전트**로 분해해 처리
- 탐색(explore/librarian)과 **구현을 동시에** 진행
- **빌드/테스트 검증 루프**를 기본으로 탑재
- 결과: **실전 배포**(Marketplace/pub.dev)까지 연결

> 어떤 구조가 이걸 가능하게 할까? →

<!--
- [~1분] 산출물을 가능하게 한 이유를 먼저 제시
- "왜 다른지"를 보여주고, 다음 슬라이드에서 "어떻게" 설명
-->

---

## 멀티 에이전트가 일하는 방식

<div style="display:flex; justify-content:center; align-items:center; gap:0; margin-top:24px;">
  <div style="background:rgba(255,137,6,0.12); border:2px solid rgba(255,137,6,0.4); border-radius:12px; padding:18px 22px; text-align:center; min-width:180px;">
    <div style="font-size:1.3em;">📐</div>
    <div style="font-size:0.72em; color:#fffffe; font-weight:700;">계획</div>
    <div style="font-size:0.52em; color:#ff8906;">Prometheus</div>
    <div style="font-size:0.45em; color:#a7a9be; margin-top:4px;">아키텍처 설계</div>
  </div>
  <div style="font-size:1.5em; color:#ff8906; padding:0 12px;">→</div>
  <div style="background:rgba(255,137,6,0.12); border:2px solid rgba(255,137,6,0.4); border-radius:12px; padding:18px 22px; text-align:center; min-width:180px;">
    <div style="font-size:1.3em;">⚙️</div>
    <div style="font-size:0.72em; color:#fffffe; font-weight:700;">실행</div>
    <div style="font-size:0.52em; color:#ff8906;">Sisyphus</div>
    <div style="font-size:0.45em; color:#a7a9be; margin-top:4px;">에이전트 조율 · 코드 작성</div>
  </div>
  <div style="font-size:1.5em; color:#ff8906; padding:0 12px;">→</div>
  <div style="background:rgba(255,137,6,0.12); border:2px solid rgba(255,137,6,0.4); border-radius:12px; padding:18px 22px; text-align:center; min-width:180px;">
    <div style="font-size:1.3em;">🔨</div>
    <div style="font-size:0.72em; color:#fffffe; font-weight:700;">심층 작업</div>
    <div style="font-size:0.52em; color:#ff8906;">Hephaestus</div>
    <div style="font-size:0.45em; color:#a7a9be; margin-top:4px;">심층 구현 · 검증</div>
  </div>
</div>

<div style="text-align:center; margin-top:16px; font-size:0.52em; color:#666;">
↕ <strong style="color:#a7a9be;">Atlas</strong>가 전체 흐름을 오케스트레이션
</div>

<!--
- [~1분] 앞 슬라이드의 "왜"를 이 구조로 해설
- "팀처럼 분업" 비유로 병렬 처리 감각 전달
- Guardian 제거, 실제 에이전트(Prometheus → Sisyphus → Hephaestus)로 구성
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
- [~1분] 메인 에이전트 3종의 전담 역할
- 계획/조율/심층 작업의 책임 분리 강조
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
- [~0.8분] Atlas가 전체 흐름을 통합하는 지점 설명
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
- [~0.9분] 지원 에이전트들이 병렬 파이프라인을 보강하는 방식
-->

---

## 설정: 모델을 자유롭게

<div style="display:flex; gap:24px; justify-content:center; align-items:flex-start; margin-top:4px;">
  <div style="flex:1.3; font-size:0.44em;">

```json
{
  "agents": {
    "sisyphus":   { "model": "openai/gpt-5.3-codex", "variant": "xhigh" },
    "oracle":     { "model": "openai/gpt-5.2",       "variant": "high"  },
    "prometheus": { "model": "openai/gpt-5.2",       "variant": "xhigh" },
    "atlas":      { "model": "anthropic/claude-sonnet-4-5" },
    "explore":    { "model": "anthropic/claude-haiku-4-5" }
  }
}
```

  </div>
  <div style="flex:1; text-align:left; font-size:0.6em;">
    <ul style="color:#a7a9be;">
      <li><strong>기본값 내장</strong> — 설정 없이 즉시 사용</li>
      <li><strong>자유로운 교체</strong> — 에이전트별 모델 선택</li>
      <li><strong>역할별 최적화</strong> — 핵심엔 비싼 모델, 탐색엔 가벼운 모델</li>
      <li><strong>variant</strong> — low·medium·high·xhigh·max</li>
    </ul>
  </div>
</div>

<!--
- [~1분] 설정 구조와 운영 원칙을 한 장으로 압축 전달
- 기본값 즉시 사용 + 역할별 최적화 가능성 강조
-->

---

## OpenCode 핵심 특징

<div style="display:grid; grid-template-columns:1fr 1fr; gap:16px; margin-top:16px; font-size:0.6em;">
  <div style="background:rgba(255,137,6,0.08); border:1px solid rgba(255,137,6,0.2); border-radius:12px; padding:20px; text-align:left;">
    <div style="font-size:1.2em; margin-bottom:6px;">⚡</div>
    <strong>터미널 중심 TUI</strong>
    <div style="color:#a7a9be; font-size:0.9em; margin-top:4px;">IDE 없이 빠른 피드백 루프</div>
  </div>
  <div style="background:rgba(255,137,6,0.08); border:1px solid rgba(255,137,6,0.2); border-radius:12px; padding:20px; text-align:left;">
    <div style="font-size:1.2em; margin-bottom:6px;">🔄</div>
    <strong>세션 기반 연속성</strong>
    <div style="color:#a7a9be; font-size:0.9em; margin-top:4px;">중단 없이 작업 이어가기</div>
  </div>
  <div style="background:rgba(255,137,6,0.08); border:1px solid rgba(255,137,6,0.2); border-radius:12px; padding:20px; text-align:left;">
    <div style="font-size:1.2em; margin-bottom:6px;">🔍</div>
    <strong>LSP + Bash 통합</strong>
    <div style="color:#a7a9be; font-size:0.9em; margin-top:4px;">코드 검증 자동화</div>
  </div>
  <div style="background:rgba(255,137,6,0.08); border:1px solid rgba(255,137,6,0.2); border-radius:12px; padding:20px; text-align:left;">
    <div style="font-size:1.2em; margin-bottom:6px;">🔗</div>
    <strong>75+ 모델/프로바이더</strong>
    <div style="color:#a7a9be; font-size:0.9em; margin-top:4px;">원하는 LLM 자유롭게 선택</div>
  </div>
</div>

<!--
- [~0.9분] 핵심 기능을 카드형으로 빠르게 인지시키기
- 바로 다음 슬라이드에서 실행 방법으로 전환
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
- [~0.8분] 바로 실행 가능한 3단계 안내
-->

---

## 한 줄 요약

<div style="text-align:center; margin-top:48px;">
<span style="font-size:1.4em; font-weight:900; background:linear-gradient(135deg, #ff8906, #f25f4c); -webkit-background-clip:text; -webkit-text-fill-color:transparent; background-clip:text;">
OpenCode + OhMyOpenCode = 반복 가능한 실전 배포
</span>
</div>

<div style="text-align:center; margin-top:24px; font-size:0.65em; color:#a7a9be;">
아이디어 → 구현 → 검증 → 배포, 이 루프를 <strong>AI 에이전트 팀</strong>과 함께
</div>

<!--
- [~0.3분] 핵심 메시지 한 줄로 각인
-->

---

## 감사합니다 / Q&A

**질문 있으신가요?**

🐙 github.com/cyberprophet

<!--
- [~0.5분] 마무리 및 질의응답
-->
