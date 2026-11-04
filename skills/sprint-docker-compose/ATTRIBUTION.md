# Attribution and modifications

- Original work: `skills/docker-compose-patterns/SKILL.md`
- Original repository: https://github.com/docker/skills
- Original author/attribution party: Docker contributors
- Reviewed upstream revision: `090ff3d39db5f8bc55d4e951c26218e7c95ea2d3`
- Original file: [skills/docker-compose-patterns/SKILL.md](https://github.com/docker/skills/blob/090ff3d39db5f8bc55d4e951c26218e7c95ea2d3/skills/docker-compose-patterns/SKILL.md)
- Original license: [Apache-2.0](https://github.com/docker/skills/blob/090ff3d39db5f8bc55d4e951c26218e7c95ea2d3/LICENSE); full text preserved in [LICENSE](LICENSE).
- This adaptation: `sprint-docker-compose`, modified on 2026-11-04 with AI assistance.
- Adaptation license: Apache-2.0.

## Changes / 수정 내역

Compose 지침을 축약하고 별도 Skill·동봉 스크립트·샘플 서비스 의존성을 제거했다. 실제 런타임 확인, 빈 DB 초기화, 재시작과 데이터 보존 검증을 추가했다.

2026-11-04 LITE 개정: 2시간 30분 제한 대회 기준의 LITE 모드를 기본값으로 고정하고, 단계별 시간 상한과 생략 항목을 명시했다.

한국어로 재작성하고 시간 제한 개발을 위한 독립 Skill로 범위를 조정했다.
원본의 동봉 스크립트·참조·자산을 그대로 복사하지 않았다.
변경본은 원본 프로젝트의 공식 배포물이 아니며 원저자의 보증·승인을 뜻하지 않는다.
출처·라이선스 링크를 읽기 위해 네트워크가 필요할 수 있으나 Skill 실행에 필수는 아니다.

## 2026-11-04 최소 검증 개정

초기 골격과 최종 통합 검사를 연결했다. 실제 볼륨 확인, 최소 준비 상태 처리, 살아 있는 워커를 API 재기동으로 실패 처리하지 않는 조건을 추가했다.
기존의 광범위한 검사·예시는 현재 SKILL.md의 필수 범위를 뜻하지 않는다.
