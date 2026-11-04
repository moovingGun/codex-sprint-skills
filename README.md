# Codex Sprint Skills

**150분 안에 실행 가능한 필수 웹 서비스를 완성**하기 위한 Agent Skill입니다.
기본 흐름은 수정 Skill 5개이며, 이해도 확인 Skill 1개는 명시 요청 시에만 사용하는 선택 항목입니다.
검증을 생략해 성공이라 하지 않되, **바뀐 부분만 다시 확인하고 통과한 검사를 반복하지 않습니다.**

## 기본 흐름

| Skill | 사용하는 시점 |
|---|---|
| [sprint-writing-plans](skills/sprint-writing-plans/SKILL.md) | 짧은 요구 체크리스트를 만들고 실행 골격부터 시작 |
| [sprint-test-driven-development](skills/sprint-test-driven-development/SKILL.md) | 관련 기능과 함께 핵심 실패 계약을 작은 테스트로 확인 |
| [sprint-property-based-testing](skills/sprint-property-based-testing/SKILL.md) | 계산 결과의 독립 제약 검증과 출력 파손 사례 확인 |
| [sprint-docker-compose](skills/sprint-docker-compose/SKILL.md) | Docker 골격을 일찍 준비하고 최종 통합과 같은 실행에서 확인 |
| [sprint-verification](skills/sprint-verification/SKILL.md) | 핵심 흐름·정확한 JSON 출력·필수 제출물 점검 |

시간표의 단일 기준은 [templates/AGENTS.md](templates/AGENTS.md)입니다.
계획 10분 → 골격 15분 → 구현 80분 → 통합 20분 → 문서 15분 → 수정·제출 버퍼 10분입니다.
검증기 전체와 모든 테스트를 먼저 만들지 않습니다. 필요한 검증은 기능과 함께 작성합니다.
출력 계약·데이터 보존·버전·권한을 작은 통합 흐름으로 묶어 확인합니다.
랜덤 생성·완전탐색·변이 캠페인·커버리지 목표·장시간 전체 검사를 강제하지 않습니다.
빠른 기존 전체 테스트가 핵심 검사를 포함하면 그것 하나로 대체합니다.
최종 확인 이후 수정하면 재현 테스트와 영향받는 검사만 다시 실행합니다.

선택: [sprint-understanding-check](skills/sprint-understanding-check/SKILL.md).
기본 시간표·자동 작업 순서에 포함하지 않으며 명시 요청이 있을 때만 사용합니다.

5개 수정본의 [출처](SOURCES.md), [변경 내역](CHANGELOG.md), [라이선스 범위](LICENSE),
[검증 기록](VALIDATION.md)을 확인하세요. 실행 스크립트·hooks·MCP 설정·필수 외부 서비스는 없습니다.
에이전트는 파일·테스트·Docker 명령을 사용할 수 있고 패키지 설치·이미지 pull/build는
네트워크를 사용할 수 있습니다. 완성 앱이나 과제 정답을 제공하는 저장소가 아닙니다.

## 설치 — 프로젝트별 복사 권장

프로젝트의 부모 폴더에서 이 저장소를 복제한 뒤, 프로젝트 루트에서 복사합니다.

```bash
# 프로젝트 루트에서 실행. 복제 대상이 이미 있으면 새로 clone하지 말고 먼저 확인합니다.
git clone https://github.com/moovingGun/codex-sprint-skills.git ../codex-sprint-skills
mkdir -p .agents/skills
for skill in sprint-writing-plans sprint-test-driven-development sprint-property-based-testing sprint-docker-compose sprint-verification; do
  if [ -e ".agents/skills/$skill" ]; then
    echo "이미 있음: .agents/skills/$skill — 차이를 확인해 수동 병합"
  else
    cp -R "../codex-sprint-skills/skills/$skill" .agents/skills/
  fi
done
if [ -e AGENTS.md ]; then
  echo "기존 AGENTS.md와 ../codex-sprint-skills/templates/AGENTS.md를 비교해 병합하세요."
else
  cp -n ../codex-sprint-skills/templates/AGENTS.md ./AGENTS.md
fi
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
$sprint-docker-compose 최소 실행 구성을 만들고 최종 통합과 묶어 기동·영속화만 확인해줘.
$sprint-verification 기존 통과 근거를 재사용하고 변경 영향과 필수 제출물만 확인해줘.
```

현재 단계에 필요한 Skill만 사용하세요. 이해도 Skill은 기본 설치에서 제외합니다.
원하면 해당 폴더 전체를 별도로 복사한 뒤 명시적으로 호출할 수 있습니다.

## 공개 자료와 작업 이력

구체적인 대회 규정의 허용 범위는 사용자가 확인해야 합니다. 이 저장소는 규정 준수나
심사 통과를 보증하지 않습니다. 공개 자료를 활용할 때 원본·수정본 URL, 사용 커밋,
사용한 Skill, 변경 내용, 라이선스를 실제 기록으로 남기세요.
공개 상태 유지 의무가 있는 경우 요구된 기간까지 이 저장소를 공개로 유지해야 합니다.
과제 원문·실데이터·비공개 요구사항·실제 제출물·세션 기록을 이 공개 저장소에 올리지 마세요.
작업과 제출은 해당 환경에서 허용된 도구·네트워크·반입 규칙 안에서 수행하세요.

## 라이선스

`sprint-writing-plans`·`sprint-test-driven-development`·`sprint-verification`·`sprint-understanding-check`는 MIT, `sprint-docker-compose`는 Apache-2.0,
`sprint-property-based-testing`은 **CC-BY-SA-4.0**입니다.
수정본을 공유할 때 각 폴더의 라이선스·출처·변경 고지를 유지하세요.
특히 CC-BY-SA 수정 Skill은 그 라이선스 조건에 따라 공유해야 합니다.
루트 문서의 CC0 표시는 개별 Skill의 라이선스를 대체하지 않습니다.
