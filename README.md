# Codex Sprint Skills

시간 제한 웹 서비스 개발을 위한 **5개의 수정된 Agent Skill**입니다.
README 요구사항 추적, 핵심 계약의 TDD, 독립 계산 검증, Docker 실행 재현성,
제출 전 근거 점검에 집중합니다. Codex의 `SKILL.md` 폴더 형식입니다.

## 포함된 Skill

| Skill | 사용할 때 | 주요 변경 |
|---|---|---|
| [sprint-writing-plans](skills/sprint-writing-plans/SKILL.md) | 명세를 읽고 구현 계획을 세울 때 | 요구 ID·파일·테스트 추적, 불필요한 승인 대기 제거 |
| [sprint-test-driven-development](skills/sprint-test-driven-development/SKILL.md) | 핵심 기능·버그 수정·리팩터링 | 실패 테스트, 데이터·권한 경계, 기존 코드 일괄 삭제 제거 |
| [sprint-property-based-testing](skills/sprint-property-based-testing/SKILL.md) | 계산·파서·검증 결과를 신뢰해야 할 때 | 독립 oracle, 불변식, 출력 파손, 소형 정답 비교 |
| [sprint-docker-compose](skills/sprint-docker-compose/SKILL.md) | 앱·DB의 실행 구성을 만들고 확인할 때 | 최소 서비스, readiness, 영속화, 초기화·재시작 확인 |
| [sprint-verification](skills/sprint-verification/SKILL.md) | 완료 선언·제출 직전 | 요구와 실행 근거 대조, 문서·실제 협업 기록 확인 |

모두 원본을 수정한 파생본입니다. [출처](SOURCES.md), [변경 내역](CHANGELOG.md),
[라이선스 범위](LICENSE), [검증 기록](VALIDATION.md)을 함께 확인하세요.
Skill 내부에는 실행 스크립트·hooks·MCP 설정·필수 외부 서비스가 없습니다.
지침을 사용하는 에이전트는 파일을 수정하고 테스트·Docker 명령을 실행할 수 있습니다.
패키지 설치, 이미지 pull/build, 출처 확인에는 네트워크가 필요할 수 있습니다.

## 설치 — 프로젝트별 복사 권장

프로젝트의 부모 폴더에서 이 저장소를 복제한 뒤, 프로젝트 루트에서 복사합니다.

```bash
git clone https://github.com/moovingGun/codex-sprint-skills.git ../codex-sprint-skills
mkdir -p .agents/skills
cp -R ../codex-sprint-skills/skills/sprint-* .agents/skills/
git -C ../codex-sprint-skills rev-parse HEAD
```

출력한 커밋을 프로젝트의 자료 사용 기록에 적습니다. 재현할 때는 그 커밋으로
checkout한 뒤 복사하세요. 폴더 전체를 복사해야 LICENSE와 ATTRIBUTION.md가 유지됩니다.
동명 폴더가 이미 있으면 먼저 차이를 확인하고 덮어쓰지 마세요.
사용자 공통 설치는 `~/.agents/skills/`를 사용할 수 있지만 제출용은 프로젝트 복사가 편합니다.
설치한 Skill이 나타나지 않으면 Codex를 재시작하세요.

공식 로컬 Skill 문서: https://learn.chatgpt.com/docs/build-skills

## 사용 예시

```text
$sprint-writing-plans README를 요구 ID·구현 파일·테스트가 연결된 계획으로 정리하고 구현을 진행해줘.
$sprint-test-driven-development 데이터 적용 실패 시 기존 데이터가 유지되는 계약부터 테스트해줘.
$sprint-property-based-testing 계산 결과의 독립 검증기를 만들고 잘못된 출력이 거부되는지 확인해줘.
$sprint-docker-compose 실제 스택에 필요한 최소 구성으로 초기화·헬스체크·재시작을 검증해줘.
$sprint-verification README와 실제 제출물을 대조하고 근거 없는 완료와 미실행 검사를 알려줘.
```

한 번에 다섯 Skill을 모두 호출할 필요는 없습니다. 현재 단계에 필요한 것을 사용하세요.
이 저장소는 완성 앱이나 과제 정답을 제공하지 않습니다. 이해도 문답 훈련도 포함하지 않습니다.

## 공개 자료와 작업 이력

구체적인 대회 규정의 허용 범위는 사용자가 확인해야 합니다. 이 저장소는 규정 준수나
심사 통과를 보증하지 않습니다. 공개 자료를 활용할 때 원본·수정본 URL, 사용 커밋,
사용한 Skill, 변경 내용, 라이선스를 실제 기록으로 남기세요.
공개 상태 유지 의무가 있는 경우 요구된 기간까지 이 저장소를 공개로 유지해야 합니다.
과제 원문·실데이터·비공개 요구사항·실제 제출물·세션 기록을 이 공개 저장소에 올리지 마세요.
작업과 제출은 해당 환경에서 허용된 도구·네트워크·반입 규칙 안에서 수행하세요.

## 라이선스

3개 Skill은 MIT, `sprint-docker-compose`는 Apache-2.0,
`sprint-property-based-testing`은 **CC-BY-SA-4.0**입니다.
수정본을 공유할 때 각 폴더의 라이선스·출처·변경 고지를 유지하세요.
특히 CC-BY-SA 수정 Skill은 그 라이선스 조건에 따라 공유해야 합니다.
루트 문서의 CC0 표시는 개별 Skill의 라이선스를 대체하지 않습니다.
