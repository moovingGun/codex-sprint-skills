---
name: sprint-property-based-testing
description: 계산·최적화 결과를 생성 코드와 독립된 검증기로 확인하고, 일부러 깨뜨린 출력이 거부되는지와 하한 대비 품질을 보여 준다. Use for independent validator, heuristic result checks, lower bound.
license: CC-BY-SA-4.0
---

# Sprint Property-Based Testing (LITE)

Modified adaptation, 2026-11-04. Source, revision, and changes: [ATTRIBUTION.md](ATTRIBUTION.md).
Adapted from Trail of Bits contributors; this adaptation is CC-BY-SA-4.0.
항상 LITE 모드로 동작한다. 랜덤 생성·완전탐색·변이 테스트는 하지 않는다.

## 1. 독립 검증기 (구현보다 먼저, 15분)
- README 운영 규칙만 보고 만든다. 플래너·생성 코드를 import하거나 참고하지 않는다.
  공유해도 되는 것은 입력 자료형과 파서뿐이다.
- 원입력 + 최종 출력만 받아 위반 목록을 반환한다. 비어 있으면 통과다.
- 검사 항목은 과제 규칙과 1:1로 맞춘다. 예:
  전원 배정·중복 없음, 제외 대상 미배정, 정원, 시각 제약, 구간 시간이 제공 데이터와 일치,
  허용 목록 밖 ID 없음.
- 생성 결과는 검증기를 통과해야만 저장한다. 위반이면 저장하지 않고 실패로 처리한다.

## 2. 깨뜨려 보기 (5분)
정상 결과가 통과하는지 확인한 뒤, 출력을 두 가지 이상 일부러 망가뜨린다.
(예: 한 운행에 정원+1명, 도착 시각 +5분, 배정 하나 삭제)
검증기가 **해당 이유로** 거부하는지 확인한다. 무관한 파싱 오류로 실패하면 통과로 치지 않는다.

## 3. 품질 근거 (5분)
- 증명 가능한 하한을 계산해 결과와 함께 표시한다. (예: 버스 수 ≥ ceil(인원/정원), 그룹별 합산)
- "실행 가능(규칙 통과)"과 "최적"을 구분한다. 하한과 같을 때만 그 지표에서 최적이라고 말한다.

## 보고
검증기 위치, 검사 항목 목록, 깨뜨려 본 사례와 결과, 하한 대비 수치를 한 단락으로 남긴다.
이 내용이 "휴리스틱 결과를 어떻게 신뢰하나" 질문의 답이 된다.

실행 스크립트·필수 외부 서비스·다른 Skill 의존성이 없다.
