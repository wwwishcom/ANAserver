# ANAserver

ANA 동아리 서버(Coss) 리소스 사용량 모니터링 프로젝트입니다.

ANA 동아리에서 주최하는 프로그래밍 대회, ANAGETDON 당일 서버 트래픽 및 리소스 사용량을 수집하고 시각화합니다.

<img width="2879" height="1621" alt="image" src="https://github.com/user-attachments/assets/ee1ec815-34c9-4c91-b62b-9ccce2f77e3e" />


## 전체 구조
```
ANA 서버
└── Docker
      ├── Node Exporter  (센서)
      ├── Prometheus     (수집/저장)
      └── Grafana        (시각화)
```

## 기술 스택

- Prometheus: 서버 메트릭 수집 및 저장
- Node Exporter: 서버 리소스 데이터 노출
- Grafana: 수집된 데이터 시각화 대시보드

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

- CPU 사용량
- 메모리 사용량
- 네트워크 트래픽
- 디스크 사용량
