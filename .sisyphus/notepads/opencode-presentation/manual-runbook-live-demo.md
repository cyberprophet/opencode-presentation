# Manual Runbook — opencode-presentation-story-demo-live (2026-02-09)

## 목적
Opus와 만들었던 기존 Marp 덱(`README.md`)을 **라이브 데모 중심 + 증거(산출물) 앞당김 + Agent Models 설명 강화** 방향으로 개편하고, 최종적으로 GitHub에 PR까지 올리는 것.

## 현재까지 확정된 결정(변경 금지)
- 데모: **라이브 데모**, **플랜 B(백업 영상) 없음**
- 발표 시간: **15~20분 유지**
- 슬라이드 수: **최대 16장**
- 금지: **타 툴 비교 슬라이드/문구 금지**
- 덱 소스: `README.md` (Marp)

## 현재 상태(정리)
- 실행 플랜(최신): `.sisyphus/plans/opencode-presentation-story-demo-live.md`
- 이전 플랜(사전녹화 전제): `.sisyphus/plans/opencode-presentation.md`
- 보울더 상태: `.sisyphus/boulder.json` -> 위 플랜을 active plan으로 지정
- 덱 소스 파일: `README.md` (현재는 **사전녹화 문구가 남아있음**)
- 증거 폴더: `.sisyphus/evidence/` (현재는 텍스트 로그만 있고 스크린샷은 없음)

## 이슈(왜 수동으로 하게 됐나)
서브에이전트 위임이 반복적으로 실패(`JSON Parse error: Unexpected EOF`)하여 자동 실행 대신 **발표자가 수동 편집**하는 경로로 전환.

---

## 수동 실행 체크리스트(발표자)

### 0) (선택) 브랜치 생성
> PR 작업을 깔끔하게 하려면 권장.

```bash
git checkout -b presentation/story-demo-live
```

---

### 1) 스크린샷 캡처 체크리스트를 “실행 가능한 매트릭스”로 교체
파일: `README.md`

`스크린샷 캡처 체크리스트 (발표자용)` 주석 블록을 아래로 교체:

```markdown
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
```

---

### 2) 슬라이드 순서 개편(증거를 6~8번 구간으로 전진)

목표 흐름(권장 최종 순서, 16장):
1. 타이틀
2. 회의론
3. OpenCode(전환점)
4. OhMyOpenCode(전환점 강화)
5. 🎬 **라이브 데모** (3분)
6. 산출물: diff-to-commit
7. 산출물: flutter_device_unique_id
8. 그 외 산출물들
9. 멀티 에이전트가 일하는 방식
10. Agent Models: 역할로 분리 (이미지 2장)
11. OpenCode 핵심 특징
12. 신화 속 에이전트들
13. 왜 결과물이 다른가(근거 기반으로 수정)
14. 시작하기
15. 감사합니다 / Q&A
16. Appendix: Agent Models (Full Map)

실행 방법(가장 쉬운 방식):
- `## 🎬 데모 타임` 슬라이드 블록을 통째로 **잘라내서** `OhMyOpenCode: 한 단계 더` 다음으로 이동(= 5번에 오도록)
- `## 산출물: diff-to-commit` ~ `## 그 외 산출물들` 블록(3장)을 **데모 직후**에 오도록 위치 조정
- `## 멀티 에이전트가 일하는 방식` 및 `## 신화 속 에이전트들`은 **증거(산출물) 뒤로** 미룸

> 참고: Marp는 `---`가 슬라이드 구분자이므로, 블록 이동 시 구분자까지 같이 옮기는 게 안전함.

---

### 3) 데모 슬라이드를 “사전녹화 -> 라이브”로 교체 (금지 키워드 제거)
파일: `README.md`

현재 `## 🎬 데모 타임` 슬라이드에는 다음 금지 문구가 남아 있음:
- `90초` / `녹화` / `영상 재생`

아래로 교체(예시 — 그대로 사용 가능):

```markdown
---

## 🎬 라이브 데모

실시간으로 OpenCode + OhMyOpenCode 실행 (3분 타임박스)

**절차**:
1. (사전 준비) 발표 5분 전에 `opencode` 1회 실행해서 초기 지연 제거
2. 터미널에서 `opencode` 실행(TUI)
3. 프롬프트 입력: `ulw - 배열 중복 제거 함수 + 테스트까지 만들어줘`
4. 멀티 에이전트 병렬 작업 흐름을 10~20초만 관찰(탭/로그 등)
5. 결과물 생성/테스트 통과 화면을 보여주고 다음 슬라이드로 이동

<!--
- [~3분] 라이브 데모
- 중단 신호(타임 오버/지연): "여기서부터는 결과 화면으로 넘어가겠습니다" 후 바로 산출물 슬라이드로
- 플랜 B 없음(라이브 단일 경로) -> 그래서 **타임박스 + 중단 멘트**가 핵심
-->
```

라이브 데모는 **정확한 명령어/프롬프트는 발표자 환경에 맞게** 조정해도 됨.
다만, 문서 검증 조건 때문에 `README.md` 내에 다음 키워드는 0건이어야 함:
- `녹화|영상 재생|OBS|QuickTime`

---

### 4) Agent Models 슬라이드 추가(이미지 링크 포함)
이미지 링크(확정):
- Sisyphus: https://raw.githubusercontent.com/code-yeongyu/oh-my-opencode/refs/heads/dev/.github/assets/sisyphus.png
- Hephaestus: https://raw.githubusercontent.com/code-yeongyu/oh-my-opencode/refs/heads/dev/.github/assets/hephaestus.png

아래 슬라이드를 적당한 위치(권장: `멀티 에이전트가 일하는 방식` 바로 뒤)로 삽입:

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
-->
```

---

### 5) Appendix 슬라이드(전체 Agent Models 표) 추가
Q&A 뒤에 아래를 추가:

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

---

### 6) "왜 결과물이 다른가" 슬라이드(근거 기반)로 문구 강화
현재는 추상(병렬/검증/프로바이더/품질) 나열이므로, 최소 1~2개는 **근거/구체**로 바꾸는 걸 권장.

예시(4줄 제한 유지):
- `ulw/ultrawork` 같은 트리거로 병렬 에이전트 동원(오케스트레이션)
- explore/librarian로 탐색을 병렬화(속도)
- 검증 루프(빌드/테스트/리뷰)로 완성도 끌어올림
- 결과: Marketplace/pub.dev 배포까지 연결

---

## 검증(발표자 로컬에서 실행)

```bash
# Marp 빌드
npx @marp-team/marp-cli --html README.md -o slides.html

# 금지 키워드(사전녹화 흔적) 제거 확인
grep -Eic '녹화|영상 재생|OBS|QuickTime' README.md

# 슬라이드 수 (--- 구분자 기반)
TOTAL=$(grep -c '^---$' README.md); echo "Slides: $((TOTAL - 1))"

# 타이밍 토큰 존재 확인
grep -o '\[~[0-9.]\+분\]' README.md
```

타이밍 총합(권장 — Python):

```bash
python - <<'PY'
import re, pathlib
text = pathlib.Path('README.md').read_text(encoding='utf-8')
mins = sum(float(x) for x in re.findall(r"\[~([0-9.]+)분\]", text))
print('Total minutes:', mins)
PY
```

---

## 스크린샷 캡처 가이드(파일명 고정)

### 공개 페이지(수동 캡처로도 OK)
- Marketplace: `.sisyphus/evidence/shot-diff-to-commit.png`
  - https://marketplace.visualstudio.com/items?itemName=Dayond.diff-to-commit
- pub.dev: `.sisyphus/evidence/shot-pubdev-flutter-device-platform-id.png`
  - https://pub.dev/packages/flutter_device_platform_id
- GitHub OpenCode: `.sisyphus/evidence/shot-github-opencode.png`
  - https://github.com/opencode-ai/opencode
- GitHub OhMyOpenCode: `.sisyphus/evidence/shot-github-oh-my-opencode.png`
  - https://github.com/code-yeongyu/oh-my-opencode

### 발표자 환경(수동)
- OpenCode TUI: `.sisyphus/evidence/opencode-tui.png`
- OMO 멀티 에이전트 화면: `.sisyphus/evidence/ohmyopencode-agents.png`
- 터미널 입력 장면: `.sisyphus/evidence/terminal-input.png`

구도 팁:
- above-the-fold(타이틀/배지/스타/설명 보이게)
- 쿠키 배너/고정 헤더에 가리지 않게
- 발표 화면 기준 글자 크기 충분히 크게

---

## GitHub Push(나중에 어시스턴트가 처리)
발표자가 `README.md` 편집 + 스크린샷 저장을 끝내면, 어시스턴트가 아래를 수행하도록 요청:
- 브랜치: `presentation/story-demo-live`
- 커밋 메시지: `docs(presentation): strengthen storyline and switch demo to live format`
- push + (가능하면) PR 생성

요청 템플릿:
"README 편집과 스크린샷 저장까지 끝났어. 이제 검증하고 GitHub에 push + PR까지 진행해줘."
