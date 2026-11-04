---
name: sprint-test-driven-development
description: 2시간 30분 제한 개발에서 점수와 직결되는 필수 계약 4개만 실패 테스트부터 작성하고 나머지는 구현 후 최소 테스트로 확인한다. Use for core tests, data apply rollback, role checks, bug fixes.
license: MIT
---

# Sprint Test-Driven Development (LITE)

Modified adaptation, 2026-11-04. Source, revision, and changes: [ATTRIBUTION.md](ATTRIBUTION.md).
항상 LITE 모드로 동작한다. 테스트 작성에 총 30분 이상 쓰지 않는다.

## 필수 테스트 4개 (Red → Green)
구현 전에 작성하고, 의도한 assertion으로 실패하는지 한 번 확인한다.
import 오류나 미설치로 인한 실패는 Red로 치지 않는다.

1. 결과 검증기: 정상 결과는 통과한다.
2. 결과 검증기: 일부러 깨뜨린 결과(정원 초과, 시각 위반)를 이유와 함께 거부한다.
3. 데이터 적용: 잘못된 입력(필수 열 누락·없는 ID 참조·빈 파일 중 하나 이상)은 거부되고
   기존 데이터·결과·버전이 그대로다.
4. 권한: 비로그인은 401, 다른 역할은 403. UI가 아니라 API를 직접 호출해 확인한다.

과제에 해당하지 않는 항목은 빼고 이유를 한 줄 남긴다.

## 나머지 기능
구현 후 필요한 것만 테스트한다. 설정·문서·스타일에는 테스트를 만들지 않는다.
버그를 고칠 때만 재현 테스트 → 수정 → 통과 순서를 지킨다.

## 테스트가 진짜인지
- 기대값은 손으로 계산 가능한 값으로 둔다. 현재 코드 출력을 그대로 정답에 박지 않는다.
- 실패한 테스트를 통과시키려고 assertion이나 요구를 약하게 바꾸지 않는다.
- 핵심 규칙을 mock으로 대체하지 않는다.
- 기존 구현을 일괄 삭제하지 않는다.

## 하지 않는 것
변이 테스트, 변경마다 전체 테스트 재실행, 커버리지 목표.
전체 테스트는 마지막에 1회 실행한다 (sprint-verification).

실행 스크립트·외부 서비스·다른 Skill 의존성이 없다.
