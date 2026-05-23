# ANAserver

ANA 동아리 서버(Coss) 리소스 사용량 모니터링 프로젝트입니다.
ANAGETDON 대회 당일 서버 트래픽 및 리소스 사용량을 수집하고 시각화합니다.
<img width="2424" height="1799" alt="image" src="https://github.com/user-attachments/assets/6999e76f-5baa-4456-9efd-62c2b1d9f5c1" />

## 기술 스택

- Prometheus: 서버 메트릭 수집 및 저장
- Node Exporter: 서버 리소스 데이터 노출
- Grafana: 수집된 데이터 시각화 대시보드
- Loki: nginx 로그 수집 및 저장
- Promtail: nginx 로그 파일을 Loki로 전송

## 대시보드

- Node Exporter Full: CPU, 메모리, 디스크, 네트워크 사용량 실시간 모니터링
- ANA Nginx 로그 분석: IP별 요청 수 Top10, HTTP Method별 요청 수, 로그 원본

## 실행 방법

```bash
docker compose up -d
```

## 접속 방법

포트터널링으로 접속합니다.

```bash
ssh -L 3001:localhost:3001 ana@anacnu.kr -p 8082
```

브라우저에서 `http://localhost:3001` 접속 후 로그인합니다.

## 수집 항목

### 서버 리소스 (Node Exporter)
- CPU 사용량
- 메모리 사용량
- 네트워크 트래픽
- 디스크 사용량

### nginx 로그 (Loki + Promtail)
- IP별 요청 수
- HTTP Method별 요청 수 (GET, POST 등)
- 로그 원본

## 로그 수집 경로

nginx proxy manager 로그를 수집합니다.

- 로그 파일 위치: `/home/ana/Desktop/ana/data/nginx-gui/data/logs/`
- 수집 대상: `proxy-host-1_access.log` (aoj.anacnu.kr)
