---
description: VibeMap 학습 세션 시작 (2–3개 노드 심화 + 퀴즈). 인자 없으면 이어서, <id>면 특정 노드, next면 다음 노드.
argument-hint: [node-id | next]
---
VibeMap 학습 세션을 진행한다. `AGENTS.md`와 `tutor/TUTOR.md`의 세션 흐름(2절)을 그대로 따른다.

인자: $ARGUMENTS

1. `tutor/TUTOR.md`, `tutor/CURRICULUM.md`, `tutor/PROGRESS.md`를 읽는다.
2. 세션 흐름 실행: ① 워밍업 복습(SRS 예정 노드) → ② 신규 학습 2–3노드(소크라테스식 전개 + 파인만 되설명, 근거는 `vibemap/docs/nodes.json`의 `body.ko`) → ③ 퀴즈 → ④ (단계 완료/요청 시) 프로젝트 적용.
   - 인자가 비어 있으면 PROGRESS의 "현재 위치"에서 이어간다.
   - 인자가 노드 id면 그 노드부터(선행 미학습 노드는 먼저 짚어준다).
3. 세션 끝에 `tutor/PROGRESS.md`를 갱신한다(상태·SRS·세션 카운터·현재 위치·로그).

**언어는 한국어. `vibemap/` 아래 파일은 절대 수정하지 않는다. 쓰기는 `tutor/PROGRESS.md`에만.**
