# VibeMap 학습 커리큘럼

VibeMap의 82개 개념을 **"아이디어 → 배포"** 순서(7단계)로 배우는 경로다. 각 단계는 VibeMap의 카테고리 하나에 대응하며, 단계 안에서는 의존 그래프(`vibemap/docs/data.js`의 엣지)를 따라 **선행 개념이 먼저** 오도록 정렬돼 있다.

- **중요도**: ⭐⭐⭐ 앵커(그 영역의 중심, `size=1`) · ⭐⭐ 핵심(`size=2`) · ⭐ 세부(`size=3`)
- **주요 연결 노드**: 그래프상 가장 밀접한 이웃. 학습 시 "이 개념이 무엇과 이어지는가"의 단서다. `[[id]]`는 VibeMap 노드 id.
- **교습 소스**: 각 노드의 실제 레슨 본문은 `vibemap/docs/nodes.json`의 `nodes[id].body.ko`. 튜터는 이 본문을 읽어 가르친다.
- 진도·숙련도는 [PROGRESS.md](./PROGRESS.md)에서 추적한다. 교습 방식은 [TUTOR.md](./TUTOR.md) 참조.

> 순서는 권장 경로일 뿐 강제가 아니다. 목표가 뚜렷하면(예: "서버리스 배포 이해") 해당 노드로 건너뛰고 선행 노드만 골라 배워도 된다.

---

## 7단계 개요

| 단계 | 카테고리 | 노드 수 | 앵커 | 한 줄 목표 |
|---|---|---|---|---|
| 1 | 핵심 | 1 | `vibe` | 바이브 코딩이 무엇이고 왜 하는가 |
| 2 | 사고방식 | 18 | — | 코드가 아니라 의도를 다루는 법 |
| 3 | AI·LLM | 11 | `claude-code` | AI를 도구가 아니라 팀원으로 부리는 법 |
| 4 | 도구 | 12 | `git` | 손을 더럽히는 기본기 (Git·터미널·PR) |
| 5 | 기술 | 11 | `tdd` | 신뢰를 만드는 테스트와 API 설계 |
| 6 | 데이터 | 11 | — | 데이터를 어디에 어떻게 담는가 |
| 7 | 운영·배포 | 18 | `serverless` | 실제로 세상에 내보내고 운영하기 |

---
<!-- CURRICULUM_BODY_START -->

### 1단계 · 핵심 (1) — 바이브 코딩이란 무엇인가

| # | id | 제목 | 중요도 | 주요 연결 노드 |
|---|---|---|---|---|
| 1 | `vibe` | 바이브 코딩 | ⭐⭐⭐ 앵커 | [[intent]] [[prompt-eng]] [[context-eng]] [[small-steps]] |

### 2단계 · 사고방식 (18) — 의도공학·요건·프롬프트/컨텍스트

| # | id | 제목 | 중요도 | 주요 연결 노드 |
|---|---|---|---|---|
| 2 | `intent` | 의도공학 | ⭐⭐ 핵심 | [[vibe]] [[requirements]] [[prompt-eng]] [[context-eng]] |
| 3 | `requirements` | 요건 정의 | ⭐⭐ 핵심 | [[intent]] [[context-eng]] [[small-steps]] [[simplify]] |
| 4 | `prompt-eng` | 프롬프트 엔지니어링 | ⭐⭐ 핵심 | [[vibe]] [[intent]] [[context-eng]] [[pitfalls]] |
| 5 | `context-eng` | 컨텍스트 엔지니어링 | ⭐⭐ 핵심 | [[vibe]] [[intent]] [[requirements]] [[prompt-eng]] |
| 6 | `small-steps` | 작은 단계 | ⭐ 세부 | [[vibe]] [[intent]] [[requirements]] [[context-eng]] |
| 7 | `convergence` | 수렴 사고 | ⭐ 세부 | [[intent]] [[context-eng]] [[small-steps]] [[simplify]] |
| 8 | `simplify` | 과감한 단순화 | ⭐ 세부 | [[vibe]] [[intent]] [[requirements]] [[small-steps]] |
| 9 | `review-mindset` | AI 코드 검토 습관 | ⭐ 세부 | [[vibe]] [[requirements]] [[simplify]] [[pitfalls]] |
| 10 | `zero-trust` | 제로 트러스트 | ⭐ 세부 | [[harness-eng]] [[security]] [[hallucination]] [[ai-coding-tools]] |
| 11 | `pitfalls` | 바이브 코딩의 함정 | ⭐⭐ 핵심 | [[vibe]] [[prompt-eng]] [[context-eng]] [[small-steps]] |
| 12 | `data-driven` | 데이터 드리븐 | ⭐⭐ 핵심 | [[vibe]] [[intent]] [[small-steps]] [[convergence]] |
| 13 | `docs` | 문서화 | ⭐⭐ 핵심 | [[vibe]] [[intent]] [[requirements]] [[context-eng]] |
| 14 | `harness-eng` | Harness Engineering (하네스 엔지니어링) | ⭐⭐ 핵심 | [[intent]] [[prompt-eng]] [[context-eng]] [[small-steps]] |
| 15 | `design-patterns` | 디자인 패턴 | ⭐⭐ 핵심 | [[intent]] [[prompt-eng]] [[context-eng]] [[simplify]] |
| 16 | `security` | 보안 | ⭐⭐ 핵심 | [[review-mindset]] [[zero-trust]] [[pitfalls]] [[harness-eng]] |
| 17 | `tidd` | TiDD (Ticket Driven Development) | ⭐⭐ 핵심 | [[intent]] [[requirements]] [[prompt-eng]] [[context-eng]] |
| 18 | `two-pizza-team` | Two Pizza Team | ⭐⭐ 핵심 | [[intent]] [[requirements]] [[review-mindset]] [[harness-eng]] |
| 19 | `llm-wiki` | LLM Wiki | ⭐⭐ 핵심 | [[intent]] [[requirements]] [[context-eng]] [[docs]] |

### 3단계 · AI·LLM (11) — Claude Code·MCP·에이전틱

| # | id | 제목 | 중요도 | 주요 연결 노드 |
|---|---|---|---|---|
| 20 | `llm-basics` | LLM 이해하기 | ⭐⭐ 핵심 | [[vibe]] [[prompt-eng]] [[context-eng]] [[harness-eng]] |
| 21 | `hallucination` | 환각 (Hallucination) | ⭐ 세부 | [[requirements]] [[prompt-eng]] [[context-eng]] [[small-steps]] |
| 22 | `ai-coding-tools` | AI 코딩 도구 | ⭐⭐ 핵심 | [[requirements]] [[prompt-eng]] [[context-eng]] [[small-steps]] |
| 23 | `claude-code` | Claude Code | ⭐⭐⭐ 앵커 | [[vibe]] [[intent]] [[requirements]] [[prompt-eng]] |
| 24 | `cc-rules` | Claude Code 규칙 (CLAUDE.md) | ⭐ 세부 | [[intent]] [[requirements]] [[prompt-eng]] [[context-eng]] |
| 25 | `cc-settings` | Claude Code 설정 (Settings) | ⭐ 세부 | [[review-mindset]] [[pitfalls]] [[harness-eng]] [[claude-code]] |
| 26 | `cc-commands` | Claude Code 커맨드 | ⭐ 세부 | [[harness-eng]] [[tidd]] [[claude-code]] [[cc-rules]] |
| 27 | `cc-skills` | Claude Code 스킬 | ⭐ 세부 | [[prompt-eng]] [[harness-eng]] [[claude-code]] [[cc-rules]] |
| 28 | `cc-hooks` | Claude Code 훅 | ⭐ 세부 | [[harness-eng]] [[tidd]] [[claude-code]] [[cc-rules]] |
| 29 | `mcp` | MCP (Model Context Protocol) | ⭐⭐ 핵심 | [[context-eng]] [[harness-eng]] [[hallucination]] [[claude-code]] |
| 30 | `agentic` | 에이전틱 워크플로우 | ⭐⭐ 핵심 | [[prompt-eng]] [[context-eng]] [[small-steps]] [[harness-eng]] |

### 4단계 · 도구 (12) — Git·터미널·PR·리팩터·IDE

| # | id | 제목 | 중요도 | 주요 연결 노드 |
|---|---|---|---|---|
| 31 | `terminal` | 터미널·CLI | ⭐⭐ 핵심 | [[harness-eng]] [[hallucination]] [[ai-coding-tools]] [[claude-code]] |
| 32 | `git-basics` | Git 기초 | ⭐ 세부 | [[small-steps]] [[tidd]] [[ai-coding-tools]] [[git]] |
| 33 | `git` | Git | ⭐⭐⭐ 앵커 | [[vibe]] [[prompt-eng]] [[context-eng]] [[small-steps]] |
| 34 | `github` | GitHub | ⭐ 세부 | [[review-mindset]] [[docs]] [[security]] [[tidd]] |
| 35 | `pr` | Pull Request | ⭐ 세부 | [[small-steps]] [[review-mindset]] [[pitfalls]] [[docs]] |
| 36 | `trunk` | 트렁크 기반 개발 | ⭐⭐ 핵심 | [[small-steps]] [[simplify]] [[review-mindset]] [[pitfalls]] |
| 37 | `ide` | IDE·에디터 | ⭐ 세부 | [[review-mindset]] [[pitfalls]] [[ai-coding-tools]] [[claude-code]] |
| 38 | `lint` | Lint·포매터 | ⭐ 세부 | [[vibe]] [[pitfalls]] [[ai-coding-tools]] [[claude-code]] |
| 39 | `refactor` | 리팩터링 | ⭐ 세부 | [[small-steps]] [[convergence]] [[simplify]] [[review-mindset]] |
| 40 | `debug` | 디버깅 | ⭐⭐ 핵심 | [[prompt-eng]] [[small-steps]] [[review-mindset]] [[pitfalls]] |
| 41 | `package-mgr` | 패키지 매니저 | ⭐ 세부 | [[review-mindset]] [[pitfalls]] [[security]] [[hallucination]] |
| 42 | `framework` | 프레임워크 | ⭐ 세부 | [[simplify]] [[pitfalls]] [[harness-eng]] [[hallucination]] |

### 5단계 · 기술 (11) — TDD·테스트·API·컨테이너

| # | id | 제목 | 중요도 | 주요 연결 노드 |
|---|---|---|---|---|
| 43 | `testing` | 테스팅 | ⭐⭐ 핵심 | [[simplify]] [[review-mindset]] [[pitfalls]] [[data-driven]] |
| 44 | `ut` | 단위 테스트 (Unit Test) | ⭐ 세부 | [[ai-coding-tools]] [[claude-code]] [[refactor]] [[debug]] |
| 45 | `it` | 통합 테스트 (Integration Test) | ⭐ 세부 | [[claude-code]] [[refactor]] [[debug]] [[testing]] |
| 46 | `e2e` | 엔드투엔드 테스트 (E2E) | ⭐ 세부 | [[review-mindset]] [[pitfalls]] [[claude-code]] [[testing]] |
| 47 | `tdd` | TDD (Test-Driven Development) | ⭐⭐⭐ 앵커 | [[vibe]] [[requirements]] [[small-steps]] [[convergence]] |
| 48 | `api` | API | ⭐⭐ 핵심 | [[context-eng]] [[simplify]] [[two-pizza-team]] [[hallucination]] |
| 49 | `rest` | REST | ⭐ 세부 | [[context-eng]] [[hallucination]] [[ai-coding-tools]] [[testing]] |
| 50 | `graphql` | GraphQL | ⭐ 세부 | [[context-eng]] [[ai-coding-tools]] [[claude-code]] [[testing]] |
| 51 | `container` | 컨테이너 | ⭐ 세부 | [[review-mindset]] [[harness-eng]] [[hallucination]] [[claude-code]] |
| 52 | `microservices` | 마이크로서비스 | ⭐ 세부 | [[zero-trust]] [[security]] [[two-pizza-team]] [[trunk]] |
| 53 | `env` | 환경변수·설정 | ⭐ 세부 | [[review-mindset]] [[pitfalls]] [[security]] [[claude-code]] |

### 6단계 · 데이터 (11) — SQL/NoSQL·DW·데이터 레이크

| # | id | 제목 | 중요도 | 주요 연결 노드 |
|---|---|---|---|---|
| 54 | `db-basics` | DB 기초 | ⭐⭐ 핵심 | [[vibe]] [[review-mindset]] [[two-pizza-team]] [[hallucination]] |
| 55 | `sql` | SQL | ⭐ 세부 | [[context-eng]] [[review-mindset]] [[hallucination]] [[testing]] |
| 56 | `nosql` | NoSQL | ⭐ 세부 | [[microservices]] [[db-basics]] [[sql]] [[sql-vs-nosql]] |
| 57 | `sql-vs-nosql` | SQL vs NoSQL | ⭐ 세부 | [[review-mindset]] [[microservices]] [[db-basics]] [[sql]] |
| 58 | `dw` | 데이터 웨어하우스 | ⭐ 세부 | [[context-eng]] [[db-basics]] [[sql]] [[nosql]] |
| 59 | `db-vs-dw` | DB vs DW | ⭐ 세부 | [[db-basics]] [[sql]] [[sql-vs-nosql]] [[dw]] |
| 60 | `datalake` | 데이터 레이크 | ⭐ 세부 | [[db-basics]] [[sql]] [[nosql]] [[dw]] |
| 61 | `lake-formation` | Lake Formation | ⭐ 세부 | [[env]] [[dw]] [[datalake]] [[glue]] |
| 62 | `glue` | AWS Glue | ⭐ 세부 | [[dw]] [[db-vs-dw]] [[datalake]] [[lake-formation]] |
| 63 | `athena` | Athena | ⭐ 세부 | [[sql]] [[dw]] [[db-vs-dw]] [[datalake]] |
| 64 | `kinesis` | Kinesis | ⭐ 세부 | [[db-basics]] [[dw]] [[db-vs-dw]] [[datalake]] |

### 7단계 · 운영·배포 (18) — 서버리스·CI/CD·모니터링·비용

| # | id | 제목 | 중요도 | 주요 연결 노드 |
|---|---|---|---|---|
| 65 | `serverless` | AWS 서버리스 | ⭐⭐⭐ 앵커 | [[vibe]] [[zero-trust]] [[security]] [[two-pizza-team]] |
| 66 | `lambda` | AWS Lambda | ⭐ 세부 | [[microservices]] [[env]] [[db-basics]] [[kinesis]] |
| 67 | `s3` | Amazon S3 | ⭐ 세부 | [[review-mindset]] [[hallucination]] [[microservices]] [[dw]] |
| 68 | `apigw` | API Gateway | ⭐ 세부 | [[api]] [[rest]] [[graphql]] [[microservices]] |
| 69 | `dynamodb` | DynamoDB | ⭐ 세부 | [[trunk]] [[microservices]] [[env]] [[db-basics]] |
| 70 | `dsql` | Aurora DSQL | ⭐ 세부 | [[db-basics]] [[sql]] [[sql-vs-nosql]] [[db-vs-dw]] |
| 71 | `memorydb` | MemoryDB for Redis | ⭐ 세부 | [[db-basics]] [[nosql]] [[sql-vs-nosql]] [[serverless]] |
| 72 | `ecs` | ECS / Fargate | ⭐ 세부 | [[container]] [[microservices]] [[env]] [[serverless]] |
| 73 | `iac` | IaC (Infrastructure as Code) | ⭐⭐ 핵심 | [[zero-trust]] [[security]] [[terminal]] [[git]] |
| 74 | `immutable-infra` | Immutable Infrastructure | ⭐⭐ 핵심 | [[container]] [[serverless]] [[lambda]] [[ecs]] |
| 75 | `cicd` | CI/CD | ⭐⭐ 핵심 | [[small-steps]] [[pitfalls]] [[security]] [[two-pizza-team]] |
| 76 | `gitops` | GitOps | ⭐⭐ 핵심 | [[zero-trust]] [[security]] [[two-pizza-team]] [[claude-code]] |
| 77 | `vercel` | Vercel | ⭐ 세부 | [[ai-coding-tools]] [[git]] [[pr]] [[framework]] |
| 78 | `domain` | 도메인·DNS | ⭐ 세부 | [[docs]] [[design-patterns]] [[api]] [[microservices]] |
| 79 | `monitoring` | 모니터링·옵저버빌리티 | ⭐ 세부 | [[zero-trust]] [[data-driven]] [[security]] [[hallucination]] |
| 80 | `cost` | 비용 관리 | ⭐ 세부 | [[ai-coding-tools]] [[github]] [[package-mgr]] [[framework]] |
| 81 | `aiops` | AIOps | ⭐⭐ 핵심 | [[zero-trust]] [[security]] [[hallucination]] [[debug]] |
| 82 | `llmops` | LLMOps | ⭐⭐ 핵심 | [[prompt-eng]] [[context-eng]] [[convergence]] [[zero-trust]] |
<!-- CURRICULUM_BODY_END -->

---

## 마일스톤

- **1–2단계 완료** → 바이브 코딩의 철학과 사고방식을 갖췄다. AI에게 "만들어줘" 대신 "의도"를 준다.
- **3단계 완료** → Claude Code를 팀원처럼 부린다. 규칙·훅·스킬·MCP로 하네스를 짠다.
- **4–5단계 완료** → Git·테스트·API로 결과물을 신뢰 가능하게 만든다.
- **6–7단계 완료** → 데이터를 담고 서버리스로 배포·운영한다. 아이디어에서 배포까지 한 바퀴 완주.
