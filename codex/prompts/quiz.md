---
description: VibeMap 능동 회상 퀴즈만 진행. due=복습 예정 노드, <id>=지정 노드, 비우면 최근 학습 노드.
argument-hint: [node-id | due]
---
VibeMap 능동 회상 퀴즈만 진행한다. `AGENTS.md`와 `tutor/TUTOR.md`의 채점 기준을 따른다.

인자: $ARGUMENTS

1. `tutor/TUTOR.md`, `tutor/PROGRESS.md`를 읽는다.
2. 대상 선정: 인자가 `due`면 복습 예정(SRS) 노드, 노드 id면 그 노드, 비어 있으면 최근 학습 노드.
3. 능동 회상 퀴즈 진행(문항 근거는 `vibemap/docs/nodes.json`의 `body.ko`). 채점 후 ✅(≥80%)/🟡 판정.
4. 결과를 `tutor/PROGRESS.md`에 반영(상태·점수·SRS·로그).

**언어는 한국어. `vibemap/` 아래 파일은 절대 수정하지 않는다. 쓰기는 `tutor/PROGRESS.md`에만.**
