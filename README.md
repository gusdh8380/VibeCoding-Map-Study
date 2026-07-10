# VibeCoding-Map Study

VibeMap 지식 베이스 위에 얹은 **Claude Code 네이티브 AI 튜터** 학습 워크스페이스입니다.
VibeMap이 그래프로 정리한 **82개 개념**(의도공학 · 바이브 코딩 · Claude Code · Git · TDD · AWS 서버리스 등)을
한국어로, "아이디어 → 배포" 순서에 따라 대화형으로 배우는 것이 목표입니다.

## 구성

| 경로 | 역할 |
|------|------|
| `vibemap/` | **지식 소스**. 82개 개념을 인터랙티브 그래프로 렌더링하는 자체 완결형 웹 프로젝트. 원본: [roboco-io/vibemap](https://github.com/roboco-io/vibemap) |
| `tutor/` | 튜터의 **교습 프로토콜·커리큘럼·진도**. `TUTOR.md`(세션 흐름/SRS/숙련 기준), `CURRICULUM.md`(82노드 학습 경로), `PROGRESS.md`(진도 추적) |
| `.claude/` | Claude Code용 튜터 **런타임**. 슬래시 커맨드(`/learn`, `/quiz`, `/review`, `/progress`, `/apply`) + `vibetutor` 스킬 |
| `AGENTS.md`, `codex/` | Codex CLI(및 AGENTS.md를 읽는 에이전트)용 진입점 + 프롬프트 |

## 튜터 사용법

Claude Code에서 이 폴더를 열고 슬래시 커맨드로 진행합니다.

- `/learn [id|next]` — 학습 세션 시작 (개념 2–3개 심화 + 퀴즈)
- `/quiz [id|due]` — 능동 회상 퀴즈
- `/review` — 재복습 노드 + SRS 예정 노드 복습
- `/progress` — 진도 대시보드
- `/apply [id]` — 배운 개념을 실제 작업에 적용

**교습 방식**: 소크라테스식 문답 + 파인만 되설명 + 능동 회상 퀴즈(세션 기반 SRS) + 프로젝트 적용.
개념 내용은 항상 `vibemap/docs/nodes.json`의 `body.ko`에서 가져오며, 진도는 `tutor/PROGRESS.md`에만 기록합니다.

### Codex CLI에서 쓰기

이 저장소에는 Codex가 자동으로 읽는 **`AGENTS.md`**가 있어, 별도 설정 없이 튜터가 동작합니다.
Codex를 이 폴더에서 실행한 뒤 `"배우자"`, `"복습하자"`, `"learn cc-hooks"`처럼 자연어로 요청하면 됩니다.

슬래시 커맨드(`/prompts:learn` 등)로 쓰고 싶다면 프롬프트를 Codex 홈에 복사한 뒤 재시작하세요:

```bash
mkdir -p ~/.codex/prompts
cp codex/prompts/*.md ~/.codex/prompts/
```

→ `/prompts:learn`, `/prompts:quiz`, `/prompts:review`, `/prompts:progress`, `/prompts:apply`
(커스텀 프롬프트는 Codex에서 deprecated지만 아직 동작합니다. 복사 안 해도 `AGENTS.md`만으로 충분합니다.)

## 지식 소스: VibeMap

이 워크스페이스의 개념 콘텐츠는 전부 VibeMap에서 옵니다.
튜터가 소비하는 컴파일된 산출물:

- `vibemap/docs/nodes.json` — 노드별 다국어 본문(`body.{ko,en,ja}`) + 참고 링크(`refs`)
- `vibemap/docs/data.js` — 그래프 골격: 노드·카테고리(7)·엣지(개념 의존 구조)
- `vibemap/raw/nodes/*.md` — 사람이 작성한 원본(SSOT, 82노드)

VibeMap 원본을 직접 실행하려면 (`vibemap/` 내부):

```bash
cd vibemap
python3 -m http.server   # 빌드 도구·npm 의존성 없음 — 정적 서버로 바로 구동
```

## 출처 및 크레딧

`vibemap/`은 [**roboco-io/vibemap**](https://github.com/roboco-io/vibemap)(공개 저장소)의 파일을 포함한 것입니다.
개념 콘텐츠의 저작·권리는 원본 프로젝트에 있으며, 이 저장소는 그 지식을 **학습 목적**으로 활용합니다.
개념 내용 수정은 이 저장소가 아니라 원본의 저작 워크플로(`raw/nodes/*.md`)에서 이루어져야 합니다.
