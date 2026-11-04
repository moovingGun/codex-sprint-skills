# Changelog

## 2026-11-04 — LITE 고정 개정

- 다섯 수정 Skill을 2시간 30분 제한 기준 LITE 모드로 고정했다. 단계별 시간 상한과 생략 항목을 명시했다.
- 필수 테스트를 4개(검증기 정상 통과, 출력 파손 거부, 잘못된 데이터셋 거부·기존 결과 유지, API 권한)로 한정했다.
- 랜덤 property test, 완전탐색, 변이 테스트, compose 재시작 시나리오를 제외했다.
- REQUIREMENTS.md를 3열 체크리스트로, DECISIONS.md를 5개 이내 한 줄 기록으로 줄였다.
- 직접 작성한 `sprint-understanding-check` Skill(MIT)을 추가했다.
- 순서·기본 구조·검증 기준을 담은 `templates/AGENTS.md`를 추가했다.

## 2026-11-04 — Initial adapted set

- Created five self-contained Korean Skills from pinned public upstreams.
- Removed mandatory approval handoffs, subagent dispatch and cross-Skill requirements.
- Removed blanket deletion of existing implementation in the TDD adaptation.
- Added requirement-to-evidence tracking, independent result validation and negative cases.
- Kept deployment guidance focused on minimal services, readiness and persistence.
- Added evidence-based submission documents and truthful AI collaboration records.
- Bundled no executable scripts, hooks, MCP configuration, app scaffold or real dataset.
- Preserved original license texts and documented per-Skill adaptation licenses.

Detailed changes: [sources.json](sources.json) and each Skill's ATTRIBUTION.md.
