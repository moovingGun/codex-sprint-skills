---
name: sprint-docker-compose
description: 웹 서비스의 최소 Docker 실행 구성을 초기에 준비하고 최종 코드에서 기동·DB·영속화만 확인하며 관련 설정 변경 때만 재검증한다.
license: Apache-2.0
---

# Sprint Docker Compose (LITE)

Modified adaptation, 2026-11-04. Source, revision, and changes: [ATTRIBUTION.md](ATTRIBUTION.md).
필요한 서비스만 사용한다. Docker 확인을 마지막의 새 프로젝트로 만들지 않는다.
시간 배분은 프로젝트 AGENTS.md를 따르고, 없다면 통합 검증 예산 안에서 진행한다.

## 실행 골격 단계
- Docker·의존성 사용 가능 여부를 짧게 확인하고 최소 Dockerfile·compose.yaml을 준비한다.
- 실제 실행 명령, 명시 버전 베이스 이미지, 과제의 호스트·포트 계약을 따른다.
- 앱 + 필요한 DB만 둔다. 작은 계산은 별도 워커 없이 구현할 수 있다.
  워커가 필요할 때만 추가하고, 큐·브로커·추가 서비스는 요구가 있을 때만 쓴다.
- .env.example에는 실제 변수와 안전한 예시를 쓰고 필수 비밀값을 표시한다.
  실비밀값은 .env 또는 환경변수에서 읽고 .env는 Git·이미지에 포함하지 않는다.
- .dockerignore에서 .git·비밀 파일·캐시를 제외하고 필요한 초기화 자산은 포함한다.

## 최소 실행 계약
- 빈 DB의 스키마·초기 계정/데이터 준비는 멱등하게 한다.
- 초기화는 한 실행 주체가 맡는다. 워커가 필요하면 초기화 완료 후 시작되게 한다.
- DB는 named volume 등 컨테이너 교체 후에도 유지되는 경로에 저장한다.
- /health는 과제 계약에 맞춰 준비 상태를 확인한다. DB 연결이 필요하면 포함한다.
- DB healthcheck + depends_on service_healthy 또는 짧고 제한된 연결 재시도 중
  하나로 시작 순서를 처리한다. 별도 readiness 시스템을 구축하지 않는다.
- restart 정책이 작업 복구를 보장한다고 설명하지 않는다.
  API만 재기동할 때 살아 있는 워커 작업을 일괄 failed로 바꾸지 않는다.
  중단 복구는 단일 실행 주체가 보장될 때만 단순 정리하거나 작업 소유권을 확인한다.

## 최종 코드에서 한 번 확인
1. docker compose config --quiet.
2. build/up → /health → 핵심 API 흐름을 최종 통합 확인과 합쳐 실행한다.
3. 저장한 결과의 영속화는 재기동 1회로 짧게 확인한다. 대규모 복구 시나리오는 생략한다.
   컨테이너 영속화 요구는 실제 Compose 재기동으로 확인하며 로컬 앱 재기동으로 대체하지 않는다.
Docker를 실행할 수 없으면 로컬 실행 범위만 확인하고 Docker·볼륨 검증은 미실행으로 적는다.

통과 후 관련 코드·설정이 바뀌지 않으면 build/up을 반복하지 않는다.
코드 변경 시 기존 컨테이너 결과를 새 코드의 증거로 쓰지 않는다. 필요하면 해당
서비스만 재빌드·재기동하고 바뀐 API만 확인한다. 전체 DB 초기화는 반복하지 않는다.
down -v, volume rm/prune 같은 기존 데이터 삭제 명령은 쓰지 않는다.
실행 스크립트는 없다. 패키지 설치·이미지 pull/build는 네트워크를 사용할 수 있다.
