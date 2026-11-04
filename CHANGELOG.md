# Changelog

## 2026-11-04 — 시간 조건을 사용자 요청으로 분리

- 활성 Skill·AGENTS 템플릿·README의 고정 마감과 단계별 시간표를 제거했다.
- 마감·첫 결과물 목표·남은 시간은 요청에서 받고, 시간 미지정 시에도 구현을 진행한다.
- 첫 결과물 피드백과 최종 제출을 구분하고 최소 검증·검사 근거 재사용은 유지했다.
- 이전 릴리스의 시간 배분은 변경 이력으로만 보존했다.

## 2026-11-04 — 완성 우선·최소 검증 개정

- 150분 시간표를 templates/AGENTS.md로 통일하고 마지막 10분을 수정·제출 버퍼로 확보했다.
- 검증기·테스트 선완성을 요구하지 않고 실행 골격부터 구현과 병행한다.
- 테스트 개수 상한 대신 JSON 출력·데이터 보존·버전·권한을 작은 흐름으로 묶는다.
- 통과한 검사 근거를 재사용하고 마지막 수정에 영향받는 검사만 다시 실행한다.
- 최종 Docker·핵심 API 확인을 같은 실행으로 합치고 긴 전체 검사 의무를 제거했다.
- 살아 있는 워커를 API 재기동으로 실패 처리하는 지침을 수정했다.
- 세션 히스토리 확인을 복원하고 이해도 Skill을 기본 설치·시간표에서 제외했다.
- 기존 AGENTS.md와 동명 Skill을 덮어쓰지 않도록 설치 명령을 변경했다.

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
