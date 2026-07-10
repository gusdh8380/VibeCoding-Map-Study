---
description: VibeMap 능동 회상 퀴즈만 진행. `due`=복습 예정 노드, `<id>`=지정 노드, 비우면 최근 학습 노드.
argument-hint: "[node-id | due]"
---

퀴즈만 진행한다(설명·되설명 없이 능동 회상). `vibetutor` 스킬과 `tutor/TUTOR.md` 4절을 따른다.

인자: `$ARGUMENTS`

1. `tutor/PROGRESS.md`를 읽어 대상 노드를 정한다: `due`면 복습 예정 큐, `<id>`면 그 노드, 비우면 마지막 세션에 학습한 노드.
2. 노드마다 2–3문항(개념 회상 / 시나리오 적용 / "왜 틀렸나"). 근거는 `vibemap/docs/nodes.json`의 `body.ko`.
3. 채점 후 정답률(%)을 `tutor/PROGRESS.md`에 반영(≥80%면 ✅ 유지/승격, 미달이면 🟡). SRS·로그 갱신.

**한국어. `vibemap/` 수정 금지. 쓰기는 `tutor/PROGRESS.md`에만.**
