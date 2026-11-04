---
name: sprint-docker-compose
description: 작은 웹 서비스에 최소 Dockerfile·compose·.env.example·헬스체크·빈 DB 초기화를 만들고 마지막에 한 번 기동 확인한다. Use for Dockerfile, docker compose, env vars, healthcheck, DB init.
license: Apache-2.0
---

# Sprint Docker Compose (LITE)

Modified adaptation, 2026-11-04. Source, revision, and changes: [ATTRIBUTION.md](ATTRIBUTION.md).
항상 LITE 모드로 동작한다. Docker 작업에 20분 이상 쓰지 않는다.

## 만들 파일
- Dockerfile: 실제 실행 명령, 고정 버전 베이스 이미지, 포트는 환경변수.
- compose.yaml (기존 파일명이 있으면 유지): 앱 + DB만. 워커가 필요하면 같은 이미지에 명령만 다르게.
  Redis·브로커·추가 DB는 넣지 않는다.
- .env.example: 코드가 실제로 읽는 변수만, 비밀값 칸은 비워 둔다. .env는 .gitignore.
- .dockerignore: .git, .env, 캐시 제외. 빌드에 필요한 데이터는 제외하지 않는다.

## 코드 쪽 필수
- 설정·비밀값은 환경변수로만 읽는다. 코드에 기본 비밀번호를 두지 않는다.
- 기동 시 스키마 생성 + 초기 계정·데이터 준비. 두 번 실행해도 안전하게(멱등).
- /health는 DB 연결까지 확인한다.
- DB 데이터는 named volume. 여러 프로세스가 DB를 초기화하면 한 곳(API)만 하게 한다.

## 확인 (마지막에 1회)
1. docker compose config --quiet
2. docker compose up --build → /health 200
3. 서버를 한 번 껐다 켜서 결과가 남는지 확인 (로컬 실행으로 대체 가능)
Docker를 쓸 수 없는 환경이면 로컬 실행으로 확인하고 "Docker 미확인"으로 기록한다.

## 하지 않는 것
compose 재시작 전체 시나리오, 이미지 digest 고정, 정교한 readiness 설계.
down -v, volume rm/prune 같은 데이터 삭제 명령은 쓰지 않는다.

이 Skill에 실행 스크립트는 없다. 이미지 pull/build는 네트워크를 쓸 수 있다.
