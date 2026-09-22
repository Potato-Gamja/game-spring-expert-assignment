# 🎮 Game Spring Expert Assignment

Spring Boot를 활용하여 게임 서버의 기본 기능을 구현하는 프로젝트입니다.

MySQL을 이용한 데이터 영속화, Redis를 이용한 접속 상태 관리,
WebSocket을 이용한 실시간 통신 등을 학습하고 구현하는 것을 목표로 합니다.

---

## 🛠 Tech Stack

### Backend
- Java 21
- Spring Boot
- Spring Data JPA
- Spring WebSocket

### Database
- MySQL 8.0
- Redis 7

### Infrastructure
- Docker

### Tools
- IntelliJ IDEA
- Git / GitHub

---

## 📌 주요 기능

### Player

- 플레이어 닉네임 등록
- 닉네임 중복 검사
- 닉네임 유효성 검사

### World

- 월드 생성
- 월드 최대 생성 개수 제한
- 월드별 Seed 및 난이도 관리
- 동시성 상황에서의 월드 생성 제한

### Chat

- 채팅 메시지 MySQL 저장
- 최근 채팅 내역 조회
- 월드별 채팅 메시지 관리
- WebSocket을 이용한 실시간 채팅
- 같은 월드 사용자에게 채팅 Broadcast

### WebSocket

- WebSocket Handshake 시 사용자 및 월드 검증
- 월드별 WebSocket Session 관리
- 중복 접속 관리
- Message Router를 통한 메시지 타입별 처리

### Presence

- Redis Sorted Set을 이용한 접속 상태 관리
- 접속 / 종료 처리
- Ping/Pong 기반 Heartbeat
- TTL 기반 비정상 종료 사용자 처리

### Player Movement

- 플레이어 위치 및 회전 정보 수신
- 이동 데이터를 게임 엔진에 전달

### Online Users

- 현재 월드의 접속 사용자 조회
- 접속 중인 WebSocket Session 기준 사용자 목록 생성

---

## 🗄 Database

MySQL을 Docker로 실행합니다.

```bash
docker run --name game-mysql \
  -e MYSQL_ROOT_PASSWORD=1234 \
  -e MYSQL_DATABASE=game \
  -p 13306:3306 \
  -d mysql:8.0
