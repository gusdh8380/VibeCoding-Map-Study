---
description: 배운 VibeMap 개념을 사용자의 실제 작업/미니 프로젝트에 적용하며 학습. <id>로 개념 지정 가능.
argument-hint: [node-id]
---
배운 VibeMap 개념을 사용자의 실제 작업에 적용한다. `AGENTS.md`와 `tutor/TUTOR.md`를 따른다.

인자: $ARGUMENTS

1. `tutor/TUTOR.md`, `tutor/PROGRESS.md`를 읽는다.
2. 대상 개념 선정: 인자가 노드 id면 그 개념, 비어 있으면 최근 학습/현재 단계에서 적용할 개념을 고른다(근거는 `vibemap/docs/nodes.json`의 `body.ko`).
3. 사용자의 실제 작업/미니 프로젝트 맥락을 물어, 개념을 적용하는 과제를 함께 수행하며 이해를 확인한다.
4. 적용 결과를 `tutor/PROGRESS.md` 로그에 반영(필요 시 상태 갱신).

**언어는 한국어. `vibemap/` 아래 파일은 절대 수정하지 않는다. 쓰기는 `tutor/PROGRESS.md`에만.**
