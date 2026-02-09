# OpenCode 발표자료 고도화 — 스토리라인 강화 + 라이브 데모/스크린샷 완성

## TL;DR

> **Quick Summary**: 기존 발표 초안을 전면 재작성하지 않고, 이야기 흐름을 더 강하게 재구성하고 라이브 데모 중심으로 데모/스크린샷 전략을 완성한다.
>
> **Deliverables**:
> - `README.md` 스토리라인 개편본 (15~20분 유지, 12~16장)
> - 라이브 데모 전용 슬라이드/스피커노트(녹화 기반 문구 제거)
> - 실행 가능한 스크린샷 캡처 매트릭스(공개 URL 자동 캡처 + 발표자 전용 항목 분리)
> - `slides.html` 재빌드 결과 및 검증 증거 파일
> - GitHub 원격 저장소로 커밋/푸시(브랜치 + PR 기본값)
>
> **Estimated Effort**: Short-Medium
> **Parallel Execution**: YES — 4 waves
> **Critical Path**: Task 1 -> Task 2 -> Task 4 -> Task 5

---

## Context

### Original Request
Opus와 준비 중이던 OpenCode 발표자료를 이번 라운드에서 더 발전시키고 싶으며, 우선순위는 스토리라인 강화 + 데모/스크린샷 완성이다.

### Interview Summary
**Key Discussions**:
- 우선 고도화 범위: 스토리라인 강화, 데모/스크린샷 완성
- 데모 형식: 라이브 데모
- 데모 플랜 B: 없음(라이브 단일 경로)
- 목표 시간: 15~20분 유지
- 청중 맥락: 이전과 동일(Claude 사용자 중심, OpenCode 친숙도 낮음)

**Research Findings**:
- 현재 발표 원본은 `README.md` 기반 Marp 문서이며 `slides.html` 빌드 산출물 존재
- 기존 플랜 `.sisyphus/plans/opencode-presentation.md`는 사전녹화(90초) 전제여서 라이브 데모 정책과 충돌

### Metis Review
**Identified Gaps** (addressed in this plan):
- 데모 슬라이드가 아직 사전녹화 문맥임 -> 라이브 데모 문맥으로 전환 태스크 명시
- 소스 파일 명 불일치(`slides.md` vs `README.md`) -> 모든 빌드/검증 명령을 `README.md` 기준으로 고정
- 스크린샷 TODO가 실행지시로 부족 -> URL/명령/출력경로 포함한 캡처 매트릭스로 구체화
- 이야기 흐름이 기능열거형으로 평면적 -> 훅/전환점/증거/행동유도 구조로 재배치

---

## Work Objectives

### Core Objective
청중이 "이건 실제로 써볼 만하다"고 느끼도록, 추상 소개 중심 덱을 증거 중심 스토리로 개편하고 라이브 데모 실행력을 높인다.

### Concrete Deliverables
- `README.md` (스토리 구조, 데모 섹션, 스피커 노트, 캡처 체크리스트 반영)
- `slides.html` (최신 빌드)
- `.sisyphus/evidence/storyline-check.txt`
- `.sisyphus/evidence/live-demo-check.txt`
- `.sisyphus/evidence/screenshot-matrix-check.txt`
- `.sisyphus/evidence/final-build-check.txt`

### Definition of Done
- [ ] `npx @marp-team/marp-cli --html README.md -o slides.html` -> exit code 0
- [ ] `README.md`에서 `녹화|영상 재생|OBS|QuickTime` 키워드 0건
- [ ] 슬라이드 수 12~16장(`grep -c "^---$" README.md` 기준 계산) 충족
- [ ] 스피커 노트 타이밍 총합 15~20분
- [ ] 스크린샷 체크리스트 각 항목에 URL 또는 명령 + 저장 경로 명시
- [ ] GitHub remote에 브랜치 푸시 완료(기본: `gh pr create`로 PR 생성)

### Must Have
- 스토리 흐름: Hook -> Skepticism -> Turning Point -> Proof -> How -> CTA
- 6~8번 슬라이드 구간에 데모/증거를 전진 배치(후반 몰림 방지)
- 라이브 데모 절차(명령/프롬프트/기대결과/중단신호) 명시
- 공개 페이지(예: Marketplace/pub.dev/GitHub) 스크린샷 자동 캡처 가능 지시 포함
- 에이전트-모델 전략(역할별 모델 분리 이유 + fallback 의미)을 1장 또는 스피커 노트로 명확히 설명

### Must NOT Have (Guardrails)
- 다른 도구 비교 슬라이드 추가 금지
- 16장 초과 금지
- CSS 대규모 개편 금지(기존 인라인 스타일에서 최소 수정만)
- 발표자 인증/개인환경이 필요한 캡처를 "자동 완료"로 간주 금지
- 데모용 신규 프로젝트 구현/개발 작업 포함 금지(발표자료 고도화 범위 밖)

---

## Verification Strategy (MANDATORY)

> **UNIVERSAL RULE: ZERO HUMAN INTERVENTION**
>
> 모든 태스크의 완료 판단은 에이전트가 실행 가능한 명령/도구 결과로 검증한다.

### Test Decision
- **Infrastructure exists**: YES (`npx @marp-team/marp-cli` 사용 가능)
- **Automated tests**: None (문서/슬라이드 작업)
- **Framework**: Marp CLI + Bash 검증 스크립트

### Agent-Executed QA Scenarios (MANDATORY — ALL tasks)

| Deliverable Type | Tool | Verification |
|---|---|---|
| 슬라이드 구조/문구 | Bash | heading 순서, 키워드, 타이밍 주석, 슬라이드 수 검사 |
| 라이브 데모 섹션 | Bash | 금지 키워드 제거 + 라이브 절차 구성요소 존재 검사 |
| 공개 웹 스크린샷 | Playwright | URL 접근, 요소 확인, 스크린샷 저장 |
| 최종 빌드 | Bash | Marp 빌드 실행 및 산출물 검사 |

---

## Execution Strategy

### Parallel Execution Waves

```
Wave 1 (Start Immediately):
├── Task 1: 스토리라인 재배치 설계
└── Task 3: 스크린샷 캡처 매트릭스/공개 자산 캡처

Wave 2 (After Task 1):
└── Task 2: README.md 본문/데모 섹션 라이브 전환

Wave 3 (After Task 2 and Task 3):
└── Task 4: 최종 통합 검증 + Marp 빌드 + evidence 정리

Wave 4 (After Task 4):
└── Task 5: Git commit + push (+ PR)

Critical Path: Task 1 -> Task 2 -> Task 4
```

### Dependency Matrix

| Task | Depends On | Blocks | Can Parallelize With |
|---|---|---|---|
| 1 | None | 2 | 3 |
| 2 | 1 | 4 | None |
| 3 | None | 4 | 1 |
| 4 | 2, 3 | None | None |
| 5 | 4 | None | None |

### Agent Dispatch Summary

| Wave | Tasks | Recommended Agents |
|---|---|---|
| 1 | 1, 3 | `task(category="writing", ...)`, `task(category="visual-engineering", load_skills=["playwright"], ...)` |
| 2 | 2 | `task(category="writing", ...)` |
| 3 | 4 | `task(category="quick", ...)` |
| 4 | 5 | `task(category="quick", load_skills=["git-master"], ...)` |

---

## TODOs

- [ ] 1. 스토리라인 재배치(기능열거 -> 증거중심 서사)

  **What to do**:
  - `README.md`의 현재 슬라이드 순서를 유지하되, 핵심 주장과 증거의 위치를 재배치
  - 2번 슬라이드 안에 "왜 회의적이었는지"를 명확히 두고, 6~8번 구간에 전환점/증거를 앞당김
  - "왜 결과물이 다른가"를 추상 나열이 아닌 근거(산출물/데모 연결) 형태로 수정
  - 스피커 노트 타이밍 합이 15~20분이 되도록 조정
  - "AGENT MODELS" 설명을 보강(표 자체는 짧게, 상세는 스피커 노트로):
    - 왜 역할별로 모델을 나누는지(품질/속도/비용/맥락 유지)
    - fallback 체인의 의미(가용성/복원력)와 예외(Hephaestus no-fallback)
    - 시각 자료: Sisyphus/Hephaestus 페르소나 이미지를 슬라이드에 삽입(원격 URL 사용 가능)

  **Must NOT do**:
  - 새 프로젝트 딥다이브 추가 금지
  - 16장 초과 금지
  - 경쟁 도구 비교 문구 삽입 금지

  **Recommended Agent Profile**:
  - **Category**: `writing`
    - Reason: 메시지 구조화/스토리텔링/발표 문구 다듬기가 핵심
  - **Skills**: [`frontend-ui-ux`]
    - `frontend-ui-ux`: 슬라이드 전달력, 정보 밀도, 시각적 메시지 밸런스 개선
  - **Skills Evaluated but Omitted**:
    - `playwright`: 이 태스크는 브라우저 상호작용보다 내러티브 편집이 중심

  **Parallelization**:
  - **Can Run In Parallel**: YES
  - **Parallel Group**: Wave 1 (with Task 3)
  - **Blocks**: Task 2
  - **Blocked By**: None

  **References**:
  - `README.md` - 현재 전체 슬라이드 콘텐츠와 스피커 노트 원본
  - `.sisyphus/plans/opencode-presentation.md` - 기존 발표 의도/가드레일/검증 기준 베이스라인
  - `slides.html` - 현재 렌더 결과의 구조와 가독성 확인용 산출물
  - `https://raw.githubusercontent.com/code-yeongyu/oh-my-opencode/refs/heads/dev/.github/assets/sisyphus.png` - Sisyphus 페르소나 이미지(슬라이드 삽입)
  - `https://raw.githubusercontent.com/code-yeongyu/oh-my-opencode/refs/heads/dev/.github/assets/hephaestus.png` - Hephaestus 페르소나 이미지(슬라이드 삽입)

  **Proposed Insert (새 슬라이드: Agent Models)**:

  ```markdown
  ---

  ## Agent Models: 역할로 분리

  <div style="display:flex; gap:32px; justify-content:center; align-items:center;">
    <div style="flex:1; text-align:center;">
      <img src="https://raw.githubusercontent.com/code-yeongyu/oh-my-opencode/refs/heads/dev/.github/assets/sisyphus.png" width="320" />
      <div style="font-size:0.75em; margin-top:8px;">Sisyphus — Orchestrator (anthropic/claude-opus-4-6)</div>
    </div>
    <div style="flex:1; text-align:center;">
      <img src="https://raw.githubusercontent.com/code-yeongyu/oh-my-opencode/refs/heads/dev/.github/assets/hephaestus.png" width="320" />
      <div style="font-size:0.75em; margin-top:8px;">Hephaestus — Craftsman (openai/gpt-5.3-codex)</div>
    </div>
  </div>

  <!--
  - [~1분] 역할별 모델 분리 이유: 품질(오케스트레이션) + 속도/비용(리서치) + 코드 특화(구현) + 결정적 검수(검증)
  - fallback 체인: 모델 가용성/복원력 확보 (단, Hephaestus는 일관성 위해 no-fallback)
  - 표(전체 매핑)는 슬라이드 본문이 아니라 스피커 노트/부록에 두는 것을 권장(텍스트 벽 방지)
  -->
  ```

  **Proposed Appendix Insert (부록 슬라이드: 전체 매핑 표)**:

  > 권장 위치: 마지막(Q&A 뒤) 또는 Q&A 직전. 발표 본문에서는 "필요하면 보여드릴게요"로 스킵 가능.

  ```markdown
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
  - [옵션] "fallback"은 1순위 모델이 실패/제한일 때 다음 모델로 이어서 작업을 완주하는 안전장치
  - 표는 Q&A에서만 잠깐 보여주고, 본문에서는 "역할 분리" 원리만 전달하는 걸 추천
  -->
  ```

  **Acceptance Criteria**:
  - [ ] 슬라이드 구조가 Hook -> Skepticism -> Turning Point -> Proof -> How -> CTA 순서로 해석 가능
  - [ ] 증거성 슬라이드(데모/실제 산출물)가 6~8번 구간에 배치
  - [ ] 스피커 노트 시간 합계 15~20분

  **Agent-Executed QA Scenarios**:

  ```text
  Scenario: 서사 구조 재배치 검증
    Tool: Bash
    Preconditions: README.md 수정 완료
    Steps:
      1. Extract headings: grep '^## ' README.md
      2. Assert: 초기 3개 heading에 문제인식/회의론 포함
      3. Assert: 6~8번째 heading 구간에 데모/산출물 증거 슬라이드 존재
      4. Save result: .sisyphus/evidence/storyline-check.txt
    Expected Result: 기능 소개가 아니라 증거 중심 전개가 확인됨
    Failure Indicators: 데모/증거가 후반부에만 몰림
    Evidence: .sisyphus/evidence/storyline-check.txt

  Scenario: 타이밍 총합 범위 검증
    Tool: Bash
    Preconditions: 스피커 노트에 [~N분] 표기 존재
    Steps:
      1. Extract timing tokens from README.md comments
      2. Sum minutes using script
      3. Assert: total >= 15 and <= 20
      4. Append output to .sisyphus/evidence/storyline-check.txt
    Expected Result: 총 발표 시간이 목표 범위 내
    Failure Indicators: 15 미만 또는 20 초과
    Evidence: .sisyphus/evidence/storyline-check.txt
  ```

  **Commit**: NO

---

- [ ] 2. 데모 섹션 라이브 전환(사전녹화 문맥 제거)

  **What to do**:
  - 데모 슬라이드 및 인접 스피커 노트를 라이브 데모 기준으로 교체
  - 라이브 데모 절차를 "환경 준비 -> 명령 실행 -> 프롬프트 입력 -> 결과 확인 -> 요약" 단계로 명시
  - 시간 초과/지연 시 중단 신호를 문서화(백업 영상 없이 진행 지속)
  - "녹화 영상 재생" 관련 문구를 전부 제거

  **Must NOT do**:
  - OBS/QuickTime/영상재생/사전녹화 지시 포함 금지
  - "플랜 B 영상" 삽입 금지(사용자 결정 준수)
  - 데모를 실제로 구현하는 개발 태스크로 확장 금지

  **Recommended Agent Profile**:
  - **Category**: `writing`
    - Reason: 라이브 데모 스크립트와 발표 문구를 안정적으로 구조화해야 함
  - **Skills**: [`frontend-ui-ux`]
    - `frontend-ui-ux`: 발표 흐름상 전환 문구와 메시지 임팩트 개선
  - **Skills Evaluated but Omitted**:
    - `playwright`: 이 태스크는 캡처 수행이 아니라 문구/절차 정의가 핵심

  **Parallelization**:
  - **Can Run In Parallel**: NO
  - **Parallel Group**: Wave 2
  - **Blocks**: Task 4
  - **Blocked By**: Task 1

  **References**:
  - `README.md` - 데모 슬라이드/스피커 노트 수정 대상
  - `https://opencode.ai/docs/cli/` - 데모에서 언급할 CLI 명령 정확도 확보
  - `https://github.com/code-yeongyu/oh-my-opencode` - 멀티 에이전트 흐름 설명 근거

  **Acceptance Criteria**:
  - [ ] `README.md`에서 `녹화|영상 재생|OBS|QuickTime` 0건
  - [ ] 라이브 데모 절차에 단계 5개 이상 명시
  - [ ] 라이브 데모 시간 상한(예: 3분)과 중단 신호 명시

  **Agent-Executed QA Scenarios**:

  ```text
  Scenario: 라이브 데모 문맥 전환 검증
    Tool: Bash
    Preconditions: README.md 데모 섹션 수정 완료
    Steps:
      1. grep -Eic '녹화|영상 재생|OBS|QuickTime' README.md
      2. Assert: output == 0
      3. grep -Eic '라이브|live|실시간' README.md
      4. Assert: output >= 1
      5. Save outputs: .sisyphus/evidence/live-demo-check.txt
    Expected Result: 사전녹화 문맥 제거, 라이브 문맥 존재
    Failure Indicators: 금지 키워드 잔존
    Evidence: .sisyphus/evidence/live-demo-check.txt

  Scenario: 라이브 데모 절차 완결성 검증
    Tool: Bash
    Preconditions: 데모 단계가 번호 목록으로 작성됨
    Steps:
      1. Locate demo block in README.md
      2. Count numbered steps in demo procedure
      3. Assert: step count >= 5
      4. Assert: block includes command, prompt text, expected outcome, cutoff signal
      5. Append results: .sisyphus/evidence/live-demo-check.txt
    Expected Result: 현장에서 그대로 읽고 진행 가능한 절차
    Failure Indicators: 요소 누락(명령/프롬프트/중단신호)
    Evidence: .sisyphus/evidence/live-demo-check.txt
  ```

  **Commit**: NO

---

- [ ] 3. 스크린샷 캡처 매트릭스 완성 + 공개 자산 자동 캡처

  **What to do**:
  - 기존 TODO 캡처 리스트를 항목별로 구체화: `source(URL/command)`, `target slide`, `output path`, `owner(agent/manual)`
  - 공개 접근 가능한 자산은 Playwright로 캡처
    - VS Code Marketplace (diff-to-commit)
    - pub.dev (flutter_device_platform_id)
    - GitHub(opencode)
    - GitHub(oh-my-opencode)
  - 발표자 전용 항목(개인 터미널/TUI 실행 장면)은 `[MANUAL]`로 명시하고 캡처 커맨드/구도 가이드 기록

  **Must NOT do**:
  - 발표자 인증/개인 환경이 필요한 화면을 자동 완료 처리 금지
  - 캡처 경로 미정 상태로 남기기 금지

  **Recommended Agent Profile**:
  - **Category**: `visual-engineering`
    - Reason: 브라우저 캡처 품질/구도/일관성 확보가 핵심
  - **Skills**: [`playwright`, `frontend-ui-ux`]
    - `playwright`: 공개 페이지 자동 캡처 실행
    - `frontend-ui-ux`: 발표 슬라이드 삽입 관점의 구도/가독성 체크
  - **Skills Evaluated but Omitted**:
    - `git-master`: Git 작업 중심 태스크가 아님

  **Parallelization**:
  - **Can Run In Parallel**: YES
  - **Parallel Group**: Wave 1 (with Task 1)
  - **Blocks**: Task 4
  - **Blocked By**: None

  **References**:
  - `README.md` - TODO 체크리스트 위치와 반영 대상
  - `https://marketplace.visualstudio.com/items?itemName=Dayond.diff-to-commit` - 확장 마켓 증거 캡처 대상
  - `https://pub.dev/packages/flutter_device_platform_id` - pub.dev 배포 증거 캡처 대상
  - `https://github.com/opencode-ai/opencode` - OpenCode 레포 증거 캡처 대상
  - `https://github.com/code-yeongyu/oh-my-opencode` - OhMyOpenCode 레포 증거 캡처 대상

  **Acceptance Criteria**:
  - [ ] 캡처 매트릭스 각 항목에 source/target/output path/owner가 모두 채워짐
  - [ ] 공개 페이지 스크린샷 4개 이상 저장 완료
  - [ ] 발표자 전용 캡처 항목은 `[MANUAL]` 태그와 커맨드 가이드 포함

  **Agent-Executed QA Scenarios**:

  ```text
  Scenario: 공개 페이지 자동 캡처 성공
    Tool: Playwright (playwright skill)
    Preconditions: 네트워크 접근 가능
    Steps:
      1. Open URL: https://marketplace.visualstudio.com/items?itemName=Dayond.diff-to-commit
      2. Wait for main content visible
      3. Screenshot save: .sisyphus/evidence/shot-diff-to-commit.png
      4. Repeat for pub.dev/opencode repo/oh-my-opencode repo
      5. Assert: all target image files exist
    Expected Result: 공개 자산 4개 이상 스크린샷 확보
    Failure Indicators: 파일 미생성, 빈 이미지, 404 페이지 캡처
    Evidence: .sisyphus/evidence/shot-*.png

  Scenario: 캡처 매트릭스 완결성 검증
    Tool: Bash
    Preconditions: README.md 체크리스트/매트릭스 업데이트 완료
    Steps:
      1. Extract screenshot checklist block from README.md
      2. Assert: each item includes source + output path + owner
      3. Assert: manual-only items are explicitly tagged [MANUAL]
      4. Save report: .sisyphus/evidence/screenshot-matrix-check.txt
    Expected Result: 자동/수동 경계가 명확한 실행 가능한 체크리스트
    Failure Indicators: source/path/owner 누락 항목 존재
    Evidence: .sisyphus/evidence/screenshot-matrix-check.txt
  ```

  **Commit**: NO

---

- [ ] 4. 최종 통합 검증 + Marp 빌드 + evidence 정리

  **What to do**:
  - `README.md` 전체에 대해 구조/키워드/시간/슬라이드 수 검증 실행
  - Marp HTML 재빌드 및 산출물 무결성 확인
  - 모든 검증 결과를 `.sisyphus/evidence/`에 저장

  **Must NOT do**:
  - 실패한 검증을 무시하고 완료 처리 금지
  - 수동 확인 문구를 acceptance 기준으로 사용 금지

  **Recommended Agent Profile**:
  - **Category**: `quick`
    - Reason: 반복 가능한 CLI 검증/빌드 수행 태스크
  - **Skills**: []
  - **Skills Evaluated but Omitted**:
    - `playwright`: 이 태스크 핵심은 문서/빌드 검증

  **Parallelization**:
  - **Can Run In Parallel**: NO
  - **Parallel Group**: Wave 3 (final)
  - **Blocks**: None
  - **Blocked By**: Task 2, Task 3

  **References**:
  - `README.md` - 최종 검증 대상 원본
  - `slides.html` - 빌드 산출물
  - `.sisyphus/evidence/` - 검증 로그/증거 저장 경로

  **Acceptance Criteria**:
  - [ ] `npx @marp-team/marp-cli --html README.md -o slides.html` 성공
  - [ ] 슬라이드 수 12~16장
  - [ ] 금지 키워드(녹화/영상재생/OBS/QuickTime) 0건
  - [ ] 타이밍 총합 15~20분
  - [ ] 최종 검증 로그 `.sisyphus/evidence/final-build-check.txt` 생성

  **Agent-Executed QA Scenarios**:

  ```text
  Scenario: 최종 빌드 및 산출물 검증
    Tool: Bash
    Preconditions: Task 2, Task 3 완료
    Steps:
      1. Run: npx @marp-team/marp-cli --html README.md -o slides.html
      2. Assert: exit code 0
      3. Assert: slides.html exists and size > 10KB
      4. Save output: .sisyphus/evidence/final-build-check.txt
    Expected Result: 최신 HTML 슬라이드 생성 성공
    Failure Indicators: 빌드 에러, 산출물 미생성
    Evidence: .sisyphus/evidence/final-build-check.txt

  Scenario: 최종 규칙 준수 검증
    Tool: Bash
    Preconditions: README.md 최신 상태
    Steps:
      1. Count separators: grep -c '^---$' README.md
      2. Compute slides count and assert 12~16
      3. grep -Eic '녹화|영상 재생|OBS|QuickTime' README.md -> assert 0
      4. Parse [~N분] annotations and assert sum 15~20
      5. Append all results: .sisyphus/evidence/final-build-check.txt
    Expected Result: 핵심 가드레일 위반 없음
    Failure Indicators: 범위 이탈(장수/시간/금지키워드)
    Evidence: .sisyphus/evidence/final-build-check.txt
  ```

  **Commit**: NO

---

- [ ] 5. Git commit + push (+ PR)

  **What to do**:
  - 변경사항이 전부 반영된 상태에서 Git 상태 확인
  - 새 브랜치 생성(기본값): `presentation/story-demo-live`
  - 커밋 생성(기본값): `docs(presentation): strengthen storyline and switch demo to live format`
  - 원격(origin)으로 푸시
  - GitHub CLI(`gh`)가 사용 가능하면 PR 생성(기본값)
    - Base: `main`
    - Title: `docs(presentation): strengthen storyline + live demo + agent models`
    - Body: 변경 포인트(스토리 재배치/라이브 데모 전환/Agent Models 슬라이드/스크린샷 매트릭스)

  **Must NOT do**:
  - `--force` 푸시 금지
  - 사용자 동의 없이 `main`에 직접 push 금지(기본은 브랜치 + PR)
  - `.env`, 토큰, 개인 키 등 시크릿 커밋 금지

  **Recommended Agent Profile**:
  - **Category**: `quick`
    - Reason: Git 작업(스테이징/커밋/브랜치/푸시/PR)은 절차적이고 짧은 태스크
  - **Skills**: [`git-master`]
    - `git-master`: 안전한 커밋 단위, 브랜치/PR, 훅 실패 대응
  - **Skills Evaluated but Omitted**:
    - `playwright`: 캡처는 이미 Task 3에서 처리

  **Parallelization**:
  - **Can Run In Parallel**: NO
  - **Parallel Group**: Wave 4 (final)
  - **Blocks**: None
  - **Blocked By**: Task 4

  **References**:
  - `.sisyphus/boulder.json` - 현재 active plan / 세션 연결 상태 확인
  - `.sisyphus/plans/opencode-presentation-story-demo-live.md` - 변경 목적/커밋 메시지 근거

  **Acceptance Criteria**:
  - [ ] `git status`가 clean 상태(커밋 후 변경 없음)
  - [ ] `git log -1 --oneline`에 위 커밋 메시지가 존재
  - [ ] `git ls-remote --heads origin presentation/story-demo-live`가 커밋을 포함
  - [ ] (가능 시) `gh pr view --json url -q .url`로 PR URL 출력

  **Agent-Executed QA Scenarios**:

  ```text
  Scenario: 브랜치 생성 + 푸시 + PR 생성
    Tool: Bash (git, gh)
    Preconditions: Task 4 완료, 네트워크 접근 가능, origin remote 설정됨
    Steps:
      1. git status --porcelain -> Assert: staged/unstaged 원하는 범위 확인
      2. git checkout -b presentation/story-demo-live (이미 존재하면 checkout)
      3. git add README.md slides.html .sisyphus/plans/opencode-presentation-story-demo-live.md
      4. git commit -m "docs(presentation): strengthen storyline and switch demo to live format"
      5. git push -u origin presentation/story-demo-live
      6. If gh available: gh pr create --base main --head presentation/story-demo-live --title "docs(presentation): strengthen storyline + live demo + agent models" --body "(autogen body)"
      7. Assert: push success, PR URL captured
    Expected Result: 원격 브랜치 푸시 + PR 생성(가능 시)
    Failure Indicators: auth 실패, remote 없음, pre-commit 훅 실패
    Evidence: PR URL + git status output captured
  ```

  **Commit**: YES

---

## Commit Strategy

| After Task | Message | Files | Verification |
|---|---|---|---|
| 5 | `docs(presentation): strengthen storyline and switch demo to live format` | `README.md`, `slides.html`, `.sisyphus/plans/opencode-presentation-story-demo-live.md` | Task 4 final build + Task 5 push |

---

## Success Criteria

### Verification Commands
```bash
# Final build
npx @marp-team/marp-cli --html README.md -o slides.html

# Forbidden pre-recorded terms must be zero
grep -Eic '녹화|영상 재생|OBS|QuickTime' README.md

# Slide count (frontmatter separator included in grep count)
TOTAL=$(grep -c '^---$' README.md); echo "Slides: $((TOTAL - 1))"

# Timing tokens existence check
grep -o '\[~[0-9.]\+분\]' README.md
```

### Final Checklist
- [ ] 라이브 데모 중심 스토리로 개편됨
- [ ] 사전녹화 문맥 완전 제거됨
- [ ] 스크린샷 체크리스트가 실행 가능한 매트릭스로 완성됨
- [ ] 공개 증거 스크린샷이 확보됨
- [ ] Marp 빌드 및 검증 로그 저장 완료
