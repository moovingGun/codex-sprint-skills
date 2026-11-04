---
name: sprint-docker-compose
description: 작은 웹 서비스의 Docker Compose 구성에서 앱·DB·필요한 워커의 환경변수, readiness, 영속화와 재기동을 검증한다.
license: Apache-2.0
---

# Sprint Docker Compose

Modified adaptation, 2026-11-04. Source, revision, and changes: [ATTRIBUTION.md](ATTRIBUTION.md).

## 최소 실행 구성
기존 스택과 대회 실행 계약을 따른다. 기본 Compose 파일은 compose.yaml을 사용한다.
사용자의 기존 파일명을 불필요하게 바꾸지 않는다.
한 앱에 필요하지 않은 Redis·브로커·별도 DB를 추가하지 않는다.
워커가 필요하면 API와 같은 이미지의 다른 실행 명령을 사용할 수 있다.
구현하지 않은 내구성·자동 복구를 설정 파일이 보장하는 것처럼 설명하지 않는다.

## 생성·검토할 파일
- Dockerfile: 실제 런타임과 맞는 빌드·실행 명령, 고정된 의존성, 실행 포트.
- .dockerignore: .git, 비밀 .env, 자격증명, 의존성 캐시, 불필요한 데이터 제외.
  빌드에 필요한 공개 예제 설정·명세는 무심코 제외하지 않는다.
- compose.yaml: 앱과 필요한 서비스, 환경변수, healthcheck, named volume.
- .env.example: 실제 읽는 변수명, 안전한 예시, 필수/선택과 개발 기본값 설명.
- HOW_TO_RUN.md: 빌드·기동·DB 초기화·접속·검사·재기동·종료 명령.

## 설정과 보존
비밀값을 이미지·소스·커밋에 넣지 않는다. .env를 Git에서 제외한다.
공개 개발 기본값은 개발용임을 표시하고 운영 비밀값으로 재사용하지 않는다.
이미지는 명시 버전을 사용한다. 필요하면 digest도 고정한다.
DB 파일 또는 DB 데이터 디렉터리는 named volume에 둔다.
SQLite를 쓰는 다중 프로세스 구성은 잠금·동시 쓰기·재시도를 실제로 확인한다.
DB 포트는 필요한 경우에만 노출하고 개발 앱 포트는 기본적으로 loopback에 묶는다.
외부 접근이 요구되면 과제의 호스트/포트 계약에 맞춘다.

## 준비 상태와 작업 상태
DB healthcheck와 depends_on의 service_healthy로 초기 준비를 모델링한다.
컨테이너 started와 서비스 ready를 구분한다. DB가 나중에 끊기는 경우도 앱에서 처리한다.
healthcheck 명령의 실행 파일이 실제 이미지에 존재하는지 확인한다.
앱의 /health는 요구에 맞게 liveness/readiness 의미를 정의한다.
restart 정책은 작업의 정확히 한 번 실행이나 계산 중단 복구를 보장하지 않는다.
내구성이 필요하면 작업·입력 버전·상태를 DB에 저장하고 재시작 동작을 테스트한다.

## 검증
프로젝트 루트에서 docker compose config --quiet로 설정을 검증한다.
실제 환경을 평가한 compose config 전체 출력은 비밀값을 노출할 수 있어 피한다.
허용된 별도 테스트 프로젝트/볼륨에서 build → up → health → 핵심 API → restart →
데이터 유지와 작업 상태 확인을 수행한다. 빈 DB 초기화는 두 번 실행해도 안전한지 확인한다.
권한이 있는 환경에서만 실행하고 실패한 단계와 미실행 단계를 정확히 보고한다.
검증용 임시 자원의 식별자와 정리 방법을 기록한다.

down -v, volume rm/prune 등 데이터 삭제 명령을 재시작이나 검증에 섞지 않는다.
명시적으로 삭제가 요청되지 않은 기존 DB/볼륨은 보존한다.
이 Skill에 실행 스크립트는 없다. Docker build/pull 및 패키지 설치는 네트워크를
사용할 수 있으므로 해당 환경의 허용 범위를 따른다.
