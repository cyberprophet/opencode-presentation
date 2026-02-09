# OpenCode 발표 준비 — 바이브 코딩 랩 발표

## TL;DR

> **Quick Summary**: 바이브 코딩 랩(20명) 대상 15~20분 OpenCode + OhMyOpenCode 실전 활용 가이드 발표를 위한 Marp 슬라이드 제작 및 발표 준비 작업 계획.
> 
> **Deliverables**:
> - Marp Markdown 슬라이드 파일 (`slides.md`) — 12~15장, 한국어 + 영어 기술용어
> - 슬라이드별 스피커 노트 (발표자용 메모)
> - 스크린샷 캡처 체크리스트 (발표자 행동 필요)
> - 데모 녹화 시나리오 스크립트
> - HTML 빌드 출력 파일 (`slides.html`)
> 
> **Estimated Effort**: Medium (슬라이드 제작 + 녹화 계획 + 빌드 검증)
> **Parallel Execution**: YES — 2 waves
> **Critical Path**: Task 1 (스크린샷 체크리스트) → Task 2 (슬라이드 제작) → Task 3 (빌드 검증)

---

## Context

### Original Request
바이브 코딩 랩에서 20명 대상으로 OpenCode에 대해 15~20분 발표 준비. 이번 주 안에 준비 필요. 발표자는 OpenCode + OhMyOpenCode를 사용하여 실제 VS Code 확장프로그램과 Flutter 패키지들을 바이브 코딩만으로 제작/배포한 경험 보유.

### Interview Summary
**Key Discussions**:
- **발표 톤**: 실전 활용 가이드 ("이렇게 쓰면 이런 결과가 나옵니다")
- **청중 수준**: 대부분 Claude 사용자, OpenCode는 이름만 들어봄
- **슬라이드 도구**: Marp (Markdown 기반 프레젠테이션)
- **강조점**: OpenCode + OhMyOpenCode 균형 있게
- **언어**: 한국어 + 영어 기술용어
- **딥다이브 프로젝트**: diff-to-commit (VS Code 확장) + flutter_device_unique_id (Flutter 플러그인, pub.dev 패키지명: `flutter_device_platform_id` / GitHub 레포명: `flutter-device-unique-id`)
- **나머지 프로젝트**: flutter_image_conversion, flutter_native_image_compress → 요약 슬라이드 1장
- **Q&A**: 발표 후 별도 자유 Q&A (15~20분 온전히 발표 내용에 사용)
- **신화 스토리**: 에이전트 캐릭터 네이밍(Prometheus, Sisyphus 등) 발표에 포함 희망
- **데모**: 녹화 영상 권장 (라이브 데모 리스크 회피)
- **다른 툴 비교**: 하지 않음 (발표자가 잘 모름)

**Research Findings**:
- **OpenCode**: 오픈소스 터미널 기반 AI 코딩 에이전트, 75+ LLM 프로바이더, Go 기반 TUI, 10.8k GitHub stars
- **OhMyOpenCode**: 멀티 에이전트 오케스트레이션 레이어, 29.6k stars, 6~7개 전문 에이전트, 병렬 실행 지원
- **발표자 산출물**: 4개 프로젝트 모두 pub.dev/VS Code Marketplace에 배포 완료, MIT 라이선스

### Metis Review
**Identified Gaps** (addressed):
- **슬라이드 언어**: 한국어 + 영어 기술용어로 확정
- **프로젝트 딥다이브 수**: 2개 (diff-to-commit, flutter_device_unique_id) + 나머지 요약 1장
- **Q&A 시간**: 별도 → 15~20분 전체 콘텐츠 사용 가능
- **스크린샷 부재**: Asset Capture Checklist를 첫 번째 태스크로 생성
- **한국어 폰트 렌더링**: Marp 커스텀 CSS에 Noto Sans KR / Pretendard 포함
- **Marp 영상 미지원**: 데모는 별도 파일로 재생, 슬라이드에 "데모 타임" 플레이스홀더
- **스코프 크리프 방지**: 커스텀 테마 금지(인라인 style만), 비교 슬라이드 금지, 프로젝트 최대 2개 딥다이브

---

## Work Objectives

### Core Objective
바이브 코딩 랩 청중이 "나도 OpenCode + OhMyOpenCode를 써보고 싶다"고 느낄 수 있는 15~20분 발표 자료 제작.

### Concrete Deliverables
- `slides.md` — Marp Markdown 슬라이드 (12~15장, frontmatter + 인라인 style 포함)
- `slides.html` — Marp 빌드 HTML 출력
- 스크린샷 캡처 체크리스트 (스피커 노트 또는 별도 섹션)
- 데모 녹화 시나리오 스크립트 (slides.md 내 주석 또는 별도 안내)

### Definition of Done
- [ ] `npx @marp-team/marp-cli --html slides.md -o slides.html` → exit code 0
- [ ] 슬라이드 수 12~15장 (검증: `awk '/^---$/{n++}END{print n}' slides.md` 결과에서 frontmatter 구분자 2개를 뺀 값이 11~14 → 즉, 총 `---` 수가 13~16)
- [ ] 모든 콘텐츠 슬라이드에 스피커 노트(`<!-- -->`) 존재
- [ ] 한국어 텍스트가 HTML 출력에서 정상 렌더링
- [ ] 슬라이드당 가시적 콘텐츠 7줄 이하 (텍스트 벽 방지)

> **NOTE: 슬라이드 수 카운트 방법**
> Marp 파일은 YAML frontmatter(`---` ... `---`)로 시작하므로, `grep -c "^---$"`는 frontmatter 구분자 2개를 포함합니다.
> 정확한 슬라이드 수 = `(총 --- 수) - 2 + 1` = `총 --- 수 - 1`
> 예: 14장 슬라이드 = frontmatter 2개 + 슬라이드 구분 13개 = 총 `---` 15개

### Must Have
- "회의론자 → 발견 → 활용 → 성과" 내러티브 구조
- OpenCode 소개 (what + why)
- OhMyOpenCode 소개 (멀티 에이전트, 신화 스토리)
- 실제 산출물 쇼케이스 (diff-to-commit 딥다이브, flutter_device_unique_id 딥다이브)
- 시작하기 가이드 (설치 명령어, 첫 단계)
- 스피커 노트 (슬라이드별 3~5개 불릿포인트)
- 이미지 플레이스홀더 (`<!-- TODO: [설명] -->` 형태)
- 타이밍 어노테이션 (스피커 노트에 `[~N분]`)

### Must NOT Have (Guardrails)
- ❌ 다른 툴(Cursor, Claude Code, Copilot)과의 비교 슬라이드
- ❌ 별도 Marp 커스텀 테마 파일 (인라인 `<style>` ≤ 40줄만)
- ❌ 프로젝트 딥다이브 3개 이상 (최대 2개 + 요약 1장)
- ❌ package.json / 빌드 시스템 구축 (npx 직접 실행)
- ❌ 발표자가 Q&A에서 설명할 수 없는 기술적 깊이
- ❌ 장문의 스피커 대본 (불릿포인트 메모만)
- ❌ 애니메이션, 임베디드 비디오 (Marp 미지원)
- ❌ `--html` 플래그 없이 raw HTML 사용

---

## Verification Strategy (MANDATORY)

> **UNIVERSAL RULE: ZERO HUMAN INTERVENTION**
>
> ALL tasks in this plan MUST be verifiable WITHOUT any human action.

### Test Decision
- **Infrastructure exists**: YES — `@marp-team/marp-cli v4.2.3` globally available
- **Automated tests**: None (프레젠테이션 프로젝트, 코드 테스트 불필요)
- **Framework**: Marp CLI for build verification

### Agent-Executed QA Scenarios (MANDATORY — ALL tasks)

**Verification Tool by Deliverable Type:**

| Type | Tool | How Agent Verifies |
|------|------|-------------------|
| Marp 슬라이드 빌드 | Bash (npx marp-cli) | 빌드 실행, exit code 확인, HTML 출력 검증 |
| 슬라이드 구조 검증 | Bash (grep/wc) | 슬라이드 수, 스피커노트 수, 콘텐츠 라인 수 |
| 한국어 렌더링 | Bash (grep) | HTML 출력에서 한국어 문자 존재 확인 |
| 이미지 플레이스홀더 | Bash (grep) | `TODO` 마커 수 확인 |

---

## Execution Strategy

### Parallel Execution Waves

```
Wave 1 (Start Immediately):
├── Task 1: 슬라이드 구조 설계 + 스크린샷 체크리스트
└── Task 3: 데모 녹화 시나리오 스크립트

Wave 2 (After Wave 1):
└── Task 2: slides.md 본문 작성 + 스피커 노트 + Marp 빌드

Critical Path: Task 1 → Task 2
Parallel Speedup: Task 3은 Task 1과 병렬 가능
```

### Dependency Matrix

| Task | Depends On | Blocks | Can Parallelize With |
|------|------------|--------|---------------------|
| 1 | None | 2 | 3 |
| 2 | 1 | None (final) | None |
| 3 | None | None | 1 |

### Agent Dispatch Summary

| Wave | Tasks | Recommended Agents |
|------|-------|-------------------|
| 1 | 1, 3 | task(category="writing") / task(category="quick") |
| 2 | 2 | task(category="writing") — 핵심 태스크 |

---

## Proposed Slide Structure (14 Slides)

> 발표 시간: 15~20분 / 슬라이드당 ~1.5분 / 한국어 + 영어 기술용어

| # | 슬라이드 제목 | 내용 요약 | 시간 |
|---|-------------|----------|------|
| 1 | 타이틀 | 발표 제목 + 발표자 소개 | 0.5분 |
| 2 | 바이브 코딩, 왜 관심 없었나 | 기존 툴의 한계, 회의론 | 1분 |
| 3 | OpenCode를 만나다 | OpenCode가 뭔지, 왜 다른지 (오픈소스, 75+ LLM, TUI) | 1.5분 |
| 4 | OpenCode 핵심 특징 | 터미널 기반, 세션 관리, LSP 통합, 프로바이더 자유 | 1.5분 |
| 5 | OhMyOpenCode: 한 단계 더 | 멀티 에이전트 오케스트레이션 소개 | 1.5분 |
| 6 | 신화 속 에이전트들 | Prometheus(기획), Sisyphus(실행) 등 에이전트 캐릭터 소개 | 1분 |
| 7 | 멀티 에이전트가 일하는 방식 | 병렬 실행, 계획→실행→검증 플로우 | 1.5분 |
| 8 | 🎬 데모 타임 | 녹화 영상 재생 (별도 파일) | 1.5분 |
| 9 | 산출물: diff-to-commit | VS Code 확장프로그램 딥다이브 | 1.5분 |
| 10 | 산출물: flutter_device_unique_id | Flutter 플러그인 딥다이브 (pub.dev 패키지명: flutter_device_platform_id) | 1.5분 |
| 11 | 그 외 산출물들 | flutter_image_conversion, native_image_compress 요약 | 1분 |
| 12 | 왜 결과물이 다른가 | 다른 툴 대비 만족도 높은 이유 (개인 경험 기반) | 1.5분 |
| 13 | 시작하기 | 설치 명령어, 첫 번째 해볼 것, 참고 링크 | 1분 |
| 14 | 감사합니다 / Q&A | 마무리 + GitHub/연락처 | 0.5분 |

---

## TODOs

- [ ] 1. 슬라이드 구조 설계 + 스크린샷 캡처 체크리스트

  **What to do**:
  - 위 "Proposed Slide Structure" 14장 기준으로 슬라이드 아웃라인 확정
  - 각 슬라이드에 필요한 스크린샷/이미지 목록 생성 (발표자가 직접 캡처해야 할 항목)
  - 스크린샷 체크리스트를 `slides.md` 맨 상단에 HTML 주석으로 포함
  - Marp frontmatter 구조 확정 (`marp: true`, `theme`, `paginate` 등)
  - 인라인 `<style>` 블록 작성 (한국어 폰트 import, 다크 테마 스타일링, ≤ 40줄)

  **Must NOT do**:
  - 별도 CSS/테마 파일 생성 금지
  - 실제 슬라이드 본문 콘텐츠 작성은 Task 2에서
  - 40줄 초과하는 스타일 금지

  **Recommended Agent Profile**:
  - **Category**: `writing`
    - Reason: 발표 구조 설계와 체크리스트 작성은 문서 작성 작업
  - **Skills**: []
    - 특별한 기술 스킬 불필요

  **Parallelization**:
  - **Can Run In Parallel**: YES
  - **Parallel Group**: Wave 1 (with Task 3)
  - **Blocks**: Task 2
  - **Blocked By**: None

  **References**:

  **Pattern References**:
  - Marp 공식 문서: https://marpit.marp.app/directives — frontmatter 및 directive 문법
  - Marp 테마 가이드: https://github.com/marp-team/marp-core/blob/main/themes/ — 빌트인 테마 참고

  **프로젝트 참고 (스크린샷 대상)**:
  - `https://marketplace.visualstudio.com/items?itemName=Dayond.diff-to-commit` — diff-to-commit Marketplace 페이지
  - `https://pub.dev/packages/flutter_device_platform_id` — flutter_device_unique_id pub.dev 페이지 (pub.dev 패키지명: flutter_device_platform_id / GitHub 레포명: flutter-device-unique-id)
  - `https://pub.dev/packages/flutter_image_conversion` — flutter_image_conversion pub.dev 페이지
  - `https://pub.dev/packages/flutter_native_image_compress` — native_image_compress pub.dev 페이지
  - `https://github.com/opencode-ai/opencode` — OpenCode GitHub (TUI 스크린샷 참고)
  - `https://github.com/code-yeongyu/oh-my-opencode` — OhMyOpenCode GitHub (에이전트 구조 참고)

  **Acceptance Criteria**:

  **Agent-Executed QA Scenarios:**

  ```
  Scenario: Marp frontmatter 및 style 블록 유효성 확인
    Tool: Bash
    Preconditions: slides.md 파일 존재
    Steps:
      1. head -5 slides.md → "marp: true" 포함 확인
      2. grep -c "<style" slides.md → 1 이상
      3. style 블록 라인 수 카운트 → 40줄 이하 확인
      4. npx @marp-team/marp-cli --html slides.md -o /tmp/test-structure.html
      5. Assert: exit code 0
    Expected Result: frontmatter 유효, style ≤ 40줄, 빌드 성공
    Evidence: 빌드 출력 로그

  Scenario: 스크린샷 체크리스트 존재 확인
    Tool: Bash
    Preconditions: slides.md 파일 존재
    Steps:
      1. grep -c "TODO:" slides.md
      2. Assert: 5개 이상의 TODO 마커 존재 (각 슬라이드별 필요 이미지)
    Expected Result: 발표자가 캡처해야 할 스크린샷 목록이 명확히 마킹됨
    Evidence: grep 출력
  ```

  **Commit**: OPTIONAL (Git 저장소가 없으면 건너뜀)
  - Pre-condition: `git rev-parse --is-inside-work-tree 2>/dev/null` → true이면 커밋 진행
  - 저장소 없으면: `git init && git add -A && git commit -m "docs(slides): add slide structure outline with asset capture checklist"`
  - Message: `docs(slides): add slide structure outline with asset capture checklist`
  - Files: `slides.md`

---

- [ ] 2. slides.md 본문 작성 + 스피커 노트 + Marp 빌드

  **What to do**:
  - Task 1에서 만든 구조 기반으로 14장 슬라이드 본문 콘텐츠 작성
  - 각 슬라이드별 스피커 노트 추가 (`<!-- 스피커 노트 내용 -->` 형식, 3~5 불릿포인트)
  - 스피커 노트에 타이밍 어노테이션 포함 (`[~1.5분]`)
  - 내러티브 구조 유지: 회의론 → 발견 → OhMyOpenCode의 힘 → 실제 성과 → 시작하기
  - 슬라이드 내용 한국어 + 영어 기술용어 혼용
  - 이미지가 필요한 곳에 `<!-- TODO: [구체적 설명] -->` 플레이스홀더 삽입
  - 코드 블록 사용하여 설치 명령어, 사용 예시 등 포함
  - 데모 슬라이드(#8)에 "▶️ 데모 타임" 플레이스홀더 + 안내
  - 최종 Marp 빌드: `npx @marp-team/marp-cli --html slides.md -o slides.html`

  **슬라이드별 콘텐츠 가이드라인**:

  | 슬라이드 | 핵심 내용 | 비고 |
  |---------|----------|------|
  | #1 타이틀 | "OpenCode + OhMyOpenCode 실전 활용기" / 발표자명 | 깔끔하게 |
  | #2 회의론 | "바이브 코딩? 글쎄..." / 기존 툴의 한계점 2~3개 | 공감 유도 |
  | #3 OpenCode 발견 | 오픈소스, 터미널 기반, 75+ LLM 지원 | 핵심 3개만 |
  | #4 OpenCode 특징 | TUI, 세션 관리, LSP, 프로바이더 자유 | 아이콘/이모지 활용 |
  | #5 OhMyOpenCode | "한 단계 더" — 멀티 에이전트 오케스트레이션 | 전환점 |
  | #6 신화 에이전트 | Prometheus→Sisyphus→Explorer 등 역할 설명 | 재미 요소 |
  | #7 작동 방식 | 계획→실행→검증 플로우 (텍스트/이모지 다이어그램) | 간결하게 |
  | #8 데모 | "▶️ 데모 타임" + 녹화 영상 재생 안내 | 별도 파일 |
  | #9 diff-to-commit | 기능 소개, Marketplace 링크, 핵심 코드 | 딥다이브 |
  | #10 flutter_device_unique_id | 5개 플랫폼 지원, pub.dev(flutter_device_platform_id), 4 stars | 딥다이브 |
  | #11 기타 산출물 | image_conversion + native_image_compress 한 줄씩 | 요약 |
  | #12 왜 다른가 | 결과물 만족도 높은 이유 (개인 경험) | 설득력 |
  | #13 시작하기 | `curl -fsSL https://opencode.ai/install \| bash` 등 | 행동 유도 |
  | #14 마무리 | 감사합니다 + GitHub 링크 | 깔끔하게 |

  **Must NOT do**:
  - 슬라이드당 7줄 초과 콘텐츠 금지
  - 다른 툴과의 비교 금지
  - 장문 스피커 대본 금지 (불릿포인트만)
  - `--html` 플래그 없이 raw HTML 사용 금지
  - 15장 초과 슬라이드 금지

  **Recommended Agent Profile**:
  - **Category**: `writing`
    - Reason: 발표 콘텐츠 작성, 스토리텔링, 스피커 노트 — 모두 문서 작성 영역
  - **Skills**: []
    - 특별한 기술 스킬 불필요

  **Parallelization**:
  - **Can Run In Parallel**: NO
  - **Parallel Group**: Wave 2 (sequential)
  - **Blocks**: None (최종 태스크)
  - **Blocked By**: Task 1

  **References**:

  **Pattern References**:
  - Marp Markdown 문법: https://marpit.marp.app/markdown — 슬라이드 구분, 이미지, 코드 블록
  - Marp directives: https://marpit.marp.app/directives — 페이지별 directive, 배경 이미지

  **콘텐츠 참고 (발표 내용 소스)**:
  - OpenCode GitHub README: `https://github.com/opencode-ai/opencode` — 기능 목록, 설치 방법
  - OpenCode 공식 문서: `https://opencode.ai/docs/cli/` — CLI 명령어, 플래그
  - OhMyOpenCode GitHub: `https://github.com/code-yeongyu/oh-my-opencode` — 에이전트 구조, 설치법
  - diff-to-commit README: `https://github.com/cyberprophet/diff-to-commit` — 기능, 명령어, 보안
  - flutter_device_unique_id README: `https://github.com/cyberprophet/flutter-device-unique-id` — 플랫폼별 구현, API
  - flutter_image_conversion README: `https://github.com/cyberprophet/flutter-image-conversion` — 플랫폼 지원 매트릭스
  - flutter_native_image_compress README: `https://github.com/cyberprophet/native-image-compress` — 포맷 지원

  **WHY Each Reference Matters**:
  - OpenCode GitHub/문서 → 슬라이드 #3, #4의 기능 목록과 설치 명령어 소스
  - OhMyOpenCode GitHub → 슬라이드 #5, #6, #7의 에이전트 구조와 작동 방식 소스
  - diff-to-commit → 슬라이드 #9 딥다이브 콘텐츠 소스
  - flutter_device_unique_id → 슬라이드 #10 딥다이브 콘텐츠 소스
  - 나머지 2개 → 슬라이드 #11 요약 콘텐츠 소스

  **Acceptance Criteria**:

  **Agent-Executed QA Scenarios:**

  ```
  Scenario: Marp 빌드 성공 및 HTML 출력 검증
    Tool: Bash
    Preconditions: slides.md에 전체 콘텐츠 작성 완료
    Steps:
      1. npx @marp-team/marp-cli --html slides.md -o slides.html
      2. Assert: exit code 0
      3. ls -la slides.html → 파일 존재, 크기 > 10KB
      4. grep -c "한국" slides.html → 1 이상 (한국어 렌더링 확인)
    Expected Result: HTML 파일 정상 생성, 한국어 포함
    Evidence: 빌드 로그 + 파일 크기

  Scenario: 슬라이드 수 범위 검증 (frontmatter --- 제외)
    Tool: Bash
    Preconditions: slides.md 작성 완료
    Steps:
      1. TOTAL_SEPARATORS=$(grep -c "^---$" slides.md)
      2. SLIDE_COUNT=$(( TOTAL_SEPARATORS - 2 + 1 ))  # frontmatter --- 2개 제외, +1은 첫 슬라이드
      3. Assert: SLIDE_COUNT가 12~15 사이
      4. 대안 검증: npx @marp-team/marp-cli --html slides.md -o /tmp/count-check.html && grep -c 'class="slide"' /tmp/count-check.html (정확한 슬라이드 수)
    Expected Result: 슬라이드 수가 목표 범위 12~15 내
    Evidence: 카운트 출력

  Scenario: 스피커 노트 완성도 확인
    Tool: Bash
    Preconditions: slides.md 작성 완료
    Steps:
      1. grep -c "<!--" slides.md
      2. SLIDE_COUNT=$(( $(grep -c "^---$" slides.md) + 1 ))
      3. Assert: 스피커 노트 수 ≥ SLIDE_COUNT - 2 (타이틀/마무리 제외)
    Expected Result: 대부분의 슬라이드에 스피커 노트 존재
    Evidence: grep 출력 비교

  Scenario: 텍스트 벽 방지 확인
    Tool: Bash
    Preconditions: slides.md 작성 완료
    Steps:
      1. awk 스크립트로 각 슬라이드 섹션의 가시적 콘텐츠 라인 수 카운트
      2. (빈 줄, 주석, frontmatter, style 블록 제외)
      3. Assert: 모든 섹션이 7줄 이하
    Expected Result: 텍스트 과다 슬라이드 없음
    Evidence: awk 스크립트 출력

  Scenario: 이미지 플레이스홀더 존재 확인
    Tool: Bash
    Preconditions: slides.md 작성 완료
    Steps:
      1. grep -c "TODO:" slides.md
      2. Assert: 5개 이상 (주요 슬라이드에 이미지 슬롯)
    Expected Result: 발표자가 채워야 할 이미지 위치가 명확히 마킹됨
    Evidence: grep 출력
  ```

  **Evidence to Capture:**
  - [ ] Marp 빌드 로그 → `.sisyphus/evidence/task-2-marp-build.log`
  - [ ] 슬라이드 수 검증 → `.sisyphus/evidence/task-2-slide-count.txt`
  - [ ] 스피커 노트 검증 → `.sisyphus/evidence/task-2-speaker-notes.txt`

  **Commit**: OPTIONAL (Git 저장소 존재 시에만)
  - Pre-condition: `git rev-parse --is-inside-work-tree 2>/dev/null` → true이면 커밋 진행
  - Message: `docs(slides): complete presentation content with speaker notes and build`
  - Files: `slides.md`, `slides.html`
  - Pre-commit: `npx @marp-team/marp-cli --html slides.md -o slides.html`

---

- [ ] 3. 데모 녹화 시나리오 스크립트

  **What to do**:
  - 90초 이내 데모 시나리오 작성 (slides.md 내 주석 블록 또는 별도 안내)
  - 시나리오: "OpenCode + OhMyOpenCode로 간단한 기능 구현하기"
  - 단계별 녹화 행동 리스트 (번호 매김, 각 단계 10~15초)
  - 녹화 도구 추천 포함 (OBS Studio, QuickTime 등)
  - slides.md의 데모 슬라이드(#8) 스피커 노트에 재생 안내 포함

  **추천 데모 시나리오**:
  ```
  1. 터미널에서 OpenCode 실행 (TUI 화면 보여주기) — 10초
  2. 간단한 프롬프트 입력 (예: "유틸리티 함수 만들어줘") — 10초
  3. OhMyOpenCode 에이전트 활성화 표시 — 10초
  4. 멀티 에이전트가 병렬로 작업하는 모습 — 20초
  5. 결과물 생성 완료 + 코드 확인 — 15초
  6. 테스트 통과 화면 — 10초
  7. 커밋 메시지 자동 생성 (diff-to-commit 시연) — 15초
  ```

  **Must NOT do**:
  - 데모를 발표 자료 완성의 블로커로 만들지 않음
  - 5분 이상의 데모 금지 (90초 이내)
  - 복잡한 프로젝트 생성 시도 금지 (간단한 유틸리티 함수 수준)

  **Recommended Agent Profile**:
  - **Category**: `quick`
    - Reason: 시나리오 스크립트 작성은 간단한 문서 태스크
  - **Skills**: []

  **Parallelization**:
  - **Can Run In Parallel**: YES
  - **Parallel Group**: Wave 1 (with Task 1)
  - **Blocks**: None
  - **Blocked By**: None

  **References**:

  **콘텐츠 참고**:
  - OhMyOpenCode 에이전트 실행 예시: `https://github.com/code-yeongyu/oh-my-opencode` — README의 실행 화면/설명
  - OpenCode CLI 명령어: `https://opencode.ai/docs/cli/` — `opencode run`, `opencode` TUI 시작
  - OhMyOpenCode YouTube 데모: `https://www.youtube.com/watch?v=G_Snfh2M41M` — 실제 사용 영상 참고 (타임스탬프 8:45~15:30)

  **WHY Each Reference Matters**:
  - OhMyOpenCode GitHub → 에이전트 실행 시 터미널에 보이는 화면 구조 파악
  - OpenCode CLI 문서 → 데모에서 사용할 정확한 명령어 확인
  - YouTube 영상 → 실제 데모 흐름 참고 (어떤 화면이 인상적인지)

  **Acceptance Criteria**:

  **Agent-Executed QA Scenarios:**

  ```
  Scenario: 데모 시나리오 스크립트 완성도 확인
    Tool: Bash
    Preconditions: slides.md 또는 별도 파일에 시나리오 존재
    Steps:
      1. grep -c "데모" slides.md → 관련 콘텐츠 존재 확인
      2. 시나리오 단계가 5개 이상 번호 매김으로 작성되었는지 확인
      3. "녹화" 또는 "OBS" 또는 "QuickTime" 키워드 존재 확인
    Expected Result: 구체적인 단계별 녹화 시나리오 + 도구 안내
    Evidence: grep 출력
  ```

  **Commit**: OPTIONAL (Task 2와 함께 커밋, Git 저장소 존재 시에만)
  - Message: `docs(slides): add demo recording scenario script`
  - Files: `slides.md` (데모 관련 주석/스피커노트)

---

## Git & Commit Strategy

> **NOTE**: 현재 워크스페이스는 Git 저장소가 아닙니다 (`/home/cyberprophet/source/presentation`에 `.git` 없음).
> 커밋은 **선택 사항**입니다. 에이전트는 먼저 `git rev-parse --is-inside-work-tree 2>/dev/null`로 확인 후:
> - ✅ Git 존재 → 커밋 진행
> - ❌ Git 미존재 → `git init` 후 커밋하거나, 커밋 단계를 건너뜀

| After Task | Message | Files | Verification |
|------------|---------|-------|--------------|
| 1 | `docs(slides): add slide structure outline with asset capture checklist` | slides.md | `head -5 slides.md` → marp: true |
| 2+3 | `docs(slides): complete presentation with content, speaker notes, and demo script` | slides.md, slides.html | `npx @marp-team/marp-cli --html slides.md -o slides.html` → exit 0 |

---

## Success Criteria

### Verification Commands
```bash
# 1. Marp 빌드 성공
npx @marp-team/marp-cli --html slides.md -o slides.html
# Expected: exit code 0, slides.html 파일 생성

# 2. 슬라이드 수 확인 (frontmatter --- 2개 제외)
TOTAL=$(grep -c "^---$" slides.md); echo "Slides: $(( TOTAL - 2 + 1 ))"
# Expected: Slides: 12~15 (총 --- 수에서 frontmatter 2개 빼고 +1)

# 3. 스피커 노트 존재 확인
grep -c "<!--" slides.md
# Expected: 10 이상

# 4. 한국어 렌더링 확인
grep -c "한국\|바이브\|발표\|에이전트" slides.html
# Expected: 1 이상

# 5. 이미지 플레이스홀더 확인
grep -c "TODO:" slides.md
# Expected: 5 이상
```

### Final Checklist
- [ ] slides.md 존재, Marp 빌드 성공
- [ ] 12~15장 슬라이드
- [ ] 모든 콘텐츠 슬라이드에 스피커 노트
- [ ] 한국어 + 영어 기술용어 혼용
- [ ] 스크린샷 캡처 체크리스트 (TODO 마커)
- [ ] 데모 녹화 시나리오 스크립트
- [ ] 타이밍 어노테이션
- [ ] 텍스트 벽 없음 (슬라이드당 ≤ 7줄)
- [ ] 다른 툴 비교 슬라이드 없음
- [ ] 프로젝트 딥다이브 ≤ 2개
