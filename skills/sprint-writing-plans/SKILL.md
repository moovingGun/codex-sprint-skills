---
name: sprint-writing-plans
description: 2시간 30분 제한 개발에서 README를 3열 체크리스트와 시간표로 바꾸고 바로 구현에 들어간다. Use at the start for README requirements checklist, time plan, clarifying questions.
license: MIT
---

# Sprint Writing Plans (LITE)

Modified adaptation, 2026-11-04. Source, revision, and changes: [ATTRIBUTION.md](ATTRIBUTION.md).
항상 LITE 모드로 동작한다. 계획에 15분 이상 쓰지 않는다.

## 1. 체크리스트 (5분)
README를 읽고 REQUIREMENTS.md를 만든다.

| ID | 요구 (한 줄) | 구현 파일 | 상태 |
|---|---|---|---|

- 상태: TODO / DONE / VERIFIED. 실행해서 확인한 것만 VERIFIED.
- README에 없는 규칙·스키마를 지어내지 않는다. 가정은 ID 옆에 "(가정)"으로 표시한다.
- 구현 파일은 처음엔 비워 두고 구현하면서 채운다.

## 2. 담당자 질문 (5분)
목적함수·이용 편의·데이터 의미처럼 설계를 바꾸는 모호함만 한 번에 묶어 질문한다.
답을 기다리는 동안 답과 무관한 작업을 계속한다. 답변은 체크리스트에 "(담당자)"로 반영한다.

## 3. 시간표
| 시간 | 할 일 |
|---|---|
| 0:00~0:15 | 체크리스트, 담당자 질문, 기술 스택 결정 |
| 0:15~0:35 | 결과 검증기 + 필수 테스트 4개 (구현보다 먼저) |
| 0:35~1:45 | 수직 기능 순서로 구현: 데이터 적용 → 생성 → 저장 → 화면 → 내보내기 → 역할 |
| 1:45~2:05 | Docker, 전체 테스트 1회, /health 확인 |
| 2:05~2:20 | HOW_TO_RUN.md, AI_COLLABORATION.md |
| 2:20~2:30 | sprint-understanding-check |

시간이 밀리면 UI 다듬기와 부가 기능부터 줄인다. 필수 테스트와 실행 가능 상태는 줄이지 않는다.

## 4. 기록 (최소)
- DECISIONS.md: 결정 5개 이내, 한 줄씩 `선택 / 대안 / 이유`.
- AI 제안을 채택·수정·폐기한 순간 한 줄 메모를 남긴다 (AI_COLLABORATION.md 재료). 지어내지 않는다.
- 워커·큐·추가 DB는 요구에 근거가 있을 때만 쓴다.

## 범위
과제 원문·실데이터·완성 앱을 포함하지 않는다. 실행 스크립트·외부 서비스·다른 Skill 의존성이 없다.
