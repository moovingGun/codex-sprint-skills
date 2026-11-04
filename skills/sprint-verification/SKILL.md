---
name: sprint-verification
description: 제출 15~20분 전에 전체 테스트·기동 확인을 한 번 실행하고 README 요구 체크리스트와 제출 문서를 실제 구현에 맞춘다. Use before submission for final check, HOW_TO_RUN, AI_COLLABORATION.
license: MIT
---

# Sprint Verification (LITE)

Modified adaptation, 2026-11-04. Source, revision, and changes: [ATTRIBUTION.md](ATTRIBUTION.md).
항상 LITE 모드로 동작한다. 총 20분 이내.

## 1. 실행 확인 (1회, 5분)
- 전체 테스트 1회 실행. 결과(통과/실패 수)를 기록한다.
- 앱 기동 → /health → 핵심 흐름 1회 (데이터 적용 → 생성 → 조회 → 내보내기).
- 실행 못 한 것은 통과로 쓰지 않고 "미실행"으로 남긴다.
- 실패하면 원인을 보고 최소 수정 후 해당 테스트만 다시 돌린다. assertion을 약하게 바꾸지 않는다.

## 2. 체크리스트 갱신 (5분)
README를 다시 읽고 REQUIREMENTS.md 상태를 실제에 맞춘다.
특히 아래 5개는 상태와 근거(테스트 이름 또는 확인 방법)를 꼭 적는다.
- 잘못된 입력 거부 + 기존 데이터·결과 유지
- 이전 결과가 새 데이터 결과로 보이지 않음
- 실패·빈 데이터·중복 실행 처리
- API 직접 호출 권한 차단
- 결과 독립 검증 + 내보내기 형식

## 3. 제출 문서 (10분)
- HOW_TO_RUN.md: 양식 항목 순서대로. 명령·환경변수·접속 주소·계정·테스트 방법이 실제 코드와 같은지.
  설계 기준과 최적화 방식은 DECISIONS.md에서 가져온다.
- AI_COLLABORATION.md: 문항 원문 그대로 두고, 작업 중 남긴 메모와 실제 사례로만 답한다.
  경험이 없는 내용은 쓰지 않는다. 문서의 주장마다 근거(파일·테스트·커밋)를 떠올릴 수 있어야 한다.
- 실제 사용한 Skill 폴더(LICENSE·ATTRIBUTION 포함)와 AGENTS.md가 작업 디렉터리에 있는지 확인.

## 최종 보고
통과 / 실패 / 미실행 / 미완료를 요구 ID와 함께 한 줄씩. 미완료가 있으면 숨기지 않는다.
비밀값과 개인정보는 기록에 넣지 않는다.

실행 스크립트·외부 서비스·다른 Skill 의존성이 없다.
